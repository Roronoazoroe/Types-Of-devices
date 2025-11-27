<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Poco F7 Ultra</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    body {
      background: #050816;
      color: #f5f5f5;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      padding: 16px 8%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid rgba(255, 255, 255, 0.06);
      position: sticky;
      top: 0;
      backdrop-filter: blur(12px);
      background: rgba(5, 8, 22, 0.9);
      z-index: 10;
    }

    .logo {
      font-weight: 700;
      letter-spacing: 0.08em;
      font-size: 0.9rem;
      text-transform: uppercase;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .logo-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background: linear-gradient(135deg, #ffcc33, #ff6a00);
      display: inline-block;
    }

    .nav {
      display: flex;
      gap: 20px;
      font-size: 0.85rem;
      text-transform: uppercase;
      opacity: 0.8;
    }

    .nav a {
      text-decoration: none;
      color: inherit;
      position: relative;
      padding-bottom: 2px;
    }

    .nav a::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: 0;
      width: 0;
      height: 2px;
      background: linear-gradient(135deg, #ffcc33, #ff6a00);
      transition: width 0.2s ease;
    }

    .nav a:hover::after {
      width: 100%;
    }

    main {
      flex: 1;
      padding: 40px 8% 60px;
      display: grid;
      grid-template-columns: minmax(0, 1.3fr) minmax(0, 1fr);
      gap: 40px;
      align-items: center;
    }

    @media (max-width: 900px) {
      main {
        grid-template-columns: 1fr;
        padding-top: 24px;
      }
    }

    .hero-tag {
      font-size: 0.8rem;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      color: #ffcc33;
      margin-bottom: 12px;
    }

    h1 {
      font-size: clamp(2.4rem, 4vw, 3.4rem);
      line-height: 1.1;
      margin-bottom: 14px;
    }

    h1 span {
      background: linear-gradient(135deg, #ffcc33, #ff6a00);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .hero-subtitle {
      font-size: 1rem;
      max-width: 32rem;
      color: rgba(245, 245, 245, 0.8);
      line-height: 1.6;
      margin-bottom: 22px;
    }

    .hero-specs {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 24px;
    }

    .chip {
      padding: 6px 12px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.14);
      font-size: 0.78rem;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      opacity: 0.9;
    }

    .actions {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 28px;
    }

    .btn-primary,
    .btn-ghost {
      padding: 10px 20px;
      border-radius: 999px;
      border: none;
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      cursor: pointer;
    }

    .btn-primary {
      background: linear-gradient(135deg, #ffcc33, #ff6a00);
      color: #050816;
      font-weight: 600;
    }

    .btn-ghost {
      background: transparent;
      border: 1px solid rgba(255, 255, 255, 0.25);
      color: #f5f5f5;
    }

    .meta {
      display: flex;
      gap: 24px;
      font-size: 0.8rem;
      text-transform: uppercase;
      opacity: 0.75;
    }

    .meta span {
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .meta span::before {
      content: "•";
      font-size: 1rem;
      line-height: 0;
    }

    .phone-card {
      border-radius: 26px;
      padding: 24px;
      background: radial-gradient(circle at 0 0, rgba(255, 204, 51, 0.1), transparent 55%),
                  radial-gradient(circle at 100% 100%, rgba(255, 106, 0, 0.18), transparent 55%),
                  #070b1e;
      border: 1px solid rgba(255, 255, 255, 0.06);
      position: relative;
      overflow: hidden;
      max-width: 420px;
      margin-inline: auto;
    }

    .phone-outline {
      width: 200px;
      height: 380px;
      border-radius: 32px;
      border: 2px solid rgba(255, 255, 255, 0.12);
      margin: 0 auto;
      position: relative;
      padding: 18px 12px;
      display: flex;
      justify-content: center;
      align-items: center;
      backdrop-filter: blur(12px);
      background: radial-gradient(circle at 20% 0%, rgba(255, 255, 255, 0.12), transparent 60%);
    }

    .phone-screen {
      width: 100%;
      height: 100%;
      border-radius: 22px;
      background: radial-gradient(circle at 0 0, #ffcc33, transparent 70%),
                  radial-gradient(circle at 100% 100%, #ff6a00, transparent 70%),
                  linear-gradient(145deg, #1a1a1a, #000000);
      position: relative;
      overflow: hidden;
    }

    .phone-notch {
      width: 60px;
      height: 16px;
      border-radius: 0 0 12px 12px;
      background: rgba(0, 0, 0, 0.85);
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
    }

    .phone-glow {
      position: absolute;
      inset: -40px;
      border-radius: inherit;
      background: radial-gradient(circle at 50% -20%, rgba(255, 255, 255, 0.2), transparent 65%);
      opacity: 0.4;
      mix-blend-mode: screen;
      pointer-events: none;
    }

    .phone-footer {
      margin-top: 16px;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      font-size: 0.78rem;
      color: rgba(245, 245, 245, 0.84);
    }

    .phone-footer h2 {
      font-size: 1.1rem;
      margin-bottom: 4px;
    }

    .badge {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      padding: 4px 10px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.24);
    }

    footer {
      padding: 16px 8%;
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      opacity: 0.6;
      border-top: 1px solid rgba(255, 255, 255, 0.06);
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">
      <span class="logo-dot"></span>
      Poco F7 Ultra
    </div>
    <nav class="nav">
      <a href="#overview">Overview</a>
      <a href="#specs">Specs</a>
      <a href="#buy">Buy</a>
    </nav>
  </header>

  <main>
    <section>
      <p class="hero-tag">Introducing</p>
      <h1><span>Poco F7 Ultra</span> – Power Meets Style</h1>
      <p class="hero-subtitle">
        Poco F7 Ultra pushes performance, display, and battery life to the next level.
        Built for gamers, creators, and heavy multitaskers who want flagship power
        without the flagship price.
      </p>

      <div class="hero-specs" id="specs">
        <span class="chip">120Hz AMOLED Display</span>
        <span class="chip">Flagship-grade Chipset</span>
        <span class="chip">5,000 mAh Battery</span>
        <span class="chip">Ultra-Fast Charging</span>
        <span class="chip">Pro-Grade Triple Camera</span>
      </div>

      <div class="actions" id="buy">
        <button class="btn-primary">Pre-order</button>
        <button class="btn-ghost">View Full Specs</button>
      </div>

      <div class="meta" id="overview">
        <span>Designed for Performance</span>
        <span>Optimized for Gaming</span>
        <span>Crafted for Everyday Use</span>
      </div>
    </section>

    <aside>
      <div class="phone-card">
        <div class="phone-outline">
          <div class="phone-screen">
            <div class="phone-notch"></div>
            <div class="phone-glow"></div>
          </div>
        </div>
        <div class="phone-footer">
          <div>
            <h2>Poco F7 Ultra</h2>
            <p>Ultra-fast. Ultra-bright. Ultra-you.</p>
          </div>
          <span class="badge">Ultra Edition</span>
        </div>
      </div>
    </aside>
  </main>

  <footer>
    Poco F7 Ultra · Concept landing page
  </footer>
</body>
</html>
