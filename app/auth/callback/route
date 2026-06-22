// app/auth/callback/route.js
// Принимает редирект от Google/Яндекс после входа, обменивает код на сессию.
import { NextResponse } from 'next/server';
import { createClient } from '../../../lib/supabase-server';

export async function GET(request) {
  const { searchParams, origin } = new URL(request.url);
  const code = searchParams.get('code');

  if (code) {
    const supabase = createClient();
    await supabase.auth.exchangeCodeForSession(code);
  }
  return NextResponse.redirect(`${origin}/learn`);
}
