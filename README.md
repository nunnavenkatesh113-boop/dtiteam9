<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>BuildLink — Labor Marketplace</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;0,9..40,800;1,9..40,400&family=JetBrains+Mono:wght@400;500;600&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet"/>

<style>
/* ============================================================
   CSS CUSTOM PROPERTIES — DESIGN TOKENS
   ============================================================ */
:root {
  --white: #FFFFFF;
  --off-white: #F7F6F3;
  --gray-50: #F4F3F0;
  --gray-100: #E8E6E1;
  --gray-200: #D0CEC8;
  --gray-300: #ABAAA4;
  --gray-400: #6B6A65;
  --gray-500: #4A4945;
  --gray-600: #333230;
  --charcoal: #1E1D1B;
  --black: #0F0F0E;

  --amber: #E8800A;
  --amber-light: #F5A033;
  --amber-dark: #C46A00;
  --amber-bg: #FFF4E6;
  --amber-bg-2: #FDEBD0;

  --green: #2D7A4F;
  --green-bg: #E8F5EE;
  --red: #C0392B;
  --red-bg: #FDECEA;
  --blue: #1A5FA8;
  --blue-bg: #E8F0FA;
  --purple: #6B3FA0;
  --purple-bg: #F0EAFA;

  --shadow-sm: 0 1px 3px rgba(0,0,0,0.07), 0 1px 2px rgba(0,0,0,0.05);
  --shadow-md: 0 4px 12px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.05);
  --shadow-lg: 0 8px 30px rgba(0,0,0,0.10), 0 4px 8px rgba(0,0,0,0.06);
  --shadow-xl: 0 16px 50px rgba(0,0,0,0.13), 0 8px 16px rgba(0,0,0,0.07);

  --radius-sm: 6px;
  --radius-md: 10px;
  --radius-lg: 16px;
  --radius-xl: 22px;
  --radius-full: 9999px;

  --nav-h: 64px;
  --font-body: 'DM Sans', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --font-display: 'DM Serif Display', serif;

  --transition: 150ms ease;
}

/* ============================================================
   RESET & BASE
   ============================================================ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; -webkit-font-smoothing: antialiased; }
body {
  font-family: var(--font-body);
  background: var(--off-white);
  color: var(--charcoal);
  font-size: 15px;
  line-height: 1.6;
  min-height: 100vh;
}
img { display: block; max-width: 100%; }
button { cursor: pointer; font-family: var(--font-body); border: none; background: none; }
input, select, textarea { font-family: var(--font-body); font-size: 15px; }
a { color: inherit; text-decoration: none; }
ul { list-style: none; }

/* ============================================================
   PAGE ROUTING — VISIBILITY
   ============================================================ */
.page { display: none; min-height: 100vh; }
.page.active { display: block; }

/* ============================================================
   NAVIGATION
   ============================================================ */
.nav {
  position: sticky;
  top: 0;
  z-index: 900;
  height: var(--nav-h);
  background: rgba(255,255,255,0.92);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(232,230,225,0.8);
  box-shadow: 0 1px 20px rgba(0,0,0,0.06);
  display: flex;
  align-items: center;
  padding: 0 24px;
  transition: box-shadow 0.3s;
}
.nav-inner {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
}
.nav-logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 800;
  font-size: 18px;
  color: var(--charcoal);
  letter-spacing: -0.3px;
  cursor: pointer;
}
.nav-logo-mark {
  width: 32px; height: 32px;
  background: var(--amber);
  border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center;
  color: white;
  font-size: 15px;
  font-weight: 800;
}
.nav-links {
  display: flex;
  align-items: center;
  gap: 4px;
}
.nav-link {
  padding: 7px 14px;
  border-radius: var(--radius-sm);
  font-weight: 500;
  font-size: 14px;
  color: var(--gray-500);
  transition: background var(--transition), color var(--transition);
  cursor: pointer;
}
.nav-link:hover { background: var(--gray-50); color: var(--charcoal); }
.nav-link.active { color: var(--amber); font-weight: 600; }
.nav-actions { display: flex; align-items: center; gap: 10px; }
.nav-role-badge {
  padding: 4px 10px;
  border-radius: var(--radius-full);
  font-size: 12px;
  font-weight: 600;
  background: var(--amber-bg);
  color: var(--amber-dark);
  border: 1px solid var(--amber-bg-2);
  letter-spacing: 0.02em;
}
.nav-hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  padding: 4px;
  cursor: pointer;
}
.nav-hamburger span {
  display: block;
  width: 22px; height: 2px;
  background: var(--charcoal);
  border-radius: 2px;
  transition: var(--transition);
}

/* ============================================================
   BUTTONS
   ============================================================ */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 10px 20px;
  border-radius: var(--radius-md);
  font-weight: 600;
  font-size: 14px;
  transition: all var(--transition);
  white-space: nowrap;
  cursor: pointer;
  border: 1.5px solid transparent;
}
.btn-primary {
  background: var(--amber);
  color: white;
  border-color: var(--amber);
}
.btn-primary:hover { background: var(--amber-dark); border-color: var(--amber-dark); transform: translateY(-1px); box-shadow: 0 4px 12px rgba(232,128,10,0.28); }
.btn-secondary {
  background: var(--white);
  color: var(--charcoal);
  border-color: var(--gray-200);
}
.btn-secondary:hover { border-color: var(--gray-300); background: var(--gray-50); }
.btn-dark {
  background: var(--charcoal);
  color: white;
  border-color: var(--charcoal);
}
.btn-dark:hover { background: var(--black); transform: translateY(-1px); }
.btn-ghost { color: var(--gray-400); }
.btn-ghost:hover { color: var(--charcoal); background: var(--gray-50); }
.btn-danger { background: var(--red-bg); color: var(--red); border-color: var(--red); }
.btn-success { background: var(--green-bg); color: var(--green); border-color: var(--green); }
.btn-sm { padding: 6px 14px; font-size: 13px; border-radius: var(--radius-sm); }
.btn-lg { padding: 14px 28px; font-size: 16px; border-radius: var(--radius-lg); }
.btn-full { width: 100%; }
.btn-icon { padding: 8px; border-radius: var(--radius-sm); }

/* ============================================================
   CARDS
   ============================================================ */
.card {
  background: var(--white);
  border-radius: var(--radius-lg);
  border: 1px solid var(--gray-100);
  box-shadow: var(--shadow-sm);
  overflow: hidden;
}
.card-pad { padding: 24px; }
.card-header {
  padding: 20px 24px;
  border-bottom: 1px solid var(--gray-100);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
}
.card-title { font-size: 16px; font-weight: 700; color: var(--charcoal); }
.card-sub { font-size: 13px; color: var(--gray-400); margin-top: 2px; }

/* ============================================================
   FORM ELEMENTS
   ============================================================ */
.form-group { display: flex; flex-direction: column; gap: 6px; }
.form-label {
  font-size: 13px;
  font-weight: 600;
  color: var(--gray-500);
  letter-spacing: 0.02em;
}
.form-label .req { color: var(--amber); margin-left: 2px; }
.form-input, .form-select, .form-textarea {
  width: 100%;
  padding: 10px 14px;
  border: 1.5px solid var(--gray-200);
  border-radius: var(--radius-md);
  background: var(--white);
  color: var(--charcoal);
  font-size: 14px;
  transition: border-color var(--transition), box-shadow var(--transition);
  outline: none;
}
.form-input:focus, .form-select:focus, .form-textarea:focus {
  border-color: var(--amber);
  box-shadow: 0 0 0 3px rgba(232,128,10,0.12);
}
.form-input::placeholder, .form-textarea::placeholder { color: var(--gray-300); }
.form-textarea { resize: vertical; min-height: 90px; }
.form-select { appearance: none; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='7' viewBox='0 0 12 7'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%236B6A65' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 12px center; padding-right: 36px; }
.form-hint { font-size: 12px; color: var(--gray-400); }
.form-error { font-size: 12px; color: var(--red); display: none; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.input-group { position: relative; }
.input-group .form-input { padding-left: 36px; }
.input-group-icon {
  position: absolute;
  left: 11px;
  top: 50%;
  transform: translateY(-50%);
  color: var(--gray-300);
  font-size: 16px;
  pointer-events: none;
}
.input-prefix {
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
  color: var(--gray-400);
  font-size: 13px;
  font-weight: 600;
}
.form-input.has-prefix { padding-left: 28px; }

/* ============================================================
   TOGGLE SWITCH
   ============================================================ */
.toggle-wrap {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 16px;
  background: var(--gray-50);
  border-radius: var(--radius-md);
  border: 1.5px solid var(--gray-100);
}
.toggle-label-text { font-size: 14px; font-weight: 500; color: var(--charcoal); }
.toggle-sub { font-size: 12px; color: var(--gray-400); }
.toggle-switch {
  position: relative;
  width: 44px;
  height: 24px;
  flex-shrink: 0;
  margin-left: auto;
}
.toggle-switch input { opacity: 0; width: 0; height: 0; }
.toggle-slider {
  position: absolute;
  inset: 0;
  background: var(--gray-200);
  border-radius: var(--radius-full);
  cursor: pointer;
  transition: background var(--transition);
}
.toggle-slider::before {
  content: '';
  position: absolute;
  left: 3px;
  top: 3px;
  width: 18px;
  height: 18px;
  background: white;
  border-radius: 50%;
  transition: transform var(--transition);
  box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
.toggle-switch input:checked + .toggle-slider { background: var(--green); }
.toggle-switch input:checked + .toggle-slider::before { transform: translateX(20px); }

/* ============================================================
   SKILL TAGS
   ============================================================ */
.skill-tags-wrap {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  padding: 12px;
  background: var(--gray-50);
  border-radius: var(--radius-md);
  border: 1.5px solid var(--gray-200);
  min-height: 54px;
}
.skill-tag {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 5px 12px;
  border-radius: var(--radius-full);
  font-size: 13px;
  font-weight: 500;
  background: var(--white);
  color: var(--gray-500);
  border: 1.5px solid var(--gray-200);
  cursor: pointer;
  transition: all var(--transition);
  user-select: none;
}
.skill-tag:hover { border-color: var(--amber); color: var(--amber-dark); }
.skill-tag.selected {
  background: var(--amber-bg);
  border-color: var(--amber);
  color: var(--amber-dark);
  font-weight: 600;
}
.skill-tag.selected::before { content: '✓ '; }

/* ============================================================
   BADGES & STATUS
   ============================================================ */
.badge {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 3px 10px;
  border-radius: var(--radius-full);
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.02em;
}
.badge-green { background: var(--green-bg); color: var(--green); }
.badge-amber { background: var(--amber-bg); color: var(--amber-dark); }
.badge-red { background: var(--red-bg); color: var(--red); }
.badge-blue { background: var(--blue-bg); color: var(--blue); }
.badge-purple { background: var(--purple-bg); color: var(--purple); }
.badge-gray { background: var(--gray-100); color: var(--gray-500); }
.badge-dot::before {
  content: '';
  display: block;
  width: 6px; height: 6px;
  border-radius: 50%;
  background: currentColor;
}

/* ============================================================
   RATING STARS
   ============================================================ */
.stars { display: inline-flex; gap: 2px; color: var(--amber); font-size: 14px; }
.stars .half { opacity: 0.5; }
.rating-wrap { display: flex; align-items: center; gap: 6px; }
.rating-num { font-family: var(--font-mono); font-size: 13px; font-weight: 500; color: var(--gray-500); }

/* ============================================================
   RELIABILITY SCORE BADGE
   ============================================================ */
.reliability-badge {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 6px 12px;
  background: var(--green-bg);
  border-radius: var(--radius-full);
  border: 1px solid rgba(45,122,79,0.2);
}
.reliability-score {
  font-family: var(--font-mono);
  font-size: 16px;
  font-weight: 600;
  color: var(--green);
}
.reliability-label { font-size: 11px; font-weight: 600; color: var(--green); letter-spacing: 0.04em; text-transform: uppercase; }

/* ============================================================
   AVATAR
   ============================================================ */
.avatar {
  border-radius: var(--radius-full);
  background: var(--gray-200);
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  color: var(--white);
  flex-shrink: 0;
  overflow: hidden;
}
.avatar-amber { background: linear-gradient(135deg, var(--amber), var(--amber-dark)); }
.avatar-blue { background: linear-gradient(135deg, #1A5FA8, #0D3D72); }
.avatar-green { background: linear-gradient(135deg, var(--green), #1a5236); }
.avatar-sm { width: 36px; height: 36px; font-size: 14px; }
.avatar-md { width: 48px; height: 48px; font-size: 18px; }
.avatar-lg { width: 72px; height: 72px; font-size: 28px; }
.avatar-xl { width: 96px; height: 96px; font-size: 36px; }

/* ============================================================
   STAT CARDS
   ============================================================ */
.stat-card {
  background: var(--white);
  border-radius: var(--radius-lg);
  border: 1px solid var(--gray-100);
  padding: 20px;
  box-shadow: var(--shadow-sm);
}
.stat-icon {
  width: 40px; height: 40px;
  border-radius: var(--radius-md);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  margin-bottom: 14px;
}
.stat-icon-amber { background: var(--amber-bg); }
.stat-icon-green { background: var(--green-bg); }
.stat-icon-blue { background: var(--blue-bg); }
.stat-icon-purple { background: var(--purple-bg); }
.stat-label { font-size: 12px; font-weight: 600; color: var(--gray-400); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 4px; }
.stat-value { font-family: var(--font-mono); font-size: 26px; font-weight: 600; color: var(--charcoal); line-height: 1.2; }
.stat-delta { font-size: 12px; color: var(--green); font-weight: 500; margin-top: 4px; }
.stat-delta.neg { color: var(--red); }

/* ============================================================
   DIVIDER
   ============================================================ */
.divider { height: 1px; background: var(--gray-100); margin: 20px 0; }
.divider-text { display: flex; align-items: center; gap: 12px; color: var(--gray-300); font-size: 13px; font-weight: 500; margin: 20px 0; }
.divider-text::before, .divider-text::after { content: ''; flex: 1; height: 1px; background: var(--gray-100); }

/* ============================================================
   MODAL OVERLAY
   ============================================================ */
.modal-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.42);
  backdrop-filter: blur(4px);
  z-index: 1000;
  align-items: center;
  justify-content: center;
  padding: 20px;
}
.modal-overlay.open { display: flex; }
.modal-box {
  background: var(--white);
  border-radius: var(--radius-xl);
  box-shadow: var(--shadow-xl);
  width: 100%;
  max-width: 540px;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
}
.modal-header {
  padding: 22px 24px 18px;
  border-bottom: 1px solid var(--gray-100);
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 12px;
  position: sticky;
  top: 0;
  background: var(--white);
  border-radius: var(--radius-xl) var(--radius-xl) 0 0;
}
.modal-title { font-size: 18px; font-weight: 700; color: var(--charcoal); }
.modal-sub { font-size: 13px; color: var(--gray-400); margin-top: 2px; }
.modal-close {
  width: 30px; height: 30px;
  border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center;
  color: var(--gray-400);
  font-size: 20px;
  flex-shrink: 0;
  cursor: pointer;
  transition: background var(--transition);
}
.modal-close:hover { background: var(--gray-50); color: var(--charcoal); }
.modal-body { padding: 24px; display: flex; flex-direction: column; gap: 18px; }
.modal-footer {
  padding: 18px 24px;
  border-top: 1px solid var(--gray-100);
  display: flex;
  gap: 10px;
  justify-content: flex-end;
  position: sticky;
  bottom: 0;
  background: var(--white);
  border-radius: 0 0 var(--radius-xl) var(--radius-xl);
}

/* ============================================================
   TABS
   ============================================================ */
.tabs { display: flex; border-bottom: 1.5px solid var(--gray-100); gap: 0; overflow-x: auto; }
.tab-item {
  padding: 12px 20px;
  font-size: 14px;
  font-weight: 500;
  color: var(--gray-400);
  border-bottom: 2px solid transparent;
  margin-bottom: -1.5px;
  cursor: pointer;
  transition: color var(--transition);
  white-space: nowrap;
}
.tab-item:hover { color: var(--charcoal); }
.tab-item.active { color: var(--amber); border-bottom-color: var(--amber); font-weight: 600; }
.tab-panel { display: none; }
.tab-panel.active { display: block; }

/* ============================================================
   LABORER CARD (search results)
   ============================================================ */
.laborer-card {
  background: var(--white);
  border: 1px solid var(--gray-100);
  border-radius: var(--radius-lg);
  padding: 20px;
  box-shadow: var(--shadow-sm);
  transition: box-shadow var(--transition), transform var(--transition);
  cursor: pointer;
}
.laborer-card:hover { box-shadow: var(--shadow-md); transform: translateY(-2px); }
.laborer-card-top { display: flex; gap: 14px; align-items: flex-start; }
.laborer-card-info { flex: 1; }
.laborer-name { font-size: 16px; font-weight: 700; color: var(--charcoal); margin-bottom: 2px; }
.laborer-title { font-size: 13px; color: var(--gray-400); margin-bottom: 8px; }
.laborer-meta { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 10px; }
.laborer-rate {
  font-family: var(--font-mono);
  font-size: 17px;
  font-weight: 600;
  color: var(--charcoal);
}
.laborer-rate span { font-size: 12px; font-weight: 400; color: var(--gray-400); }
.laborer-card-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 16px;
  padding-top: 14px;
  border-top: 1px solid var(--gray-100);
  gap: 10px;
  flex-wrap: wrap;
}
.same-day-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 5px 12px;
  border-radius: var(--radius-full);
  font-size: 12px;
  font-weight: 700;
  background: var(--amber);
  color: white;
  letter-spacing: 0.02em;
  transition: background var(--transition);
}
.same-day-btn:hover { background: var(--amber-dark); }

/* ============================================================
   FILTER SIDEBAR
   ============================================================ */
.filter-wrap {
  background: var(--white);
  border-radius: var(--radius-lg);
  border: 1px solid var(--gray-100);
  box-shadow: var(--shadow-sm);
  overflow: hidden;
}
.filter-section { padding: 18px; border-bottom: 1px solid var(--gray-100); }
.filter-section:last-child { border-bottom: none; }
.filter-title { font-size: 13px; font-weight: 700; color: var(--gray-500); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 12px; }
.filter-checkbox-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 5px 0;
  font-size: 14px;
  color: var(--gray-600);
  cursor: pointer;
}
.filter-checkbox-item input[type="checkbox"] {
  width: 16px; height: 16px;
  border: 1.5px solid var(--gray-300);
  border-radius: 4px;
  accent-color: var(--amber);
  cursor: pointer;
}
.range-slider { width: 100%; accent-color: var(--amber); cursor: pointer; }
.range-vals { display: flex; justify-content: space-between; font-family: var(--font-mono); font-size: 12px; color: var(--gray-400); margin-top: 4px; }

/* ============================================================
   BOOKING STATUS TIMELINE
   ============================================================ */
.booking-status-list { display: flex; flex-direction: column; gap: 0; }
.booking-status-item { display: flex; gap: 16px; }
.booking-status-left { display: flex; flex-direction: column; align-items: center; }
.booking-status-dot {
  width: 14px; height: 14px;
  border-radius: 50%;
  background: var(--gray-200);
  border: 2px solid var(--gray-200);
  flex-shrink: 0;
  margin-top: 3px;
}
.booking-status-dot.done { background: var(--green); border-color: var(--green); }
.booking-status-dot.active { background: var(--amber); border-color: var(--amber); box-shadow: 0 0 0 4px rgba(232,128,10,0.18); }
.booking-status-line {
  width: 2px;
  flex: 1;
  background: var(--gray-100);
  min-height: 32px;
}
.booking-status-line.done { background: var(--green); }
.booking-status-content { padding-bottom: 28px; flex: 1; }
.booking-status-title { font-size: 14px; font-weight: 600; color: var(--charcoal); margin-bottom: 2px; }
.booking-status-meta { font-size: 12px; color: var(--gray-400); }
.booking-status-item:last-child .booking-status-content { padding-bottom: 0; }

/* ============================================================
   JOB HISTORY ROW
   ============================================================ */
.job-row {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 14px 0;
  border-bottom: 1px solid var(--gray-100);
}
.job-row:last-child { border-bottom: none; }
.job-row-icon {
  width: 38px; height: 38px;
  background: var(--gray-50);
  border-radius: var(--radius-md);
  display: flex; align-items: center; justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}
.job-row-info { flex: 1; }
.job-row-title { font-size: 14px; font-weight: 600; color: var(--charcoal); }
.job-row-meta { font-size: 12px; color: var(--gray-400); margin-top: 2px; }
.job-row-amount { font-family: var(--font-mono); font-size: 14px; font-weight: 600; color: var(--charcoal); text-align: right; }
.job-row-date { font-size: 11px; color: var(--gray-300); text-align: right; margin-top: 2px; }

/* ============================================================
   SEARCH BAR
   ============================================================ */
.search-bar {
  display: flex;
  gap: 0;
  background: var(--white);
  border: 1.5px solid var(--gray-200);
  border-radius: var(--radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-md);
  transition: border-color var(--transition);
}
.search-bar:focus-within { border-color: var(--amber); }
.search-input {
  flex: 1;
  border: none;
  outline: none;
  padding: 14px 18px;
  font-size: 15px;
  background: transparent;
  color: var(--charcoal);
}
.search-input::placeholder { color: var(--gray-300); }
.search-divider { width: 1px; background: var(--gray-100); margin: 10px 0; }
.search-btn {
  padding: 12px 20px;
  background: var(--amber);
  color: white;
  font-weight: 700;
  font-size: 14px;
  border: none;
  cursor: pointer;
  transition: background var(--transition);
  display: flex;
  align-items: center;
  gap: 8px;
}
.search-btn:hover { background: var(--amber-dark); }

/* ============================================================
   LANDING PAGE
   ============================================================ */
.hero {
  background: linear-gradient(145deg, #16150F 0%, #1E1D1B 45%, #1a1916 100%);
  min-height: calc(100vh - var(--nav-h));
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}
.hero-bg-orb {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
  filter: blur(80px);
}
.hero-bg-orb-1 {
  width: 600px; height: 600px;
  top: -160px; right: -120px;
  background: radial-gradient(circle, rgba(232,128,10,0.22) 0%, transparent 65%);
}
.hero-bg-orb-2 {
  width: 400px; height: 400px;
  bottom: -100px; left: -80px;
  background: radial-gradient(circle, rgba(26,95,168,0.15) 0%, transparent 70%);
}
.hero-bg-orb-3 {
  width: 300px; height: 300px;
  top: 40%; left: 35%;
  background: radial-gradient(circle, rgba(232,128,10,0.08) 0%, transparent 70%);
}
.hero-noise {
  position: absolute;
  inset: 0;
  opacity: 0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  pointer-events: none;
}
.hero-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 80px 24px;
  position: relative;
  z-index: 2;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}
.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 14px;
  background: rgba(232,128,10,0.18);
  border: 1px solid rgba(232,128,10,0.3);
  border-radius: var(--radius-full);
  font-size: 12px;
  font-weight: 700;
  color: var(--amber-light);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 24px;
}
.hero-h1 {
  font-family: var(--font-display);
  font-size: clamp(36px, 5vw, 58px);
  line-height: 1.12;
  color: var(--white);
  margin-bottom: 20px;
  letter-spacing: -0.5px;
}
.hero-h1 .accent { color: var(--amber-light); font-style: italic; }
.hero-desc { font-size: 17px; color: rgba(255,255,255,0.62); line-height: 1.65; margin-bottom: 36px; max-width: 480px; }
.hero-actions { display: flex; gap: 14px; flex-wrap: wrap; }
.hero-stats { display: flex; gap: 32px; margin-top: 48px; padding-top: 36px; border-top: 1px solid rgba(255,255,255,0.1); }
.hero-stat-num {
  font-family: var(--font-mono);
  font-size: 28px;
  font-weight: 600;
  color: var(--white);
}
.hero-stat-label { font-size: 13px; color: rgba(255,255,255,0.5); margin-top: 2px; }
.hero-visual { position: relative; padding-bottom: 24px; }
.hero-card-float {
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.1);
  backdrop-filter: blur(8px);
  border-radius: var(--radius-xl);
  padding: 22px;
  color: white;
}
.hero-card-float .badge-amber { background: rgba(232,128,10,0.28); border: 1px solid rgba(232,128,10,0.4); }
.hero-card-inner-title { font-size: 15px; font-weight: 600; margin-bottom: 14px; }
.hero-mini-laborer {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px;
  background: rgba(255,255,255,0.05);
  border-radius: var(--radius-md);
  margin-bottom: 10px;
}
.hero-mini-laborer:last-child { margin-bottom: 0; }
.hero-mini-info { flex: 1; }
.hero-mini-name { font-size: 14px; font-weight: 600; }
.hero-mini-skill { font-size: 12px; color: rgba(255,255,255,0.5); }
.hero-mini-rate { font-family: var(--font-mono); font-size: 14px; color: var(--amber-light); font-weight: 600; }
.hero-floating-tag {
  position: absolute;
  bottom: -16px;
  right: 20px;
  background: linear-gradient(135deg, var(--amber), var(--amber-dark));
  color: white;
  padding: 10px 18px;
  border-radius: var(--radius-full);
  font-size: 13px;
  font-weight: 700;
  box-shadow: 0 8px 24px rgba(232,128,10,0.4);
  letter-spacing: 0.01em;
  border: 1.5px solid rgba(255,255,255,0.2);
}

/* Features section */
.section { padding: 80px 24px; }
.section-inner { max-width: 1200px; margin: 0 auto; }
.section-eyebrow {
  font-size: 12px;
  font-weight: 700;
  color: var(--amber);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 12px;
}
.section-title { font-family: var(--font-display); font-size: clamp(28px, 4vw, 42px); color: var(--charcoal); margin-bottom: 16px; line-height: 1.2; }
.section-desc { font-size: 16px; color: var(--gray-400); max-width: 520px; line-height: 1.65; }
.features-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-top: 52px; }
.feature-card {
  background: var(--white);
  border: 1px solid var(--gray-100);
  border-radius: var(--radius-lg);
  padding: 28px;
  box-shadow: var(--shadow-sm);
  transition: box-shadow var(--transition), transform var(--transition);
}
.feature-card:hover { box-shadow: 0 12px 40px rgba(0,0,0,0.10), 0 4px 8px rgba(0,0,0,0.06); transform: translateY(-4px); border-color: var(--amber-bg-2); }
.feature-icon { font-size: 28px; margin-bottom: 16px; }
.feature-title { font-size: 16px; font-weight: 700; color: var(--charcoal); margin-bottom: 8px; }
.feature-desc { font-size: 14px; color: var(--gray-400); line-height: 1.6; }

/* CTA section */
.cta-section {
  background: linear-gradient(145deg, #16150F 0%, #1E1D1B 60%, #1a1916 100%);
  padding: 100px 24px;
  text-align: center;
  position: relative;
  overflow: hidden;
}
.cta-section::before {
  content: '';
  position: absolute;
  top: -120px; left: 50%;
  transform: translateX(-50%);
  width: 700px; height: 400px;
  background: radial-gradient(ellipse, rgba(232,128,10,0.14) 0%, transparent 70%);
  pointer-events: none;
}
.cta-title { font-family: var(--font-display); font-size: clamp(28px, 4vw, 46px); color: var(--white); margin-bottom: 16px; }
.cta-desc { font-size: 17px; color: rgba(255,255,255,0.55); margin-bottom: 36px; }
.cta-actions { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }

/* ============================================================
   AUTH PAGE
   ============================================================ */
.auth-page {
  min-height: 100vh;
  background: var(--off-white);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px 20px;
}
.auth-box {
  background: var(--white);
  border-radius: var(--radius-xl);
  box-shadow: var(--shadow-xl);
  width: 100%;
  max-width: 460px;
  overflow: hidden;
}
.auth-header {
  padding: 56px 32px 24px;
  border-bottom: 1px solid var(--gray-100);
  text-align: center;
  position: relative;
}
.auth-logo { margin: 0 auto 16px; width: fit-content; }
.auth-title { font-size: 22px; font-weight: 800; color: var(--charcoal); margin-bottom: 4px; }
.auth-sub { font-size: 14px; color: var(--gray-400); }
.auth-body { padding: 28px 32px; }
.auth-footer { padding: 16px 32px 24px; text-align: center; font-size: 13px; color: var(--gray-400); }
.auth-footer a { color: var(--amber); font-weight: 600; cursor: pointer; }

.role-selector { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 22px; }
.role-option {
  border: 2px solid var(--gray-200);
  border-radius: var(--radius-lg);
  padding: 16px;
  text-align: center;
  cursor: pointer;
  transition: all var(--transition);
  background: var(--white);
}
.role-option:hover { border-color: var(--amber); }
.role-option.selected { border-color: var(--amber); background: var(--amber-bg); }
.role-icon { font-size: 28px; margin-bottom: 8px; }
.role-name { font-size: 15px; font-weight: 700; color: var(--charcoal); margin-bottom: 2px; }
.role-desc { font-size: 12px; color: var(--gray-400); }

/* ============================================================
   DASHBOARD LAYOUT
   ============================================================ */
.dashboard-layout {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 24px;
  display: grid;
  grid-template-columns: 260px 1fr;
  gap: 28px;
  align-items: start;
}
.dashboard-sidebar { display: flex; flex-direction: column; gap: 16px; position: sticky; top: calc(var(--nav-h) + 20px); }
.dashboard-main { display: flex; flex-direction: column; gap: 24px; }
.stats-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; }
.stats-grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); gap: 16px; }
.two-col-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; align-items: start; }

/* Sidebar quick nav */
.sidebar-nav { display: flex; flex-direction: column; gap: 2px; }
.sidebar-nav-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 14px;
  border-radius: var(--radius-md);
  font-size: 14px;
  font-weight: 500;
  color: var(--gray-500);
  cursor: pointer;
  transition: all var(--transition);
}
.sidebar-nav-item:hover { background: var(--gray-50); color: var(--charcoal); }
.sidebar-nav-item.active { background: var(--amber-bg); color: var(--amber-dark); font-weight: 600; }
.sidebar-nav-icon { font-size: 17px; width: 22px; text-align: center; }

/* Profile sidebar card */
.profile-sidebar-card { text-align: center; padding: 24px; }
.profile-sidebar-card .avatar { margin: 0 auto 14px; }
.profile-sidebar-name { font-size: 16px; font-weight: 700; color: var(--charcoal); }
.profile-sidebar-role { font-size: 13px; color: var(--gray-400); margin-bottom: 12px; }

/* ============================================================
   SEARCH PAGE
   ============================================================ */
.search-layout {
  max-width: 1200px;
  margin: 0 auto;
  padding: 28px 24px;
  display: grid;
  grid-template-columns: 260px 1fr;
  gap: 24px;
  align-items: start;
}
.search-results { display: flex; flex-direction: column; gap: 16px; }
.search-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 4px;
}
.search-count { font-size: 14px; color: var(--gray-400); }
.search-count strong { color: var(--charcoal); }
.sort-select { border: 1.5px solid var(--gray-200); border-radius: var(--radius-md); padding: 7px 32px 7px 12px; font-size: 13px; font-weight: 500; appearance: none; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6' viewBox='0 0 10 6'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%236B6A65' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 10px center; outline: none; cursor: pointer; }

/* ============================================================
   PROFILE CREATION
   ============================================================ */
.profile-create-layout {
  max-width: 780px;
  margin: 0 auto;
  padding: 36px 24px 60px;
}
.steps-bar { display: flex; gap: 0; margin-bottom: 36px; }
.step-item { flex: 1; display: flex; flex-direction: column; align-items: center; gap: 8px; position: relative; }
.step-item:not(:last-child)::after {
  content: '';
  position: absolute;
  left: 50%;
  top: 16px;
  width: 100%;
  height: 2px;
  background: var(--gray-100);
  z-index: 0;
}
.step-item.done::after, .step-item.active::after { background: var(--amber); }
.step-dot {
  width: 32px; height: 32px;
  border-radius: 50%;
  background: var(--gray-100);
  color: var(--gray-400);
  font-size: 13px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 1;
  transition: all var(--transition);
}
.step-item.active .step-dot { background: var(--amber); color: white; }
.step-item.done .step-dot { background: var(--green); color: white; }
.step-label { font-size: 11px; font-weight: 600; color: var(--gray-400); text-transform: uppercase; letter-spacing: 0.05em; text-align: center; }
.step-item.active .step-label { color: var(--amber); }

/* ============================================================
   BOOKING DURATION SELECTOR
   ============================================================ */
.duration-selector { display: grid; grid-template-columns: repeat(4, 1fr); gap: 8px; }
.duration-option {
  border: 2px solid var(--gray-200);
  border-radius: var(--radius-md);
  padding: 10px 8px;
  text-align: center;
  cursor: pointer;
  transition: all var(--transition);
}
.duration-option:hover { border-color: var(--amber); }
.duration-option.selected { border-color: var(--amber); background: var(--amber-bg); }
.duration-num { font-family: var(--font-mono); font-size: 18px; font-weight: 700; color: var(--charcoal); }
.duration-unit { font-size: 11px; color: var(--gray-400); margin-top: 2px; font-weight: 500; }
.duration-option.selected .duration-num { color: var(--amber-dark); }

/* ============================================================
   EMPTY STATE
   ============================================================ */
.empty-state {
  text-align: center;
  padding: 60px 24px;
  color: var(--gray-400);
}
.empty-icon { font-size: 48px; margin-bottom: 16px; opacity: 0.4; }
.empty-title { font-size: 16px; font-weight: 600; color: var(--gray-500); margin-bottom: 6px; }
.empty-desc { font-size: 14px; }

/* ============================================================
   TOAST NOTIFICATION
   ============================================================ */
.toast-container { position: fixed; bottom: 28px; right: 28px; z-index: 2000; display: flex; flex-direction: column; gap: 10px; pointer-events: none; }
.toast {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 14px 18px;
  background: var(--charcoal);
  color: white;
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-xl);
  font-size: 14px;
  font-weight: 500;
  min-width: 280px;
  max-width: 360px;
  pointer-events: all;
  opacity: 0;
  transform: translateX(20px);
  transition: all 0.3s ease;
}
.toast.show { opacity: 1; transform: translateX(0); }
.toast-icon { font-size: 18px; }

/* ============================================================
   FOOTER
   ============================================================ */
.footer {
  background: linear-gradient(180deg, #16150F 0%, #0F0F0E 100%);
  color: rgba(255,255,255,0.45);
  padding: 40px 24px;
  font-size: 13px;
  border-top: 1px solid rgba(255,255,255,0.06);
}
.footer-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  flex-wrap: wrap;
}
.footer-logo { font-weight: 800; color: white; display: flex; align-items: center; gap: 8px; }

/* ============================================================
   RESPONSIVE
   ============================================================ */
@media (max-width: 1024px) {
  .stats-grid { grid-template-columns: repeat(2, 1fr); }
  .features-grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 768px) {
  :root { --nav-h: 56px; }
  .nav-links, .nav-role-badge { display: none; }
  .nav-hamburger { display: flex; }
  .hero-inner { grid-template-columns: 1fr; }
  .hero-visual { display: none; }
  .dashboard-layout { grid-template-columns: 1fr; }
  .dashboard-sidebar { position: static; }
  .stats-grid { grid-template-columns: 1fr 1fr; }
  .search-layout { grid-template-columns: 1fr; }
  .filter-wrap { display: none; }
  .two-col-grid { grid-template-columns: 1fr; }
  .form-row { grid-template-columns: 1fr; }
  .hero-stats { flex-wrap: wrap; gap: 20px; }
  .features-grid { grid-template-columns: 1fr; }
  .duration-selector { grid-template-columns: repeat(2, 1fr); }
  .auth-body { padding: 20px; }
  .auth-header { padding: 24px 20px 18px; }
  .auth-footer { padding: 12px 20px 20px; }
}

@media (max-width: 480px) {
  .stats-grid { grid-template-columns: 1fr; }
  .hero-actions { flex-direction: column; }
  .cta-actions { flex-direction: column; align-items: center; }
}

/* ============================================================
   PAGE HEADER STRIP
   ============================================================ */
.page-header-strip {
  background: var(--white);
  border-bottom: 1px solid var(--gray-100);
  padding: 20px 24px;
}
.page-header-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  flex-wrap: wrap;
}
.page-title { font-size: 22px; font-weight: 800; color: var(--charcoal); letter-spacing: -0.3px; }
.page-desc { font-size: 14px; color: var(--gray-400); margin-top: 2px; }

/* ============================================================
   MOBILE NAV DRAWER
   ============================================================ */
.mobile-nav-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.4);
  z-index: 850;
}
.mobile-nav-overlay.open { display: block; }
.mobile-nav-drawer {
  position: fixed;
  top: 0; right: 0;
  width: 260px;
  height: 100%;
  background: var(--white);
  z-index: 860;
  transform: translateX(100%);
  transition: transform 0.28s ease;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 6px;
  box-shadow: var(--shadow-xl);
}
.mobile-nav-overlay.open + .mobile-nav-drawer,
.mobile-nav-drawer.open { transform: translateX(0); }


/* ============================================================
   PREMIUM ADDITIONS
   ============================================================ */

/* Pulse animation for live badge */
@keyframes pulse-badge {
  0%, 100% { box-shadow: 0 0 0 0 rgba(232,128,10,0.4); }
  50% { box-shadow: 0 0 0 6px rgba(232,128,10,0); }
}

/* Smooth page transition feel */
.page.active { animation: pageFadeIn 0.25s ease; }
@keyframes pageFadeIn {
  from { opacity: 0; transform: translateY(6px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Premium stat card hover */
.stat-card {
  transition: box-shadow 0.2s ease, transform 0.2s ease;
}
.stat-card:hover {
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}

/* Gold gradient logo mark */
.nav-logo-mark {
  background: linear-gradient(135deg, var(--amber) 0%, var(--amber-dark) 100%) !important;
  box-shadow: 0 2px 8px rgba(232,128,10,0.35);
}

/* Premium input focus ring */
.form-input:focus, .form-select:focus, .form-textarea:focus {
  border-color: var(--amber);
  box-shadow: 0 0 0 3px rgba(232,128,10,0.14), 0 1px 4px rgba(0,0,0,0.06);
}

/* Premium btn-primary glow */
.btn-primary {
  box-shadow: 0 2px 8px rgba(232,128,10,0.25);
}
.btn-primary:hover {
  box-shadow: 0 6px 20px rgba(232,128,10,0.38);
}

/* Smooth sidebar nav */
.sidebar-nav-item {
  transition: background 0.15s, color 0.15s, padding-left 0.15s;
}
.sidebar-nav-item:hover { padding-left: 18px; }

/* Auth box elevated shadow */
.auth-box {
  box-shadow: 0 24px 80px rgba(0,0,0,0.16), 0 8px 24px rgba(0,0,0,0.08) !important;
}

/* Section alternating premium bg */
.section-alt {
  background: linear-gradient(180deg, var(--white) 0%, var(--off-white) 100%);
}

/* Premium avatar ring */
.avatar-lg {
  box-shadow: 0 0 0 3px var(--white), 0 0 0 5px var(--amber-bg-2);
}

/* Scrollbar styling */
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: var(--gray-50); }
::-webkit-scrollbar-thumb { background: var(--gray-200); border-radius: 99px; }
::-webkit-scrollbar-thumb:hover { background: var(--gray-300); }

/* Hero card float elevated */
.hero-card-float {
  box-shadow: 0 20px 60px rgba(0,0,0,0.4), inset 0 1px 0 rgba(255,255,255,0.08) !important;
}

/* Laborer card — selected/highlighted state */
.laborer-card:focus-within { border-color: var(--amber); box-shadow: 0 0 0 3px rgba(232,128,10,0.12); }

/* Trust strip under hero */
.trust-strip {
  background: var(--white);
  border-bottom: 1px solid var(--gray-100);
  padding: 20px 24px;
}
.trust-strip-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 40px;
  flex-wrap: wrap;
}
.trust-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 13px;
  font-weight: 600;
  color: var(--gray-500);
}
.trust-icon {
  width: 32px; height: 32px;
  border-radius: var(--radius-md);
  background: var(--amber-bg);
  display: flex; align-items: center; justify-content: center;
  font-size: 15px;
  flex-shrink: 0;
}

/* Testimonial cards */
.testimonial-section {
  padding: 80px 24px;
  background: var(--off-white);
}
.testimonial-grid {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 20px;
  margin-top: 48px;
}
@media(max-width:900px){ .testimonial-grid { grid-template-columns:1fr; } }
.testimonial-card {
  background: var(--white);
  border-radius: var(--radius-lg);
  border: 1px solid var(--gray-100);
  padding: 28px;
  box-shadow: var(--shadow-sm);
  transition: box-shadow 0.2s, transform 0.2s;
}
.testimonial-card:hover { box-shadow: var(--shadow-md); transform: translateY(-3px); }
.testimonial-quote {
  font-size: 15px;
  color: var(--gray-500);
  line-height: 1.7;
  margin-bottom: 20px;
  font-style: italic;
}
.testimonial-author {
  display: flex;
  align-items: center;
  gap: 12px;
}
.testimonial-name { font-size: 14px; font-weight: 700; color: var(--charcoal); }
.testimonial-role { font-size: 12px; color: var(--gray-400); margin-top: 1px; }

/* Booking status card premium */
.booking-status-page-grid .card {
  transition: box-shadow 0.2s;
}
.booking-status-page-grid .card:hover {
  box-shadow: var(--shadow-md);
}


/* ============================================================
   AI SMART MATCH — Floating Button + Panel
   ============================================================ */
.ai-match-fab {
  position: fixed;
  bottom: 32px;
  left: 32px;
  z-index: 1600;
  display: none; /* shown only on search page */
}
.ai-match-fab.visible { display: block; }
.ai-match-fab-btn {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 14px 22px;
  background: linear-gradient(135deg, #6B3FA0, #4a2870);
  color: white;
  border: none;
  border-radius: var(--radius-full);
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  box-shadow: 0 8px 28px rgba(107,63,160,0.45);
  transition: transform 0.2s, box-shadow 0.2s;
  letter-spacing: 0.01em;
}
.ai-match-fab-btn:hover { transform: translateY(-2px); box-shadow: 0 12px 36px rgba(107,63,160,0.55); }
.ai-match-fab-btn .fab-pulse {
  width: 8px; height: 8px;
  background: #A78BFA;
  border-radius: 50%;
  animation: fabPulse 1.8s infinite;
  flex-shrink: 0;
}
@keyframes fabPulse {
  0%,100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.5); opacity: 0.6; }
}

/* AI Panel Drawer */
.ai-panel-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 1700;
  backdrop-filter: blur(3px);
}
.ai-panel-overlay.open { display: block; }
.ai-panel {
  position: fixed;
  bottom: 0; left: 0; right: 0;
  max-height: 90vh;
  background: var(--white);
  border-radius: 24px 24px 0 0;
  z-index: 1800;
  transform: translateY(100%);
  transition: transform 0.35s cubic-bezier(0.32,0.72,0,1);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}
.ai-panel.open { transform: translateY(0); }
.ai-panel-header {
  background: linear-gradient(135deg, #1e1340 0%, #2d1b6b 100%);
  padding: 24px 28px 20px;
  color: white;
  position: relative;
  flex-shrink: 0;
}
.ai-panel-title {
  font-size: 18px;
  font-weight: 800;
  margin-bottom: 4px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.ai-panel-sub { font-size: 13px; color: rgba(255,255,255,0.6); }
.ai-panel-close {
  position: absolute;
  top: 20px; right: 20px;
  background: rgba(255,255,255,0.12);
  border: none;
  color: white;
  width: 32px; height: 32px;
  border-radius: 50%;
  font-size: 16px;
  cursor: pointer;
  display: flex; align-items: center; justify-content: center;
  transition: background 0.15s;
}
.ai-panel-close:hover { background: rgba(255,255,255,0.22); }
.ai-panel-body {
  padding: 24px 28px;
  overflow-y: auto;
  flex: 1;
}
.ai-input-row {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
.ai-input-row .form-input { flex: 1; }
.ai-send-btn {
  padding: 10px 18px;
  background: linear-gradient(135deg, #6B3FA0, #4a2870);
  color: white;
  border: none;
  border-radius: var(--radius-md);
  font-weight: 700;
  font-size: 14px;
  cursor: pointer;
  white-space: nowrap;
  transition: opacity 0.15s;
}
.ai-send-btn:hover { opacity: 0.9; }
.ai-send-btn:disabled { opacity: 0.5; cursor: not-allowed; }

.ai-messages { display: flex; flex-direction: column; gap: 16px; }
.ai-msg {
  display: flex;
  gap: 12px;
  animation: msgSlide 0.3s ease;
}
@keyframes msgSlide {
  from { opacity: 0; transform: translateY(8px); }
  to { opacity: 1; transform: translateY(0); }
}
.ai-msg-avatar {
  width: 32px; height: 32px;
  border-radius: 50%;
  flex-shrink: 0;
  display: flex; align-items: center; justify-content: center;
  font-size: 16px;
  margin-top: 2px;
}
.ai-msg-avatar.bot { background: linear-gradient(135deg,#6B3FA0,#4a2870); }
.ai-msg-avatar.user { background: var(--amber); }
.ai-msg-bubble {
  background: var(--gray-50);
  border: 1px solid var(--gray-100);
  border-radius: 4px 16px 16px 16px;
  padding: 12px 16px;
  font-size: 14px;
  line-height: 1.6;
  color: var(--charcoal);
  max-width: 560px;
}
.ai-msg.user .ai-msg-bubble {
  background: linear-gradient(135deg,#6B3FA0,#4a2870);
  color: white;
  border-radius: 16px 4px 16px 16px;
  border: none;
  margin-left: auto;
}
.ai-msg.user { flex-direction: row-reverse; }
.ai-match-card {
  background: var(--white);
  border: 2px solid var(--purple-bg);
  border-radius: var(--radius-lg);
  padding: 16px;
  margin-top: 12px;
  cursor: pointer;
  transition: border-color 0.2s, box-shadow 0.2s;
}
.ai-match-card:hover { border-color: #6B3FA0; box-shadow: 0 4px 16px rgba(107,63,160,0.15); }
.ai-match-card-top { display: flex; align-items: center; gap: 12px; margin-bottom: 10px; }
.ai-match-score {
  padding: 4px 10px;
  background: #F0EAFA;
  color: #6B3FA0;
  border-radius: var(--rad... (134 KB left)
