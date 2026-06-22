// app/layout.js
import '../styles/globals.css';

export const metadata = {
  title: 'ПДД AI — умная подготовка к экзамену ГИБДД',
  description: 'Адаптивный тренажёр теории ПДД (категории A, B, M): подстраивается под твои слабые темы и объясняет каждую ошибку.',
};

export const viewport = {
  width: 'device-width',
  initialScale: 1,
  themeColor: '#1565D8',
};

export default function RootLayout({ children }) {
  return (
    <html lang="ru">
      <head>
        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link rel="preconnect" href="https://fonts.gstatic.com" crossOrigin="anonymous" />
        <link
          href="https://fonts.googleapis.com/css2?family=Manrope:wght@600;700;800&family=Inter:wght@400;500;600&display=swap"
          rel="stylesheet"
        />
      </head>
      <body>{children}</body>
    </html>
  );
}
