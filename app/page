// app/page.js
import Link from 'next/link';
import Header from '../components/Header';
import Mascot from '../components/Mascot';

export default function Home() {
  return (
    <>
      <Header />

      {/* HERO */}
      <section style={{ padding: '64px 0 48px' }}>
        <div className="container" style={{
          display: 'grid', gridTemplateColumns: '1.3fr 1fr', gap: 40, alignItems: 'center',
        }}>
          <div>
            <span className="badge" style={{ marginBottom: 20 }}>Категории A · B · M</span>
            <h1 style={{ marginBottom: 16 }}>
              Подготовка к ПДД, которая <span style={{ color: 'var(--blue)' }}>подстраивается под тебя</span>
            </h1>
            <p style={{ fontSize: 19, color: 'var(--ink-soft)', maxWidth: 520, marginBottom: 28 }}>
              Тренажёр находит твои слабые темы и объясняет каждую ошибку — почему так,
              на какой пункт ПДД опирается и с чем её путают. Не зубрёжка, а понимание.
            </p>
            <div style={{ display: 'flex', gap: 12, flexWrap: 'wrap' }}>
              <Link href="/learn" className="btn btn-primary">Начать бесплатно</Link>
              <Link href="/reference" className="btn btn-ghost">Справочник знаков</Link>
            </div>
            <p className="muted" style={{ fontSize: 14, marginTop: 16 }}>
              Первые темы — бесплатно, без карты. Полный доступ — разовый платёж, без подписки.
            </p>
          </div>
          <div className="center">
            <Mascot size={180} state="happy" />
          </div>
        </div>
      </section>

      {/* ТРИ ОПОРЫ ПРОДУКТА */}
      <section style={{ padding: '32px 0 72px' }}>
        <div className="container" style={{
          display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: 20,
        }}>
          {[
            { t: 'Адаптация по темам', d: 'Маршрут пересобирается после каждого ответа — ты всегда работаешь над тем, что проседает.' },
            { t: 'Разбор каждой ошибки', d: 'AI объясняет простыми словами, ссылается на пункт ПДД и показывает типичную ловушку.' },
            { t: 'Честная готовность', d: 'Видишь не «процент пройдено», а реальную готовность к экзамену по слабым темам и симуляциям.' },
          ].map((x) => (
            <div className="card" key={x.t}>
              <h3 style={{ color: 'var(--blue-deep)' }}>{x.t}</h3>
              <p className="muted" style={{ margin: 0 }}>{x.d}</p>
            </div>
          ))}
        </div>
      </section>

      <footer style={{ borderTop: '1px solid var(--line)', padding: '28px 0' }}>
        <div className="container muted" style={{ fontSize: 14, display: 'flex', justifyContent: 'space-between', flexWrap: 'wrap', gap: 12 }}>
          <span>ПДД AI — тренажёр для самоподготовки. Не является автошколой.</span>
          <span>© {new Date().getFullYear()}</span>
        </div>
      </footer>
    </>
  );
}
