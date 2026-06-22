// app/login/page.js
'use client';
import { useState } from 'react';
import Link from 'next/link';
import { createClient } from '../../lib/supabase-browser';
import Mascot from '../../components/Mascot';

export default function Login() {
  const [step, setStep] = useState('email');   // email → code
  const [email, setEmail] = useState('');
  const [code, setCode] = useState('');
  const [msg, setMsg] = useState('');
  const [loading, setLoading] = useState(false);
  const supabase = createClient();

  async function sendCode(e) {
    e.preventDefault();
    setLoading(true); setMsg('');
    const { error } = await supabase.auth.signInWithOtp({
      email,
      options: { shouldCreateUser: true },
    });
    setLoading(false);
    if (error) setMsg('Не удалось отправить код: ' + error.message);
    else { setStep('code'); setMsg(''); }
  }

  async function verify(e) {
    e.preventDefault();
    setLoading(true); setMsg('');
    const { error } = await supabase.auth.verifyOtp({
      email, token: code, type: 'email',
    });
    setLoading(false);
    if (error) setMsg('Неверный код. Проверь почту и попробуй снова.');
    else window.location.href = '/learn';
  }

  async function oauth(provider) {
    await supabase.auth.signInWithOAuth({
      provider,
      options: { redirectTo: `${window.location.origin}/auth/callback` },
    });
  }

  return (
    <main style={{ minHeight: '100vh', display: 'grid', placeItems: 'center', padding: 20 }}>
      <div className="card" style={{ width: '100%', maxWidth: 420 }}>
        <div className="center" style={{ marginBottom: 8 }}>
          <Mascot size={84} state="think" />
        </div>
        <h2 className="center" style={{ marginBottom: 4 }}>Вход в ПДД AI</h2>
        <p className="center muted" style={{ marginTop: 0, marginBottom: 24, fontSize: 15 }}>
          {step === 'email' ? 'Войдём по коду на почту — без пароля' : `Код отправлен на ${email}`}
        </p>

        {step === 'email' ? (
          <form onSubmit={sendCode} className="stack">
            <input
              className="input" type="email" required
              placeholder="твоя почта"
              value={email} onChange={(e) => setEmail(e.target.value)}
            />
            <button className="btn btn-primary btn-block" disabled={loading}>
              {loading ? 'Отправляю…' : 'Получить код'}
            </button>
          </form>
        ) : (
          <form onSubmit={verify} className="stack">
            <input
              className="input center" inputMode="numeric"
              placeholder="код из письма" style={{ letterSpacing: 4, fontSize: 20 }}
              value={code} onChange={(e) => setCode(e.target.value)}
            />
            <button className="btn btn-primary btn-block" disabled={loading}>
              {loading ? 'Проверяю…' : 'Войти'}
            </button>
            <button type="button" className="btn btn-ghost btn-block"
              onClick={() => { setStep('email'); setCode(''); }}>
              Изменить почту
            </button>
          </form>
        )}

        {msg && <p style={{ color: 'var(--warn)', fontSize: 14, marginTop: 14 }}>{msg}</p>}

        {step === 'email' && (
          <>
            <div style={{ display: 'flex', alignItems: 'center', gap: 12, margin: '22px 0', color: 'var(--ink-faint)', fontSize: 13 }}>
              <span style={{ flex: 1, height: 1, background: 'var(--line)' }} />
              или
              <span style={{ flex: 1, height: 1, background: 'var(--line)' }} />
            </div>
            <div className="stack">
              <button className="btn btn-ghost btn-block" onClick={() => oauth('google')}>
                Войти через Google
              </button>
              <button className="btn btn-ghost btn-block" onClick={() => oauth('yandex')}>
                Войти через Яндекс
              </button>
            </div>
          </>
        )}

        <p className="center muted" style={{ fontSize: 13, marginTop: 22, marginBottom: 0 }}>
          <Link href="/">← На главную</Link>
        </p>
      </div>
    </main>
  );
}
