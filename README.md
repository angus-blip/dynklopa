[dynk-redesign-v6.html](https://github.com/user-attachments/files/27185892/dynk-redesign-v6.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DYNK — Redesign v3</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;9..144,400;9..144,500;9..144,600&family=Geist:wght@300;400;500;600;700&family=Geist+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg-page: #F4F1EC; --bg-canvas: #FAFAF7; --bg-card: #FFFFFF; --bg-subtle: #F5F4EF; --bg-inverse: #0B0B0B;
  --border: #EAE7DF; --border-strong: #D8D4CA;
  --text-primary: #0B0B0B; --text-secondary: #6B6B66; --text-tertiary: #9B9B94; --text-inverse: #FFFFFF;
  --accent: #EC6A1C; --accent-soft: #FFEDD9;
  --success: #15803D; --success-soft: #DCFCE7;
  --danger: #B91C1C; --danger-soft: #FEE2E2;
  --info: #1D4ED8; --info-soft: #DBEAFE;
  --purple: #6D28D9; --purple-soft: #EDE9FE;
  --gold: #B45309; --gold-soft: #FEF3C7;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: 'Geist', sans-serif; background: var(--bg-page); color: var(--text-primary); padding: 60px 40px; -webkit-font-smoothing: antialiased; font-feature-settings: "ss01"; }
.page-header { max-width: 1600px; margin: 0 auto 60px; display: flex; justify-content: space-between; align-items: flex-end; flex-wrap: wrap; gap: 20px; padding-bottom: 32px; border-bottom: 1px solid var(--border-strong); }
.page-title { font-family: 'Fraunces', serif; font-size: 56px; font-weight: 400; letter-spacing: -0.02em; line-height: 1; }
.page-title em { font-style: italic; font-weight: 300; }
.page-title .v { font-size: 28px; color: var(--accent); margin-left: 6px; font-family: 'Geist Mono', monospace; }
.page-meta { display: flex; gap: 32px; font-size: 13px; color: var(--text-secondary); }
.page-meta strong { color: var(--text-primary); font-weight: 500; display: block; margin-top: 4px; font-size: 14px; }
.section-heading { max-width: 1600px; margin: 48px auto 24px; font-family: 'Fraunces', serif; font-size: 22px; font-weight: 400; letter-spacing: -0.02em; color: var(--text-secondary); padding-left: 4px; display: flex; align-items: baseline; gap: 12px; }
.section-heading em { font-style: italic; }
.section-heading .count { font-family: 'Geist Mono', monospace; font-size: 11px; color: var(--text-tertiary); letter-spacing: 0.08em; }
.screens-grid { max-width: 1600px; margin: 0 auto; display: grid; grid-template-columns: repeat(auto-fit, minmax(340px, 1fr)); gap: 48px 32px; justify-items: center; }
.screen-wrap { display: flex; flex-direction: column; align-items: center; gap: 16px; }
.screen-label { font-size: 11px; font-weight: 500; letter-spacing: 0.12em; text-transform: uppercase; color: var(--text-tertiary); text-align: center; }
.screen-label .new { display: inline-block; background: var(--accent); color: white; padding: 2px 6px; border-radius: 4px; font-size: 9px; letter-spacing: 0.08em; margin-left: 6px; }
.phone { width: 340px; height: 720px; background: var(--bg-canvas); border-radius: 48px; box-shadow: 0 0 0 10px #1a1a1a, 0 0 0 12px #2d2d2d, 0 30px 60px -20px rgba(0,0,0,0.3); overflow: hidden; position: relative; display: flex; flex-direction: column; }
.notch { position: absolute; top: 10px; left: 50%; transform: translateX(-50%); width: 100px; height: 26px; background: #000; border-radius: 18px; z-index: 10; }
.status-bar { height: 44px; display: flex; align-items: center; justify-content: space-between; padding: 0 28px 0 24px; font-size: 13px; font-weight: 600; flex-shrink: 0; }
.status-icons { display: flex; gap: 5px; align-items: center; }
.screen-body { flex: 1; overflow: hidden; display: flex; flex-direction: column; }
.screen-scroll { flex: 1; overflow-y: auto; padding: 8px 20px 80px; scrollbar-width: none; }
.screen-scroll::-webkit-scrollbar { display: none; }
.wallet-bar { display: flex; align-items: center; gap: 8px; padding: 12px 20px 8px; border-bottom: 1px solid var(--border); background: var(--bg-canvas); }
.wallet-pills { flex: 1; display: flex; gap: 6px; overflow-x: auto; scrollbar-width: none; }
.wallet-pills::-webkit-scrollbar { display: none; }
.wallet-pill { padding: 6px 12px; border-radius: 100px; font-size: 12px; font-weight: 500; color: var(--text-secondary); white-space: nowrap; cursor: pointer; display: flex; align-items: center; gap: 6px; border: 1px solid transparent; }
.wallet-pill.active { background: var(--bg-card); border-color: var(--border-strong); color: var(--text-primary); }
.wallet-pill .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent); }
.wallet-pill.savings .dot { background: var(--info); }
.wallet-pill.nft .dot { background: var(--gold); }
.wallet-add { width: 28px; height: 28px; border-radius: 50%; background: var(--bg-card); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; cursor: pointer; flex-shrink: 0; }
.app-header { display: flex; justify-content: space-between; align-items: center; padding: 12px 0 20px; }
.hello { font-family: 'Fraunces', serif; font-size: 26px; font-weight: 400; letter-spacing: -0.02em; line-height: 1.1; }
.hello em { font-style: italic; font-weight: 300; }
.sub-label { font-size: 12px; color: var(--text-secondary); margin-top: 2px; }
.header-actions { display: flex; gap: 8px; align-items: center; }
.icon-btn { width: 38px; height: 38px; border-radius: 50%; background: var(--bg-card); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; cursor: pointer; }
.avatar { width: 38px; height: 38px; border-radius: 50%; background: linear-gradient(135deg, #EC6A1C, #F59E3B); color: white; display: flex; align-items: center; justify-content: center; font-weight: 600; font-size: 13px; }
.card { background: var(--bg-card); border: 1px solid var(--border); border-radius: 22px; padding: 20px; }
.label-xs { font-size: 11px; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; color: var(--text-tertiary); }
.section-title { font-family: 'Fraunces', serif; font-size: 18px; font-weight: 400; letter-spacing: -0.01em; margin: 24px 0 12px; display: flex; justify-content: space-between; align-items: baseline; }
.section-title em { font-style: italic; font-weight: 300; }
.section-title .see-all { font-family: 'Geist', sans-serif; font-size: 12px; color: var(--accent); font-weight: 500; }
.balance-inline { padding: 20px 0 12px; }
.balance-inline-label { font-size: 12px; color: var(--text-secondary); }
.balance-inline-amount { font-family: 'Fraunces', serif; font-size: 46px; font-weight: 300; letter-spacing: -0.03em; line-height: 1; margin-top: 6px; }
.balance-inline-amount .cents { font-size: 28px; color: var(--text-secondary); }
.balance-inline-amount .unit { font-size: 18px; color: var(--text-secondary); margin-left: 6px; font-family: 'Geist', sans-serif; }
.balance-change { display: inline-flex; align-items: center; gap: 5px; margin-top: 8px; font-size: 12px; color: var(--success); font-weight: 500; }
.quick-actions-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 8px; margin-top: 20px; }
.qa-btn { background: var(--bg-card); border: 1px solid var(--border); border-radius: 14px; padding: 12px 6px 10px; display: flex; flex-direction: column; align-items: center; gap: 6px; cursor: pointer; font-size: 11px; font-weight: 500; color: var(--text-primary); font-family: inherit; }
.qa-btn .ic-wrap { width: 32px; height: 32px; border-radius: 10px; background: var(--bg-subtle); display: flex; align-items: center; justify-content: center; }
.qa-btn .ic-wrap.accent { background: var(--accent-soft); color: var(--accent); }
.qa-btn .ic-wrap.info { background: var(--info-soft); color: var(--info); }
.holding-row { display: flex; align-items: center; gap: 14px; padding: 14px 4px; border-bottom: 1px solid var(--border); }
.holding-row:last-child { border-bottom: none; }
.token-icon { width: 40px; height: 40px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700; font-size: 15px; flex-shrink: 0; color: white; }
.token-dynk { background: linear-gradient(135deg, #EC6A1C, #F59E3B); }
.token-sol { background: linear-gradient(135deg, #9945FF, #14F195); font-size: 11px; }
.token-usdc { background: #2775CA; font-size: 11px; }
.token-btc { background: #F7931A; }
.token-eth { background: linear-gradient(135deg, #627EEA, #3C4FB0); font-size: 11px; }
.holding-info { flex: 1; }
.holding-name { font-size: 14px; font-weight: 500; }
.holding-sub { font-size: 12px; color: var(--text-secondary); margin-top: 1px; }
.holding-value { text-align: right; }
.holding-amt { font-size: 14px; font-weight: 500; font-feature-settings: "tnum"; }
.holding-usd { font-size: 12px; color: var(--text-secondary); margin-top: 1px; font-feature-settings: "tnum"; }
.cold-wallet-card { background: linear-gradient(135deg, #0B0B0B, #2a2a2a); color: white; border-radius: 22px; padding: 20px; position: relative; overflow: hidden; margin-top: 16px; cursor: pointer; }
.cold-wallet-card::after { content: ''; position: absolute; top: -50%; right: -30%; width: 200px; height: 200px; background: radial-gradient(circle, rgba(236,106,28,0.3), transparent 70%); }
.cold-wallet-inner { position: relative; display: flex; gap: 14px; align-items: center; }
.cold-card-visual { width: 64px; height: 42px; border-radius: 6px; background: linear-gradient(135deg, #1a1a1a, #3a3a3a); border: 1px solid rgba(255,255,255,0.1); display: flex; align-items: center; justify-content: center; flex-shrink: 0; box-shadow: 0 4px 12px rgba(0,0,0,0.3); position: relative; }
.cold-card-visual::before { content: ''; position: absolute; top: 4px; left: 4px; width: 10px; height: 7px; border-radius: 1px; background: linear-gradient(135deg, #d4af37, #b8941f); }
.cold-card-visual .logo { font-family: 'Fraunces', serif; font-size: 20px; color: var(--accent); font-weight: 500; }
.cold-content { flex: 1; }
.cold-title { font-family: 'Fraunces', serif; font-size: 18px; font-weight: 400; line-height: 1.2; }
.cold-title em { font-style: italic; font-weight: 300; }
.cold-sub { font-size: 11px; opacity: 0.7; margin-top: 4px; line-height: 1.4; }
.cold-arrow { background: white; color: var(--text-primary); width: 28px; height: 28px; border-radius: 50%; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
.nft-holder-hero { background: linear-gradient(135deg, #1a1208, #2d1f0f 60%, #0B0B0B); color: white; border-radius: 28px; padding: 24px 22px; position: relative; overflow: hidden; margin-top: 16px; }
.nft-holder-hero::after { content: ''; position: absolute; top: -50%; right: -40%; width: 300px; height: 300px; background: radial-gradient(circle, rgba(236,106,28,0.4), transparent 60%); }
.nft-tag { display: inline-flex; align-items: center; gap: 5px; font-size: 10px; letter-spacing: 0.12em; text-transform: uppercase; font-weight: 600; color: #F59E3B; background: rgba(245,158,59,0.12); border: 1px solid rgba(245,158,59,0.25); padding: 4px 8px; border-radius: 100px; position: relative; }
.nft-holder-label { font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; opacity: 0.6; margin-top: 14px; position: relative; }
.nft-lifetime { font-family: 'Fraunces', serif; font-size: 38px; font-weight: 300; letter-spacing: -0.03em; line-height: 1; margin-top: 4px; position: relative; }
.nft-lifetime .unit { font-size: 14px; opacity: 0.5; margin-left: 4px; font-family: 'Geist', sans-serif; }
.nft-stats-row { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 12px; margin-top: 18px; padding-top: 16px; border-top: 1px solid rgba(255,255,255,0.1); position: relative; }
.nft-stat-l { font-size: 9px; opacity: 0.5; letter-spacing: 0.08em; text-transform: uppercase; }
.nft-stat-v { font-size: 14px; font-weight: 500; margin-top: 3px; font-feature-settings: "tnum"; }
.claim-cta { width: 100%; margin-top: 16px; padding: 12px; background: var(--accent); color: white; border: none; border-radius: 12px; font-family: inherit; font-weight: 600; font-size: 13px; cursor: pointer; position: relative; }
.nft-mini-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; }
.nft-mini { aspect-ratio: 1; background: linear-gradient(135deg, #FFEDD9, #FFD8B0); border-radius: 10px; display: flex; flex-direction: column; align-items: center; justify-content: center; position: relative; cursor: pointer; border: 1px solid var(--border); }
.nft-mini-num { font-family: 'Geist Mono', monospace; font-size: 10px; font-weight: 600; color: var(--accent); margin-top: 2px; }
.nft-mini-logo { font-family: 'Fraunces', serif; font-size: 24px; color: var(--accent); font-weight: 500; line-height: 1; }
.nft-tier-badge { position: absolute; top: 4px; right: 4px; font-size: 8px; font-weight: 700; padding: 2px 5px; border-radius: 100px; letter-spacing: 0.04em; }
.nft-tier-badge.gold { background: var(--gold); color: white; }
.nft-tier-badge.silver { background: #94A3B8; color: white; }
.analytic-row { display: flex; justify-content: space-between; align-items: center; padding: 10px 0; border-bottom: 1px solid var(--border); }
.analytic-row:last-child { border-bottom: none; }
.analytic-row .l { display: flex; align-items: center; gap: 10px; }
.analytic-rank { width: 22px; height: 22px; border-radius: 50%; background: var(--bg-subtle); color: var(--text-secondary); display: flex; align-items: center; justify-content: center; font-size: 11px; font-weight: 600; font-family: 'Geist Mono', monospace; }
.analytic-rank.top { background: var(--accent); color: white; }
.analytic-thumb { width: 34px; height: 34px; border-radius: 8px; background: linear-gradient(135deg, #FFEDD9, #FFD8B0); display: flex; align-items: center; justify-content: center; font-family: 'Fraunces', serif; font-weight: 500; color: var(--accent); font-size: 18px; }
.analytic-name { font-size: 13px; font-weight: 500; }
.analytic-sub { font-size: 11px; color: var(--text-secondary); margin-top: 1px; }
.analytic-val { font-size: 13px; font-weight: 600; font-feature-settings: "tnum"; text-align: right; }
.analytic-val-usd { font-size: 11px; color: var(--text-secondary); margin-top: 1px; font-feature-settings: "tnum"; }
.analytic-chg { font-size: 11px; color: var(--success); margin-top: 1px; }
.analytic-chg.down { color: var(--danger); }
.mode-toggle { display: inline-flex; padding: 3px; background: var(--bg-subtle); border-radius: 100px; margin: 0; }
.mode-toggle span { padding: 6px 14px; border-radius: 100px; font-size: 12px; font-weight: 500; color: var(--text-secondary); cursor: pointer; }
.mode-toggle span.active { background: var(--bg-card); color: var(--text-primary); box-shadow: 0 1px 3px rgba(0,0,0,0.06); }
.trade-tabs { display: flex; gap: 4px; border-bottom: 1px solid var(--border); margin-bottom: 20px; }
.trade-tab { flex: 1; text-align: center; padding: 10px 0 12px; font-size: 13px; font-weight: 500; color: var(--text-tertiary); cursor: pointer; border-bottom: 2px solid transparent; margin-bottom: -1px; }
.trade-tab.active { color: var(--text-primary); border-bottom-color: var(--accent); }
.featured-coin-card { background: linear-gradient(135deg, #EC6A1C, #F59E3B); color: white; border-radius: 22px; padding: 18px 20px; margin-bottom: 14px; position: relative; overflow: hidden; cursor: pointer; }
.featured-coin-card::after { content: ''; position: absolute; top: -30%; right: -20%; width: 160px; height: 160px; border-radius: 50%; background: radial-gradient(circle, rgba(255,255,255,0.18), transparent 70%); }
.featured-badge { display: inline-block; font-size: 9px; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; padding: 3px 7px; background: rgba(255,255,255,0.18); border-radius: 100px; position: relative; }
.featured-row { display: flex; align-items: center; gap: 14px; margin-top: 12px; position: relative; }
.featured-icon { width: 44px; height: 44px; border-radius: 50%; background: white; color: var(--accent); display: flex; align-items: center; justify-content: center; font-family: 'Fraunces', serif; font-size: 22px; font-weight: 500; }
.featured-name { font-size: 15px; font-weight: 600; }
.featured-sub { font-size: 11px; opacity: 0.85; margin-top: 2px; }
.featured-price { font-size: 16px; font-weight: 600; font-feature-settings: "tnum"; }
.featured-change { font-size: 11px; opacity: 0.85; margin-top: 2px; }
.coin-row { display: flex; align-items: center; gap: 14px; padding: 14px 4px; border-bottom: 1px solid var(--border); cursor: pointer; }
.coin-row:last-child { border-bottom: none; }
.coin-info { flex: 1; }
.coin-name-row { display: flex; align-items: baseline; gap: 8px; }
.coin-name { font-size: 14px; font-weight: 600; }
.coin-symbol { font-size: 11px; color: var(--text-tertiary); font-family: 'Geist Mono', monospace; }
.coin-sparkline { height: 24px; width: 60px; margin-top: 2px; }
.coin-price { font-size: 14px; font-weight: 500; font-feature-settings: "tnum"; text-align: right; }
.coin-change { font-size: 11px; margin-top: 2px; font-feature-settings: "tnum"; }
.coin-change.up { color: var(--success); }
.coin-change.down { color: var(--danger); }
.trade-input-card { background: var(--bg-card); border: 1px solid var(--border); border-radius: 16px; padding: 16px 18px; margin-bottom: 10px; }
.trade-input-row { display: flex; justify-content: space-between; align-items: center; gap: 12px; }
.trade-input-label { font-size: 11px; color: var(--text-tertiary); letter-spacing: 0.06em; text-transform: uppercase; margin-bottom: 8px; }
.trade-input-amount { font-family: 'Fraunces', serif; font-size: 36px; font-weight: 300; letter-spacing: -0.02em; flex: 1; border: none; outline: none; background: transparent; color: var(--text-primary); min-width: 0; width: 100%; }
.token-chip { display: inline-flex; align-items: center; gap: 6px; padding: 6px 10px 6px 6px; background: var(--bg-subtle); border-radius: 100px; font-size: 13px; font-weight: 600; cursor: pointer; flex-shrink: 0; }
.token-chip .ti { width: 22px; height: 22px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 10px; font-weight: 700; color: white; }
.trade-hint { display: flex; justify-content: space-between; margin-top: 6px; font-size: 11px; color: var(--text-secondary); }
.trade-hint .link { color: var(--accent); font-weight: 500; cursor: pointer; }
.swap-indicator { width: 36px; height: 36px; border-radius: 12px; background: var(--bg-card); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; margin: -14px auto; position: relative; z-index: 2; }
.trade-summary { margin-top: 16px; padding: 14px; background: var(--bg-subtle); border-radius: 12px; font-size: 12px; }
.trade-summary-row { display: flex; justify-content: space-between; padding: 4px 0; }
.trade-summary-row .l { color: var(--text-secondary); }
.trade-summary-row .r { font-weight: 500; font-feature-settings: "tnum"; }
.big-cta { margin-top: 16px; width: 100%; padding: 16px; border: none; border-radius: 14px; font-family: inherit; font-size: 14px; font-weight: 600; cursor: pointer; }
.big-cta.primary { background: var(--bg-inverse); color: var(--text-inverse); }
.big-cta.accent { background: var(--accent); color: white; }
.big-cta.success { background: var(--success); color: white; }
.price-hero-sm { padding: 12px 0; display: flex; justify-content: space-between; align-items: flex-end; }
.price-large-sm { font-family: 'Fraunces', serif; font-size: 38px; font-weight: 300; letter-spacing: -0.03em; line-height: 1; }
.price-large-sm .unit { font-size: 14px; color: var(--text-secondary); margin-left: 6px; font-family: 'Geist', sans-serif; }
.price-change-sm { display: inline-flex; align-items: center; gap: 4px; padding: 3px 8px; border-radius: 100px; font-size: 11px; font-weight: 500; background: var(--success-soft); color: var(--success); }
.price-chart-card { padding: 0; overflow: hidden; margin-top: 12px; }
.price-chart-svg { width: 100%; height: 140px; display: block; }
.timeframe-tabs { display: flex; gap: 4px; padding: 10px 14px 12px; border-top: 1px solid var(--border); }
.timeframe-tab { padding: 5px 10px; border-radius: 6px; font-size: 11px; font-weight: 500; color: var(--text-tertiary); cursor: pointer; font-family: 'Geist Mono', monospace; }
.timeframe-tab.active { background: var(--bg-inverse); color: var(--text-inverse); }
.orderbook { font-family: 'Geist Mono', monospace; font-size: 11px; margin-top: 16px; }
.ob-header { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; padding: 0 4px 6px; font-size: 9px; color: var(--text-tertiary); letter-spacing: 0.06em; text-transform: uppercase; }
.ob-col-header { display: flex; justify-content: space-between; }
.ob-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.ob-col { display: flex; flex-direction: column; gap: 2px; }
.ob-row { display: flex; justify-content: space-between; align-items: center; padding: 3px 6px; border-radius: 4px; position: relative; overflow: hidden; }
.ob-row.bid::before { content: ''; position: absolute; inset: 0; background: var(--success-soft); opacity: 0.6; width: var(--depth, 50%); right: auto; }
.ob-row.ask::before { content: ''; position: absolute; inset: 0; background: var(--danger-soft); opacity: 0.6; width: var(--depth, 50%); left: auto; right: 0; }
.ob-row.bid .p { color: var(--success); }
.ob-row.ask .p { color: var(--danger); }
.ob-row > * { position: relative; }
.trade-actions-split { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 16px; }
.btn-buy-sm, .btn-sell-sm { padding: 12px; border-radius: 12px; font-family: inherit; font-size: 13px; font-weight: 600; cursor: pointer; border: none; }
.btn-buy-sm { background: var(--success); color: white; }
.btn-sell-sm { background: var(--danger); color: white; }
.view-toggle { display: inline-flex; padding: 3px; background: var(--bg-subtle); border-radius: 10px; margin-bottom: 16px; }
.view-toggle span { padding: 6px 14px; border-radius: 7px; font-size: 12px; font-weight: 500; color: var(--text-secondary); cursor: pointer; display: inline-flex; align-items: center; gap: 5px; }
.view-toggle span.active { background: var(--bg-card); color: var(--text-primary); box-shadow: 0 1px 2px rgba(0,0,0,0.05); }
.stat-big { font-family: 'Fraunces', serif; font-size: 32px; font-weight: 300; letter-spacing: -0.025em; line-height: 1; margin-top: 4px; }
.stat-big .unit { font-size: 14px; color: var(--text-secondary); margin-left: 4px; font-family: 'Geist', sans-serif; }
.stat-big-secondary { font-size: 13px; color: var(--text-secondary); margin-top: 4px; font-feature-settings: "tnum"; }
.chart-card { margin-bottom: 12px; }
.chart-header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 12px; }
.chart-svg { width: 100%; height: 100px; display: block; }
.hub-hero { background: linear-gradient(135deg, #0B0B0B, #1f1f1f); color: white; border-radius: 28px; padding: 24px 22px; position: relative; overflow: hidden; margin-bottom: 16px; }
.hub-hero::after { content: ''; position: absolute; bottom: -60px; right: -40px; width: 180px; height: 180px; background: radial-gradient(circle, rgba(236,106,28,0.28), transparent 70%); }
.hub-hero-label { font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; opacity: 0.6; position: relative; }
.hub-hero-amt { font-family: 'Fraunces', serif; font-size: 40px; font-weight: 300; letter-spacing: -0.03em; line-height: 1; margin-top: 6px; position: relative; }
.hub-hero-amt .unit { font-size: 16px; opacity: 0.5; margin-left: 4px; font-family: 'Geist', sans-serif; }
.hub-hero-sub { font-size: 12px; opacity: 0.6; margin-top: 8px; position: relative; }
.hub-list { display: flex; flex-direction: column; gap: 10px; }
.hub-row { display: flex; align-items: center; gap: 14px; padding: 16px 18px; background: var(--bg-card); border: 1px solid var(--border); border-radius: 16px; cursor: pointer; }
.hub-ic { width: 42px; height: 42px; border-radius: 12px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
.hub-ic.accent { background: var(--accent-soft); color: var(--accent); }
.hub-ic.success { background: var(--success-soft); color: var(--success); }
.hub-ic.info { background: var(--info-soft); color: var(--info); }
.hub-ic.purple { background: var(--purple-soft); color: var(--purple); }
.hub-ic.dark { background: var(--bg-inverse); color: white; }
.hub-ic.gold { background: var(--gold-soft); color: var(--gold); }
.hub-content { flex: 1; }
.hub-title { font-size: 14px; font-weight: 600; display: flex; align-items: center; gap: 8px; }
.hub-tag { font-size: 9px; padding: 2px 6px; background: var(--accent-soft); color: var(--accent); border-radius: 4px; letter-spacing: 0.04em; text-transform: uppercase; font-weight: 600; }
.hub-sub { font-size: 12px; color: var(--text-secondary); margin-top: 2px; line-height: 1.4; }
.google-search { display: flex; align-items: center; gap: 10px; padding: 14px 18px; background: var(--bg-card); border: 1px solid var(--border); border-radius: 100px; cursor: text; margin-bottom: 16px; }
.google-g { width: 22px; height: 22px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
.google-input { flex: 1; font-size: 13px; color: var(--text-tertiary); }
.google-mic { color: var(--accent); }
.featured-app { background: linear-gradient(135deg, #EC6A1C, #F59E3B); color: white; border-radius: 22px; padding: 20px; margin-bottom: 16px; position: relative; overflow: hidden; }
.featured-app::after { content: ''; position: absolute; top: -30%; right: -20%; width: 180px; height: 180px; border-radius: 50%; background: radial-gradient(circle, rgba(255,255,255,0.15), transparent 70%); }
.featured-label { font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; opacity: 0.8; font-weight: 600; position: relative; }
.featured-title { font-family: 'Fraunces', serif; font-size: 22px; font-weight: 400; letter-spacing: -0.01em; margin-top: 4px; position: relative; }
.featured-title em { font-style: italic; font-weight: 300; }
.featured-desc { font-size: 12px; opacity: 0.9; margin-top: 6px; position: relative; }
.featured-cta { margin-top: 14px; background: white; color: var(--accent); border: none; padding: 9px 16px; border-radius: 100px; font-family: inherit; font-size: 12px; font-weight: 600; cursor: pointer; position: relative; }
.apps-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 16px; }
.app-tile { background: var(--bg-card); border: 1px solid var(--border); border-radius: 16px; padding: 14px; cursor: pointer; }
.app-tile-ic { width: 38px; height: 38px; border-radius: 10px; display: flex; align-items: center; justify-content: center; margin-bottom: 10px; font-weight: 700; font-size: 14px; color: white; }
.app-tile-name { font-size: 13px; font-weight: 600; }
.app-tile-cat { font-size: 10px; color: var(--text-tertiary); margin-top: 2px; letter-spacing: 0.04em; text-transform: uppercase; }
.back-header { display: flex; align-items: center; gap: 12px; padding: 12px 0 16px; }
.back-btn { width: 36px; height: 36px; border-radius: 50%; background: var(--bg-card); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; cursor: pointer; }
.page-title-sm { font-family: 'Fraunces', serif; font-size: 20px; font-weight: 400; letter-spacing: -0.01em; }
.page-title-sm em { font-style: italic; font-weight: 300; }
.send-input-pill { display: flex; align-items: center; gap: 10px; padding: 12px 16px; background: var(--bg-card); border: 1px solid var(--border); border-radius: 100px; margin-bottom: 16px; }
.send-input-pill input { flex: 1; border: none; outline: none; background: transparent; font-family: inherit; font-size: 13px; color: var(--text-primary); }
.scan-pill { display: flex; align-items: center; gap: 6px; padding: 4px 10px; background: var(--accent-soft); color: var(--accent); border-radius: 100px; font-size: 11px; font-weight: 600; cursor: pointer; }
.contact-row { display: flex; align-items: center; gap: 14px; padding: 12px 4px; border-bottom: 1px solid var(--border); cursor: pointer; }
.contact-row:last-child { border-bottom: none; }
.contact-avatar { width: 42px; height: 42px; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-weight: 600; font-size: 14px; flex-shrink: 0; }
.contact-info { flex: 1; }
.contact-name { font-size: 14px; font-weight: 500; }
.contact-handle { font-size: 11px; color: var(--text-secondary); margin-top: 1px; font-family: 'Geist Mono', monospace; }
.contact-badge { font-size: 9px; padding: 2px 6px; border-radius: 4px; letter-spacing: 0.04em; text-transform: uppercase; font-weight: 600; background: var(--success-soft); color: var(--success); }
.add-contact-row { display: flex; align-items: center; gap: 14px; padding: 14px; background: var(--bg-card); border: 1px dashed var(--border-strong); border-radius: 16px; cursor: pointer; margin-bottom: 16px; }
.add-ic { width: 42px; height: 42px; border-radius: 50%; background: var(--accent-soft); color: var(--accent); display: flex; align-items: center; justify-content: center; }
.stake-hero { background: linear-gradient(135deg, #0f3a1f, #15803D); color: white; border-radius: 28px; padding: 24px 22px; position: relative; overflow: hidden; margin-bottom: 16px; }
.stake-hero::after { content: ''; position: absolute; top: -30%; right: -30%; width: 220px; height: 220px; background: radial-gradient(circle, rgba(220,252,231,0.2), transparent 70%); }
.apy-big { font-family: 'Fraunces', serif; font-size: 54px; font-weight: 300; letter-spacing: -0.035em; line-height: 1; margin-top: 8px; position: relative; }
.apy-big .unit { font-size: 20px; opacity: 0.6; margin-left: 4px; font-family: 'Geist', sans-serif; }
.term-tabs { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 16px; }
.term-tab { padding: 14px 10px; border: 1px solid var(--border); border-radius: 12px; text-align: center; cursor: pointer; background: var(--bg-card); }
.term-tab.active { border-color: var(--success); background: var(--success-soft); }
.term-d { font-size: 16px; font-weight: 600; font-family: 'Fraunces', serif; }
.term-apy { font-size: 11px; color: var(--text-secondary); margin-top: 2px; font-weight: 500; }
.term-tab.active .term-apy { color: var(--success); }
.calc-row { display: flex; justify-content: space-between; padding: 10px 0; font-size: 13px; border-bottom: 1px solid var(--border); }
.calc-row:last-child { border-bottom: none; }
.calc-row .l { color: var(--text-secondary); }
.calc-row .r { font-weight: 500; font-feature-settings: "tnum"; }
.calc-row .r.success { color: var(--success); }
.refer-big-code { font-family: 'Geist Mono', monospace; font-size: 32px; font-weight: 500; letter-spacing: -0.01em; margin: 12px 0; display: flex; justify-content: space-between; align-items: center; }
.refer-reward-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px; margin: 16px 0; }
.reward-tile { padding: 14px 12px; background: var(--bg-card); border: 1px solid var(--border); border-radius: 12px; text-align: center; }
.reward-level { font-size: 9px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--text-tertiary); font-weight: 600; }
.reward-amt { font-family: 'Fraunces', serif; font-size: 22px; font-weight: 400; letter-spacing: -0.02em; margin-top: 4px; }
.reward-label { font-size: 10px; color: var(--text-secondary); margin-top: 2px; }
.lb-tabs { display: flex; padding: 3px; background: var(--bg-subtle); border-radius: 10px; margin-bottom: 16px; }
.lb-tabs span { flex: 1; text-align: center; padding: 8px; border-radius: 7px; font-size: 13px; font-weight: 500; color: var(--text-secondary); cursor: pointer; }
.lb-tabs span.active { background: var(--bg-card); color: var(--text-primary); box-shadow: 0 1px 3px rgba(0,0,0,0.05); }
.market-row { display: flex; align-items: center; gap: 14px; padding: 14px 4px; border-bottom: 1px solid var(--border); cursor: pointer; }
.market-row:last-child { border-bottom: none; }
.market-info { flex: 1; }
.market-name { font-size: 14px; font-weight: 500; }
.market-sub { font-size: 11px; color: var(--text-secondary); margin-top: 1px; }
.market-apy-val { font-size: 14px; font-weight: 600; color: var(--success); font-feature-settings: "tnum"; }
.market-apy-lbl { font-size: 10px; color: var(--text-tertiary); margin-top: 2px; letter-spacing: 0.04em; text-transform: uppercase; }
.gov-banner { background: linear-gradient(135deg, #2d1a4a, #6D28D9); color: white; border-radius: 22px; padding: 18px 20px; margin-bottom: 16px; position: relative; overflow: hidden; }
.gov-banner::after { content: ''; position: absolute; top: -40%; right: -30%; width: 200px; height: 200px; background: radial-gradient(circle, rgba(255,255,255,0.12), transparent 70%); }
.gov-banner-title { font-family: 'Fraunces', serif; font-size: 18px; font-weight: 400; line-height: 1.3; position: relative; }
.gov-banner-title em { font-style: italic; font-weight: 300; }
.gov-banner-sub { font-size: 11px; opacity: 0.85; margin-top: 6px; position: relative; }
.gov-voting-notice { display: flex; gap: 10px; padding: 12px 14px; background: var(--accent-soft); border-radius: 12px; margin-bottom: 16px; align-items: center; }
.gov-voting-notice .ic { width: 28px; height: 28px; border-radius: 50%; background: var(--accent); color: white; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
.gov-voting-notice-text { flex: 1; font-size: 11px; color: var(--text-primary); line-height: 1.4; }
.gov-voting-notice-text strong { font-weight: 600; }
.proposal-card { background: var(--bg-card); border: 1px solid var(--border); border-radius: 16px; padding: 16px 18px; margin-bottom: 10px; cursor: pointer; }
.proposal-meta { display: flex; align-items: center; gap: 8px; font-size: 11px; color: var(--text-secondary); margin-bottom: 8px; }
.proposal-status { font-size: 9px; padding: 3px 7px; border-radius: 100px; font-weight: 600; letter-spacing: 0.04em; text-transform: uppercase; }
.proposal-status.active { background: var(--success-soft); color: var(--success); }
.proposal-status.ended { background: var(--bg-subtle); color: var(--text-secondary); }
.proposal-status.pending { background: var(--info-soft); color: var(--info); }
.proposal-title { font-size: 14px; font-weight: 600; line-height: 1.35; }
.proposal-sub { font-size: 12px; color: var(--text-secondary); margin-top: 4px; line-height: 1.4; }
.vote-bar { display: flex; height: 6px; border-radius: 100px; overflow: hidden; margin-top: 12px; gap: 2px; }
.vote-bar .yes { background: var(--success); }
.vote-bar .no { background: var(--danger); }
.vote-bar .abstain { background: var(--text-tertiary); }
.vote-legend { display: flex; justify-content: space-between; font-size: 11px; margin-top: 6px; color: var(--text-secondary); }
.vote-legend .yes-t { color: var(--success); font-weight: 500; }
.vote-legend .no-t { color: var(--danger); font-weight: 500; }
.bottom-nav { position: absolute; bottom: 0; left: 0; right: 0; background: rgba(255,255,255,0.92); backdrop-filter: blur(20px); border-top: 1px solid var(--border); padding: 8px 8px 24px; display: grid; grid-template-columns: repeat(5, 1fr); }
.nav-item { display: flex; flex-direction: column; align-items: center; gap: 3px; padding: 6px 4px; cursor: pointer; color: var(--text-tertiary); font-size: 10px; font-weight: 500; }
.nav-item.active { color: var(--text-primary); }
.nav-item svg { width: 22px; height: 22px; }
@media (max-width: 600px) { body { padding: 20px 12px; } .page-title { font-size: 36px; } .phone { transform: scale(0.92); } }
</style>
</head>
<body>
<header class="page-header">
  <div>
    <h1 class="page-title">DYNK — <em>Redesign</em><span class="v">v6</span></h1>
    <p style="color: var(--text-secondary); margin-top: 8px; font-size: 14px;">Three user tiers · Banking-first language · Jupiter swaps · Gamified NFT wallets · Governance</p>
  </div>
  <div class="page-meta">
    <div>Wallet tiers<strong>Everyday · Savings · Founder</strong></div>
    <div>New this round<strong>3 screens</strong></div>
    <div>Total<strong>16</strong></div>
  </div>
</header>
<div class="section-heading">All <em>screens</em> <span class="count">16 total · v5 ordered flow</span></div>
<div class="screens-grid">
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg><svg width="15" height="11" viewBox="0 0 15 11" fill="currentColor"><path d="M7.5 0C4.8 0 2.3 1 .4 2.7l1.4 1.4C3.3 2.7 5.3 1.8 7.5 1.8s4.2.9 5.7 2.3l1.4-1.4C12.7 1 10.2 0 7.5 0zm0 3.7c-1.7 0-3.3.6-4.5 1.8l1.4 1.4c.8-.8 2-1.3 3.1-1.3s2.3.5 3.1 1.3l1.4-1.4c-1.2-1.2-2.8-1.8-4.5-1.8zm0 3.7c-.7 0-1.4.3-1.9.8L7.5 11l1.9-1.9c-.5-.4-1.2-.7-1.9-.7z"/></svg><svg width="25" height="11" viewBox="0 0 25 11" fill="none"><rect x="0.5" y="0.5" width="21" height="10" rx="2.5" stroke="currentColor"/><rect x="2" y="2" width="18" height="7" rx="1" fill="currentColor"/><rect x="22.5" y="3.5" width="1.5" height="4" rx="0.5" fill="currentColor"/></svg></div></div>
<div class="wallet-bar"><div class="wallet-pills"><div class="wallet-pill active"><span class="dot"></span>Everyday</div><div class="wallet-pill savings">Savings</div><div class="wallet-pill nft">NFT Wallet</div></div><div class="wallet-add"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll">
<div class="app-header" style="padding-top: 16px;"><div><div class="hello">Hi, <em>Angus</em></div><div class="sub-label">Everyday wallet</div></div><div class="header-actions"><button class="icon-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M6 8a6 6 0 0 1 12 0c0 7 3 9 3 9H3s3-2 3-9"/><path d="M10.3 21a1.94 1.94 0 0 0 3.4 0"/></svg></button><div class="avatar">A</div></div></div>
<div class="balance-inline"><div class="balance-inline-label">Available balance</div><div class="balance-inline-amount">$49<span class="cents">.69</span><span class="unit">USD</span></div><div class="balance-change"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round"><polyline points="5 12 12 5 19 12"/></svg>+$0.00 today</div></div>
<div class="quick-actions-4">
<button class="qa-btn"><div class="ic-wrap accent"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/></svg></div>Send</button>
<button class="qa-btn"><div class="ic-wrap"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="19" x2="12" y2="5"/><polyline points="5 12 12 5 19 12"/></svg></div>Deposit</button>
<button class="qa-btn"><div class="ic-wrap"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="6" width="18" height="13" rx="2"/><path d="M3 10h18"/></svg></div>Pay</button>
<button class="qa-btn"><div class="ic-wrap info"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg></div>Stake</button>
</div>
<div class="cold-wallet-card"><div class="cold-wallet-inner"><div class="cold-card-visual"><div class="logo">D</div></div><div class="cold-content"><div class="cold-title">Secure with <em>Tangem</em></div><div class="cold-sub">Protect your keys with the DYNK cold wallet card · Tap-to-sign with NFC</div></div><div class="cold-arrow"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg></div></div></div>
<h2 class="section-title" style="margin: 18px 0 10px;"><em>Everyday</em> <span class="see-all">See all ›</span></h2>
<div class="card" style="padding: 4px 16px;">
<div class="holding-row"><div class="token-icon token-dynk">D</div><div class="holding-info"><div class="holding-name">DYNK</div><div class="holding-sub">Primary · +0.00%</div></div><div class="holding-value"><div class="holding-amt">24.97</div><div class="holding-usd">$43.19</div></div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">01 · Everyday <span class="new">Updated</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg><svg width="15" height="11" viewBox="0 0 15 11" fill="currentColor"><path d="M7.5 0C4.8 0 2.3 1 .4 2.7l1.4 1.4C3.3 2.7 5.3 1.8 7.5 1.8s4.2.9 5.7 2.3l1.4-1.4C12.7 1 10.2 0 7.5 0z"/></svg><svg width="25" height="11" viewBox="0 0 25 11" fill="none"><rect x="0.5" y="0.5" width="21" height="10" rx="2.5" stroke="currentColor"/><rect x="2" y="2" width="18" height="7" rx="1" fill="currentColor"/></svg></div></div>
<div class="wallet-bar"><div class="wallet-pills"><div class="wallet-pill">Everyday</div><div class="wallet-pill savings active"><span class="dot"></span>Savings</div><div class="wallet-pill nft">NFT Wallet</div></div><div class="wallet-add"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll">
<div class="app-header" style="padding-top: 16px;"><div><div class="hello">Your <em>Savings</em></div><div class="sub-label">Separate from your everyday funds</div></div><div class="header-actions"><div class="avatar">A</div></div></div>
<div class="balance-inline"><div class="balance-inline-label">Savings balance</div><div class="balance-inline-amount">$1,284<span class="cents">.50</span><span class="unit">USD</span></div><div style="display: inline-flex; align-items: center; gap: 5px; margin-top: 8px; font-size: 12px; color: var(--info); font-weight: 500;"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>Isolated from dapp connections</div></div>
<div class="quick-actions-4">
<button class="qa-btn"><div class="ic-wrap info"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg></div>Transfer</button>
<button class="qa-btn"><div class="ic-wrap"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="19" x2="12" y2="5"/><polyline points="5 12 12 5 19 12"/></svg></div>Deposit</button>
<button class="qa-btn"><div class="ic-wrap"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg></div>Withdraw</button>
<button class="qa-btn"><div class="ic-wrap accent"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg></div>Info</button>
</div>
<div class="card" style="margin-top: 18px; background: var(--info-soft); border-color: transparent;">
<div style="display: flex; gap: 10px; align-items: flex-start;"><div style="width:28px; height:28px; border-radius: 50%; background: var(--info); color: white; display:flex; align-items:center; justify-content:center; flex-shrink: 0;"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg></div>
<div><div style="font-size: 13px; font-weight: 600; color: var(--info);">Why keep savings here?</div><div style="font-size: 12px; color: var(--text-primary); margin-top: 4px; line-height: 1.5;">Your Savings wallet uses a separate key from your Everyday wallet. If a dapp is ever compromised, your savings stay safe.</div></div></div>
</div>
<h2 class="section-title" style="margin: 18px 0 10px;"><em>Savings</em> <span class="see-all">See all ›</span></h2>
<div class="card" style="padding: 4px 16px;">
<div class="holding-row"><div class="token-icon token-dynk">D</div><div class="holding-info"><div class="holding-name">DYNK</div></div><div class="holding-value"><div class="holding-amt">450.00</div><div class="holding-usd">$778.50</div></div></div>
<div class="holding-row"><div class="token-icon token-btc">₿</div><div class="holding-info"><div class="holding-name">Bitcoin</div></div><div class="holding-value"><div class="holding-amt">0.0048</div><div class="holding-usd">$322.80</div></div></div>
<div class="holding-row"><div class="token-icon token-eth">E</div><div class="holding-info"><div class="holding-name">Ethereum</div></div><div class="holding-value"><div class="holding-amt">0.052</div><div class="holding-usd">$177.84</div></div></div>
<div class="holding-row"><div class="token-icon token-sol">S</div><div class="holding-info"><div class="holding-name">Solana</div></div><div class="holding-value"><div class="holding-amt">0.072</div><div class="holding-usd">$5.85</div></div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">02 · Savings <span class="new">New</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="wallet-bar"><div class="wallet-pills"><div class="wallet-pill">Everyday</div><div class="wallet-pill savings">Savings</div><div class="wallet-pill nft active"><span class="dot"></span>NFT Wallet</div></div></div>
<div class="screen-body"><div class="screen-scroll">
<div class="app-header" style="padding-top: 16px;"><div><div class="hello">Founder <em>Holder</em></div><div class="sub-label">1 of 2,100 · Member since 2024</div></div><div class="header-actions"><div class="avatar">A</div></div></div>
<div class="nft-holder-hero">
<div class="nft-tag"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Founder · 1 of 2,100</div>
<div class="nft-holder-label">Lifetime earnings</div>
<div class="nft-lifetime">1,247<span class="unit">DYNK</span></div>
<div style="font-size: 11px; opacity: 0.6; margin-top: 4px; position: relative;">≈ $2,157 USD · From transaction fees</div>
<div class="nft-stats-row" style="grid-template-columns: 1fr 1fr;">
<div><div class="nft-stat-l">Fee share</div><div class="nft-stat-v">0.0476%</div></div>
<div><div class="nft-stat-l">Pending</div><div class="nft-stat-v">42.30 DYNK</div></div>
</div>
<button class="claim-cta">Claim 42.30 DYNK rewards</button>
</div>

<h2 class="section-title">Revenue <em>generated</em></h2>
<div style="display: flex; gap: 4px; margin-bottom: 12px;"><div class="timeframe-tab active">Daily</div><div class="timeframe-tab">Weekly</div><div class="timeframe-tab">Monthly</div></div>
<div class="card chart-card">
<div class="chart-header"><div>
<div class="label-xs">Today's earnings</div>
<div class="stat-big">$3.42<span class="unit">USD</span></div>
<div class="stat-big-secondary">1.98 DYNK</div>
<div class="balance-change" style="margin-top: 4px;"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round"><polyline points="5 12 12 5 19 12"/></svg>+12.6% vs yesterday</div>
</div></div>
<svg class="chart-svg" viewBox="0 0 300 100" preserveAspectRatio="none">
<defs><linearGradient id="founderGrad" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#EC6A1C" stop-opacity="0.35"/><stop offset="1" stop-color="#EC6A1C" stop-opacity="0"/></linearGradient></defs>
<path d="M0,75 L25,68 L50,72 L75,55 L100,60 L125,45 L150,52 L175,38 L200,42 L225,28 L250,32 L275,20 L300,15 L300,100 L0,100 Z" fill="url(#founderGrad)"/>
<path d="M0,75 L25,68 L50,72 L75,55 L100,60 L125,45 L150,52 L175,38 L200,42 L225,28 L250,32 L275,20 L300,15" stroke="#EC6A1C" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
<circle cx="300" cy="15" r="3" fill="#EC6A1C"/>
</svg>
<div style="display:flex; justify-content: space-between; font-size: 9px; color: var(--text-tertiary); font-family: 'Geist Mono', monospace; margin-top: 4px;"><span>00:00</span><span>06:00</span><span>12:00</span><span>18:00</span><span>Now</span></div>
</div>

<h2 class="section-title">Founder <em>requirement</em></h2>
<div class="card" style="display: flex; align-items: center; gap: 18px;">
<svg width="92" height="92" viewBox="0 0 92 92" style="flex-shrink: 0;">
<circle cx="46" cy="46" r="38" fill="none" stroke="var(--bg-subtle)" stroke-width="9"/>
<circle cx="46" cy="46" r="38" fill="none" stroke="#EC6A1C" stroke-width="9" stroke-linecap="round" stroke-dasharray="238.76" stroke-dashoffset="42.4" transform="rotate(-90 46 46)"/>
<text x="46" y="44" text-anchor="middle" font-family="Fraunces" font-size="20" font-weight="400" fill="#0B0B0B" letter-spacing="-1">82%</text>
<text x="46" y="58" text-anchor="middle" font-family="Geist Mono" font-size="8" fill="#6B6B66">held</text>
</svg>
<div style="flex: 1;">
<div style="font-size: 13px; font-weight: 600;">8,247 / 10,000 DYNK</div>
<div style="font-size: 11px; color: var(--text-secondary); margin-top: 4px; line-height: 1.5;">Hold a minimum of 10,000 DYNK to keep your founder perks: fee share, voting and boosted referrals.</div>
<div style="margin-top: 8px; font-size: 11px; color: var(--accent); font-weight: 600;">+1,753 DYNK to go ›</div>
</div>
</div>

<h2 class="section-title">Perks <em>locked</em> <span class="see-all" style="color: var(--text-tertiary);">Hold 10k DYNK to unlock</span></h2>
<div class="card" style="padding: 4px 18px; opacity: 0.55;">
<div class="analytic-row"><div class="l"><div class="analytic-rank" style="background: var(--bg-subtle); color: var(--text-tertiary);"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg></div><div class="analytic-name" style="color: var(--text-secondary);">Equal fee share</div></div><div class="analytic-val" style="color: var(--text-tertiary);">Locked</div></div>
<div class="analytic-row"><div class="l"><div class="analytic-rank" style="background: var(--bg-subtle); color: var(--text-tertiary);"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg></div><div class="analytic-name" style="color: var(--text-secondary);">Governance voting</div></div><div class="analytic-val" style="color: var(--text-tertiary);">Locked</div></div>
<div class="analytic-row"><div class="l"><div class="analytic-rank" style="background: var(--bg-subtle); color: var(--text-tertiary);"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg></div><div class="analytic-name" style="color: var(--text-secondary);">Boosted referrals</div></div><div class="analytic-val" style="color: var(--text-tertiary);">Locked</div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">03 · Founder Wallet <span class="new">Updated</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div class="page-title-sm">Send <em>to</em></div></div>
<div class="send-input-pill">
<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.3-4.3"/></svg>
<input placeholder="Search name, username or address" />
<div class="scan-pill"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg>Scan</div>
</div>
<div class="add-contact-row">
<div class="add-ic"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="8.5" cy="7" r="4"/><line x1="20" y1="8" x2="20" y2="14"/><line x1="23" y1="11" x2="17" y2="11"/></svg></div>
<div style="flex:1;"><div style="font-size: 13px; font-weight: 600;">Add new contact</div><div style="font-size: 11px; color: var(--text-secondary); margin-top: 2px;">Scan QR, enter username, or paste address</div></div>
<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><polyline points="9 18 15 12 9 6"/></svg>
</div>
<h2 class="section-title" style="margin-top: 8px;">Favourites</h2>
<div class="contact-row"><div class="contact-avatar" style="background: linear-gradient(135deg, #F59E3B, #EC6A1C);">M</div><div class="contact-info"><div class="contact-name">Mum</div><div class="contact-handle">@margaret · 7Z3v…ZJ6Q</div></div><svg width="14" height="14" viewBox="0 0 24 24" fill="#EC6A1C" stroke="#EC6A1C" stroke-width="2"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg></div>
<div class="contact-row"><div class="contact-avatar" style="background: linear-gradient(135deg, #6D28D9, #A78BFA);">S</div><div class="contact-info"><div class="contact-name">Sarah</div><div class="contact-handle">@sarahj · 9Xc2…8vKp</div></div><span class="contact-badge">On DYNK</span></div>
<h2 class="section-title">Recent</h2>
<div class="contact-row"><div class="contact-avatar" style="background: linear-gradient(135deg, #1D4ED8, #3B82F6);">T</div><div class="contact-info"><div class="contact-name">Tom — roommate</div><div class="contact-handle">@thomasp · Last sent 2d ago</div></div><span class="contact-badge">On DYNK</span></div>
<div class="contact-row"><div class="contact-avatar" style="background: linear-gradient(135deg, #15803D, #22C55E);">J</div><div class="contact-info"><div class="contact-name">Jake</div><div class="contact-handle">Hd2v…5ZpQ · Phantom wallet</div></div><span class="contact-badge" style="background: var(--bg-subtle); color: var(--text-secondary);">External</span></div>
<div class="contact-row"><div class="contact-avatar" style="background: linear-gradient(135deg, #B45309, #D97706);">E</div><div class="contact-info"><div class="contact-name">Emma — sister</div><div class="contact-handle">@emma_smith · Last sent 1w ago</div></div><span class="contact-badge">On DYNK</span></div>
<h2 class="section-title">All contacts</h2>
<div class="contact-row"><div class="contact-avatar" style="background: linear-gradient(135deg, #9B9B94, #6B6B66);">D</div><div class="contact-info"><div class="contact-name">Dad</div><div class="contact-handle">@dadsmith · 4Kp9…2xLm</div></div><span class="contact-badge">On DYNK</span></div>
</div>
<nav class="bottom-nav">
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">06 · Send · Contacts <span class="new">New</span></div></div>

<!-- 06b CONTACT PROFILE -->
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div style="flex:1;"></div><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="1"/><circle cx="19" cy="12" r="1"/><circle cx="5" cy="12" r="1"/></svg></div></div>

<div style="text-align: center; padding: 16px 0 24px;">
<div class="contact-avatar" style="width: 84px; height: 84px; font-size: 30px; margin: 0 auto 14px; background: linear-gradient(135deg, #F59E3B, #EC6A1C);">M</div>
<div style="font-family: 'Fraunces', serif; font-size: 28px; font-weight: 400; letter-spacing: -0.02em; line-height: 1.1;">Mum</div>
<div style="font-size: 12px; color: var(--text-secondary); margin-top: 4px; font-family: 'Geist Mono', monospace;">@margaret · 7Z3v…ZJ6Q</div>
<div style="margin-top: 8px; display: inline-flex; align-items: center; gap: 6px; padding: 4px 10px; background: var(--success-soft); color: var(--success); border-radius: 100px; font-size: 11px; font-weight: 600;">
<svg width="10" height="10" viewBox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="6"/></svg>
On DYNK · Active now
</div>
</div>

<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 18px;">
<button class="qa-btn" style="padding: 14px 6px 12px;"><div class="ic-wrap accent"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="7" y1="17" x2="17" y2="7"/><polyline points="7 7 17 7 17 17"/></svg></div>Send</button>
<button class="qa-btn" style="padding: 14px 6px 12px;"><div class="ic-wrap" style="background: var(--success-soft); color: var(--success);"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="17" y1="7" x2="7" y2="17"/><polyline points="17 17 7 17 7 7"/></svg></div>Request</button>
<button class="qa-btn" style="padding: 14px 6px 12px;"><div class="ic-wrap info"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg></div>Message</button>
</div>

<h2 class="section-title" style="margin-top: 0;">Recent <em>activity</em></h2>
<div class="card" style="padding: 4px 16px;">
<div class="holding-row">
<div class="hub-ic" style="width: 36px; height: 36px; background: var(--success-soft); color: var(--success);"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="17" y1="7" x2="7" y2="17"/><polyline points="17 17 7 17 7 7"/></svg></div>
<div class="holding-info"><div class="holding-name">You sent</div><div class="holding-sub">Birthday gift · 3 days ago</div></div>
<div class="holding-value"><div class="holding-amt">50 DYNK</div><div class="holding-usd">$86.50</div></div>
</div>
<div class="holding-row">
<div class="hub-ic" style="width: 36px; height: 36px; background: var(--accent-soft); color: var(--accent);"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg></div>
<div class="holding-info"><div class="holding-name">"Thanks love x"</div><div class="holding-sub">3 days ago</div></div>
</div>
<div class="holding-row">
<div class="hub-ic" style="width: 36px; height: 36px; background: var(--info-soft); color: var(--info);"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="7" y1="17" x2="17" y2="7"/><polyline points="7 7 17 7 17 17" transform="rotate(180 12 12)"/></svg></div>
<div class="holding-info"><div class="holding-name">Mum sent you</div><div class="holding-sub">Lunch · 2 weeks ago</div></div>
<div class="holding-value"><div class="holding-amt">25 DYNK</div><div class="holding-usd">$43.25</div></div>
</div>
</div>

<h2 class="section-title">Contact <em>details</em></h2>
<div class="card" style="padding: 4px 16px;">
<div class="holding-row" style="cursor: pointer;">
<div style="font-size: 12px; color: var(--text-secondary); width: 90px;">Username</div>
<div class="holding-info"><div style="font-size: 13px; font-weight: 500; font-family: 'Geist Mono', monospace;">@margaret</div></div>
<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
</div>
<div class="holding-row" style="cursor: pointer;">
<div style="font-size: 12px; color: var(--text-secondary); width: 90px;">Address</div>
<div class="holding-info"><div style="font-size: 13px; font-weight: 500; font-family: 'Geist Mono', monospace;">7Z3vQb…ZJ6Q</div></div>
<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
</div>
<div class="holding-row">
<div style="font-size: 12px; color: var(--text-secondary); width: 90px;">Added</div>
<div class="holding-info"><div style="font-size: 13px; font-weight: 500;">14 March 2025</div></div>
</div>
</div>

<button class="big-cta" style="background: transparent; color: var(--danger); border: 1px solid var(--danger-soft); margin-top: 14px;">Remove contact</button>
</div>
<nav class="bottom-nav">
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">06b · Contact Profile <span class="new">New</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello"><em>Trade</em></div><div class="sub-label">Buy, sell &amp; swap</div></div><div class="header-actions"><div class="mode-toggle"><span class="active">Simple</span><span>Advanced</span></div></div></div>
<div class="trade-tabs"><div class="trade-tab active">Buy</div><div class="trade-tab">Sell</div><div class="trade-tab">Swap</div><div class="trade-tab">NFTs</div></div>
<h2 class="section-title" style="margin-top: 0;">Buy <em>DYNK</em></h2>
<div class="trade-input-card">
<div class="trade-input-label">You pay</div>
<div class="trade-input-row"><input class="trade-input-amount" value="100.00" readonly><div class="token-chip"><div class="ti" style="background:#2775CA;">U</div>USDC<svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"><polyline points="6 9 12 15 18 9"/></svg></div></div>
<div class="trade-hint"><span>Balance: $243.50</span><span class="link">Max</span></div>
</div>
<div class="swap-indicator"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"/><polyline points="19 12 12 19 5 12"/></svg></div>
<div class="trade-input-card">
<div class="trade-input-label">You receive</div>
<div class="trade-input-row"><input class="trade-input-amount" value="57.80" readonly><div class="token-chip"><div class="ti" style="background: linear-gradient(135deg, #EC6A1C, #F59E3B);">D</div>DYNK<svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round"><polyline points="6 9 12 15 18 9"/></svg></div></div>
<div class="trade-hint"><span>1 DYNK = 1.73 USDC</span><span>≈ $100.00</span></div>
</div>
<div class="trade-summary">
<div class="trade-summary-row"><span class="l">You'll receive</span><span class="r">57.80 DYNK</span></div>
<div class="trade-summary-row"><span class="l">Network fee</span><span class="r">$0.01</span></div>
</div>
<button class="big-cta accent">Buy DYNK now</button>

<h2 class="section-title">Buy <em>cryptocurrency</em></h2>
<div class="card" style="padding: 4px 16px;">
<div class="coin-row"><div class="token-icon token-btc">₿</div><div class="coin-info"><div class="coin-name-row"><span class="coin-name">Bitcoin</span><span class="coin-symbol">BTC</span></div><svg class="coin-sparkline" viewBox="0 0 60 24" preserveAspectRatio="none"><polyline points="0,15 10,12 20,14 30,8 40,10 50,5 60,4" stroke="#15803D" stroke-width="1.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/></svg></div><div><div class="coin-price">$67,250</div><div class="coin-change up">+2.4%</div></div></div>
<div class="coin-row"><div class="token-icon token-eth">E</div><div class="coin-info"><div class="coin-name-row"><span class="coin-name">Ethereum</span><span class="coin-symbol">ETH</span></div><svg class="coin-sparkline" viewBox="0 0 60 24" preserveAspectRatio="none"><polyline points="0,10 10,12 20,8 30,11 40,14 50,18 60,16" stroke="#B91C1C" stroke-width="1.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/></svg></div><div><div class="coin-price">$3,420</div><div class="coin-change down">−1.2%</div></div></div>
<div class="coin-row"><div class="token-icon token-sol">S</div><div class="coin-info"><div class="coin-name-row"><span class="coin-name">Solana</span><span class="coin-symbol">SOL</span></div><svg class="coin-sparkline" viewBox="0 0 60 24" preserveAspectRatio="none"><polyline points="0,18 10,16 20,12 30,14 40,8 50,6 60,4" stroke="#15803D" stroke-width="1.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/></svg></div><div><div class="coin-price">$81.25</div><div class="coin-change up">+4.1%</div></div></div>
<div class="coin-row"><div class="token-icon token-usdc">U</div><div class="coin-info"><div class="coin-name-row"><span class="coin-name">USD Coin</span><span class="coin-symbol">USDC</span></div><svg class="coin-sparkline" viewBox="0 0 60 24" preserveAspectRatio="none"><polyline points="0,12 10,12 20,12 30,12 40,12 50,12 60,12" stroke="#9B9B94" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></div><div><div class="coin-price">$1.00</div><div class="coin-change" style="color: var(--text-tertiary);">0.00%</div></div></div>
</div>

<div class="add-contact-row" style="margin-top: 14px;">
<div class="add-ic"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div>
<div style="flex:1;"><div style="font-size: 13px; font-weight: 600;">Import a token</div><div style="font-size: 11px; color: var(--text-secondary); margin-top: 2px;">Paste any token contract address</div></div>
<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><polyline points="9 18 15 12 9 6"/></svg>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">04 · Trade · Simple <span class="new">Alt coins · $0.01 fee</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello">DYNK <em>/ USDC</em></div><div class="sub-label">Advanced · Order book</div></div><div class="header-actions"><div class="mode-toggle"><span>Simple</span><span class="active">Advanced</span></div></div></div>
<div class="price-hero-sm"><div><div class="price-large-sm">1.73<span class="unit">USDC</span></div><div class="price-change-sm" style="margin-top: 6px;"><svg width="8" height="8" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round"><polyline points="5 12 12 5 19 12"/></svg>+0.00%</div></div><div style="text-align:right; font-size: 11px; color: var(--text-secondary);"><div>24h Vol</div><div style="font-weight:500; color: var(--text-primary); margin-top: 2px; font-feature-settings: 'tnum';">0 DYNK</div></div></div>
<div class="card price-chart-card">
<svg class="price-chart-svg" viewBox="0 0 340 140" preserveAspectRatio="none">
<defs><linearGradient id="priceGrad" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#EC6A1C" stop-opacity="0.35"/><stop offset="1" stop-color="#EC6A1C" stop-opacity="0"/></linearGradient></defs>
<line x1="0" y1="35" x2="340" y2="35" stroke="#EAE7DF" stroke-dasharray="2 4"/>
<line x1="0" y1="70" x2="340" y2="70" stroke="#EAE7DF" stroke-dasharray="2 4"/>
<line x1="0" y1="105" x2="340" y2="105" stroke="#EAE7DF" stroke-dasharray="2 4"/>
<path d="M0,80 L20,85 L40,75 L60,90 L80,70 L100,65 L120,78 L140,55 L160,60 L180,42 L200,50 L220,38 L240,45 L260,28 L280,35 L300,22 L320,30 L340,25 L340,140 L0,140 Z" fill="url(#priceGrad)"/>
<path d="M0,80 L20,85 L40,75 L60,90 L80,70 L100,65 L120,78 L140,55 L160,60 L180,42 L200,50 L220,38 L240,45 L260,28 L280,35 L300,22 L320,30 L340,25" stroke="#EC6A1C" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
<circle cx="340" cy="25" r="3.5" fill="#EC6A1C"/>
<circle cx="340" cy="25" r="7" fill="#EC6A1C" fill-opacity="0.2"/>
<text x="10" y="32" font-family="Geist Mono" font-size="9" fill="#9B9B94">$1.85</text>
<text x="10" y="67" font-family="Geist Mono" font-size="9" fill="#9B9B94">$1.50</text>
<text x="10" y="102" font-family="Geist Mono" font-size="9" fill="#9B9B94">$1.15</text>
</svg>
<div class="timeframe-tabs"><div class="timeframe-tab">1H</div><div class="timeframe-tab active">1D</div><div class="timeframe-tab">1W</div><div class="timeframe-tab">1M</div><div class="timeframe-tab">1Y</div><div class="timeframe-tab">ALL</div></div>
</div>
<div class="orderbook">
<div class="ob-header"><div class="ob-col-header"><span>Bids</span><span>Size</span></div><div class="ob-col-header"><span>Price</span><span>Asks</span></div></div>
<div class="ob-grid">
<div class="ob-col">
<div class="ob-row bid" style="--depth: 22%"><span class="p">1.50</span><span>9.00</span></div>
<div class="ob-row bid" style="--depth: 24%"><span class="p">1.40</span><span>10.00</span></div>
<div class="ob-row bid" style="--depth: 100%"><span class="p">1.30</span><span>42.00</span></div>
<div class="ob-row bid" style="--depth: 76%"><span class="p">1.26</span><span>32.00</span></div>
<div class="ob-row bid" style="--depth: 24%"><span class="p">1.20</span><span>10.00</span></div>
</div>
<div class="ob-col">
<div class="ob-row ask" style="--depth: 100%"><span>15.00</span><span class="p">1.76</span></div>
<div class="ob-row ask" style="--depth: 93%"><span>14.00</span><span class="p">1.80</span></div>
<div class="ob-row ask" style="--depth: 66%"><span>10.00</span><span class="p">2.11</span></div>
<div class="ob-row ask" style="--depth: 33%"><span>5.00</span><span class="p">10.00</span></div>
<div class="ob-row ask" style="--depth: 20%"><span>3.00</span><span class="p">12.00</span></div>
</div>
</div>
</div>
<div class="trade-actions-split"><button class="btn-buy-sm">Buy</button><button class="btn-sell-sm">Sell</button></div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">05 · Trade · Advanced <span class="new">Chart added</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello"><em>Marketplace</em></div><div class="sub-label">Buy or auction NFTs</div></div><div class="header-actions"><button class="icon-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.3-4.3"/></svg></button><div class="avatar">A</div></div></div>
<div class="view-toggle"><span class="active"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/></svg>Browse</span><span><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3v18h18"/><path d="M7 14l4-4 4 4 6-6"/></svg>Analytics</span></div>
<div style="display: flex; gap: 6px; overflow-x: auto; padding-bottom: 14px; scrollbar-width: none;">
<div class="wallet-pill active" style="background: var(--bg-inverse); color: white; border-color: var(--bg-inverse);">All</div>
<div class="wallet-pill">Auction</div>
<div class="wallet-pill">Fixed</div>
<div class="wallet-pill">Ended</div>
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 12px;">
<div class="card" style="padding: 0; overflow: hidden; cursor: pointer;">
<div style="aspect-ratio: 1; background: linear-gradient(135deg, #FFEDD9, #FFD8B0); display: flex; align-items: center; justify-content: center; position: relative;">
<div style="position: absolute; top: 8px; left: 8px; padding: 3px 8px; border-radius: 100px; background: rgba(11,11,11,0.75); color: white; font-size: 9px; font-weight: 500; letter-spacing: 0.04em; text-transform: uppercase;">Fixed</div>
<div style="text-align:center;"><div style="font-family: 'Fraunces', serif; font-size: 44px; color: #EC6A1C; font-weight: 500; line-height: 1;">D</div><div style="font-size: 8px; letter-spacing: 0.2em; color: #7A4A1C; margin-top: 4px; font-weight: 600;">OWN IT · GROW IT</div></div>
</div>
<div style="padding: 12px;">
<div style="font-size: 13px; font-weight: 600;">DYNK #0042</div>
<div style="font-size: 11px; color: var(--text-secondary); margin-top: 1px;">Founder Wallet</div>
<div style="display: flex; justify-content: space-between; align-items: center; margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border);">
<div><div style="font-size: 10px; color: var(--text-tertiary); letter-spacing: 0.04em; text-transform: uppercase;">Price</div><div style="font-size: 13px; font-weight: 600; margin-top: 1px; font-feature-settings: 'tnum';">1,000 DYNK</div></div>
</div>
</div>
</div>

<div class="card" style="padding: 0; overflow: hidden; cursor: pointer;">
<div style="aspect-ratio: 1; background: linear-gradient(135deg, #FFD8B0, #FFC089); display: flex; align-items: center; justify-content: center; position: relative;">
<div style="position: absolute; top: 8px; left: 8px; padding: 3px 8px; border-radius: 100px; background: rgba(236,106,28,0.9); color: white; font-size: 9px; font-weight: 500; letter-spacing: 0.04em; text-transform: uppercase;">Auction</div>
<div style="text-align:center;"><div style="font-family: 'Fraunces', serif; font-size: 44px; color: #EC6A1C; font-weight: 500; line-height: 1;">D</div><div style="font-size: 8px; letter-spacing: 0.2em; color: #7A4A1C; margin-top: 4px; font-weight: 600;">OWN IT · GROW IT</div></div>
</div>
<div style="padding: 12px;">
<div style="font-size: 13px; font-weight: 600;">DYNK #0053</div>
<div style="font-size: 11px; color: var(--text-secondary); margin-top: 1px;">Founder Wallet</div>
<div style="display: flex; justify-content: space-between; align-items: center; margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border);">
<div><div style="font-size: 10px; color: var(--text-tertiary); letter-spacing: 0.04em; text-transform: uppercase;">Top bid</div><div style="font-size: 13px; font-weight: 600; margin-top: 1px; font-feature-settings: 'tnum';">17.30 USD</div></div>
</div>
</div>
</div>

<div class="card" style="padding: 0; overflow: hidden; cursor: pointer;">
<div style="aspect-ratio: 1; background: linear-gradient(135deg, #FFEDD9, #F5DDB8); display: flex; align-items: center; justify-content: center; position: relative;">
<div style="position: absolute; top: 8px; left: 8px; padding: 3px 8px; border-radius: 100px; background: rgba(107,107,102,0.85); color: white; font-size: 9px; font-weight: 500; letter-spacing: 0.04em; text-transform: uppercase;">Ended</div>
<div style="text-align:center;"><div style="font-family: 'Fraunces', serif; font-size: 44px; color: #EC6A1C; font-weight: 500; line-height: 1;">D</div><div style="font-size: 8px; letter-spacing: 0.2em; color: #7A4A1C; margin-top: 4px; font-weight: 600;">OWN IT · GROW IT</div></div>
</div>
<div style="padding: 12px;">
<div style="font-size: 13px; font-weight: 600;">DYNK #0026</div>
<div style="font-size: 11px; color: var(--text-secondary); margin-top: 1px;">Founder Wallet</div>
<div style="display: flex; justify-content: space-between; align-items: center; margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border);">
<div><div style="font-size: 10px; color: var(--text-tertiary); letter-spacing: 0.04em; text-transform: uppercase;">Sold for</div><div style="font-size: 13px; font-weight: 600; margin-top: 1px; font-feature-settings: 'tnum';">20 DYNK</div></div>
</div>
</div>
</div>

<div class="card" style="padding: 0; overflow: hidden; cursor: pointer;">
<div style="aspect-ratio: 1; background: linear-gradient(135deg, #FFD8B0, #FFC089); display: flex; align-items: center; justify-content: center; position: relative;">
<div style="position: absolute; top: 8px; left: 8px; padding: 3px 8px; border-radius: 100px; background: rgba(21,128,61,0.9); color: white; font-size: 9px; font-weight: 500; letter-spacing: 0.04em; text-transform: uppercase;">Live</div>
<div style="text-align:center;"><div style="font-family: 'Fraunces', serif; font-size: 44px; color: #EC6A1C; font-weight: 500; line-height: 1;">D</div><div style="font-size: 8px; letter-spacing: 0.2em; color: #7A4A1C; margin-top: 4px; font-weight: 600;">OWN IT · GROW IT</div></div>
</div>
<div style="padding: 12px;">
<div style="font-size: 13px; font-weight: 600;">DYNK #0049</div>
<div style="font-size: 11px; color: var(--text-secondary); margin-top: 1px;">Founder Wallet</div>
<div style="display: flex; justify-content: space-between; align-items: center; margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--border);">
<div><div style="font-size: 10px; color: var(--text-tertiary); letter-spacing: 0.04em; text-transform: uppercase;">Price</div><div style="font-size: 13px; font-weight: 600; margin-top: 1px; font-feature-settings: 'tnum';">17.30 USD</div></div>
</div>
</div>
</div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">12 · NFT Browse <span class="new">New</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello">NFT <em>Analytics</em></div><div class="sub-label">Market insights</div></div><div class="header-actions"><div class="avatar">A</div></div></div>
<div class="view-toggle"><span><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/></svg>Browse</span><span class="active"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3v18h18"/><path d="M7 14l4-4 4 4 6-6"/></svg>Analytics</span></div>
<div style="display: flex; gap: 4px; margin-bottom: 12px;"><div class="timeframe-tab">1D</div><div class="timeframe-tab active">1W</div><div class="timeframe-tab">1M</div><div class="timeframe-tab">1Y</div><div class="timeframe-tab">ALL</div></div>
<div class="card chart-card">
<div class="chart-header"><div>
<div class="label-xs">Volume bidded</div>
<div class="stat-big">$4,238<span class="unit">USD</span></div>
<div class="stat-big-secondary">2,450 DYNK</div>
<div class="balance-change" style="margin-top: 4px;"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round"><polyline points="5 12 12 5 19 12"/></svg>+18.4% vs last week</div>
</div></div>
<svg class="chart-svg" viewBox="0 0 300 100" preserveAspectRatio="none">
<defs><linearGradient id="volGrad2" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#EC6A1C" stop-opacity="0.3"/><stop offset="1" stop-color="#EC6A1C" stop-opacity="0"/></linearGradient></defs>
<path d="M0,80 L30,72 L60,78 L90,58 L120,62 L150,42 L180,50 L210,30 L240,38 L270,18 L300,22 L300,100 L0,100 Z" fill="url(#volGrad2)"/>
<path d="M0,80 L30,72 L60,78 L90,58 L120,62 L150,42 L180,50 L210,30 L240,38 L270,18 L300,22" stroke="#EC6A1C" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
<circle cx="270" cy="18" r="3" fill="#EC6A1C"/>
</svg>
<div style="display:flex; justify-content: space-between; font-size: 9px; color: var(--text-tertiary); font-family: 'Geist Mono', monospace; margin-top: 4px;"><span>Mon</span><span>Tue</span><span>Wed</span><span>Thu</span><span>Fri</span><span>Sat</span><span>Sun</span></div>
</div>
<div class="card chart-card">
<div class="chart-header"><div>
<div class="label-xs">Floor price</div>
<div class="stat-big">$493<span class="unit">USD</span></div>
<div class="stat-big-secondary">285 DYNK</div>
<div class="balance-change" style="margin-top: 4px; color: var(--danger);"><svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" style="transform: rotate(180deg);"><polyline points="5 12 12 5 19 12"/></svg>−3.2% vs last week</div>
</div></div>
<svg class="chart-svg" viewBox="0 0 300 100" preserveAspectRatio="none">
<defs><linearGradient id="floorGrad2" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#0B0B0B" stop-opacity="0.15"/><stop offset="1" stop-color="#0B0B0B" stop-opacity="0"/></linearGradient></defs>
<path d="M0,30 L30,38 L60,28 L90,42 L120,35 L150,55 L180,48 L210,62 L240,55 L270,68 L300,60 L300,100 L0,100 Z" fill="url(#floorGrad2)"/>
<path d="M0,30 L30,38 L60,28 L90,42 L120,35 L150,55 L180,48 L210,62 L240,55 L270,68 L300,60" stroke="#0B0B0B" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
<circle cx="300" cy="60" r="3" fill="#0B0B0B"/>
</svg>
</div>
<h2 class="section-title">Highest <em>sold</em> <span class="see-all">This week ›</span></h2>
<div class="card" style="padding: 4px 18px;">
<div class="analytic-row"><div class="l"><div class="analytic-rank top">1</div><div class="analytic-thumb">D</div><div><div class="analytic-name">DYNK #0007</div><div class="analytic-sub">Founder Wallet</div></div></div><div><div class="analytic-val">$21,625 USD</div><div class="analytic-val-usd">12,500 DYNK</div><div class="analytic-chg">+47%</div></div></div>
<div class="analytic-row"><div class="l"><div class="analytic-rank">2</div><div class="analytic-thumb">D</div><div><div class="analytic-name">DYNK #0042</div><div class="analytic-sub">Founder Wallet</div></div></div><div><div class="analytic-val">$14,186 USD</div><div class="analytic-val-usd">8,200 DYNK</div><div class="analytic-chg">+22%</div></div></div>
<div class="analytic-row"><div class="l"><div class="analytic-rank">3</div><div class="analytic-thumb">D</div><div><div class="analytic-name">DYNK #0019</div><div class="analytic-sub">Founder Wallet</div></div></div><div><div class="analytic-val">$9,429 USD</div><div class="analytic-val-usd">5,450 DYNK</div><div class="analytic-chg down">−8%</div></div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">13 · NFT Analytics <span class="new">USD added</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello"><em>Earn</em></div><div class="sub-label">Put your crypto to work</div></div><div class="header-actions"><div class="avatar">A</div></div></div>
<div class="hub-hero">
<div class="hub-hero-label">Total earned (all time)</div>
<div class="hub-hero-amt">0<span class="unit">DYNK</span></div>
<div class="hub-hero-sub">≈ $0.00 · Choose a way to earn below</div>
</div>
<h2 class="section-title" style="margin-top: 8px;">Ways to <em>earn</em></h2>
<div class="hub-list">
<div class="hub-row"><div class="hub-ic success"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg></div><div class="hub-content"><div class="hub-title">Stake</div><div class="hub-sub">Earn rewards on DYNK, SOL, ETH and more</div></div><div style="text-align: right; flex-shrink: 0;"><div style="font-size: 13px; font-weight: 600; color: var(--success); font-feature-settings: 'tnum';">Up to 10.5%</div><div style="font-size: 10px; color: var(--text-tertiary); margin-top: 2px;">APY</div></div></div>
<div class="hub-row"><div class="hub-ic accent"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 11h-6"/><path d="M19 8v6"/></svg></div><div class="hub-content"><div class="hub-title">Refer</div><div class="hub-sub">Invite friends · Earn across 3 levels</div></div><div style="text-align: right; flex-shrink: 0;"><div style="font-size: 13px; font-weight: 600; color: var(--accent); font-feature-settings: 'tnum';">10% / 5% / 2%</div><div style="font-size: 10px; color: var(--text-tertiary); margin-top: 2px;">Per level</div></div></div>
<div class="hub-row"><div class="hub-ic info"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="19" x2="12" y2="5"/><polyline points="5 12 12 5 19 12"/></svg></div><div class="hub-content"><div class="hub-title">Lend</div><div class="hub-sub">Supply assets · Earn interest from borrowers</div></div><div style="text-align: right; flex-shrink: 0;"><div style="font-size: 13px; font-weight: 600; color: var(--info); font-feature-settings: 'tnum';">4.20%</div><div style="font-size: 10px; color: var(--text-tertiary); margin-top: 2px;">Supply APY</div></div></div>
<div class="hub-row"><div class="hub-ic purple"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"/><polyline points="19 12 12 19 5 12"/></svg></div><div class="hub-content"><div class="hub-title">Borrow</div><div class="hub-sub">Borrow against your crypto · Keep your assets</div></div><div style="text-align: right; flex-shrink: 0;"><div style="font-size: 13px; font-weight: 600; color: var(--purple); font-feature-settings: 'tnum';">From 5.80%</div><div style="font-size: 10px; color: var(--text-tertiary); margin-top: 2px;">Borrow APR</div></div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">07 · Earn Hub <span class="new">New</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div class="page-title-sm"><em>Stake</em></div></div>
<div class="stake-hero">
<div class="hub-hero-label" style="position: relative;">DYNK staking</div>
<div class="apy-big">8.5<span class="unit">% APY</span></div>
<div style="font-size: 12px; opacity: 0.85; margin-top: 8px; position: relative;">Stake anytime · 7-day unstake period</div>
</div>

<div class="trade-input-card">
<div class="trade-input-label">Amount to stake</div>
<div class="trade-input-row"><input class="trade-input-amount" value="100" readonly><div class="token-chip"><div class="ti" style="background: linear-gradient(135deg, #EC6A1C, #F59E3B);">D</div>DYNK</div></div>
<div class="trade-hint"><span>Available: 24.97 DYNK</span><span class="link">Max</span></div>
</div>

<div class="card" style="margin-top: 16px;">
<div class="label-xs" style="margin-bottom: 12px;">You will earn</div>
<div class="calc-row"><span class="l">Estimated rewards / year</span><span class="r success">+8.50 DYNK</span></div>
<div class="calc-row"><span class="l">Paid daily</span><span class="r">~0.023 DYNK/day</span></div>
<div class="calc-row"><span class="l">Unstake period</span><span class="r">7 days</span></div>
</div>
<button class="big-cta success">Stake 100 DYNK</button>

<h2 class="section-title">Stake <em>other coins</em></h2>
<div class="card" style="padding: 4px 16px;">
<div class="market-row"><div class="token-icon token-sol">S</div><div class="market-info"><div class="market-name">Solana</div><div class="market-sub">SOL · Proof of Stake</div></div><div style="text-align: right;"><div class="market-apy-val">6.80%</div><div class="market-apy-lbl">APY</div></div></div>
<div class="market-row"><div class="token-icon token-eth">E</div><div class="market-info"><div class="market-name">Ethereum</div><div class="market-sub">ETH · Proof of Stake</div></div><div style="text-align: right;"><div class="market-apy-val">3.20%</div><div class="market-apy-lbl">APY</div></div></div>
<div class="market-row"><div class="token-icon" style="background: linear-gradient(135deg, #E84142, #B71C1C); font-size: 11px;">A</div><div class="market-info"><div class="market-name">Avalanche</div><div class="market-sub">AVAX · Proof of Stake</div></div><div style="text-align: right;"><div class="market-apy-val">7.40%</div><div class="market-apy-lbl">APY</div></div></div>
<div class="market-row"><div class="token-icon" style="background: linear-gradient(135deg, #0033AD, #001A66); font-size: 11px;">A</div><div class="market-info"><div class="market-name">Cardano</div><div class="market-sub">ADA · Proof of Stake</div></div><div style="text-align: right;"><div class="market-apy-val">4.10%</div><div class="market-apy-lbl">APY</div></div></div>
<div class="market-row"><div class="token-icon" style="background: linear-gradient(135deg, #E6007A, #BC0061); font-size: 11px;">P</div><div class="market-info"><div class="market-name">Polkadot</div><div class="market-sub">DOT · Proof of Stake</div></div><div style="text-align: right;"><div class="market-apy-val">10.50%</div><div class="market-apy-lbl">APY</div></div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">08 · Stake <span class="new">Updated</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div class="page-title-sm">Refer &amp; <em>earn</em></div></div>
<div class="hub-hero">
<div class="hub-hero-label">You've earned</div>
<div class="hub-hero-amt">0<span class="unit">DYNK</span></div>
<div class="hub-hero-sub">From 0 friends · Start inviting below</div>
</div>
<h2 class="section-title" style="margin-top: 8px;">Your <em>code</em></h2>
<div class="card">
<div class="refer-big-code"><span>8vhlcy4n</span><div class="icon-btn" style="width: 32px; height: 32px;"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg></div></div>
<button class="big-cta primary" style="margin-top: 4px;"><span style="display: inline-flex; align-items: center; gap: 8px;"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="18" cy="5" r="3"/><circle cx="6" cy="12" r="3"/><circle cx="18" cy="19" r="3"/><line x1="8.59" y1="13.51" x2="15.42" y2="17.49"/><line x1="15.41" y1="6.51" x2="8.59" y2="10.49"/></svg>Share invite link</span></button>
</div>
<h2 class="section-title">Rewards by <em>level</em></h2>
<div class="refer-reward-grid">
<div class="reward-tile"><div class="reward-level">Level 1</div><div class="reward-amt">10%</div><div class="reward-label">Direct invite</div></div>
<div class="reward-tile"><div class="reward-level">Level 2</div><div class="reward-amt">5%</div><div class="reward-label">Their invites</div></div>
<div class="reward-tile"><div class="reward-level">Level 3</div><div class="reward-amt">2%</div><div class="reward-label">Network</div></div>
</div>
<div class="card" style="background: var(--bg-card); padding: 18px;">
<div class="label-xs" style="margin-bottom: 8px;">Total referral rewards</div>
<div class="stat-big">$0.00<span class="unit">USD</span></div>
<div class="stat-big-secondary">0 DYNK · All time</div>
<svg class="chart-svg" viewBox="0 0 300 80" preserveAspectRatio="none" style="margin-top: 12px;">
<defs><linearGradient id="referGrad" x1="0" x2="0" y1="0" y2="1"><stop offset="0" stop-color="#EC6A1C" stop-opacity="0.3"/><stop offset="1" stop-color="#EC6A1C" stop-opacity="0"/></linearGradient></defs>
<path d="M0,70 L30,68 L60,65 L90,60 L120,58 L150,55 L180,50 L210,45 L240,38 L270,30 L300,22 L300,80 L0,80 Z" fill="url(#referGrad)"/>
<path d="M0,70 L30,68 L60,65 L90,60 L120,58 L150,55 L180,50 L210,45 L240,38 L270,30 L300,22" stroke="#EC6A1C" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
<circle cx="300" cy="22" r="3" fill="#EC6A1C"/>
</svg>
<div style="display:flex; justify-content: space-between; font-size: 9px; color: var(--text-tertiary); font-family: 'Geist Mono', monospace; margin-top: 4px;"><span>Jan</span><span>Feb</span><span>Mar</span><span>Apr</span></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">09 · Refer <span class="new">Updated</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div class="page-title-sm"><em>Lend</em></div></div>
<div class="card" style="background: var(--bg-inverse); color: white; border: none; margin-bottom: 16px;">
<div class="label-xs" style="color: rgba(255,255,255,0.5);">Your supplied</div>
<div style="font-family: 'Fraunces', serif; font-size: 32px; font-weight: 300; letter-spacing: -0.025em; margin-top: 4px;">$0.00</div>
<div style="font-size: 11px; opacity: 0.6; margin-top: 4px;">Earning 0.00 DYNK / day</div>
</div>
<h2 class="section-title" style="margin-top: 8px;">Supply <em>markets</em></h2>
<div class="card" style="padding: 4px 16px;">
<div class="market-row"><div class="token-icon token-usdc">U</div><div class="market-info"><div class="market-name">USDC</div><div class="market-sub">Low risk · Stable</div></div><div style="text-align: right;"><div class="market-apy-val">4.20%</div><div class="market-apy-lbl">Supply APY</div></div></div>
<div class="market-row"><div class="token-icon token-dynk">D</div><div class="market-info"><div class="market-name">DYNK</div><div class="market-sub">Medium risk · Native</div></div><div style="text-align: right;"><div class="market-apy-val">8.75%</div><div class="market-apy-lbl">Supply APY</div></div></div>
<div class="market-row"><div class="token-icon token-sol">S</div><div class="market-info"><div class="market-name">SOL</div><div class="market-sub">Medium risk · Volatile</div></div><div style="text-align: right;"><div class="market-apy-val">5.40%</div><div class="market-apy-lbl">Supply APY</div></div></div>
<div class="market-row"><div class="token-icon token-btc">₿</div><div class="market-info"><div class="market-name">wBTC</div><div class="market-sub">Medium risk · Volatile</div></div><div style="text-align: right;"><div class="market-apy-val">3.10%</div><div class="market-apy-lbl">Supply APY</div></div></div>
</div>
<div class="card" style="margin-top: 16px; background: var(--info-soft); border-color: transparent;">
<div style="display: flex; gap: 10px; align-items: flex-start;">
<div style="width:28px; height:28px; border-radius: 50%; background: var(--info); color: white; display:flex; align-items:center; justify-content:center; flex-shrink: 0;"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg></div>
<div><div style="font-size: 13px; font-weight: 600; color: var(--info);">How lending works</div><div style="font-size: 12px; color: var(--text-primary); margin-top: 4px; line-height: 1.5;">Supply crypto to the pool, earn interest from borrowers. Withdraw anytime. No lock-up.</div></div>
</div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">10 · Lend</div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div class="page-title-sm"><em>Borrow</em></div></div>
<div class="card" style="background: linear-gradient(135deg, #2d1a4a, #6D28D9); color: white; border: none; margin-bottom: 16px; position: relative; overflow: hidden;">
<div class="label-xs" style="color: rgba(255,255,255,0.5);">Available to borrow</div>
<div style="font-family: 'Fraunces', serif; font-size: 32px; font-weight: 300; letter-spacing: -0.025em; margin-top: 4px;">$0.00</div>
<div style="font-size: 11px; opacity: 0.7; margin-top: 4px;">Deposit collateral to unlock borrowing</div>
</div>

<h2 class="section-title" style="margin-top: 8px;">Borrow <em>markets</em></h2>
<div class="card" style="padding: 4px 16px;">
<div class="market-row"><div class="token-icon token-usdc">U</div><div class="market-info"><div class="market-name">USDC</div><div class="market-sub">Borrow against collateral</div></div><div style="text-align: right;"><div class="market-apy-val" style="color: var(--purple);">5.80%</div><div class="market-apy-lbl">Borrow APR</div></div></div>
<div class="market-row"><div class="token-icon token-dynk">D</div><div class="market-info"><div class="market-name">DYNK</div><div class="market-sub">Borrow against collateral</div></div><div style="text-align: right;"><div class="market-apy-val" style="color: var(--purple);">9.40%</div><div class="market-apy-lbl">Borrow APR</div></div></div>
<div class="market-row"><div class="token-icon token-sol">S</div><div class="market-info"><div class="market-name">SOL</div><div class="market-sub">Borrow against collateral</div></div><div style="text-align: right;"><div class="market-apy-val" style="color: var(--purple);">7.20%</div><div class="market-apy-lbl">Borrow APR</div></div></div>
<div class="market-row"><div class="token-icon token-btc">₿</div><div class="market-info"><div class="market-name">wBTC</div><div class="market-sub">Borrow against collateral</div></div><div style="text-align: right;"><div class="market-apy-val" style="color: var(--purple);">4.50%</div><div class="market-apy-lbl">Borrow APR</div></div></div>
</div>

<h2 class="section-title">Your <em>collateral</em></h2>
<div class="card" style="padding: 18px; text-align: center;">
<div style="width: 48px; height: 48px; border-radius: 50%; background: var(--bg-subtle); margin: 0 auto 10px; display: flex; align-items: center; justify-content: center; color: var(--text-tertiary);">
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
</div>
<div style="font-size: 13px; font-weight: 600;">No collateral deposited</div>
<div style="font-size: 11px; color: var(--text-secondary); margin-top: 4px; line-height: 1.5;">Deposit DYNK, SOL, or USDC to borrow up to 75% of its value.</div>
<button class="big-cta accent" style="margin-top: 14px;">Deposit collateral</button>
</div>

<div class="card" style="margin-top: 16px; background: var(--info-soft); border-color: transparent;">
<div style="display: flex; gap: 10px; align-items: flex-start;">
<div style="width:28px; height:28px; border-radius: 50%; background: var(--info); color: white; display:flex; align-items:center; justify-content:center; flex-shrink: 0;"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg></div>
<div><div style="font-size: 13px; font-weight: 600; color: var(--info);">How borrowing works</div><div style="font-size: 12px; color: var(--text-primary); margin-top: 4px; line-height: 1.5;">Lock up crypto as collateral, borrow against its value. Get cash without selling your assets.</div></div>
</div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">11 · Borrow <span class="new">New</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello"><em>Discover</em></div><div class="sub-label">Search the web · Explore apps</div></div><div class="header-actions"><div class="avatar">A</div></div></div>
<div class="google-search">
<div class="google-g"><svg width="18" height="18" viewBox="0 0 24 24"><path fill="#4285F4" d="M23.49 12.27c0-.79-.07-1.54-.19-2.27H12v4.51h6.44c-.28 1.49-1.12 2.75-2.38 3.6v3h3.86c2.26-2.08 3.57-5.15 3.57-8.84z"/><path fill="#34A853" d="M12 24c3.24 0 5.95-1.08 7.93-2.91l-3.86-3c-1.08.72-2.45 1.16-4.07 1.16-3.13 0-5.78-2.11-6.73-4.96H1.29v3.09C3.26 21.3 7.31 24 12 24z"/><path fill="#FBBC05" d="M5.27 14.29c-.25-.72-.38-1.49-.38-2.29s.14-1.57.38-2.29V6.62H1.29C.47 8.24 0 10.06 0 12s.47 3.76 1.29 5.38l3.98-3.09z"/><path fill="#EA4335" d="M12 4.75c1.77 0 3.35.61 4.6 1.8l3.42-3.42C17.95 1.19 15.24 0 12 0 7.31 0 3.26 2.7 1.29 6.62l3.98 3.09C6.22 6.86 8.87 4.75 12 4.75z"/></svg></div>
<div class="google-input">Search Google or enter URL</div>
<div class="google-mic"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2a3 3 0 0 0-3 3v7a3 3 0 0 0 6 0V5a3 3 0 0 0-3-3z"/><path d="M19 10v2a7 7 0 0 1-14 0v-2"/><line x1="12" y1="19" x2="12" y2="23"/></svg></div>
</div>
<div class="featured-app">
<div class="featured-label">Sponsored · Earn 500 DYNK</div>
<div class="featured-title">Try <em>Jupiter</em></div>
<div class="featured-desc">Complete one swap this week and earn DYNK rewards</div>
<button class="featured-cta">Launch app →</button>
</div>
<h2 class="section-title">DeFi <em>apps</em> <span class="see-all">All ›</span></h2>
<div class="apps-grid">
<div class="app-tile"><div class="app-tile-ic" style="background: linear-gradient(135deg, #9945FF, #14F195);">Jp</div><div class="app-tile-name">Jupiter</div><div class="app-tile-cat">Aggregator</div></div>
<div class="app-tile"><div class="app-tile-ic" style="background: linear-gradient(135deg, #FF006E, #8338EC);">Rd</div><div class="app-tile-name">Raydium</div><div class="app-tile-cat">DEX</div></div>
<div class="app-tile"><div class="app-tile-ic" style="background: linear-gradient(135deg, #3DDCFF, #0075FF);">Mr</div><div class="app-tile-name">Marinade</div><div class="app-tile-cat">Staking</div></div>
<div class="app-tile"><div class="app-tile-ic" style="background: linear-gradient(135deg, #FFA726, #FF6F00);">Ka</div><div class="app-tile-name">Kamino</div><div class="app-tile-cat">Lending</div></div>
<div class="app-tile"><div class="app-tile-ic" style="background: linear-gradient(135deg, #00C9A7, #0077B6);">Dr</div><div class="app-tile-name">Drift</div><div class="app-tile-cat">Perps</div></div>
<div class="app-tile"><div class="app-tile-ic" style="background: linear-gradient(135deg, #F72585, #7209B7);">Me</div><div class="app-tile-name">Magic Eden</div><div class="app-tile-cat">NFTs</div></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">14 · Discover <span class="new">Google search top</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="app-header"><div><div class="hello"><em>Assistance</em></div><div class="sub-label">Support, settings &amp; governance</div></div><div class="header-actions"><div class="avatar">A</div></div></div>
<div class="hub-hero" style="background: linear-gradient(135deg, #EC6A1C, #D85A10); margin-bottom: 12px;">
<div class="hub-hero-label" style="opacity: 0.85;">AI Assistant</div>
<div style="font-family: 'Fraunces', serif; font-size: 26px; font-weight: 400; letter-spacing: -0.02em; line-height: 1.2; margin-top: 6px; position: relative;">Ask DYNK <em style="font-style: italic; font-weight: 300;">anything</em></div>
<div class="hub-hero-sub" style="opacity: 0.9;">Get help with trades, explain crypto terms, track your portfolio.</div>
<button class="featured-cta" style="background: white; color: var(--accent); margin-top: 14px;"><span style="display: inline-flex; align-items: center; gap: 6px;"><svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>Start chat</span></button>
</div>
<h2 class="section-title" style="margin-top: 12px;">Account</h2>
<div class="hub-list">
<div class="hub-row"><div class="hub-ic purple"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M6 9l6-6 6 6"/><path d="M6 15l6 6 6-6"/><line x1="12" y1="3" x2="12" y2="21"/></svg></div><div class="hub-content"><div class="hub-title">Governance <span class="hub-tag" style="background: var(--purple-soft); color: var(--purple);">3 active</span></div><div class="hub-sub">Shape DYNK's future · NFT wallet holders vote</div></div><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><polyline points="9 18 15 12 9 6"/></svg></div>
<div class="hub-row"><div class="hub-ic success"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg></div><div class="hub-content"><div class="hub-title">Security</div><div class="hub-sub">ZK multi-auth, biometrics, backup</div></div><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><polyline points="9 18 15 12 9 6"/></svg></div>
<div class="hub-row"><div class="hub-ic dark"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 1 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 1 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 1 1-2.83-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 1 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 1 1 2.83-2.83l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 1 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 1 1 2.83 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 1 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg></div><div class="hub-content"><div class="hub-title">Settings</div><div class="hub-sub">Preferences, currency, notifications</div></div><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><polyline points="9 18 15 12 9 6"/></svg></div>
<div class="hub-row"><div class="hub-ic info"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg></div><div class="hub-content"><div class="hub-title">Help Center</div><div class="hub-sub">Guides, FAQs, contact support</div></div><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color: var(--text-tertiary);"><polyline points="9 18 15 12 9 6"/></svg></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">15 · Assist <span class="new">Governance entry</span></div></div>
<div class="screen-wrap"><div class="phone"><div class="notch"></div>
<div class="status-bar"><span>9:41</span><div class="status-icons"><svg width="17" height="11" viewBox="0 0 17 11" fill="currentColor"><rect x="0" y="6" width="3" height="5" rx="0.5"/><rect x="4.5" y="4" width="3" height="7" rx="0.5"/><rect x="9" y="2" width="3" height="9" rx="0.5"/><rect x="13.5" y="0" width="3" height="11" rx="0.5"/></svg></div></div>
<div class="screen-body"><div class="screen-scroll" style="padding-top: 16px;">
<div class="back-header"><div class="back-btn"><svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg></div><div class="page-title-sm"><em>Governance</em></div></div>
<div class="gov-banner">
<div class="gov-banner-title">Shape the future of <em>DYNK</em></div>
<div class="gov-banner-sub">3 active proposals · 126 voters · 2,100 eligible NFT wallets</div>
</div>
<div class="gov-voting-notice">
<div class="ic"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg></div>
<div class="gov-voting-notice-text"><strong>You can view all proposals.</strong> To vote, you'll need an NFT wallet. <span style="color: var(--accent); font-weight: 600;">Get one ›</span></div>
</div>
<h2 class="section-title" style="margin-top: 8px;">Active <em>proposals</em></h2>
<div class="proposal-card">
<div class="proposal-meta"><span class="proposal-status active">Voting open</span><span>· Ends in 3 days</span></div>
<div class="proposal-title">Reduce network transaction fee from $0.01 to $0.005</div>
<div class="proposal-sub">Proposed by NFT #0042 · Lower fees to drive volume growth</div>
<div class="vote-bar"><div class="yes" style="flex: 72;"></div><div class="no" style="flex: 18;"></div><div class="abstain" style="flex: 10;"></div></div>
<div class="vote-legend"><span class="yes-t">72% Yes · 1,512 votes</span><span class="no-t">18% No · 378</span></div>
</div>
<div class="proposal-card">
<div class="proposal-meta"><span class="proposal-status active">Voting open</span><span>· Ends in 5 days</span></div>
<div class="proposal-title">Partner with Tangem for bundled cold wallet cards</div>
<div class="proposal-sub">Offer a discounted DYNK-branded Tangem card to new users</div>
<div class="vote-bar"><div class="yes" style="flex: 85;"></div><div class="no" style="flex: 9;"></div><div class="abstain" style="flex: 6;"></div></div>
<div class="vote-legend"><span class="yes-t">85% Yes · 1,785 votes</span><span class="no-t">9% No · 189</span></div>
</div>
<div class="proposal-card">
<div class="proposal-meta"><span class="proposal-status active">Voting open</span><span>· Ends in 7 days</span></div>
<div class="proposal-title">Allocate 100k DYNK from treasury for marketing Q3</div>
<div class="proposal-sub">Social campaigns targeting non-crypto users aged 30+</div>
<div class="vote-bar"><div class="yes" style="flex: 48;"></div><div class="no" style="flex: 42;"></div><div class="abstain" style="flex: 10;"></div></div>
<div class="vote-legend"><span class="yes-t">48% Yes · 1,008 votes</span><span class="no-t">42% No · 882</span></div>
</div>
<h2 class="section-title">Recently <em>closed</em></h2>
<div class="proposal-card">
<div class="proposal-meta"><span class="proposal-status ended">Passed</span><span>· Closed 2 weeks ago</span></div>
<div class="proposal-title">Add Jupiter aggregator for alt-coin swaps</div>
<div class="proposal-sub">Enable BTC, ETH, SOL trading via Jupiter</div>
<div class="vote-bar"><div class="yes" style="flex: 91;"></div><div class="no" style="flex: 5;"></div><div class="abstain" style="flex: 4;"></div></div>
<div class="vote-legend"><span class="yes-t">91% Yes · 1,911 votes</span><span class="no-t">5% No · 105</span></div>
</div>
</div>
<nav class="bottom-nav">
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12l9-9 9 9"/><path d="M5 10v10a1 1 0 0 0 1 1h3v-6h6v6h3a1 1 0 0 0 1-1V10"/></svg>Home</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3l4 4-4 4"/><path d="M21 7H7"/><path d="M7 21l-4-4 4-4"/><path d="M3 17h14"/></svg>Trade</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2l3 7 7 1-5 5 1 7-6-3-6 3 1-7-5-5 7-1 3-7z"/></svg>Earn</div>
<div class="nav-item"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M16.24 7.76l-2.12 6.36-6.36 2.12 2.12-6.36 6.36-2.12z"/></svg>Discover</div>
<div class="nav-item active"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>Assist</div>
</nav></div></div><div class="screen-label">16 · Governance</div></div>
</div>

<section style="max-width: 1600px; margin: 80px auto 0; padding: 40px; background: var(--bg-card); border: 1px solid var(--border); border-radius: 22px;">
<h2 style="font-family: 'Fraunces', serif; font-size: 28px; font-weight: 400; letter-spacing: -0.02em; margin-bottom: 20px;">What <em style="font-style: italic; font-weight: 300;">changed</em> in v3</h2>
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 24px; margin-top: 20px;">
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Three wallet tiers</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Everyday (transactional) · Savings (isolated key for safety) · NFT Wallet (Genesis holders with fee share, governance, boosted referrals). Each gets its own home view.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Tangem cold wallet</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Promo card on Everyday home. Visualised as a physical Tangem card with DYNK branding. Tap-to-sign NFC.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Trade · Simple</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">DYNK featured card at top · Alt coins (BTC/ETH/SOL/USDC) listed below via Jupiter · Network fee shown as $0.01 · Slippage removed from user view.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Trade · Advanced</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Full price chart with 1H/1D/1W/1M/1Y/ALL timeframes. Order book kept for power users.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Send — bank-style</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Contacts flow: favourites, recents, all contacts. Add new by QR scan, username, or pasted address. Nicknames like "Mum" and "Tom — roommate" replace raw addresses.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">NFT Analytics</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Volume bidded and floor price now show USD primary, DYNK secondary. Rankings, charts, % change vs previous period.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Earn detail pages</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Stake (30/60/90-day terms with earnings calculator), Refer (code + share + level rewards + NFT bonus callout), Lend/Borrow (supply markets with APY).</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Governance in Assist</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Everyday users can view proposals with vote bars · Clear "get NFT wallet to vote" notice drives NFT demand · 3 live proposals + closed archive.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">Discover · Google + DeFi</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Google search bar up top as requested (test feature). DeFi apps grid below with sponsored slot — AI stays in Assist for now.</p></div>
<div><h3 style="font-size: 13px; font-weight: 600; margin-bottom: 6px;">What's next</h3><p style="font-size: 13px; color: var(--text-secondary); line-height: 1.5;">Ready to design next: Send amount entry + confirm, NFT detail view, Deposit flow, AI chat screen, Governance proposal detail with voting, Buy Jupiter alt coin flow, Onboarding.</p></div>
</div>
</section>

</body>
</html>
