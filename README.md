<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Group Supplier Portal (GSP) - IT Report</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Sora:wght@500;600;700;800&family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css" rel="stylesheet">
    
    <style>
        :root {
            --primary-color: #019eaf;
            --primary-rgb: 1, 158, 175;
            --primary-deep: #018896;
            --primary-soft: rgba(1, 158, 175, 0.10);
            --planned-bg: rgba(189, 194, 232, 0.1);
            --planned-border: #BDC2E8;
            --planned-text: #7A82B5;
            --bg-color: #f4f5f7;
            --sidebar-bg: #ffffff;
            --sidebar-width: 260px;
            --sidebar-gap: 10px;
            --font-display: 'Sora', 'Noto Sans TC', sans-serif;
            --font-body: 'Plus Jakarta Sans', 'Noto Sans TC', 'Segoe UI', sans-serif;
            --bs-primary: #019eaf;
            --bs-primary-rgb: 1, 158, 175;
        }
        * { -webkit-font-smoothing: antialiased; }
        body {
            background-color: var(--bg-color);
            font-family: var(--font-body);
            color: #495057;
            margin: 0; padding: 0; overflow-x: hidden;
        }
        h1,h2,h3,h4,h5,h6,
        .iq-card-header, .sidebar-brand .brand-text, .info-value,
        .risk-card-title, .subcard-title, .timeline-title, .attachment-name {
            font-family: var(--font-display);
        }

        body::before {
            content: ''; position: fixed; inset: 0; z-index: -2; pointer-events: none;
            background:
                radial-gradient(1100px 560px at 88% -8%, rgba(1,158,175,0.07), transparent 60%),
                radial-gradient(900px 520px at -8% 108%, rgba(189,194,232,0.12), transparent 60%);
        }
        body::after {
            content: ''; position: fixed; inset: 0; z-index: -2; pointer-events: none;
            background-image: radial-gradient(rgba(33,37,41,0.035) 1px, transparent 1px);
            background-size: 22px 22px; opacity: .55;
        }

        .dashboard-wrapper { display: flex; min-height: 100vh; padding: var(--sidebar-gap); gap: var(--sidebar-gap); }

        .sidebar {
            width: var(--sidebar-width); background-color: var(--sidebar-bg);
            border-radius: 16px; box-shadow: 0 8px 32px rgba(34, 41, 47, 0.08);
            position: fixed; top: var(--sidebar-gap); left: var(--sidebar-gap); bottom: var(--sidebar-gap);
            overflow-y: auto; overflow-x: hidden; padding: 20px 0; z-index: 1000;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .sidebar.collapsed { width: 0; padding: 0; opacity: 0; pointer-events: none; }

        .sidebar-header { display: flex; align-items: center; justify-content: space-between; padding: 0 18px 20px; border-bottom: 1px solid #f0f0f0; margin-bottom: 16px; }
        .sidebar-brand { display: flex; align-items: center; gap: 12px; flex-grow: 1; }
        .sidebar-brand .brand-logo {
            width: 46px; height: 46px; flex-shrink: 0;
            border-radius: 13px; overflow: hidden;
            box-shadow: 0 4px 12px rgba(1,158,175,0.28);
            transition: transform 0.3s ease;
        }
        .sidebar-brand:hover .brand-logo { transform: rotate(-4deg) scale(1.04); }
        .sidebar-brand .brand-logo svg { display: block; width: 100%; height: 100%; }
        .sidebar-brand .brand-text { font-size: 1.15rem; font-weight: 700; color: #212529; white-space: nowrap; letter-spacing: -0.01em; }

        .sidebar-toggle-btn { background: #f8f9fa; border: none; border-radius: 8px; width: 32px; height: 32px; display: flex; align-items: center; justify-content: center; cursor: pointer; color: #6c757d; transition: all 0.2s; flex-shrink: 0; }
        .sidebar-toggle-btn:hover { background: #e9ecef; color: var(--primary-color); }
        .sidebar-toggle-btn i { font-size: 0.95rem; }

        .sidebar-expand-btn {
            display: none; position: fixed; top: calc(var(--sidebar-gap) + 10px); left: calc(var(--sidebar-gap) + 10px); z-index: 1050;
            background: var(--primary-color); color: white; border: none; border-radius: 11px;
            width: 40px; height: 40px; font-size: 1.15rem; cursor: pointer;
            box-shadow: 0 4px 16px rgba(1, 158, 175, 0.35);
            align-items: center; justify-content: center; transition: all 0.3s;
        }
        .sidebar-expand-btn:hover { background: var(--primary-deep); transform: scale(1.06); box-shadow: 0 6px 20px rgba(1, 158, 175, 0.45); }
        .sidebar-expand-btn.show { display: flex; }

        .sidebar-menu { list-style: none; padding: 0 12px; margin: 0; }
        .sidebar-menu-item { padding: 10px 12px; display: flex; align-items: center; gap: 12px; color: #495057; text-decoration: none; font-size: 0.95rem; font-weight: 600; transition: all 0.2s ease; cursor: pointer; border-radius: 9px; margin-bottom: 4px; }
        .sidebar-menu-item:hover { background-color: #f8f9fa; color: var(--primary-color); }
        .sidebar-menu-item.active { background-color: rgba(1, 158, 175, 0.08); color: var(--primary-color); }
        .sidebar-menu-item i.menu-icon { font-size: 1.1rem; width: 20px; text-align: center; }
        .sidebar-menu-item .arrow { margin-left: auto; font-size: 0.8rem; color: #adb5bd; transition: transform 0.3s; }
        .sidebar-menu-item.expanded .arrow { transform: rotate(180deg); }

        .sidebar-submenu { list-style: none; padding: 0; margin: 0 0 8px 0; display: none; }
        .sidebar-submenu.show { display: block; }
        .sidebar-submenu-item { padding: 8px 12px 8px 44px; display: flex; align-items: center; color: #6c757d; text-decoration: none; font-size: 0.88rem; transition: all 0.2s ease; position: relative; border-radius: 7px; margin-bottom: 2px; }
        .sidebar-submenu-item::before { content: ''; position: absolute; left: 28px; width: 5px; height: 5px; border-radius: 50%; background-color: #dee2e6; transition: all 0.2s; }
        .sidebar-submenu-item:hover { color: var(--primary-color); background-color: #f8f9fa; }
        .sidebar-submenu-item.active { color: var(--primary-color); font-weight: 600; background-color: rgba(1, 158, 175, 0.05); }
        .sidebar-submenu-item.active::before { background-color: var(--primary-color); width: 6px; height: 6px; left: 27px; }

        .main-content {
            margin-left: calc(var(--sidebar-width) + var(--sidebar-gap) * 2);
            flex-grow: 1; padding: 32px 40px; min-height: calc(100vh - var(--sidebar-gap) * 2);
            transition: margin-left 0.3s cubic-bezier(0.4, 0, 0.2, 1); max-width: 100%;
        }
        .main-content.expanded { margin-left: auto; margin-right: auto; max-width: 1400px; }

        .iq-card { border: none; border-radius: 14px; box-shadow: 0 4px 24px 0 rgba(34, 41, 47, 0.05); background: #ffffff; transition: all 0.3s ease; margin-bottom: 24px; }
        .iq-card:hover { box-shadow: 0 10px 34px 0 rgba(34, 41, 47, 0.10); transform: translateY(-2px); }
        .iq-card-header { border-bottom: 1px solid #f0f0f0; padding: 20px 24px; background: transparent; font-weight: 700; color: var(--primary-color); font-size: 24px; display: flex; align-items: center; gap: 10px; letter-spacing: -0.01em; }
        .iq-card-header i:not(.toggle-icon) { font-size: 1.5rem; }
        .iq-card-body { padding: 32px; }

        .info-card-horizontal .iq-card-body { padding: 16px 20px; display: flex; align-items: center; }
        .info-icon-box { width: 48px; height: 48px; border-radius: 50%; display: flex; align-items: center; justify-content: center; flex-shrink: 0; margin-right: 16px; }
        .info-icon-box i { font-size: 1.3rem; }
        .info-content { flex-grow: 1; min-width: 0; }
        .info-label { font-size: 0.8rem; color: #6c757d; margin-bottom: 2px; }
        .info-value { font-size: 1.1rem; font-weight: 700; color: #212529; margin-bottom: 2px; line-height: 1.3; }
        .info-sub { font-size: 0.8rem; color: #6c757d; }

        .status-badge {
            font-size: 17px; padding: 9px 18px; border-radius: 10px; font-weight: 700;
            letter-spacing: 0.01em; display: inline-flex; align-items: center; gap: 8px; width: fit-content;
            font-family: var(--font-display);
        }
        .status-ontrack { background-color: rgba(25,135,84,0.10); color: #198754; }
        .status-delayed { background-color: rgba(220,53,69,0.10); color: #dc3545; }
        .status-atrisk  { background-color: rgba(255,193,7,0.14); color: #b88600; }

        .current-phase-badge {
            display: inline-flex; align-items: center; gap: 8px;
            padding: 8px 16px; border-radius: 10px;
            background: var(--primary-soft); color: var(--primary-color);
            font-family: var(--font-display); font-size: 0.9rem; font-weight: 700;
            border: 1.5px solid rgba(1, 158, 175, 0.25);
            transition: all 0.3s ease;
        }
        .current-phase-badge .phase-dot {
            width: 8px; height: 8px; border-radius: 50%;
            background: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(1, 158, 175, 0.20);
            animation: phasePulse 2s infinite;
        }
        @keyframes phasePulse {
            0% { box-shadow: 0 0 0 0 rgba(1, 158, 175, 0.40); }
            70% { box-shadow: 0 0 0 6px rgba(1, 158, 175, 0); }
            100% { box-shadow: 0 0 0 0 rgba(1, 158, 175, 0); }
        }

        .progress-subcard { border-radius: 10px; padding: 20px; margin-bottom: 20px; transition: all 0.2s ease; }
        .progress-subcard:last-child { margin-bottom: 0; }
        .subcard-completed { background-color: rgba(25, 135, 84, 0.05); border-left: 4px solid #198754; }
        .subcard-completed .subcard-title { color: #198754; }
        .subcard-planned { background-color: var(--planned-bg); border-left: 4px solid var(--planned-border); }
        .subcard-planned .subcard-title { color: var(--planned-text); }
        .subcard-title { font-size: 1rem; font-weight: 700; margin-bottom: 16px; display: flex; align-items: center; gap: 8px; }
        .task-item { display: flex; align-items: flex-start; margin-bottom: 12px; font-size: 0.95rem; line-height: 1.5; }
        .task-item:last-child { margin-bottom: 0; }
        .task-icon { margin-top: 4px; margin-right: 12px; flex-shrink: 0; }

        .iq-card-body--feed { display: flex; flex-direction: column; gap: 14px; }
        .risk-card {
            position: relative; background: #fff;
            border: 1px solid #eceef1; border-left: 4px solid var(--rc, #adb5bd);
            border-radius: 12px; padding: 16px 18px;
            box-shadow: 0 2px 10px rgba(34,41,47,0.05);
            transition: transform .22s cubic-bezier(.2,.7,.2,1), box-shadow .22s ease, border-left-width .22s ease;
        }
        .risk-card:hover { transform: translateY(-3px); box-shadow: 0 12px 26px rgba(34,41,47,0.12); border-left-width: 6px; }
        .risk-card.risk-high   { --rc: #dc3545; }
        .risk-card.risk-medium { --rc: #f0a500; }
        .risk-card.risk-low    { --rc: #0dcaf0; }
        .risk-card-title { font-size: 1.06rem; font-weight: 700; color: #212529; margin: 0 0 6px; line-height: 1.35; letter-spacing: -0.01em; }
        .risk-card-text { font-size: 0.9rem; color: #5f6b76; margin: 0; line-height: 1.62; }

        .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(190px, 1fr)); gap: 16px; }
        .gallery-item {
            position: relative; border: none; padding: 0; margin: 0; cursor: pointer;
            border-radius: 12px; overflow: hidden; aspect-ratio: 4 / 3; background: #eef0f2;
            box-shadow: 0 2px 10px rgba(34,41,47,0.06); transition: transform 0.25s ease, box-shadow 0.25s ease;
        }
        .gallery-item:hover { transform: translateY(-4px); box-shadow: 0 12px 28px rgba(34,41,47,0.14); }
        .gallery-item img { width: 100%; height: 100%; object-fit: cover; display: block; transition: transform 0.4s ease; }
        .gallery-item:hover img { transform: scale(1.07); }
        .gallery-overlay {
            position: absolute; inset: 0; display: flex; flex-direction: column;
            align-items: center; justify-content: center; gap: 8px;
            background: linear-gradient(to top, rgba(1,40,46,0.78) 0%, rgba(1,40,46,0.15) 55%, transparent 100%);
            opacity: 0; transition: opacity 0.25s ease; color: #fff; padding: 12px; text-align: center;
        }
        .gallery-item:hover .gallery-overlay { opacity: 1; }
        .gallery-overlay i { font-size: 1.7rem; transform: scale(0.7); transition: transform 0.3s cubic-bezier(.2,.8,.2,1); }
        .gallery-item:hover .gallery-overlay i { transform: scale(1); }
        .gallery-cap { font-size: 0.82rem; font-weight: 600; line-height: 1.3; text-shadow: 0 1px 4px rgba(0,0,0,0.4); }

        .lightbox {
            position: fixed; inset: 0; z-index: 2000; display: flex; align-items: center; justify-content: center;
            background: rgba(15,20,24,0.92); backdrop-filter: blur(6px);
            opacity: 0; visibility: hidden; transition: opacity 0.3s ease, visibility 0.3s ease; padding: 24px;
        }
        .lightbox.open { opacity: 1; visibility: visible; }
        .lb-figure { margin: 0; max-width: min(1100px, 92vw); max-height: 86vh; display: flex; flex-direction: column; align-items: center; }
        .lb-figure img {
            max-width: 100%; max-height: 78vh; border-radius: 12px; object-fit: contain;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            transform: scale(0.94); opacity: 0; transition: transform 0.35s cubic-bezier(.2,.8,.2,1), opacity 0.35s ease;
        }
        .lightbox.open .lb-figure img { transform: scale(1); opacity: 1; }
        .lb-figure figcaption { color: #e9ecef; font-size: 0.95rem; font-weight: 500; margin-top: 16px; text-align: center; }
        .lb-btn {
            position: absolute; background: rgba(255,255,255,0.10); border: 1px solid rgba(255,255,255,0.18);
            color: #fff; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center;
            transition: all 0.2s ease; backdrop-filter: blur(4px);
        }
        .lb-btn:hover { background: var(--primary-color); border-color: var(--primary-color); transform: scale(1.08); }
        .lb-close { top: 22px; right: 24px; width: 46px; height: 46px; font-size: 1.5rem; }
        .lb-prev, .lb-next { top: 50%; transform: translateY(-50%); width: 52px; height: 52px; font-size: 1.8rem; }
        .lb-prev { left: 24px; } .lb-next { right: 24px; }
        .lb-prev:hover, .lb-next:hover { transform: translateY(-50%) scale(1.08); }
        .lb-counter { position: absolute; bottom: 22px; left: 50%; transform: translateX(-50%); color: #adb5bd; font-size: 0.85rem; font-weight: 600; letter-spacing: 0.05em; }

        .phase-tabs-wrapper {
            padding: 16px 24px 0;
        }
        .phase-tabs {
            display: inline-flex; gap: 6px; padding: 5px;
            background: #f4f5f7; border-radius: 12px;
        }
        .phase-tab {
            padding: 8px 20px; border-radius: 8px;
            font-family: var(--font-display); font-size: 0.88rem; font-weight: 600;
            color: #6c757d; background: transparent; border: none; cursor: pointer;
            transition: all 0.25s cubic-bezier(.2,.7,.2,1);
            display: inline-flex; align-items: center; gap: 8px;
        }
        .phase-tab:hover { color: var(--primary-color); background: rgba(1,158,175,0.06); }
        .phase-tab.active {
            background: var(--primary-color); color: #fff;
            box-shadow: 0 4px 12px rgba(1, 158, 175, 0.30);
        }

        .phase-panel { display: none; animation: phaseFadeIn 0.4s ease; }
        .phase-panel.active { display: block; }
        @keyframes phaseFadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: none; }
        }

        .iq-timeline { position: relative; padding-left: 0; list-style: none; margin: 0; }
        .timeline-item { position: relative; display: flex; padding-bottom: 32px; }
        .timeline-item:last-child { padding-bottom: 0; }
        .timeline-marker { display: flex; flex-direction: column; align-items: center; position: relative; z-index: 1; margin-right: 24px; flex-shrink: 0; min-width: 14px; }
        .marker-dot { width: 14px; height: 14px; border-radius: 50%; background-color: #e9ecef; border: 2px solid #ffffff; box-shadow: 0 0 0 2px #e9ecef; flex-shrink: 0; transition: all 0.3s ease; }
        .marker-dot.completed { background-color: #adb5bd; box-shadow: 0 0 0 2px rgba(173, 181, 189, 0.25); }
        .marker-dot.current { background-color: var(--primary-color); box-shadow: 0 0 0 2px rgba(1, 158, 175, 0.2); animation: pulse-primary 2s infinite; }
        .marker-dot.pending { background-color: #ffc107; box-shadow: 0 0 0 2px rgba(255, 193, 7, 0.2); }
        .marker-line { width: 2px; flex-grow: 1; background-color: #e9ecef; margin-top: 8px; min-height: 30px; }
        .timeline-item:last-child .marker-line { display: none; }
        .timeline-content { flex-grow: 1; padding-top: 0; }
        .timeline-date-top { font-size: 0.85rem; color: #6c757d; font-weight: 500; margin-bottom: 12px; display: block; }
        .timeline-header { display: flex; align-items: center; margin-bottom: 8px; flex-wrap: wrap; gap: 10px; }
        .timeline-title { font-size: 1.1rem; font-weight: 700; color: #212529; margin: 0; transition: all 0.3s ease; }
        .timeline-desc { font-size: 0.9rem; color: #6c757d; margin: 0; line-height: 1.6; transition: all 0.3s ease; }
        .timeline-badge { display: inline-block; padding: 4px 12px; border-radius: 20px; font-size: 0.75rem; font-weight: 600; background-color: rgba(1, 158, 175, 0.15); color: var(--primary-color); }

        .timeline-item.completed .timeline-title { color: #adb5bd !important; }
        .timeline-item.completed .timeline-date-top { color: #adb5bd !important; }
        .timeline-item.completed .timeline-desc { color: #ced4da !important; }
        .timeline-item.current .timeline-title { color: var(--primary-color) !important; font-size: 1.2rem; font-weight: 800; }
        .timeline-item.current .timeline-date-top { color: var(--primary-color) !important; font-weight: 700; }
        .timeline-item.current .timeline-desc { color: #495057 !important; font-weight: 500; }
        .timeline-item.pending .timeline-title { color: #495057 !important; font-weight: 600; }
        .timeline-item.pending .timeline-date-top { color: #6c757d !important; }
        .timeline-item.pending .timeline-desc { color: #6c757d !important; }

        @keyframes pulse-primary {
            0% { box-shadow: 0 0 0 0 rgba(1, 158, 175, 0.4); }
            70% { box-shadow: 0 0 0 8px rgba(1, 158, 175, 0); }
            100% { box-shadow: 0 0 0 0 rgba(1, 158, 175, 0); }
        }

        .progress { height: 8px; border-radius: 4px; background-color: #e0f7fa; }
        .progress-bar { border-radius: 4px; }

        .attachment-item { display: flex; align-items: center; padding: 16px; border-radius: 10px; background-color: #f8f9fa; text-decoration: none; color: #495057; transition: all 0.2s; border: 1px solid transparent; height: 100%; }
        .attachment-item:hover { background-color: #e0f7fa; color: var(--primary-color); border-color: #b2ebf2; transform: translateY(-2px); }
        .attachment-icon { font-size: 1.8rem; margin-right: 16px; }
        .attachment-info { flex-grow: 1; }
        .attachment-name { font-weight: 600; font-size: 1rem; margin-bottom: 4px; }
        .attachment-size { font-size: 0.8rem; color: #6c757d; }

        .collapse-toggle-btn { background: none; border: none; color: var(--primary-color); padding: 0; display: flex; align-items: center; justify-content: center; transition: transform 0.2s ease; }
        .collapse-toggle-btn:hover { color: var(--primary-deep); }
        .collapse-toggle-btn .toggle-icon { font-size: 1.2rem; transition: transform 0.3s ease; }
        .collapse-toggle-btn.collapsed .toggle-icon { transform: rotate(-180deg); }

        [data-reveal].will-reveal { opacity: 0; transform: translateY(20px); }
        [data-reveal].revealed { opacity: 1; transform: none; transition: opacity 0.6s ease, transform 0.6s cubic-bezier(.2,.7,.2,1); }

        @media (min-width: 1600px) { .main-content.expanded { max-width: 1600px; } }
        @media (min-width: 1400px) and (max-width: 1599px) { .main-content.expanded { max-width: 1400px; } }
        @media (min-width: 1200px) and (max-width: 1399px) { .main-content.expanded { max-width: 1200px; } .iq-card-body { padding: 24px; } }
        @media (min-width: 992px) and (max-width: 1199px) { .main-content.expanded { max-width: 100%; padding: 24px; } .iq-card-header { font-size: 20px; } .project-title { font-size: 32px !important; } }
        @media (max-width: 992px) {
            .dashboard-wrapper { padding: 0; gap: 0; }
            .sidebar { left: 0; top: 0; bottom: 0; border-radius: 0; transform: translateX(-100%); width: var(--sidebar-width) !important; padding: 20px 0 !important; }
            .sidebar.mobile-show { transform: translateX(0); box-shadow: 4px 0 24px rgba(0,0,0,0.15); }
            .sidebar.collapsed { width: var(--sidebar-width) !important; padding: 20px 0 !important; opacity: 1; pointer-events: auto; }
            .sidebar-toggle-btn { display: none; }
            .sidebar-expand-btn { display: flex !important; top: 10px; left: 10px; }
            .main-content { margin-left: 0 !important; padding: 20px 16px; padding-top: 70px; min-height: 100vh; max-width: 100% !important; }
            .main-content.expanded { margin-left: 0 !important; }
            .sidebar-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); z-index: 999; }
            .sidebar-overlay.show { display: block; }
            .project-title { font-size: 28px !important; }
            .iq-card-header { font-size: 18px; padding: 16px 20px; }
            .lb-prev { left: 10px; } .lb-next { right: 10px; }
            .phase-tabs { width: 100%; overflow-x: auto; }
            .phase-tab { flex-shrink: 0; }
        }
        @media (max-width: 576px) {
            .timeline-item { padding-bottom: 24px; }
            .timeline-marker { margin-right: 16px; }
            .timeline-item.current .timeline-title { font-size: 1.05rem; }
            .main-content { padding: 16px 12px; padding-top: 68px; }
            .iq-card-body { padding: 20px; }
            .project-title { font-size: 24px !important; }
            .gallery-grid { grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 12px; }
            .current-phase-badge { font-size: 0.82rem; padding: 7px 14px; }
        }
        @media (prefers-reduced-motion: reduce) {
            [data-reveal].will-reveal { opacity: 1 !important; transform: none !important; }
            .marker-dot.current, .current-phase-badge .phase-dot { animation: none; }
            .phase-panel { animation: none; }
        }
    </style>
</head>
<body>

<div class="dashboard-wrapper">
    
    <button class="sidebar-expand-btn" id="sidebarExpandBtn" onclick="handleExpandClick()">
        <i class="bi bi-list"></i>
    </button>

    <div class="sidebar-overlay" id="sidebarOverlay" onclick="toggleMobileSidebar()"></div>
    
    <aside class="sidebar" id="sidebar">
        <div class="sidebar-header">
            <div class="sidebar-brand">
                <span class="brand-logo">
                    <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" aria-label="IT Report logo">
                        <defs>
                            <clipPath id="logoClip"><rect x="0" y="0" width="100" height="100" rx="24" ry="24"/></clipPath>
                        </defs>
                        <g clip-path="url(#logoClip)">
                            <rect x="0" y="0" width="100" height="100" fill="#019eaf"/>
                            <rect x="0" y="80" width="100" height="22" fill="#e6333f"/>
                        </g>
                        <path d="M27 36 L40 68 L50 49 L60 68 L73 36" fill="none" stroke="#ffffff" stroke-width="9" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                </span>
                <span class="brand-text">IT Report</span>
            </div>
            <button class="sidebar-toggle-btn" onclick="toggleDesktopSidebar()" title="收合選單">
                <i class="bi bi-chevron-left"></i>
            </button>
        </div>
        
 <ul class="sidebar-menu">
            <li>
                <a class="sidebar-menu-item active expanded" onclick="toggleSubmenu('submenu-wang', this)">
                    <i class="bi bi-person-circle menu-icon"></i><span>王大明</span><i class="bi bi-chevron-down arrow"></i>
                </a>
                <ul class="sidebar-submenu show" id="submenu-wang">
                    <li><a class="sidebar-submenu-item active" href="#">GSP 智能客服系統升級專案</a></li>
                    <li><a class="sidebar-submenu-item" href="#">CRM 客戶管理系統重構</a></li>
                    <li><a class="sidebar-submenu-item" href="#">內部知識庫平台建置</a></li>
                </ul>
            </li>
            <li>
                <a class="sidebar-menu-item" onclick="toggleSubmenu('submenu-jane', this)">
                    <i class="bi bi-person-circle menu-icon"></i><span>Jane</span><i class="bi bi-chevron-down arrow"></i>
                </a>
                <ul class="sidebar-submenu" id="submenu-jane">
                    <li><a class="sidebar-submenu-item" href="#">雲端基礎架構遷移專案</a></li>
                    <li><a class="sidebar-submenu-item" href="#">DevOps 自動化流程導入</a></li>
                </ul>
            </li>
            <li>
                <a class="sidebar-menu-item" onclick="toggleSubmenu('submenu-katherine', this)">
                    <i class="bi bi-person-circle menu-icon"></i><span>Katherine</span><i class="bi bi-chevron-down arrow"></i>
                </a>
                <ul class="sidebar-submenu" id="submenu-katherine">
                    <li><a class="sidebar-submenu-item" href="#">企業官網 UI/UX 全面改版</a></li>
                    <li><a class="sidebar-submenu-item" href="#">設計系統 (Design System) 建置</a></li>
                </ul>
            </li>
            <li>
                <a class="sidebar-menu-item" onclick="toggleSubmenu('submenu-carol', this)">
                    <i class="bi bi-person-circle menu-icon"></i><span>Carol</span><i class="bi bi-chevron-down arrow"></i>
                </a>
                <ul class="sidebar-submenu" id="submenu-carol">
                    <li><a class="sidebar-submenu-item" href="#">銷售數據視覺化儀表板</a></li>
                    <li><a class="sidebar-submenu-item" href="#">使用者行為分析模型建置</a></li>
                </ul>
            </li>
            <li>
                <a class="sidebar-menu-item" onclick="toggleSubmenu('submenu-clary', this)">
                    <i class="bi bi-person-circle menu-icon"></i><span>Clary</span><i class="bi bi-chevron-down arrow"></i>
                </a>
                <ul class="sidebar-submenu" id="submenu-clary">
                    <li><a class="sidebar-submenu-item" href="#">核心系統自動化測試覆蓋率提升</a></li>
                    <li><a class="sidebar-submenu-item" href="#">資安弱點掃描與修複專案</a></li>
                </ul>
            </li>
        </ul>
    </aside>


    <main class="main-content" id="mainContent">
        
        <!-- 1. 專案名稱與狀態 -->
        <div class="d-flex flex-wrap justify-content-between align-items-start mb-4">
            <div>
                <h1 class="fw-bold mb-2 text-dark project-title" style="font-size: 40px; line-height: 1.25; letter-spacing: -0.02em;">
                    Group Supplier Portal (GSP)
                </h1>
                <div class="mt-2">
                    <span class="current-phase-badge" id="currentPhaseBadge">
                        <span class="phase-dot"></span>
                        <span id="currentPhaseText">Phase 1</span>
                    </span>
                </div>
            </div>
            <div class="mt-3 mt-md-0">
                <span class="status-badge status-ontrack">
                    <i class="bi bi-check-circle-fill"></i> On Track
                </span>
            </div>
        </div>

        <!-- 2. 專案基本資訊 -->
        <div class="row">
            <div class="col-md-4">
                <div class="iq-card info-card-horizontal">
                    <div class="iq-card-body">
                        <div class="info-icon-box" style="background-color: rgba(1, 158, 175, 0.1);"><i class="bi bi-person-fill" style="color: #019eaf;"></i></div>
                        <div class="info-content">
                            <div class="info-label">專案負責人</div>
                            <div class="info-value">王大明 (Product Manager)</div>
                            <div class="info-sub">daming.wang@company.com</div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="iq-card info-card-horizontal">
                    <div class="iq-card-body">
                        <div class="info-icon-box" style="background-color: rgba(13, 202, 240, 0.1);"><i class="bi bi-calendar-event" style="color: #0dcaf0;"></i></div>
                        <div class="info-content">
                            <div class="info-label">專案開始時間</div>
                            <div class="info-value">2023 年 10 月 28 日</div>
                            <div class="info-sub">已執行 12 週</div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="iq-card info-card-horizontal">
                    <div class="iq-card-body">
                        <div class="info-icon-box" style="background-color: rgba(255, 193, 7, 0.1);"><i class="bi bi-rocket-takeoff" style="color: #ffc107;"></i></div>
                        <div class="info-content">
                            <div class="info-label">預計上線時間</div>
                            <div class="info-value">2024 年 8 月 25 日</div>
                            <div class="info-sub">剩餘 4 週</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="row mt-4">
            <!-- 3. 進度報告 -->
            <div class="col-lg-8">
                <div class="iq-card">
                    <div class="iq-card-header"><i class="bi bi-graph-up-arrow"></i> 進度報告</div>
                    <div class="iq-card-body">
                        <div class="mb-4">
                            <div class="d-flex justify-content-between mb-1">
                                <span class="fw-semibold">專案整體進度</span>
                                <span class="fw-bold" style="color: var(--primary-color);">88.6%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar" role="progressbar" style="width: 88.6%; background-color: var(--primary-color);" aria-valuenow="88.6" aria-valuemin="0" aria-valuemax="100"></div>
                            </div>
                            <div class="d-flex justify-content-between mt-2" style="font-size: 0.82rem; color: #6c757d;">
                                <span>Item Creation: <strong style="color: #198754;">98%</strong> (VB in UAT)</span>
                                <span>Item Enrichment: <strong style="color: #198754;">91%</strong></span>
                                <span>Item Listing: <strong style="color: #f0a500;">77%</strong></span>
                            </div>
                        </div>
                        <div class="progress-subcard subcard-completed">
                            <div class="subcard-title"><i class="bi bi-check-circle-fill"></i> 近期已完成事項</div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>GSP GIT development quotation 確認 ($175,000)</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>10/28 GSP kicked-off meeting 完成</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>12/19 signed off FDS (Item Creation / Item enrichment) (Kitty revise)</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>FDS: Kevin 2/25 signed off, Steven 3/4 signed off (Completed)</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>Part1: Item creation / Enrichment – GIT 2/4 provided</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>Part2: 上下架/MP integration / Sales dashboard - GIT 2/2 provided</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>User Function Access Right List (Completed)</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>Sales Dashboard: UAT Data preparation LIT提供2年資料 (Completed)</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>新品貨號分配: RETEK改成500000開始給號 (Completed)；6/23確認 994xxx 及 6xxxxx 不會給號重複</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>7/23 Internal Training Buyer (Done)</span></div>
                            <div class="task-item"><i class="bi bi-check2 task-icon text-success"></i><span>7 隻新品建立完成，進行審核流程</span></div>
                        </div>
                        <div class="progress-subcard subcard-planned">
                            <div class="subcard-title"><i class="bi bi-calendar-check-fill"></i> 下週工作計畫</div>
                            <div class="task-item"><i class="bi bi-arrow-right-short task-icon" style="color: var(--planned-text); font-weight: bold;"></i><span>8/5 SC Training 安排</span></div>
                            <div class="task-item"><i class="bi bi-arrow-right-short task-icon" style="color: var(--planned-text); font-weight: bold;"></i><span>7/28 Tradevan to GSP Data Migration 會議討論</span></div>
                            <div class="task-item"><i class="bi bi-arrow-right-short task-icon" style="color: var(--planned-text); font-weight: bold;"></i><span>7/30 圖片檔結構匯出格式與 GIT 確認，並提供給關貿</span></div>
                            <div class="task-item"><i class="bi bi-arrow-right-short task-icon" style="color: var(--planned-text); font-weight: bold;"></i><span>8 月初以 10 個 pilot supplier 進行評估，完成初步測試</span></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- 4. 風險與議題 -->
            <div class="col-lg-4">
                <div class="iq-card h-100">
                    <div class="iq-card-header text-danger"><i class="bi bi-exclamation-triangle-fill"></i> 風險與議題</div>
                    <div class="iq-card-body iq-card-body--feed">
                        <article class="risk-card risk-high">
                            <h6 class="risk-card-title">Tradevan 資料遷移成本與權限限制</h6>
                            <p class="risk-card-text">Tradevan Support 提供 raw data (EC提報/新品提報) 可能產生額外費用 (RISK: need $$?)；且關貿權限無法個別專注設定，僅能關閉廠商功能列上的 EC 提報。已 Align 以提報廠商方式進行，7/28 會議確認最終方案。</p>
                        </article>
                        <article class="risk-card risk-medium">
                            <h6 class="risk-card-title">Pilot Supplier 測試時程壓縮</h6>
                            <p class="risk-card-text">關貿將以 10 個 pilot supplier 進行評估 (希望 8 月初完成初步測試)。資料格式需新增兩欄 (狀態/申請類型)，圖片檔結構匯出格式需 7/30 與 GIT 確認後提供給關貿，時程較為緊湊。</p>
                        </article>
                        <article class="risk-card risk-low">
                            <h6 class="risk-card-title">Phase 2 功能範圍確認</h6>
                            <p class="risk-card-text">Sales dashboard export / 門市 View / 新增 SDD 改動，TA 已同意移至 Phase 2 上線。AI Chatbot My 開發中，預計可在 Phase 1 上線。需持續追蹤 Phase 2 範圍與資源配置。</p>
                        </article>
                    </div>
                </div>
            </div>
        </div>

        <!-- 5. 附圖說明 -->
        <div class="row mt-4">
            <div class="col-12">
                <div class="iq-card" data-reveal>
                    <div class="iq-card-header"><i class="bi bi-images"></i> 附圖說明</div>
                    <div class="iq-card-body">
                        <div class="gallery-grid" id="galleryGrid">
                            <button class="gallery-item" data-full="C:\Users\clarysung\Downloads\GSP_PHOTO 1.png" data-caption="進度表">
                                <img src="C:\Users\clarysung\Downloads\GSP_PHOTO 1.png" alt="進度表" loading="lazy">
                                <span class="gallery-overlay"><i class="bi bi-zoom-in"></i><span class="gallery-cap">進度表</span></span>
                            </button>
                            <button class="gallery-item" data-full="C:\Users\clarysung\Downloads\GSP_PHOTO 2.png" data-caption="廠商名單">
                                <img src="C:\Users\clarysung\Downloads\GSP_PHOTO 2.png" alt="廠商名單" loading="lazy">
                                <span class="gallery-overlay"><i class="bi bi-zoom-in"></i><span class="gallery-cap">廠商名單</span></span>
                            </button>
                            <button class="gallery-item" data-full="C:\Users\clarysung\Downloads\GSP_PHOTO 3.png" data-caption="GSP後台">
                                <img src="C:\Users\clarysung\Downloads\GSP_PHOTO 3.png" alt="GSP後台" loading="lazy">
                                <span class="gallery-overlay"><i class="bi bi-zoom-in"></i><span class="gallery-cap">GSP後台</span></span>
                            </button>
                            <button class="gallery-item" data-full="https://picsum.photos/seed/gsp-pilot/1400/900" data-caption="10 個 Pilot Supplier 測試清單">
                                <img src="https://picsum.photos/seed/gsp-pilot/480/360" alt="Pilot Supplier 清單" loading="lazy">
                                <span class="gallery-overlay"><i class="bi bi-zoom-in"></i><span class="gallery-cap">10 個 Pilot Supplier 測試清單</span></span>
                            </button>
                            <button class="gallery-item" data-full="https://picsum.photos/seed/gsp-dashboard/1400/900" data-caption="Sales Dashboard UAT 畫面 (LIT 2年資料)">
                                <img src="https://picsum.photos/seed/gsp-dashboard/480/360" alt="Sales Dashboard" loading="lazy">
                                <span class="gallery-overlay"><i class="bi bi-zoom-in"></i><span class="gallery-cap">Sales Dashboard UAT 畫面</span></span>
                            </button>
                            <button class="gallery-item" data-full="https://picsum.photos/seed/gsp-sku/1400/900" data-caption="RETEK 新品貨號分配邏輯 (500000起)">
                                <img src="https://picsum.photos/seed/gsp-sku/480/360" alt="貨號分配邏輯" loading="lazy">
                                <span class="gallery-overlay"><i class="bi bi-zoom-in"></i><span class="gallery-cap">RETEK 新品貨號分配邏輯</span></span>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 6. 專案歷程 (Phase Tabs) -->
        <div class="row mt-4">
            <div class="col-12">
                <div class="iq-card" data-reveal>
                    <div class="iq-card-header">
                        <i class="bi bi-signpost-2"></i> 專案歷程
                        <button class="btn collapse-toggle-btn ms-auto" type="button" data-bs-toggle="collapse" data-bs-target="#timelineCollapse" aria-expanded="true" aria-controls="timelineCollapse">
                            <i class="bi bi-chevron-down toggle-icon"></i>
                        </button>
                    </div>
                    <div class="collapse show" id="timelineCollapse">
                        <div class="phase-tabs-wrapper">
                            <div class="phase-tabs" role="tablist">
                                <button class="phase-tab active" data-phase="phase1" role="tab" aria-selected="true">
                                    Phase 1
                                </button>
                                <button class="phase-tab" data-phase="phase2" role="tab" aria-selected="false">
                                    Phase 2
                                </button>
                            </div>
                        </div>

                        <div class="iq-card-body">
                            <!-- Phase 1 Panel -->
                            <div class="phase-panel active" id="phase1">
                                <ul class="iq-timeline">
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">7 / 15</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Decision making</h6><span class="timeline-badge">Done</span></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">7 / 23</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Internal Training Buyer</h6><span class="timeline-badge">Done</span></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">7 / 27 ~ 8 / 3</span>
                                            <div class="timeline-header"><h6 class="timeline-title">End 2 End testing + Load Test (壓測)</h6><span class="timeline-badge">WIP</span></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">7 / 28</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Tradevan to GSP Data Migration 會議</h6></div>
                                            <p class="timeline-desc">討論 raw data 提供方式與成本，確認權限控管方案 (Align 以提報廠商方式進行)。</p>
                                        </div>
                                    </li>
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">7 / 30</span>
                                            <div class="timeline-header"><h6 class="timeline-title">圖片檔結構匯出格式確認</h6></div>
                                            <p class="timeline-desc">與 GIT 確認格式後提供給關貿，新增兩欄 (狀態/申請類型)。</p>
                                        </div>
                                    </li>
                                    <li class="timeline-item current">
                                        <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">8 / 3 ~ 8 / 10</span>
                                            <div class="timeline-header"><h6 class="timeline-title">VB UAT</h6><span class="timeline-badge">WIP, 提早</span></div>
                                            <p class="timeline-desc">Item Creation 98% 通過，Item Enrichment 91%，Item Listing 77%。</p>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">8 / 5</span>
                                            <div class="timeline-header"><h6 class="timeline-title">SC Training</h6></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">8 月初</span>
                                            <div class="timeline-header"><h6 class="timeline-title">10 個 Pilot Supplier 初步測試</h6></div>
                                            <p class="timeline-desc">以現行 Excel 格式新增狀態/申請類型欄位進行評估。</p>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">8 / 10 ~ 8 / 17</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Supplier Training</h6></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">8 / 24 ~ 8 / 25</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Data Migration</h6></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">8 / 25</span>
                                            <div class="timeline-header"><h6 class="timeline-title">System Deployment</h6></div>
                                            <p class="timeline-desc">AI Chatbot My 預計可於 Phase 1 上線。</p>
                                        </div>
                                    </li>
                                </ul>
                            </div>

                            <!-- Phase 2 Panel -->
                            <div class="phase-panel" id="phase2">
                                <ul class="iq-timeline">
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">6 / 18</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Phase 2 Supply Chain Module – Discussion</h6></div>
                                            <p class="timeline-desc">To review which TradeVan SC functions shall be covered by GSP Phase 2 And Reports, Email.</p>
                                        </div>
                                    </li>
                                    <li class="timeline-item completed">
                                        <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">6 / 23 ~ 7 / 9</span>
                                            <div class="timeline-header"><h6 class="timeline-title">現行功能與報表評估</h6></div>
                                            <p class="timeline-desc">初步已提供現行會使用的功能及 email 提醒等報表給 GSP 評估確認。</p>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">Phase 2 規劃</span>
                                            <div class="timeline-header"><h6 class="timeline-title">Sales Dashboard Export / 門市 View / 新增 SDD 改動</h6><span class="timeline-badge">TA 同意延至 Phase 2</span></div>
                                        </div>
                                    </li>
                                    <li class="timeline-item pending">
                                        <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                        <div class="timeline-content">
                                            <span class="timeline-date-top">Phase 2 規劃</span>
                                            <div class="timeline-header"><h6 class="timeline-title">AI Chatbot My 功能擴充</h6></div>
                                            <p class="timeline-desc">Phase 1 可先上線基礎版本，Phase 2 持續擴充功能。</p>
                                        </div>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 7. 附件 -->
        <div class="row mt-4">
            <div class="col-12">
                <div class="iq-card" data-reveal>
                    <div class="iq-card-header"><i class="bi bi-paperclip"></i> 附件</div>
                    <div class="iq-card-body">
                        <div class="row g-3">
                            <div class="col-md-4">
                                <a href="#" class="attachment-item">
                                    <i class="bi bi-file-earmark-pdf-fill attachment-icon text-danger"></i>
                                    <div class="attachment-info"><div class="attachment-name">GSP_GIT_Quotation.pdf</div><div class="attachment-size">$175,000</div></div>
                                    <i class="bi bi-download text-muted fs-5"></i>
                                </a>
                            </div>
                            <div class="col-md-4">
                                <a href="#" class="attachment-item">
                                    <i class="bi bi-file-earmark-word-fill attachment-icon text-primary"></i>
                                    <div class="attachment-info"><div class="attachment-name">FDS_SignedOff_Item_Creation.docx</div><div class="attachment-size">Kevin & Steven Signed</div></div>
                                    <i class="bi bi-download text-muted fs-5"></i>
                                </a>
                            </div>
                            <div class="col-md-4">
                                <a href="#" class="attachment-item">
                                    <i class="bi bi-file-earmark-excel-fill attachment-icon text-success"></i>
                                    <div class="attachment-info"><div class="attachment-name">UAT_Progress_Report.xlsx</div><div class="attachment-size">88.6% Pass Rate</div></div>
                                    <i class="bi bi-download text-muted fs-5"></i>
                                </a>
                            </div>
                            <div class="col-md-4">
                                <a href="#" class="attachment-item">
                                    <i class="bi bi-file-earmark-excel-fill attachment-icon text-success"></i>
                                    <div class="attachment-info"><div class="attachment-name">User_Function_Access_Right_List.xlsx</div><div class="attachment-size">Completed</div></div>
                                    <i class="bi bi-download text-muted fs-5"></i>
                                </a>
                            </div>
                            <div class="col-md-4">
                                <a href="#" class="attachment-item">
                                    <i class="bi bi-file-earmark-excel-fill attachment-icon text-success"></i>
                                    <div class="attachment-info"><div class="attachment-name">Pilot_Supplier_List_10.xlsx</div><div class="attachment-size">8月初測試用</div></div>
                                    <i class="bi bi-download text-muted fs-5"></i>
                                </a>
                            </div>
                            <div class="col-md-4">
                                <a href="#" class="attachment-item">
                                    <i class="bi bi-file-earmark-ppt-fill attachment-icon text-warning"></i>
                                    <div class="attachment-info"><div class="attachment-name">Tradevan_Migration_Plan.pptx</div><div class="attachment-size">7/28 會議資料</div></div>
                                    <i class="bi bi-download text-muted fs-5"></i>
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </main>
</div>

<!-- Lightbox -->
<div class="lightbox" id="lightbox" aria-hidden="true">
    <button class="lb-btn lb-close" id="lbClose" aria-label="關閉"><i class="bi bi-x-lg"></i></button>
    <button class="lb-btn lb-prev" id="lbPrev" aria-label="上一張"><i class="bi bi-chevron-left"></i></button>
    <button class="lb-btn lb-next" id="lbNext" aria-label="下一張"><i class="bi bi-chevron-right"></i></button>
    <figure class="lb-figure">
        <img id="lbImg" src="" alt="">
        <figcaption id="lbCap"></figcaption>
    </figure>
    <div class="lb-counter" id="lbCounter"></div>
</div>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
<script>
    function isMobile() { return window.innerWidth <= 992; }

    function toggleDesktopSidebar() {
        if (isMobile()) return;
        const sidebar = document.getElementById('sidebar');
        const mainContent = document.getElementById('mainContent');
        const expandBtn = document.getElementById('sidebarExpandBtn');
        sidebar.classList.toggle('collapsed');
        mainContent.classList.toggle('expanded');
        expandBtn.classList.toggle('show', sidebar.classList.contains('collapsed'));
    }
    function toggleMobileSidebar() {
        document.getElementById('sidebar').classList.toggle('mobile-show');
        document.getElementById('sidebarOverlay').classList.toggle('show');
    }
    function handleExpandClick() { isMobile() ? toggleMobileSidebar() : toggleDesktopSidebar(); }

    function toggleSubmenu(id, element) {
        const submenu = document.getElementById(id);
        const isShown = submenu.classList.contains('show');
        submenu.classList.toggle('show', !isShown);
        element.classList.toggle('expanded', !isShown);
    }

    /* ===== Phase Tab 切換邏輯 ===== */
    (function(){
        const tabs = document.querySelectorAll('.phase-tab');
        const panels = document.querySelectorAll('.phase-panel');
        const phaseText = document.getElementById('currentPhaseText');
        const phaseBadge = document.getElementById('currentPhaseBadge');

        const phaseLabels = {
            phase1: 'Phase 1',
            phase2: 'Phase 2'
        };

        tabs.forEach(tab => {
            tab.addEventListener('click', () => {
                const targetPhase = tab.dataset.phase;

                tabs.forEach(t => {
                    t.classList.remove('active');
                    t.setAttribute('aria-selected', 'false');
                });
                tab.classList.add('active');
                tab.setAttribute('aria-selected', 'true');

                panels.forEach(p => p.classList.remove('active'));
                const targetPanel = document.getElementById(targetPhase);
                if (targetPanel) {
                    targetPanel.classList.remove('active');
                    void targetPanel.offsetWidth;
                    targetPanel.classList.add('active');
                }

                if (phaseText && phaseLabels[targetPhase]) {
                    phaseText.textContent = phaseLabels[targetPhase];
                    phaseBadge.style.transform = 'scale(1.04)';
                    setTimeout(() => { phaseBadge.style.transform = ''; }, 200);
                }
            });
        });
    })();

    /* ===== Lightbox ===== */
    (function(){
        const items = Array.from(document.querySelectorAll('#galleryGrid .gallery-item'));
        const lb = document.getElementById('lightbox');
        const lbImg = document.getElementById('lbImg');
        const lbCap = document.getElementById('lbCap');
        const lbCounter = document.getElementById('lbCounter');
        let current = 0;

        function render(i){
            const it = items[i];
            lbImg.src = it.dataset.full;
            lbImg.alt = it.dataset.caption || '';
            lbCap.textContent = it.dataset.caption || '';
            lbCounter.textContent = (i + 1) + ' / ' + items.length;
        }
        function open(i){
            current = i; render(i);
            lb.classList.add('open'); lb.setAttribute('aria-hidden','false');
            document.body.style.overflow = 'hidden';
        }
        function close(){
            lb.classList.remove('open'); lb.setAttribute('aria-hidden','true');
            document.body.style.overflow = '';
        }
        function step(d){ current = (current + d + items.length) % items.length; render(current); }

        items.forEach((it, i) => it.addEventListener('click', () => open(i)));
        document.getElementById('lbClose').addEventListener('click', close);
        document.getElementById('lbPrev').addEventListener('click', (e)=>{ e.stopPropagation(); step(-1); });
        document.getElementById('lbNext').addEventListener('click', (e)=>{ e.stopPropagation(); step(1); });
        lb.addEventListener('click', (e)=>{ if (e.target === lb) close(); });
        document.addEventListener('keydown', (e)=>{
            if (!lb.classList.contains('open')) return;
            if (e.key === 'Escape') close();
            else if (e.key === 'ArrowLeft') step(-1);
            else if (e.key === 'ArrowRight') step(1);
        });
    })();

    /* ===== 滾動淡入 ===== */
    (function(){
        const els = document.querySelectorAll('[data-reveal]');
        if (!('IntersectionObserver' in window)) return;
        els.forEach(el => el.classList.add('will-reveal'));
        const io = new IntersectionObserver((entries)=>{
            entries.forEach(en => {
                if (en.isIntersecting){ en.target.classList.add('revealed'); io.unobserve(en.target); }
            });
        }, { threshold: 0.12 });
        els.forEach(el => io.observe(el));
    })();
</script>

</body>
</html>
