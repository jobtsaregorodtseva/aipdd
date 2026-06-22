// app/learn/page.js
import Header from '../../components/Header';

// Заглушка экрана обучения. На Этапе 2 здесь появятся:
// карта-путь тем (листается), адаптивная тренировка, работа над ошибками.
const THEMES = [
  'Общие положения и термины', 'Обязанности водителя и документы',
  'Спецсигналы и приоритет МТС', 'Светофоры и регулировщик', 'Дорожные знаки',
  'Дорожная разметка', 'Начало движения и маневрирование', 'Расположение ТС и скорость',
  'Обгон и встречный разъезд', 'Остановка и стоянка', 'Проезд перекрёстков',
  'Пешеходные переходы', 'Ж/д переезды, магистрали, жилые зоны', 'Внешние приборы и сигналы',
  'Буксировка, перевозка людей и грузов', 'Велосипеды, мопеды, СИМ',
  'Неисправности и допуск ТС', 'Первая помощь', 'Ответственность водителя',
];

export default function Learn() {
  return (
    <>
      <Header />
      <main className="container" style={{ padding: '40px 0 80px' }}>
        <span className="badge" style={{ marginBottom: 14 }}>Этап 2 · скоро здесь появится тренировка</span>
        <h1 style={{ marginBottom: 8 }}>Твой путь обучения</h1>
        <p className="muted" style={{ maxWidth: 560, marginBottom: 32 }}>
          Карта тем как маршрут: станции открываются по мере освоения. Сейчас это превью структуры —
          адаптивная тренировка и работа над ошибками подключатся на следующем этапе.
        </p>

        {/* карта-путь тем (превью) */}
        <div style={{ display: 'flex', flexDirection: 'column', gap: 0 }}>
          {THEMES.map((t, i) => (
            <div key={t} style={{ display: 'flex', alignItems: 'center', gap: 16 }}>
              <div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center' }}>
                <div style={{
                  width: 44, height: 44, borderRadius: '50%',
                  display: 'grid', placeItems: 'center',
                  background: i < 2 ? 'var(--blue)' : 'var(--blue-soft)',
                  color: i < 2 ? '#fff' : 'var(--blue)',
                  fontFamily: 'var(--font-display)', fontWeight: 800,
                  border: '2px solid ' + (i < 2 ? 'var(--blue)' : 'var(--blue-line)'),
                }}>{i + 1}</div>
                {i < THEMES.length - 1 && (
                  <div style={{ width: 2, height: 22, background: 'var(--blue-line)' }} />
                )}
              </div>
              <div style={{
                flex: 1, padding: '12px 16px', borderRadius: 'var(--r-sm)',
                background: 'var(--surface)', border: '1px solid var(--line)',
                marginBottom: i < THEMES.length - 1 ? 8 : 0,
              }}>
                <span style={{ fontWeight: 600 }}>{t}</span>
              </div>
            </div>
          ))}
        </div>
      </main>
    </>
  );
}
