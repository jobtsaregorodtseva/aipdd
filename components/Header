// components/Header.js
'use client';
import Link from 'next/link';

export default function Header() {
  return (
    <header style={{
      borderBottom: '1px solid var(--line)',
      background: 'var(--surface)',
      position: 'sticky', top: 0, zIndex: 50,
    }}>
      <div className="container" style={{
        display: 'flex', alignItems: 'center', justifyContent: 'space-between',
        height: 64,
      }}>
        <Link href="/" style={{
          display: 'flex', alignItems: 'center', gap: 10,
          fontFamily: 'var(--font-display)', fontWeight: 800, fontSize: 20,
          color: 'var(--ink)', textDecoration: 'none',
        }}>
          <span aria-hidden style={{
            display: 'inline-flex', alignItems: 'center', justifyContent: 'center',
            width: 32, height: 32, borderRadius: 9,
            background: 'var(--blue)', color: '#fff', fontSize: 16,
          }}>П</span>
          ПДД <span style={{ color: 'var(--blue)' }}>AI</span>
        </Link>
        <nav style={{ display: 'flex', alignItems: 'center', gap: 8 }}>
          <Link href="/learn" className="btn btn-ghost" style={{ padding: '9px 16px', fontSize: 14 }}>
            Учиться
          </Link>
          <Link href="/login" className="btn btn-primary" style={{ padding: '9px 18px', fontSize: 14 }}>
            Войти
          </Link>
        </nav>
      </div>
    </header>
  );
}
