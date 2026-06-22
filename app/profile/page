// app/profile/page.js
'use client';
import { useEffect, useState } from 'react';
import Link from 'next/link';
import Header from '../../components/Header';
import { createClient } from '../../lib/supabase-browser';

export default function Profile() {
  const [user, setUser] = useState(undefined); // undefined=загрузка, null=не вошёл
  const supabase = createClient();

  useEffect(() => {
    supabase.auth.getUser().then(({ data }) => setUser(data.user ?? null));
  }, []);

  async function logout() {
    await supabase.auth.signOut();
    window.location.href = '/';
  }

  return (
    <>
      <Header />
      <main className="container" style={{ padding: '40px 0 80px', maxWidth: 560 }}>
        <h1>Профиль</h1>
        {user === undefined && <p className="muted">Загрузка…</p>}
        {user === null && (
          <div className="card">
            <p>Ты ещё не вошёл.</p>
            <Link href="/login" className="btn btn-primary">Войти</Link>
          </div>
        )}
        {user && (
          <div className="card stack">
            <div>
              <div className="muted" style={{ fontSize: 13 }}>Почта</div>
              <div style={{ fontWeight: 600 }}>{user.email}</div>
            </div>
            <button className="btn btn-ghost" onClick={logout}>Выйти</button>
          </div>
        )}
      </main>
    </>
  );
}
