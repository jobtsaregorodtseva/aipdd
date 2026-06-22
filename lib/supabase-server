// lib/supabase-server.js
// Клиент Supabase для серверной части (server components, route handlers).
// Работает с cookie, чтобы сессия пользователя жила между запросами.
import { createServerClient } from '@supabase/ssr';
import { cookies } from 'next/headers';

export function createClient() {
  const cookieStore = cookies();
  return createServerClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY,
    {
      cookies: {
        getAll() {
          return cookieStore.getAll();
        },
        setAll(cookiesToSet) {
          try {
            cookiesToSet.forEach(({ name, value, options }) =>
              cookieStore.set(name, value, options)
            );
          } catch {
            // вызов из server component — игнорируем, обновит middleware
          }
        },
      },
    }
  );
}
