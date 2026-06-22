// components/Mascot.js
// Маскот ПДД AI — дружелюбный светофор. Временная SVG-версия
// (позже заменится на фирменную рисовку / анимацию).
// state: 'idle' | 'happy' | 'think'
export default function Mascot({ size = 120, state = 'idle' }) {
  const eye = state === 'happy' ? 3 : 4;
  return (
    <svg width={size} height={size * 1.3} viewBox="0 0 100 130" fill="none" aria-hidden>
      {/* корпус */}
      <rect x="22" y="8" width="56" height="104" rx="28" fill="#16202E" />
      <rect x="26" y="12" width="48" height="96" rx="24" fill="#0C3F86" />
      {/* три огонька */}
      <circle cx="50" cy="34" r="11" fill={state === 'warn' ? '#C2410C' : '#9FB4CE'} opacity={state === 'warn' ? 1 : .35} />
      <circle cx="50" cy="60" r="11" fill={state === 'think' ? '#E8A317' : '#9FB4CE'} opacity={state === 'think' ? 1 : .35} />
      <circle cx="50" cy="86" r="11" fill={state === 'happy' ? '#1E9E62' : '#9FB4CE'} opacity={state === 'happy' ? 1 : .35} />
      {/* глазки на среднем огоньке */}
      <circle cx="45" cy="59" r={eye} fill="#16202E" />
      <circle cx="55" cy="59" r={eye} fill="#16202E" />
      {state === 'happy' && (
        <path d="M44 64 Q50 69 56 64" stroke="#16202E" strokeWidth="2" strokeLinecap="round" fill="none" />
      )}
      {/* ножки */}
      <rect x="38" y="112" width="7" height="14" rx="3.5" fill="#16202E" />
      <rect x="55" y="112" width="7" height="14" rx="3.5" fill="#16202E" />
    </svg>
  );
}
