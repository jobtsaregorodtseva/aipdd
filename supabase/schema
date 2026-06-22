-- ============================================================
-- ПДД AI — схема базы данных (Supabase / PostgreSQL)
-- Выполни этот SQL в Supabase: проект → SQL Editor → New query →
-- вставь весь файл → Run. Создаст все таблицы и правила доступа.
-- ============================================================

-- 1. ПРОФИЛИ ПОЛЬЗОВАТЕЛЕЙ
-- Расширяет встроенную таблицу auth.users (её Supabase ведёт сам).
create table if not exists profiles (
  id          uuid primary key references auth.users(id) on delete cascade,
  email       text,
  display_name text,
  category    text default 'B',          -- выбранная категория A/B/M
  is_paid     boolean default false,      -- купил ли полный доступ
  paid_at     timestamptz,
  exam_date   date,                       -- дата экзамена (если указал)
  created_at  timestamptz default now()
);

-- 2. ПРОГРЕСС ПО ТЕМАМ (ядро адаптации)
-- На каждого пользователя — строка по каждой из 19 тем.
create table if not exists theme_progress (
  id          bigint generated always as identity primary key,
  user_id     uuid references auth.users(id) on delete cascade,
  theme       text not null,              -- одна из 19 канонических тем
  score       int default 0,              -- балл уверенности 0..100
  seen        int default 0,              -- сколько вопросов по теме отвечено
  last_seen   timestamptz,
  unique (user_id, theme)
);

-- 3. ОЧЕРЕДЬ ИНТЕРВАЛЬНОГО ПОВТОРЕНИЯ
-- Проваленные вопросы, которые надо вернуть через интервал.
create table if not exists review_queue (
  id          bigint generated always as identity primary key,
  user_id     uuid references auth.users(id) on delete cascade,
  question_id text not null,              -- id вопроса (t1_q5 и т.п.)
  stage       int default 0,              -- этап 0..3 (10мин→1д→3д→7д)
  due_at      timestamptz not null,       -- когда вернуть
  unique (user_id, question_id)
);

-- 4. ЛОГ ОТВЕТОВ (для аналитики и уточнения сложности)
create table if not exists answer_log (
  id          bigint generated always as identity primary key,
  user_id     uuid references auth.users(id) on delete cascade,
  question_id text not null,
  theme       text,
  is_correct  boolean,
  used_hint   boolean default false,
  mode        text,                       -- learn / review / exam / free
  answered_at timestamptz default now()
);

-- 5. ИСТОРИЯ СИМУЛЯЦИЙ ЭКЗАМЕНА
create table if not exists simulations (
  id          bigint generated always as identity primary key,
  user_id     uuid references auth.users(id) on delete cascade,
  score       int,                        -- верных из 20
  passed      boolean,                    -- <=2 ошибок
  finished_at timestamptz default now()
);

-- ============================================================
-- БЕЗОПАСНОСТЬ: Row Level Security
-- Каждый пользователь видит и меняет ТОЛЬКО свои данные.
-- ============================================================
alter table profiles       enable row level security;
alter table theme_progress enable row level security;
alter table review_queue   enable row level security;
alter table answer_log     enable row level security;
alter table simulations    enable row level security;

-- профиль: владелец читает/пишет свой
create policy "own profile read"  on profiles for select using (auth.uid() = id);
create policy "own profile write" on profiles for update using (auth.uid() = id);
create policy "own profile insert" on profiles for insert with check (auth.uid() = id);

-- остальные таблицы: владелец делает всё со своими строками
create policy "own progress" on theme_progress for all using (auth.uid() = user_id) with check (auth.uid() = user_id);
create policy "own review"   on review_queue   for all using (auth.uid() = user_id) with check (auth.uid() = user_id);
create policy "own answers"  on answer_log     for all using (auth.uid() = user_id) with check (auth.uid() = user_id);
create policy "own sims"     on simulations    for all using (auth.uid() = user_id) with check (auth.uid() = user_id);

-- ============================================================
-- АВТОСОЗДАНИЕ ПРОФИЛЯ при регистрации нового пользователя
-- ============================================================
create or replace function handle_new_user()
returns trigger as $$
begin
  insert into profiles (id, email)
  values (new.id, new.email)
  on conflict (id) do nothing;
  return new;
end;
$$ language plpgsql security definer;

drop trigger if exists on_auth_user_created on auth.users;
create trigger on_auth_user_created
  after insert on auth.users
  for each row execute function handle_new_user();
