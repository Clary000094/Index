<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weekly Executive Report</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Sora:wght@500;600;700;800&family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css" rel="stylesheet">
    
    <style>
        :root {
            --primary-color: #00a99d;
            --primary-dark: #008f85;
            --primary-light: rgba(0, 169, 157, 0.1);
            --success-color: #198754;
            --success-light: rgba(25, 135, 84, 0.12);
            --warning-color: #d97706;
            --danger-color: #dc3545;
            --bg-color: #f8f9fa;
            --font-display: 'Sora', 'Noto Sans TC', sans-serif;
            --font-body: 'Plus Jakarta Sans', 'Noto Sans TC', sans-serif;
            --header-bg-start: #0f2027;
            --header-bg-mid: #203a43;
            --header-bg-end: #2c5364;
        }
        
        * { -webkit-font-smoothing: antialiased; box-sizing: border-box; }
        
        body {
            background-color: var(--bg-color);
            font-family: var(--font-body);
            color: #495057;
            margin: 0;
            padding: 32px 20px;
        }
        
        .report-container {
            max-width: 1240px;
            margin: 0 auto;
            background: transparent;
            box-shadow: none;
            border-radius: 0;
            padding: 0 8px;
        }
        
        .top-header {
            position: sticky;
            top: 0;
            z-index: 950;
            background: rgba(248, 249, 250, 0.94);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border-bottom: 1px solid #e2e8ea;
            margin: -32px -20px 32px -20px;
        }
        
        .top-header-inner {
            max-width: 1240px;
            margin: 0 auto;
            padding: 12px 8px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 20px;
        }
        
        .watsons-icon {
            width: 40px;
            height: 40px;
            object-fit: contain;
            border-radius: 10px;
            flex-shrink: 0;
            display: block;
        }
        
        .header-tabs {
            display: flex;
            align-items: center;
            gap: 24px;
            flex-shrink: 0;
        }
        
        .tab-btn {
            padding: 4px 0;
            border: none;
            background: transparent;
            color: #6c757d;
            font-family: var(--font-display);
            font-size: 0.85rem;
            font-weight: 600;
            letter-spacing: 0.05em;
            text-transform: uppercase;
            cursor: pointer;
            transition: color 0.2s ease;
        }
        
        .tab-btn:hover { color: var(--primary-dark); }
        .tab-btn.active { color: var(--primary-color); font-weight: 800; }
        
        .back-to-top {
            position: fixed;
            right: 24px;
            bottom: 24px;
            z-index: 940;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            border: 1px solid rgba(0, 169, 157, 0.3);
            background: rgba(255, 255, 255, 0.95);
            color: var(--primary-dark);
            font-size: 1.1rem;
            cursor: pointer;
            box-shadow: 0 4px 14px rgba(0, 0, 0, 0.12);
            backdrop-filter: blur(6px);
            transition: all 0.2s ease;
        }
        
        .back-to-top:hover {
            background: var(--primary-color);
            border-color: var(--primary-color);
            color: #ffffff;
            transform: translateY(-2px);
        }
        
        .report-header {
            position: relative;
            padding: 40px 48px;
            border-radius: 16px;
            margin-bottom: 32px;
            overflow: hidden;
            background-color: var(--header-bg-start);
            background-image: 
                repeating-linear-gradient(45deg, rgba(255, 255, 255, 0.03) 0px, rgba(255, 255, 255, 0.03) 1px, transparent 1px, transparent 8px),
                linear-gradient(135deg, var(--header-bg-start) 0%, var(--header-bg-mid) 50%, var(--header-bg-end) 100%);
            box-shadow: 0 10px 40px rgba(15, 32, 39, 0.15), 0 2px 8px rgba(0, 0, 0, 0.05);
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 40px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }
        
        .report-header::after {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(0, 169, 157, 0.12) 0%, transparent 60%);
            border-radius: 50%;
            pointer-events: none;
        }
        
        .header-content { flex: 1; position: relative; z-index: 1; }
        
        .report-header h1 {
            font-family: var(--font-display);
            font-size: 46px;
            font-weight: 700;
            margin: 0 0 16px 0;
            letter-spacing: -0.02em;
            line-height: 1.2;
            color: #ffffff;
        }
        
        .report-summary-text {
            font-size: 0.95rem;
            line-height: 1.6;
            margin: 0 0 28px 0;
            color: rgba(255, 255, 255, 0.85);
            max-width: 800px;
            font-weight: 400;
        }
        
        .report-meta { display: flex; flex-wrap: wrap; gap: 12px; }
        
        .meta-pill {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 8px 16px;
            border-radius: 8px;
            font-size: 0.78rem;
            font-weight: 600;
            font-family: var(--font-display);
            letter-spacing: 0.04em;
            text-transform: uppercase;
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.12);
            color: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(4px);
        }
        
        .meta-pill .pill-label { color: rgba(255, 255, 255, 0.5); font-weight: 500; }
        .meta-pill .pill-value { color: #ffffff; font-weight: 600; }
        
        .header-logo-card {
            flex-shrink: 0;
            position: relative;
            z-index: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 12px;
            padding: 0;
            background: transparent;
            box-shadow: none;
            border: none;
        }
        
        .watsons-logo { height: 46px; width: auto; object-fit: contain; display: block; }
        
        .logo-slogan {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            font-size: 11px;
            font-weight: 600;
            color: rgba(255, 255, 255, 0.72);
            letter-spacing: 0.18em;
            text-transform: uppercase;
            font-family: var(--font-display);
            white-space: nowrap;
            background: transparent;
            border: none;
            padding: 0;
            backdrop-filter: none;
        }
        
        .logo-slogan::before,
        .logo-slogan::after {
            content: '';
            display: inline-block;
            width: 18px;
            height: 1px;
            background: rgba(255, 255, 255, 0.4);
        }
        
        .exec-summary {
            background: #ffffff;
            border: 1px solid #eef0f2;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.03);
            padding: 24px;
            margin-bottom: 28px;
        }
        
        .exec-delivery-list { list-style: none; margin: 0; padding: 0; }
        
        .exec-delivery-list li {
            position: relative;
            padding-left: 20px;
            margin-bottom: 8px;
            font-size: 0.9rem;
            color: #495057;
            line-height: 1.65;
        }
        
        .exec-delivery-list li:last-child { margin-bottom: 0; }
        
        .exec-delivery-list li::before {
            content: '';
            position: absolute;
            left: 4px;
            top: 0.62em;
            width: 7px;
            height: 7px;
            border-radius: 50%;
            background: var(--primary-color);
        }
        
        .exec-delivery-list li strong { color: #212529; }
        
        .exec-stats {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin-top: 18px;
            margin-bottom: 0;
        }
        
        .exec-stats.store-stats { grid-template-columns: repeat(2, 1fr); }
        
        .exec-stat {
            background: #f8f9fa;
            border: 1px solid #eef0f2;
            border-radius: 10px;
            padding: 12px 16px;
            display: flex;
            flex-direction: column;
            gap: 2px;
        }
        
        .exec-stat-value {
            font-family: var(--font-display);
            font-size: 1.4rem;
            font-weight: 800;
            line-height: 1.2;
        }
        
        .exec-stat-label { font-size: 0.78rem; color: #6c757d; font-weight: 600; }
        
        .section-title {
            font-family: var(--font-display);
            font-size: 30px;
            font-weight: 700;
            color: #212529;
            margin: 0 0 24px 0;
            letter-spacing: -0.02em;
        }
        
        .projects-list {
            position: relative;
            margin-bottom: 24px;
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 24px;
        }
        
        .project-card {
            border: 1px solid #eef0f2;
            border-radius: 12px;
            padding: 24px;
            background: #ffffff;
            box-shadow: 0 2px 8px rgba(0,0,0,0.03);
            display: flex;
            flex-direction: column;
            scroll-margin-top: 88px;
            transition: box-shadow 0.2s ease, transform 0.2s ease;
            width: 100%;
        }
        
        .project-card:hover {
            box-shadow: 0 8px 24px rgba(0,0,0,0.06);
            transform: translateY(-2px);
        }
        
        .project-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 16px;
            gap: 16px;
        }
        
        .project-header-left { flex: 1; min-width: 0; }
        
        .project-title-row {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 12px;
            flex-wrap: wrap;
        }
        
        .project-title {
            font-family: var(--font-display);
            font-size: 1.5rem;
            font-weight: 700;
            color: #212529;
            margin: 0;
            letter-spacing: -0.01em;
        }
        
        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 5px;
            padding: 5px 12px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.78rem;
            font-family: var(--font-display);
            flex-shrink: 0;
        }
        
        .status-ontrack { background: var(--success-light); color: var(--success-color); }
        .status-attention { background: rgba(217, 119, 6, 0.12); color: var(--warning-color); }
        .status-delayed { background: rgba(220, 53, 69, 0.12); color: var(--danger-color); }
        .status-wip { background: rgba(111, 66, 193, 0.12); color: #6f42c1; }
        .status-monitor { background: rgba(13, 202, 240, 0.12); color: #0dcaf0; }
        
        .project-tags {
            font-size: 0.82rem;
            font-weight: 500;
            color: #6c757d;
            letter-spacing: 0.01em;
            padding-bottom: 12px;
            border-bottom: 1px solid #f0f0f0;
            margin-bottom: 12px;
        }
        
        .gallery-btn-mini {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            padding: 6px 12px;
            background: rgba(0, 169, 157, 0.06);
            color: var(--primary-dark);
            border: 1px solid rgba(0, 169, 157, 0.2);
            border-radius: 6px;
            font-weight: 600;
            font-size: 0.78rem;
            cursor: pointer;
            transition: all 0.2s ease;
            flex-shrink: 0;
            margin-top: 2px;
        }
        
        .gallery-btn-mini:hover {
            background: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
            transform: translateY(-1px);
        }
        
        .gallery-btn-mini i { font-size: 0.9rem; }
        
        .image-count-mini {
            background: var(--primary-color);
            color: white;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: 700;
        }
        
        .gallery-btn-mini:hover .image-count-mini { background: white; color: var(--primary-color); }
        
        .card-section { margin-bottom: 20px; }
        .card-section:last-of-type { margin-bottom: 0; }
        .card-section.hidden-section { display: none !important; }
        
        .card-section-title {
            font-family: var(--font-display);
            font-size: 16px;
            font-weight: 700;
            color: var(--primary-dark);
            margin: 0 0 8px 0;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .progress-head {
            display: grid;
            grid-template-columns: 74px 1fr;
            column-gap: 12px;
            align-items: center;
            margin-bottom: 26px;
        }
        
        .progress-head .card-section-title { margin: 0; }
        .progress-head .progress-text { margin: 0; }
        
        .progress-layout {
            display: grid;
            grid-template-columns: 74px 1fr;
            column-gap: 12px;
            row-gap: 26px;
            align-items: center;
        }
        
        .progress-layout.progress-editing {
            display: flex;
            flex-direction: column;
            align-items: stretch;
            gap: 12px;
        }
        
        .progress-layout .progress-bar-custom { margin: 0; }
        
        .progress-bar-custom {
            position: relative;
            height: 10px;
            background: #e9ecef;
            border-radius: 5px;
            overflow: visible;
            margin-bottom: 6px;
            margin-top: 4px;
        }
        
        .progress-fill {
            height: 100%;
            width: var(--p, 0%);
            background: linear-gradient(90deg, var(--primary-color) 0%, var(--primary-dark) 100%);
            border-radius: 5px;
            transition: width 0.3s ease;
        }
        
        .progress-percent {
            position: absolute;
            top: -22px;
            left: clamp(38px, var(--p, 0%), 100%);
            transform: translateX(-100%);
            font-size: 0.78rem;
            font-weight: 700;
            color: var(--primary-dark);
            font-family: var(--font-display);
            white-space: nowrap;
            pointer-events: none;
        }
        
        .progress-text { color: #6c757d; font-size: 0.85rem; margin: 0; }
        
        .progress-label {
            font-family: var(--font-display);
            font-size: 0.78rem;
            font-weight: 700;
            color: #6c757d;
            text-transform: uppercase;
            letter-spacing: 0.04em;
        }
        
        .progress-fill.fill-uat { background: linear-gradient(90deg, #56ccf2 0%, #2f80ed 100%); }
        .progress-fill.fill-preprod { background: linear-gradient(90deg, #f2c94c 0%, #f2994a 100%); }
        
        .progress-percent.pc-uat { color: #2f80ed; }
        .progress-percent.pc-preprod { color: #e08600; }
        
        .progress-row-edit {
            display: flex;
            align-items: center;
            gap: 10px;
            flex-wrap: wrap;
        }
        
        .progress-row-edit select,
        .progress-row-edit input {
            padding: 5px 8px;
            border: 1px solid #dfe3e6;
            border-radius: 6px;
            font-size: 0.85rem;
            font-family: var(--font-body);
            box-sizing: border-box;
        }
        
        .progress-row-edit select { width: 140px; }
        .progress-row-edit .progress-percent-input { width: 70px; }
        .progress-unit { font-size: 0.85rem; color: #6c757d; }
        
        .desc-del-btn {
            margin-left: 8px;
            border: none;
            background: transparent;
            color: var(--danger-color);
            cursor: pointer;
            font-size: 0.72rem;
            padding: 2px 4px;
            vertical-align: middle;
        }
        
        .desc-del-btn:hover { color: #a71d2a; }
        
        .subproject {
            background: transparent;
            border: none;
            border-radius: 0;
            padding: 0;
            margin: 0;
        }
        
        .card-section-title + .subproject { margin-top: 16px; }
        
        .subproject + .subproject {
            margin-top: 16px;
            padding-top: 16px;
            position: relative;
        }
        
        .subproject + .subproject::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 32px;
            height: 2px;
            border-radius: 1px;
            background: #d8dcdf;
        }
        
        .subproject-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 12px;
            margin-bottom: 12px;
        }
        
        .subproject-title {
            font-family: var(--font-display);
            font-size: 15px;
            font-weight: 700;
            color: #212529;
            margin: 0;
        }
        
        .subproject .note-list li {
            font-size: 0.9rem;
            color: #495057;
        }
        
        .plan-section {
            margin-top: 0;
            border-top: 1px solid #f0f0f0;
            padding-top: 20px;
            margin-bottom: 0;
        }
        
        .plan-section.hidden-section { display: none !important; }
        
        .plan-section.hidden-plan .card-section-title,
        .plan-section.hidden-plan [data-plan-desc-container] {
            display: none;
        }
        
        .key-points { margin: 16px 0 0 0; padding-left: 20px; }
        .key-points li { color: #495057; font-size: 0.9rem; line-height: 1.6; margin-bottom: 4px; }
        
        .risk-card {
            background: #fff5f7;
            border-left: 3px solid var(--danger-color);
            border-radius: 6px;
            padding: 12px 16px;
        }
        
        .risk-title {
            font-family: var(--font-display);
            font-weight: 700;
            color: var(--danger-color);
            font-size: 14.4px;
            margin: 0 0 8px 0;
            line-height: 1.4;
        }
        
        .risk-card .key-points { margin: 0; padding-left: 18px; }
        
        .decision-table-wrap {
            background: #ffffff;
            border: 1px solid #eef0f2;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.03);
            overflow-x: auto;
            margin-bottom: 24px;
        }
        
        .decision-table {
            width: 100%;
            border-collapse: collapse;
            min-width: 960px;
        }
        
        .decision-table thead th {
            background: #f4f6f9;
            color: #6b7683;
            font-family: var(--font-display);
            font-size: 16px;
            font-weight: 700;
            letter-spacing: 0.02em;
            text-align: left;
            padding: 14px 20px;
            border-bottom: 1px solid #e7eaee;
            white-space: nowrap;
        }
        
        .decision-table thead th:nth-child(1) { width: 24%; }
        .decision-table thead th:nth-child(2) { width: 38%; }
        .decision-table thead th:nth-child(3) { width: 20%; }
        .decision-table thead th:nth-child(4) { width: 8%; }
        .decision-table thead th:nth-child(5) { width: 10%; }
        
        .decision-table tbody td {
            padding: 18px 20px;
            border-bottom: 1px solid #eef0f2;
            color: #495057;
            font-size: 14px;
            line-height: 1.55;
            vertical-align: top;
        }
        
        .decision-table tbody tr:last-child td { border-bottom: none; }
        
        .dt-action { font-weight: 700; color: #212529; }
        .dt-due { font-weight: 700; color: #212529; white-space: nowrap; }
        
        .dt-status {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 6px;
            font-family: var(--font-display);
            font-size: 0.72rem;
            font-weight: 700;
            white-space: nowrap;
        }
        
        .st-urgent { background: rgba(220, 53, 69, 0.12); color: var(--danger-color); }
        .st-general { background: rgba(217, 119, 6, 0.12); color: var(--warning-color); }
        
        .note-collapse-wrapper { margin-top: 16px; border-top: 1px solid #f0f0f0; padding-top: 16px; }
        .note-title { color: #6c757d; }
        
        .note-group { margin-bottom: 12px; }
        .note-group:last-child { margin-bottom: 0; }
        
        .note-group-no-tag::before { display: none; }
        
        .note-tag {
            display: inline-block;
            padding: 3px 10px;
            border-radius: 6px;
            font-family: var(--font-display);
            font-size: 0.72rem;
            font-weight: 700;
            letter-spacing: 0.04em;
            margin-bottom: 8px;
        }
        
        .note-tag-select {
            display: inline-block;
            padding: 3px 8px;
            border: 1px solid #dfe3e6;
            border-radius: 6px;
            font-family: var(--font-display);
            font-size: 0.72rem;
            font-weight: 700;
            margin-bottom: 8px;
            background: white;
            vertical-align: middle;
        }
        
        .tag-completed { background: var(--success-light); color: var(--success-color); }
        .tag-inprogress { background: rgba(217, 119, 6, 0.12); color: var(--warning-color); }
        .tag-insit { background: rgba(111, 66, 193, 0.12); color: #6f42c1; }
        .tag-pending { background: rgba(108, 117, 125, 0.12); color: #6c757d; }
        .tag-other { background: rgba(13, 202, 240, 0.12); color: #0dcaf0; }
        
        .note-list { list-style: none; margin: 0; padding: 0; }
        .note-list li {
            position: relative;
            padding-left: 18px;
            margin-bottom: 6px;
            font-size: 0.85rem;
            color: #6c757d;
            line-height: 1.6;
        }
        .note-list li:last-child { margin-bottom: 0; }
        .note-list li::before {
            content: '';
            position: absolute;
            left: 4px;
            top: 0.62em;
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: #adb5bd;
        }
        
        .timeline-collapse-wrapper { margin-top: 16px; border-top: 1px solid #f0f0f0; padding-top: 16px; }
        
        .timeline-collapse-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            padding: 4px 0;
            user-select: none;
        }
        
        .timeline-collapse-title {
            font-family: var(--font-display);
            font-size: 16px;
            font-weight: 700;
            color: var(--primary-dark);
            margin: 0;
            letter-spacing: 0.05em;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .timeline-collapse-toggle {
            width: 28px;
            height: 28px;
            border-radius: 6px;
            background: rgba(0, 169, 157, 0.08);
            border: 1px solid rgba(0, 169, 157, 0.2);
            color: var(--primary-dark);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s ease;
            flex-shrink: 0;
        }
        
        .timeline-collapse-toggle i { font-size: 0.85rem; line-height: 1; display: block; }
        
        .timeline-collapse-header:hover .timeline-collapse-toggle {
            background: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }
        
        .timeline-collapse-body {
            overflow: hidden;
            transition: max-height 0.3s ease;
            max-height: 0;
            padding-top: 0; 
        }
        
        .timeline-collapse-body.show { max-height: 5000px; }
        
        .iq-timeline { position: relative; list-style: none; margin: 0; padding-top: 12px; padding-left: 12px; }
        .timeline-item { position: relative; display: flex; padding-bottom: 20px; }
        .timeline-item:last-child { padding-bottom: 0; }
        
        .timeline-marker { 
            display: flex; flex-direction: column; align-items: center; 
            position: relative; z-index: 1; margin-right: 16px; flex-shrink: 0; min-width: 14px; 
        }
        
        .marker-dot { 
            width: 12px; height: 12px; border-radius: 50%; 
            background-color: #e9ecef; border: 2px solid #ffffff; 
            box-shadow: 0 0 0 2px #e9ecef; flex-shrink: 0; transition: all 0.3s ease; 
        }
        
        .marker-dot.completed { background-color: var(--success-color); box-shadow: 0 0 0 2px rgba(25, 135, 84, 0.25); }
        .marker-dot.current { background-color: var(--warning-color); box-shadow: 0 0 0 2px rgba(217, 119, 6, 0.2); animation: pulse-primary 2s infinite; }
        .marker-dot.pending { background-color: #adb5bd; box-shadow: 0 0 0 2px rgba(173, 181, 189, 0.25); }
        
        .marker-line { width: 2px; flex-grow: 1; background-color: #e9ecef; margin-top: 6px; min-height: 20px; }
        .timeline-item:last-child .marker-line { display: none; }
        
        .timeline-content { flex-grow: 1; padding-top: 0; }
        
        .timeline-date-top { 
            font-size: 0.72rem; color: #6c757d; font-weight: 700; margin-bottom: 4px; 
            display: block; text-transform: uppercase; letter-spacing: 0.03em; line-height: 1.3;
        }
        
        .timeline-header { display: flex; align-items: center; margin-bottom: 4px; flex-wrap: wrap; gap: 8px; }
        .timeline-title { font-size: 0.9rem; font-weight: 700; color: #212529; margin: 0; line-height: 1.3; }
        .timeline-desc { font-size: 0.8rem; color: #6c757d; margin: 0; line-height: 1.5; }
        
        .timeline-item-edit {
            border: 2px dashed var(--primary-color);
            padding: 12px;
            margin-bottom: 12px;
            border-radius: 8px;
            background: rgba(0, 169, 157, 0.05);
            box-sizing: border-box;
            width: 100%;
        }
        
        .timeline-item-edit .timeline-edit-row {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 8px;
            flex-wrap: wrap;
        }
        
        .timeline-item-edit .timeline-edit-row:last-child {
            margin-bottom: 0;
        }
        
        .timeline-item-edit select,
        .timeline-item-edit input {
            padding: 5px 8px;
            border: 1px solid #dfe3e6;
            border-radius: 6px;
            font-size: 0.85rem;
            font-family: var(--font-body);
            box-sizing: border-box;
            min-width: 0;
        }
        
        .timeline-item-edit select { width: 130px; flex-shrink: 0; }
        .timeline-item-edit .timeline-date-input { width: 120px; flex-shrink: 0; }
        .timeline-item-edit .timeline-title-input { flex: 1; min-width: 100px; }
        .timeline-item-edit .timeline-desc-input { flex: 1; min-width: 100px; }
        
        .timeline-edit-controls {
            display: flex;
            justify-content: flex-end;
            margin-top: 12px;
        }
        
        @keyframes pulse-primary {
            0% { box-shadow: 0 0 0 0 rgba(217, 119, 6, 0.4); }
            70% { box-shadow: 0 0 0 6px rgba(217, 119, 6, 0); }
            100% { box-shadow: 0 0 0 0 rgba(217, 119, 6, 0); }
        }
        
        .lightbox-modal {
            display: none;
            position: fixed;
            z-index: 9999;
            left: 0; top: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.92);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
        }
        
        .lightbox-modal.active { display: flex; align-items: center; justify-content: center; }
        
        .lightbox-content { 
            position: relative;
            max-width: 90vw;
            max-height: 90vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .lightbox-img { 
            max-width: 100%; max-height: 85vh; object-fit: contain; 
            border-radius: 8px; box-shadow: 0 20px 60px rgba(0,0,0,0.5);
        }
        
        .lightbox-close { 
            position: absolute; top: -50px; right: 0; color: white; font-size: 1.2rem; cursor: pointer; 
            background: rgba(255, 255, 255, 0.15); border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%; width: 40px; height: 40px;
            display: flex; align-items: center; justify-content: center;
            transition: all 0.2s; backdrop-filter: blur(4px); padding: 0;
        }
        
        .lightbox-close:hover { background: rgba(255, 255, 255, 0.3); transform: scale(1.1); }
        
        .lightbox-nav { 
            position: absolute; top: 50%; transform: translateY(-50%); 
            background: rgba(255, 255, 255, 0.15); color: white; 
            border: 1px solid rgba(255, 255, 255, 0.3);
            width: 48px; height: 48px; border-radius: 50%; font-size: 1.5rem; cursor: pointer; 
            transition: all 0.2s; display: flex; align-items: center; justify-content: center;
            backdrop-filter: blur(4px);
        }
        
        .lightbox-nav:hover { background: rgba(255, 255, 255, 0.3); transform: translateY(-50%) scale(1.1); }
        .lightbox-prev { left: -70px; }
        .lightbox-next { right: -70px; }
        
        .lightbox-counter { 
            position: absolute; bottom: -40px; left: 50%; transform: translateX(-50%); 
            color: white; font-weight: 600; font-size: 0.85rem;
            background: rgba(255, 255, 255, 0.1); padding: 6px 16px; border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2); backdrop-filter: blur(4px);
        }
        
        .lightbox-caption {
            position: absolute;
            top: calc(100% + 48px);
            left: 50%;
            transform: translateX(-50%);
            color: white;
            font-size: 0.9rem;
            font-weight: 500;
            text-align: center;
            background: rgba(0, 0, 0, 0.65);
            padding: 10px 24px;
            border-radius: 8px;
            max-width: 80%;
            backdrop-filter: blur(4px);
            line-height: 1.5;
            border: 1px solid rgba(255, 255, 255, 0.1);
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .guideline-modal {
            display: none;
            position: fixed;
            z-index: 10000;
            left: 0; top: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .guideline-modal.active { display: flex; }
        
        .guideline-content {
            background: #ffffff;
            border-radius: 16px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.2);
            max-width: 1100px;
            width: 100%;
            max-height: 85vh;
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        
        .guideline-header {
            flex-shrink: 0;
            padding: 32px 40px 24px 40px;
            position: relative;
            z-index: 2;
            background: #ffffff;
        }
        
        .guideline-header::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 40px;
            right: 40px;
            height: 1px;
            background: #eef0f2;
        }
        
        .guideline-close {
            position: absolute;
            top: 20px;
            right: 20px;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: #f4f6f9;
            border: none;
            color: #6c757d;
            font-size: 1.1rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s;
            z-index: 3;
        }
        
        .guideline-close:hover { background: #e9ecef; color: #212529; }
        
        .guideline-title {
            font-family: var(--font-display);
            font-size: 24px;
            font-weight: 700;
            color: #212529;
            margin: 0 0 8px 0;
            padding-right: 40px;
        }
        
        .guideline-subtitle {
            font-size: 0.9rem;
            color: #6c757d;
            margin: 0;
            padding-right: 40px;
        }
        
        .guideline-scroll {
            overflow-y: auto;
            flex: 1;
            padding: 24px 40px 32px 40px;
            scrollbar-gutter: stable;
        }
        
        .guideline-scroll::-webkit-scrollbar { width: 8px; }
        .guideline-scroll::-webkit-scrollbar-track { background: transparent; margin: 12px 0; }
        .guideline-scroll::-webkit-scrollbar-thumb { background: #c5c9ce; border-radius: 4px; border: 2px solid #ffffff; }
        .guideline-scroll::-webkit-scrollbar-thumb:hover { background: #a8adb3; }
        
        .guideline-section {
            margin-bottom: 24px;
            padding-bottom: 24px;
            border-bottom: 1px solid #eef0f2;
        }
        
        .guideline-section:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }
        
        .guideline-section-title {
            font-family: var(--font-display);
            font-size: 16px;
            font-weight: 700;
            color: var(--primary-dark);
            margin: 0 0 12px 0;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .guideline-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 10px;
        }
        
        .guideline-item {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 10px 14px;
            background: #f8f9fa;
            border-radius: 8px;
            font-size: 0.85rem;
            color: #495057;
        }
        
        .color-swatch {
            width: 16px;
            height: 16px;
            border-radius: 4px;
            flex-shrink: 0;
            border: 1px solid rgba(0,0,0,0.08);
        }
        
        .color-hex {
            font-family: monospace;
            font-size: 0.78rem;
            color: #6c757d;
            margin-left: auto;
        }
        
        .guideline-text-list { list-style: none; padding: 0; margin: 0; }
        .guideline-text-list li {
            padding: 6px 0;
            font-size: 0.88rem;
            color: #495057;
            display: flex;
            align-items: flex-start;
            gap: 12px;
            line-height: 1.5;
        }
        .guideline-text-list code {
            background: #f4f6f9;
            padding: 2px 6px;
            border-radius: 4px;
            font-family: monospace;
            font-size: 0.82rem;
            color: var(--primary-dark);
            white-space: nowrap;
        }
        
        .edit-mode .editable-field {
            outline: 2px dashed var(--primary-color);
            outline-offset: 2px;
            padding: 2px 6px;
            border-radius: 4px;
            background: rgba(0, 169, 157, 0.05);
            cursor: text;
        }
        
        .edit-mode .editable-field:focus {
            outline: 2px solid var(--primary-color);
            background: rgba(0, 169, 157, 0.1);
        }
        
        .edit-hint {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--primary-color);
            color: white;
            padding: 10px 16px;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.9rem;
            z-index: 9999;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            display: none;
            align-items: center;
            gap: 10px;
        }
        
        .edit-hint.show {
            display: flex;
            animation: slideIn 0.3s ease;
        }
        
        @keyframes slideIn {
            from { transform: translateX(400px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        
        .edit-hint .edit-btn { margin-left: 4px; }
        
        .edit-controls {
            display: none;
            margin-top: 16px;
            padding-top: 16px;
            border-top: 1px dashed #eef0f2;
        }
        
        .edit-mode .edit-controls {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }
        
        .edit-controls.delete-project-controls {
            justify-content: flex-end;
            border-top: none;
            padding-top: 8px;
            margin-top: 8px;
        }
        
        .edit-btn {
            padding: 6px 12px;
            border-radius: 6px;
            border: 1px solid var(--primary-color);
            background: white;
            color: var(--primary-dark);
            font-size: 0.82rem;
            font-weight: 600;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            transition: all 0.2s;
        }
        
        .edit-btn:hover { background: var(--primary-color); color: white; }
        
        .edit-btn.danger { border-color: var(--danger-color); color: var(--danger-color); }
        .edit-btn.danger:hover { background: var(--danger-color); color: white; }
        
        @media (max-width: 1400px) {
            .lightbox-prev { left: 10px; }
            .lightbox-next { right: 10px; }
        }
        
        @media (max-width: 992px) {
            .projects-list { grid-template-columns: 1fr; }
            .exec-stats { grid-template-columns: repeat(2, 1fr); }
            .exec-stats.store-stats { grid-template-columns: repeat(2, 1fr); }
        }
        
        @media (max-width: 768px) {
            body { padding: 20px 12px; }
            .top-header { margin: -20px -12px 24px -12px; }
            .top-header-inner { padding: 10px 8px; }
            .watsons-icon { width: 36px; height: 36px; border-radius: 8px; }
            .tab-btn { font-size: 0.8rem; }
            .header-tabs { gap: 16px; }
            .report-header { 
                padding: 24px 20px; 
                flex-direction: column;
                align-items: flex-start;
                gap: 24px;
            }
            .report-header h1 { font-size: 32px; }
            .header-logo-card { align-self: flex-start; flex-direction: column; align-items: center; gap: 10px; }
            .watsons-logo { height: 36px; }
            .logo-slogan { font-size: 10px; letter-spacing: 0.14em; }
            .section-title { font-size: 24px; }
            .exec-summary { padding: 18px; }
            .exec-stats { grid-template-columns: 1fr 1fr; }
            .project-title { font-size: 1.25rem; }
            .project-header { flex-direction: column; gap: 12px; }
            .project-header-left { width: 100%; }
            .gallery-btn-mini { align-self: flex-start; }
            .project-card { padding: 16px 18px; scroll-margin-top: 76px; }
            .report-meta { flex-direction: column; align-items: flex-start; }
            .progress-head, .progress-layout { grid-template-columns: 64px 1fr; column-gap: 10px; }
            .progress-head { margin-bottom: 22px; }
            .progress-layout { row-gap: 22px; }
            .back-to-top { right: 16px; bottom: 16px; width: 40px; height: 40px; }
            .decision-table thead th { padding: 12px 14px; font-size: 14px; }
            .decision-table tbody td { padding: 14px; font-size: 13px; }
            .guideline-header { padding: 24px 20px 20px 20px; }
            .guideline-header::after { left: 20px; right: 20px; }
            .guideline-scroll { padding: 20px; }
            .guideline-grid { grid-template-columns: 1fr; }
            .lightbox-close { top: 10px; right: 10px; }
            .lightbox-counter { bottom: 10px; }
            .lightbox-caption {
                top: calc(100% + 8px);
                font-size: 0.8rem;
                padding: 8px 16px;
                max-width: 90%;
            }
        }
    </style>
</head>
<body>

<div class="edit-hint" id="editHint">
    <span><i class="bi bi-pencil-square me-2"></i>編輯模式已開啟</span>
    <button class="edit-btn" id="saveDownloadBtn" onclick="saveAndDownload()">
        <i class="bi bi-download"></i> 保存並下載
    </button>
</div>

<header class="top-header">
    <div class="top-header-inner">
        <img src="C:\Users\clarysung\Downloads\watsons-icon.png" alt="Watsons Icon" class="watsons-icon">
        <div class="header-tabs">
            <button class="tab-btn active" data-tab="ec">EC</button>
            <button class="tab-btn" data-tab="store">Store</button>
            <button class="tab-btn" data-tab="decision">Decision</button>
        </div>
    </div>
</header>

<div class="report-container">
    <div class="report-header">
        <div class="header-content">
            <h1>Weekly Executive Report</h1>
            <p class="report-summary-text" id="reportSummary">Group Supplier Portal · Group Seller Center · New DS · AIMAS O+O coupon · Oracle PRIME HCM · OMM x Shopee Integration</p>
            <div class="report-meta">
                <div class="meta-pill">
                    <span class="pill-label">Period ·</span>
                    <span class="pill-value editable-field" id="reportPeriod" data-field="period">2026/8/4 - 2026/8/11</span>
                </div>
                <div class="meta-pill">
                    <span class="pill-label">Scope ·</span>
                    <span class="pill-value" id="reportScope">6 Workstreams</span>
                </div>
            </div>
        </div>
        
        <div class="header-logo-card">
            <img src="C:\Users\clarysung\Downloads\watsons-logo.png" alt="Watsons Logo" class="watsons-logo">
            <div class="logo-slogan">185 TH · 同心同行</div>
        </div>
    </div>
    
    <!-- EC Content -->
    <div id="ec-content">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 24px;">
            <h2 class="section-title" style="margin: 0;">工作流進度</h2>
            <button class="edit-btn" id="addProjectBtn" style="display: none;" onclick="addProjectCard()">
                <i class="bi bi-plus-lg"></i> 新增專案卡片
            </button>
        </div>
        
        <div class="projects-list" id="projectsList">
            <!-- Project 1 -->
            <div class="project-card" id="project-1" data-images='[{"src":"https://picsum.photos/seed/gsp-e2e/800/600","caption":"GSP E2E 壓測與 VB UAT 排程"},{"src":"https://picsum.photos/seed/gsp-buyer/800/600","caption":"GSP Buyer 訓練完成"},{"src":"https://picsum.photos/seed/gsp-git/800/600","caption":"GSP GIT 開發報價與 RETEK 新品貨號確認"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title editable-field" data-field="title">Group Supplier Portal</h3>
                            <select class="edit-select status-select" data-project="1" style="display: none;">
                                <option value="ontrack" data-class="status-ontrack">On Track</option>
                                <option value="attention" data-class="status-attention">Attention</option>
                                <option value="delayed" data-class="status-delayed" selected>Delayed</option>
                                <option value="wip" data-class="status-wip">In Progress</option>
                                <option value="monitor" data-class="status-monitor">Monitor</option>
                            </select>
                            <span class="status-badge status-delayed">Delayed</span>
                        </div>
                        <div class="project-tags editable-field" data-field="tags">Phase 1 · Data Migration · Digital Procurement</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(0)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">3</span>
                    </button>
                </div>
                
                <div class="card-section gap-16">
                    <div class="progress-head">
                        <h4 class="card-section-title">進度</h4>
                        <p class="progress-text editable-field" data-field="progress-text">Item Creation: 98% · Item Enrichment: 91% · Item Listing: 77%</p>
                    </div>
                    <div class="progress-layout" data-progress-container="true">
                        <span class="progress-label">SIT</span>
                        <div class="progress-bar-custom" style="--p: 100%"><div class="progress-fill"></div><span class="progress-percent">100%</span></div>
                        <span class="progress-label">UAT</span>
                        <div class="progress-bar-custom" style="--p: 77%"><div class="progress-fill fill-uat"></div><span class="progress-percent pc-uat">77%</span></div>
                        <span class="progress-label">Pre-Prod</span>
                        <div class="progress-bar-custom" style="--p: 45%"><div class="progress-fill fill-preprod"></div><span class="progress-percent pc-preprod">45%</span></div>
                    </div>
                    <div class="edit-controls" data-progress-controls="true">
                        <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                    </div>
                    <ul class="key-points" data-desc-container="true">
                        <li>GSP GIT development quotation $175,000</li>
                        <li>Sales Dashboard: UAT Data preparation LIT提供2年資料</li>
                        <li>新品貨號分配，關貿不須改動現有邏輯，RETEK需改成500000開始給號</li>
                    </ul>
                    <div class="edit-controls" data-desc-controls="true">
                        <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section" data-risk-section="true">
                    <div class="risk-card">
                        <h5 class="risk-title">Risk &amp; Issue</h5>
                        <ul class="key-points" data-risk-desc-container="true">
                            <li>TradeVan 出口資料解決方案與 Capex 待 31 Jul 回覆</li>
                            <li>任何開發前置時間可能影響 go-live 規劃</li>
                        </ul>
                    </div>
                    <div class="edit-controls" data-risk-controls="true">
                        <button class="edit-btn" data-toggle-type="risk" onclick="toggleRiskSection(this)"><i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue</button>
                        <button class="edit-btn" onclick="addRiskDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points" data-plan-desc-container="true">
                        <li>8/3 – 8/10：VB UAT（In Progress，提早）</li>
                        <li>8/10 – 8/17：Supplier Training</li>
                        <li>8/24 – 8/25：Data Migration</li>
                    </ul>
                    <div class="edit-controls" data-plan-controls="true">
                        <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                        <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group">
                            <span class="note-tag tag-completed">#Completed</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>7/15 Decision making 完成，確認 Phase 1 範圍與 Data Migration 策略</li>
                                <li>7/23 完成內部 Buyer 訓練；E2E 壓測與 VB UAT 排程定案</li>
                                <li>確認 GIT 開發報價 $175,000；RETEK 新品貨號自 500000 起給號</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-insit">#In SIT</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>E2E 壓測（7/27–8/3）進行中</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-inprogress">#In progress</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>VB UAT（8/3–8/10，提早）進行中</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-other">#Other</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>Supplier Portal 操作手冊初稿完成，待訓練後定稿</li>
                            </ul>
                        </div>
                        <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                            <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                        </div>
                    </div>
                </div>
                
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline" data-timeline-container="true">
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">7/15</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Decision making</h6></div>
                                    <p class="timeline-desc">Done</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">7/23</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Internal Training Buyer</h6></div>
                                    <p class="timeline-desc">Done</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">7/27 ~ 8/3</span>
                                    <div class="timeline-header"><h6 class="timeline-title">End 2 End testing + Load Test</h6></div>
                                    <p class="timeline-desc">In Progress</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">8/3 ~ 8/10</span>
                                    <div class="timeline-header"><h6 class="timeline-title">VB UAT</h6></div>
                                    <p class="timeline-desc">In Progress，提早</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">8/10 ~ 8/17</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Supplier Training</h6></div>
                                    <p class="timeline-desc"></p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">8/24 ~ 8/25</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Data Migration</h6></div>
                                    <p class="timeline-desc"></p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">8/25 ~</span>
                                    <div class="timeline-header"><h6 class="timeline-title">System Deployment</h6></div>
                                    <p class="timeline-desc"></p>
                                </div>
                            </li>
                        </ul>
                        <div class="edit-controls" data-timeline-controls="true">
                            <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                        </div>
                    </div>
                </div>
                
                <div class="edit-controls delete-project-controls">
                    <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
                </div>
            </div>
            
            <!-- Project 2 -->
            <div class="project-card" id="project-2" data-images='[{"src":"https://picsum.photos/seed/sc-uat/800/600","caption":"Seller Center UAT 測試環境"},{"src":"https://picsum.photos/seed/sc-mm/800/600","caption":"Seller Center 帳務及發票改動"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title editable-field" data-field="title">Group Seller Center</h3>
                            <select class="edit-select status-select" data-project="2" style="display: none;">
                                <option value="ontrack" data-class="status-ontrack">On Track</option>
                                <option value="attention" data-class="status-attention" selected>Attention</option>
                                <option value="delayed" data-class="status-delayed">Delayed</option>
                                <option value="wip" data-class="status-wip">In Progress</option>
                                <option value="monitor" data-class="status-monitor">Monitor</option>
                            </select>
                            <span class="status-badge status-attention">Attention</span>
                        </div>
                        <div class="project-tags editable-field" data-field="tags">Phase 1 · Product Onboarding · ECommerce Platform</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(1)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">2</span>
                    </button>
                </div>
                
                <div class="card-section gap-16">
                    <div class="progress-head">
                        <h4 class="card-section-title">進度</h4>
                        <p class="progress-text editable-field" data-field="progress-text">UAT Training: Done · E2E Target: 17 Aug</p>
                    </div>
                    <div class="progress-layout" data-progress-container="true">
                        <span class="progress-label">SIT</span>
                        <div class="progress-bar-custom" style="--p: 90%"><div class="progress-fill"></div><span class="progress-percent">90%</span></div>
                        <span class="progress-label">UAT</span>
                        <div class="progress-bar-custom" style="--p: 65%"><div class="progress-fill fill-uat"></div><span class="progress-percent pc-uat">65%</span></div>
                        <span class="progress-label">Pre-Prod</span>
                        <div class="progress-bar-custom" style="--p: 20%"><div class="progress-fill fill-preprod"></div><span class="progress-percent pc-preprod">20%</span></div>
                    </div>
                    <div class="edit-controls" data-progress-controls="true">
                        <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                    </div>
                    <ul class="key-points" data-desc-container="true">
                        <li>預計有20個Supplier，約6500個SKU上線</li>
                        <li>For pilot supplier onboarding in Sep/Oct，focus on業績小的廠商先搬到SC & 盡全力新招商新品牌</li>
                        <li>關貿帳務及發票改動 $141,228 (未稅)</li>
                    </ul>
                    <div class="edit-controls" data-desc-controls="true">
                        <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section" data-risk-section="true">
                    <div class="risk-card">
                        <h5 class="risk-title">Risk &amp; Issue</h5>
                        <ul class="key-points" data-risk-desc-container="true">
                            <li>EMIS / MM 需區分 Gross Basis 與 Commission Basis</li>
                            <li>關貿帳務及發票改動估算 $141,228（未稅）待確認</li>
                        </ul>
                    </div>
                    <div class="edit-controls" data-risk-controls="true">
                        <button class="edit-btn" data-toggle-type="risk" onclick="toggleRiskSection(this)"><i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue</button>
                        <button class="edit-btn" onclick="addRiskDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points" data-plan-desc-container="true">
                        <li>8/5：Training & UAT 階段完成</li>
                        <li>8/17：首次 E2E 測試</li>
                        <li>SEP：Ph 1 – CDS Go-Live</li>
                    </ul>
                    <div class="edit-controls" data-plan-controls="true">
                        <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                        <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group">
                            <span class="note-tag tag-completed">#Completed</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>7/27 Phase 1 進入 UAT；Training & UAT（7/10–8/5）啟動</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-inprogress">#In progress</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>UAT 執行中；首次 E2E 目標 17 Aug、UAT 完成目標 4 Sep</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-pending">#Pending</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>關貿帳務及發票改動估算 $141,228（未稅），EMIS／MM 欄位邏輯待確認</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-other">#Other</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>本期另有 3 個新品牌表達入駐意願，待招商團隊評估</li>
                            </ul>
                        </div>
                        <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                            <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                        </div>
                    </div>
                </div>
                
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline" data-timeline-container="true">
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">7/27</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Phase 1 Status</h6></div>
                                    <p class="timeline-desc">in UAT</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">7/10 ~ 8/5</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Training & UAT</h6></div>
                                    <p class="timeline-desc"></p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">Jul ~ Sep 2026</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Ph 1 – CDS</h6></div>
                                    <p class="timeline-desc">target UAT in Jul, System ready in Aug, Go-Live in Sep. 2026</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">Nov ~ Dec 2026</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Ph 2 – CVS FamiMart</h6></div>
                                    <p class="timeline-desc">Go-Live in Nov & Dec. 2026</p>
                                </div>
                            </li>
                        </ul>
                        <div class="edit-controls" data-timeline-controls="true">
                            <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                        </div>
                    </div>
                </div>
                
                <div class="edit-controls delete-project-controls">
                    <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
                </div>
            </div>
            
            <!-- Project 3 -->
            <div class="project-card" id="project-3" data-images='[{"src":"https://picsum.photos/seed/ds-arch/800/600","caption":"New DS 架構設計圖"},{"src":"https://picsum.photos/seed/ds-case/800/600","caption":"New DS Business Case 投資效益分析"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title editable-field" data-field="title">New DS</h3>
                            <select class="edit-select status-select" data-project="3" style="display: none;">
                                <option value="ontrack" data-class="status-ontrack">On Track</option>
                                <option value="attention" data-class="status-attention">Attention</option>
                                <option value="delayed" data-class="status-delayed">Delayed</option>
                                <option value="wip" data-class="status-wip" selected>In Progress</option>
                                <option value="monitor" data-class="status-monitor">Monitor</option>
                            </select>
                            <span class="status-badge status-wip">In Progress</span>
                        </div>
                        <div class="project-tags editable-field" data-field="tags">Business case · Architecture · e-Invoice</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(2)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">2</span>
                    </button>
                </div>
                
                <div class="card-section gap-16">
                    <div class="progress-head">
                        <h4 class="card-section-title">進度</h4>
                        <p class="progress-text editable-field" data-field="progress-text">Technical direction forming · Business case pending</p>
                    </div>
                    <div class="progress-layout" data-progress-container="true">
                        <span class="progress-label">SIT</span>
                        <div class="progress-bar-custom" style="--p: 55%"><div class="progress-fill"></div><span class="progress-percent">55%</span></div>
                        <span class="progress-label">UAT</span>
                        <div class="progress-bar-custom" style="--p: 25%"><div class="progress-fill fill-uat"></div><span class="progress-percent pc-uat">25%</span></div>
                        <span class="progress-label">Pre-Prod</span>
                        <div class="progress-bar-custom" style="--p: 5%"><div class="progress-fill fill-preprod"></div><span class="progress-percent pc-preprod">5%</span></div>
                    </div>
                    <div class="edit-controls" data-progress-controls="true">
                        <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                    </div>
                    <ul class="key-points" data-desc-container="true">
                        <li>Capex 1.5M: Steven to provide quantified business benefits</li>
                        <li>GLSoft Block B Hybris is Java-based; same language for Block A and B</li>
                        <li>Block A admin page warranty/support contract TBC</li>
                    </ul>
                    <div class="edit-controls" data-desc-controls="true">
                        <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section" data-risk-section="true">
                    <div class="risk-card">
                        <h5 class="risk-title">Risk &amp; Issue</h5>
                        <ul class="key-points" data-risk-desc-container="true">
                            <li>Capex 1.5M 投資效益待 Steven 量化</li>
                            <li>Block A 維保合約、e-Invoice Capex 影響待確認</li>
                        </ul>
                    </div>
                    <div class="edit-controls" data-risk-controls="true">
                        <button class="edit-btn" data-toggle-type="risk" onclick="toggleRiskSection(this)"><i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue</button>
                        <button class="edit-btn" onclick="addRiskDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points" data-plan-desc-container="true">
                        <li>TBC：1.5M Capex 效益量化（Steven）</li>
                        <li>TBC：Block A 維保合約確認</li>
                        <li>TBC：e-Invoice Capex 影響評估</li>
                    </ul>
                    <div class="edit-controls" data-plan-controls="true">
                        <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                        <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group">
                            <span class="note-tag tag-completed">#Completed</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>技術方向成形，Block B Hybris 採 Java-based 以降低開發成本</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-pending">#Pending</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>Capex 1.5M 投資效益待 Steven 量化</li>
                                <li>Block A 維保合約、e-Invoice Capex 影響待確認</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-other">#Other</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>eLab 已示範 Block B 管理介面原型，會議紀錄另行發放</li>
                            </ul>
                        </div>
                        <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                            <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                        </div>
                    </div>
                </div>
                
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline" data-timeline-container="true">
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">24 JUL</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Direction Formed</h6></div>
                                    <p class="timeline-desc">Technical direction</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Business Case</h6></div>
                                    <p class="timeline-desc">1.5M Capex</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Approval</h6></div>
                                    <p class="timeline-desc">Final decision</p>
                                </div>
                            </li>
                        </ul>
                        <div class="edit-controls" data-timeline-controls="true">
                            <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                        </div>
                    </div>
                </div>
                
                <div class="edit-controls delete-project-controls">
                    <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
                </div>
            </div>
            
            <!-- Project 4 -->
            <div class="project-card" id="project-4" data-images='[{"src":"https://picsum.photos/seed/aimas-coupon/800/600","caption":"AIMAS O+O 優惠券規則引擎"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title editable-field" data-field="title">AIMAS O+O coupon</h3>
                            <select class="edit-select status-select" data-project="4" style="display: none;">
                                <option value="ontrack" data-class="status-ontrack">On Track</option>
                                <option value="attention" data-class="status-attention">Attention</option>
                                <option value="delayed" data-class="status-delayed">Delayed</option>
                                <option value="wip" data-class="status-wip" selected>In Progress</option>
                                <option value="monitor" data-class="status-monitor">Monitor</option>
                            </select>
                            <span class="status-badge status-wip">In Progress</span>
                        </div>
                        <div class="project-tags editable-field" data-field="tags">O+O Coupon · AIMAS · Marketing</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(3)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">1</span>
                    </button>
                </div>
                
                <div class="card-section">
                    <div class="progress-head">
                        <h4 class="card-section-title">進度</h4>
                        <p class="progress-text editable-field" data-field="progress-text">Coupon rule engine In Progress · Store redemption TBC</p>
                    </div>
                    <div class="progress-layout" data-progress-container="true">
                        <span class="progress-label">SIT</span>
                        <div class="progress-bar-custom" style="--p: 70%"><div class="progress-fill"></div><span class="progress-percent">70%</span></div>
                        <span class="progress-label">UAT</span>
                        <div class="progress-bar-custom" style="--p: 45%"><div class="progress-fill fill-uat"></div><span class="progress-percent pc-uat">45%</span></div>
                        <span class="progress-label">Pre-Prod</span>
                        <div class="progress-bar-custom" style="--p: 10%"><div class="progress-fill fill-preprod"></div><span class="progress-percent pc-preprod">10%</span></div>
                    </div>
                    <div class="edit-controls" data-progress-controls="true">
                        <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                    </div>
                    <ul class="key-points" data-desc-container="true">
                        <li>O+O 優惠券發放與核銷流程整合 AIMAS 開發中。</li>
                        <li>門市端核銷介面與 POS 連動設計確認中。</li>
                    </ul>
                    <div class="edit-controls" data-desc-controls="true">
                        <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points" data-plan-desc-container="true">
                        <li>AUG：行銷端發放情境確認</li>
                        <li>TBC：門市核銷介面與 POS 連動設計</li>
                        <li>TBC：Store Pilot 規劃</li>
                    </ul>
                    <div class="edit-controls" data-plan-controls="true">
                        <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                        <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group">
                            <span class="note-tag tag-completed">#Completed</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>完成優惠券規則與核銷流程需求確認</li>
                                <li>AIMAS 介接規格初稿完成</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-inprogress">#In progress</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>AIMAS 介接開發中，待與行銷端確認發放情境</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-other">#Other</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>行銷端提出雙 11 檔期發放需求，時程待評估</li>
                            </ul>
                        </div>
                        <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                            <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                        </div>
                    </div>
                </div>
                
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline" data-timeline-container="true">
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">24 JUL</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Requirement Confirmed</h6></div>
                                    <p class="timeline-desc">Done</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">AIMAS Integration</h6></div>
                                    <p class="timeline-desc">In Progress</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Store Pilot</h6></div>
                                    <p class="timeline-desc">Planned</p>
                                </div>
                            </li>
                        </ul>
                        <div class="edit-controls" data-timeline-controls="true">
                            <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                        </div>
                    </div>
                </div>
                
                <div class="edit-controls delete-project-controls">
                    <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
                </div>
            </div>
            
            <!-- Project 5 -->
            <div class="project-card" id="project-5" data-images='[{"src":"https://picsum.photos/seed/hcm-uat/800/600","caption":"HCM 介面 UAT 92% 進度"},{"src":"https://picsum.photos/seed/hcm-dm/800/600","caption":"HCM Core HR 資料遷移完成"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title editable-field" data-field="title">Oracle PRIME HCM</h3>
                            <select class="edit-select status-select" data-project="5" style="display: none;">
                                <option value="ontrack" data-class="status-ontrack" selected>On Track</option>
                                <option value="attention" data-class="status-attention">Attention</option>
                                <option value="delayed" data-class="status-delayed">Delayed</option>
                                <option value="wip" data-class="status-wip">In Progress</option>
                                <option value="monitor" data-class="status-monitor">Monitor</option>
                            </select>
                            <span class="status-badge status-ontrack">On Track</span>
                        </div>
                        <div class="project-tags editable-field" data-field="tags">Core HR · Interface · Break Hour</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(4)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">2</span>
                    </button>
                </div>
                
                <div class="card-section gap-16">
                    <div class="progress-head">
                        <h4 class="card-section-title">進度</h4>
                        <p class="progress-text editable-field" data-field="progress-text">Interface UAT: 92% · Core HR Pre-prod DM: 100%</p>
                    </div>
                    <div class="progress-layout" data-progress-container="true">
                        <span class="progress-label">SIT</span>
                        <div class="progress-bar-custom" style="--p: 100%"><div class="progress-fill"></div><span class="progress-percent">100%</span></div>
                        <span class="progress-label">UAT</span>
                        <div class="progress-bar-custom" style="--p: 92%"><div class="progress-fill fill-uat"></div><span class="progress-percent pc-uat">92%</span></div>
                        <span class="progress-label">Pre-Prod</span>
                        <div class="progress-bar-custom" style="--p: 70%"><div class="progress-fill fill-preprod"></div><span class="progress-percent pc-preprod">70%</span></div>
                    </div>
                    <div class="edit-controls" data-progress-controls="true">
                        <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                    </div>
                    <ul class="key-points" data-desc-container="true">
                        <li>Interface UAT 92% as of 21 Jul; HCM_INT_117_AD in UAT, HCM_INT_118_IDCS pending GIT notification</li>
                        <li>Core HR pre-production data migration completed 24 Jul (plan 21–29 Jul)</li>
                        <li>Break Hour direction: retain leave handling in Qisda and interface result to HCM</li>
                    </ul>
                    <div class="edit-controls" data-desc-controls="true">
                        <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section" data-risk-section="true">
                    <div class="risk-card">
                        <h5 class="risk-title">Risk &amp; Issue</h5>
                        <ul class="key-points" data-risk-desc-container="true">
                            <li>確認 Qisda 額外介面範圍 / Capex</li>
                            <li>待 Aaron 正式書面確認 Break Hour 方向</li>
                        </ul>
                    </div>
                    <div class="edit-controls" data-risk-controls="true">
                        <button class="edit-btn" data-toggle-type="risk" onclick="toggleRiskSection(this)"><i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue</button>
                        <button class="edit-btn" onclick="addRiskDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points" data-plan-desc-container="true">
                        <li>7/31：Break Hour 正式書面確認（Aaron）</li>
                        <li>AUG：HCM_INT_118_IDCS 啟動（待 GIT 通知）</li>
                        <li>TBC：Formal Approval</li>
                    </ul>
                    <div class="edit-controls" data-plan-controls="true">
                        <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                        <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group">
                            <span class="note-tag tag-completed">#Completed</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>7/24 Core HR 預產環境資料遷移完成（原計畫 21–29 Jul）</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-inprogress">#In progress</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>7/21 介面 UAT 追平至 92%（HCM_INT_117_AD 測試中）</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-pending">#Pending</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>Break Hour 方向：保留 Qisda、介面回傳 HCM；待 Aaron 正式書面確認</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-other">#Other</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>HR 每月異動報表已切換由 HCM 輸出</li>
                            </ul>
                        </div>
                        <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                            <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                        </div>
                    </div>
                </div>
                
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline" data-timeline-container="true">
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">21 JUL</span>
                                    <div class="timeline-header"><h6 class="timeline-title">HCM 92%</h6></div>
                                    <p class="timeline-desc">Interface UAT caught up</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">24 JUL</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Core HR DM</h6></div>
                                    <p class="timeline-desc">Pre-production complete</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">31 JUL</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Break Hour</h6></div>
                                    <p class="timeline-desc">Confirmation due</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Formal Approval</h6></div>
                                    <p class="timeline-desc">Sign-off</p>
                                </div>
                            </li>
                        </ul>
                        <div class="edit-controls" data-timeline-controls="true">
                            <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                        </div>
                    </div>
                </div>
                
                <div class="edit-controls delete-project-controls">
                    <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
                </div>
            </div>
            
            <!-- Project 6 -->
            <div class="project-card" id="project-6" data-images='[{"src":"https://picsum.photos/seed/omm-shopee/800/600","caption":"OMM x Shopee API 整合測試"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title editable-field" data-field="title">OMM x Shopee Integration</h3>
                            <select class="edit-select status-select" data-project="6" style="display: none;">
                                <option value="ontrack" data-class="status-ontrack">On Track</option>
                                <option value="attention" data-class="status-attention">Attention</option>
                                <option value="delayed" data-class="status-delayed">Delayed</option>
                                <option value="wip" data-class="status-wip" selected>In Progress</option>
                                <option value="monitor" data-class="status-monitor">Monitor</option>
                            </select>
                            <span class="status-badge status-wip">In Progress</span>
                        </div>
                        <div class="project-tags editable-field" data-field="tags">OMM · Shopee · Integration</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(5)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">1</span>
                    </button>
                </div>
                
                <div class="card-section">
                    <div class="progress-head">
                        <h4 class="card-section-title">進度</h4>
                        <p class="progress-text editable-field" data-field="progress-text">API development In Progress · UAT TBC</p>
                    </div>
                    <div class="progress-layout" data-progress-container="true">
                        <span class="progress-label">SIT</span>
                        <div class="progress-bar-custom" style="--p: 60%"><div class="progress-fill"></div><span class="progress-percent">60%</span></div>
                        <span class="progress-label">UAT</span>
                        <div class="progress-bar-custom" style="--p: 30%"><div class="progress-fill fill-uat"></div><span class="progress-percent pc-uat">30%</span></div>
                        <span class="progress-label">Pre-Prod</span>
                        <div class="progress-bar-custom" style="--p: 5%"><div class="progress-fill fill-preprod"></div><span class="progress-percent pc-preprod">5%</span></div>
                    </div>
                    <div class="edit-controls" data-progress-controls="true">
                        <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                    </div>
                    <ul class="key-points" data-desc-container="true">
                        <li>Shopee 訂單／商品同步 API 開發中，目標 9 月完成整合測試。</li>
                        <li>OMM 欄位映射與錯誤重試／對帳機制設計確認中。</li>
                    </ul>
                    <div class="edit-controls" data-desc-controls="true">
                        <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points" data-plan-desc-container="true">
                        <li>SEP：Shopee 整合測試完成</li>
                        <li>TBC：欄位映射與對帳機制確認</li>
                        <li>TBC：UAT</li>
                    </ul>
                    <div class="edit-controls" data-plan-controls="true">
                        <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                        <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                    </div>
                </div>
                
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group">
                            <span class="note-tag tag-completed">#Completed</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>完成整合範圍確認與 API 規格初稿</li>
                                <li>Shopee 端沙盒帳號與權限申請已送出</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-inprogress">#In progress</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>Shopee 訂單／商品同步 API 開發中，目標 9 月完成整合測試</li>
                            </ul>
                        </div>
                        <div class="note-group">
                            <span class="note-tag tag-other">#Other</span>
                            <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                            <ul class="note-list" data-note-container="true">
                                <li>Shopee 通知 9 月將升級 Open Platform v2，需評估 API 相容性</li>
                            </ul>
                        </div>
                        <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                            <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                        </div>
                    </div>
                </div>
                
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline" data-timeline-container="true">
                            <li class="timeline-item" data-marker-state="completed">
                                <div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">24 JUL</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Scope Confirmed</h6></div>
                                    <p class="timeline-desc">Done</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="current">
                                <div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">Integration Test</h6></div>
                                    <p class="timeline-desc">In Progress</p>
                                </div>
                            </li>
                            <li class="timeline-item" data-marker-state="pending">
                                <div class="timeline-marker"><div class="marker-dot pending"></div></div>
                                <div class="timeline-content">
                                    <span class="timeline-date-top">TBC</span>
                                    <div class="timeline-header"><h6 class="timeline-title">UAT</h6></div>
                                    <p class="timeline-desc">Planned</p>
                                </div>
                            </li>
                        </ul>
                        <div class="edit-controls" data-timeline-controls="true">
                            <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                        </div>
                    </div>
                </div>
                
                <div class="edit-controls delete-project-controls">
                    <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Store Content -->
    <div id="store-content" style="display: none;">
        <h2 class="section-title">工作流進度</h2>
        <div class="projects-list">
            <div class="project-card" id="project-7" data-images='[{"src":"https://picsum.photos/seed/tw-mpos/800/600","caption":"TW mPOS－門市裝置部署"},{"src":"https://picsum.photos/seed/mpos-payment/800/600","caption":"TW mPOS－行動支付核銷測試"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title">TW mPOS</h3>
                            <span class="status-badge status-ontrack">On Track</span>
                        </div>
                        <div class="project-tags">mPOS · Store Rollout · Payment</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(6)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">2</span>
                    </button>
                </div>
                <div class="card-section">
                    <h4 class="card-section-title">進度</h4>
                    <div class="subproject">
                        <div class="subproject-header"><h5 class="subproject-title">LINE Pay</h5></div>
                        <div class="note-group"><span class="note-tag tag-completed">#Completed</span><ul class="note-list"><li>SIT：特約條款與費率確認完成，交易主流程測試通過</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-inprogress">#In progress</span><ul class="note-list"><li>UAT：門市退貨／取消交易流程驗證中</li></ul></div>
                    </div>
                    <div class="subproject">
                        <div class="subproject-header"><h5 class="subproject-title">街口支付</h5></div>
                        <div class="note-group"><span class="note-tag tag-inprogress">#In progress</span><ul class="note-list"><li>SIT：主流程測試完成，例外情境補測中</li><li>UAT：對帳檔案規格與財務確認中</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-pending">#Pending</span><ul class="note-list"><li>Pre-Prod：待對帳規格定案後啟動</li></ul></div>
                    </div>
                    <div class="subproject">
                        <div class="subproject-header"><h5 class="subproject-title">全支付</h5></div>
                        <div class="note-group"><span class="note-tag tag-inprogress">#In progress</span><ul class="note-list"><li>SIT：業者 API 回檔延遲，例外流程待補測</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-pending">#Pending</span><ul class="note-list"><li>UAT／Pre-Prod：待 API 回檔後執行</li></ul></div>
                    </div>
                </div>
                <div class="card-section" data-risk-section="true">
                    <div class="risk-card">
                        <h5 class="risk-title">Risk &amp; Issue</h5>
                        <ul class="key-points">
                            <li>全支付支線因業者 API 延遲，可能影響 9 月 Batch 3 門市部署時程</li>
                            <li>剩餘門市排入 9 月梯次，需確保部署人力與裝置到位</li>
                        </ul>
                    </div>
                </div>
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points">
                        <li>8/15：LINE Pay UAT 完成</li>
                        <li>8/20：街口對帳規格定案</li>
                        <li>8/29：全支付 API 回歸測試</li>
                        <li>SEP：Batch 3 門市部署</li>
                    </ul>
                </div>
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group"><span class="note-tag tag-completed">#Completed</span><ul class="note-list"><li>完成第二梯次門市部署與教育訓練</li><li>裝置維運 SOP 已交付門市營運團隊</li><li>付款流程回歸測試通過，無重大缺陷</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-pending">#Pending</span><ul class="note-list"><li>剩餘門市排入 9 月梯次（Batch 3）</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-other">#Other</span><ul class="note-list"><li>門市端回饋 mPOS 離線模式需求，待評估</li></ul></div>
                    </div>
                </div>
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline">
                            <li class="timeline-item"><div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div><div class="timeline-content"><span class="timeline-date-top">21 JUL</span><div class="timeline-header"><h6 class="timeline-title">Batch 2 Rollout</h6></div><p class="timeline-desc">Done</p></div></li>
                            <li class="timeline-item"><div class="timeline-marker"><div class="marker-dot pending"></div><div class="marker-line"></div></div><div class="timeline-content"><span class="timeline-date-top">TBC</span><div class="timeline-header"><h6 class="timeline-title">Batch 3 Rollout</h6></div><p class="timeline-desc">Planned</p></div></li>
                            <li class="timeline-item"><div class="timeline-marker"><div class="marker-dot pending"></div></div><div class="timeline-content"><span class="timeline-date-top">TBC</span><div class="timeline-header"><h6 class="timeline-title">Full Rollout</h6></div><p class="timeline-desc">Planned</p></div></li>
                        </ul>
                    </div>
                </div>
            </div>
            
            <div class="project-card" id="project-8" data-images='[{"src":"https://picsum.photos/seed/store-cee/800/600","caption":"Store CEE－合規差異分析"},{"src":"https://picsum.photos/seed/cee-fields/800/600","caption":"Store CEE－欄位調整設計"}]'>
                <div class="project-header">
                    <div class="project-header-left">
                        <div class="project-title-row">
                            <h3 class="project-title">Store CEE</h3>
                            <span class="status-badge status-monitor">Monitor</span>
                        </div>
                        <div class="project-tags">Store CEE · Compliance · Enhancement</div>
                    </div>
                    <button class="gallery-btn-mini" onclick="openLightbox(7)">
                        <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">2</span>
                    </button>
                </div>
                <div class="card-section">
                    <h4 class="card-section-title">進度</h4>
                    <div class="subproject">
                        <div class="subproject-header"><h5 class="subproject-title">合規差異分析</h5></div>
                        <div class="note-group"><span class="note-tag tag-completed">#Completed</span><ul class="note-list"><li>差異分析與影響範圍盤點完成</li></ul></div>
                    </div>
                    <div class="subproject">
                        <div class="subproject-header"><h5 class="subproject-title">欄位合規調整</h5></div>
                        <div class="note-group"><span class="note-tag tag-inprogress">#In progress</span><ul class="note-list"><li>欄位調整設計中，與 owner 確認優先順序與驗收標準</li></ul></div>
                    </div>
                    <div class="subproject">
                        <div class="subproject-header"><h5 class="subproject-title">門市版本升級</h5></div>
                        <div class="note-group"><span class="note-tag tag-pending">#Pending</span><ul class="note-list"><li>待 store 端版本排程確認後啟動開發</li></ul></div>
                    </div>
                </div>
                <div class="card-section plan-section" data-plan-section="true">
                    <h4 class="card-section-title">預計執行</h4>
                    <ul class="key-points">
                        <li>TBC：Store 端版本排程確認</li>
                        <li>TBC：CEE Enhancement 開發啟動</li>
                        <li>TBC：Rollout</li>
                    </ul>
                </div>
                <div class="note-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <div class="note-group"><span class="note-tag tag-completed">#Completed</span><ul class="note-list"><li>完成合規差異分析與影響範圍盤點</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-pending">#Pending</span><ul class="note-list"><li>待確認 store 端版本排程後啟動開發</li></ul></div>
                        <div class="note-group"><span class="note-tag tag-other">#Other</span><ul class="note-list"><li>與 Store CEE owner 確認優先順序與驗收標準</li></ul></div>
                    </div>
                </div>
                <div class="timeline-collapse-wrapper">
                    <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                        <h4 class="timeline-collapse-title">里程碑</h4>
                        <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                    </div>
                    <div class="timeline-collapse-body">
                        <ul class="iq-timeline">
                            <li class="timeline-item"><div class="timeline-marker"><div class="marker-dot completed"></div><div class="marker-line"></div></div><div class="timeline-content"><span class="timeline-date-top">24 JUL</span><div class="timeline-header"><h6 class="timeline-title">Gap Analysis</h6></div><p class="timeline-desc">Done</p></div></li>
                            <li class="timeline-item"><div class="timeline-marker"><div class="marker-dot current"></div><div class="marker-line"></div></div><div class="timeline-content"><span class="timeline-date-top">TBC</span><div class="timeline-header"><h6 class="timeline-title">CEE Enhancement</h6></div><p class="timeline-desc">In Progress</p></div></li>
                            <li class="timeline-item"><div class="timeline-marker"><div class="marker-dot pending"></div></div><div class="timeline-content"><span class="timeline-date-top">TBC</span><div class="timeline-header"><h6 class="timeline-title">Rollout</h6></div><p class="timeline-desc">Planned</p></div></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Decision Content -->
    <div id="decision-content" style="display: none;">
        <h2 class="section-title">本期摘要</h2>
        <section class="exec-summary">
            <ul class="exec-delivery-list">
                <li><strong>Group Supplier Portal</strong> — 完成 Buyer 訓練，進入 E2E 壓測與 VB UAT（提早）；整體進度 88.6%。</li>
                <li><strong>Group Seller Center</strong> — 7/27 進入 UAT；約 20 個 Supplier、6,500 SKU 本期規劃上線，首次 E2E 目標 17 Aug。</li>
                <li><strong>Oracle PRIME HCM</strong> — 介面 UAT 追平至 92%；Core HR 預產環境資料遷移於 7/24 如期完成。</li>
                <li><strong>New DS by eLab</strong> — 確認 Block B Hybris 採 Java-based 以降低開發成本；1.5M Capex 效益與 Block A 維保合約待補齊。</li>
                <li><strong>AIMAS O+O coupon</strong> — 優惠券規則與核銷流程需求確認完成，AIMAS 介接開發中。</li>
                <li><strong>OMM x Shopee Integration</strong> — 整合範圍確認與 API 規格初稿完成，Shopee 端沙盒帳號申請已送出。</li>
                <li><strong>TW mPOS</strong> — 第二梯次門市部署完成、回歸測試通過；行動支付支線中全支付因業者 API 延遲。</li>
                <li><strong>Store CEE</strong> — 合規差異分析完成；欄位調整與門市版本升級待 store 端版本排程。</li>
            </ul>
            <div class="exec-stats">
                <div class="exec-stat"><span class="exec-stat-value" style="color: var(--primary-dark);">88.6%</span><span class="exec-stat-label">GSP 整體進度 · Listing 77%</span></div>
                <div class="exec-stat"><span class="exec-stat-value" style="color: var(--warning-color);">65%</span><span class="exec-stat-label">Seller Center · 7/27 UAT 啟動</span></div>
                <div class="exec-stat"><span class="exec-stat-value" style="color: var(--success-color);">92%</span><span class="exec-stat-label">HCM Interface UAT · Core HR DM Done</span></div>
                <div class="exec-stat"><span class="exec-stat-value" style="color: var(--danger-color);">4</span><span class="exec-stat-label">Management Watch · 決策／依賴待關閉</span></div>
            </div>
        </section>
        
        <h2 class="section-title">決策追蹤</h2>
        <div class="decision-table-wrap">
            <table class="decision-table">
                <thead><tr><th>Decision / Action</th><th>Expected Outcome</th><th>Owner / Parties</th><th>Due</th><th>Status</th></tr></thead>
                <tbody>
                    <tr><td class="dt-action">Break Hour: confirm Qisda interface option</td><td>Lock solution scope, Capex and formal approval while keeping SO / STORE operations unchanged.</td><td>Aaron · Qisda · HCM team</td><td class="dt-due">TBC</td><td><span class="dt-status st-urgent">Urgent</span></td></tr>
                    <tr><td class="dt-action">Seller Center: close TLOG / MM design</td><td>Confirm TLOG change scope and add Commission Basis cost field / accounting logic before validation.</td><td>Vivian · GIT Store · Retek · OSB · EMIS</td><td class="dt-due">Before 17 Aug</td><td><span class="dt-status st-urgent">Urgent</span></td></tr>
                    <tr><td class="dt-action">New DS: complete 1.5M business case</td><td>Quantify benefits and confirm Block A support contract plus e-Invoice Capex impact.</td><td>Steven · GIT Store · EMIS</td><td class="dt-due">TBC</td><td><span class="dt-status st-general">General</span></td></tr>
                    <tr><td class="dt-action">GSP: obtain TradeVan response</td><td>Confirm export-data approach, development scope, Capex and impact to go-live plan.</td><td>GSP team · TradeVan</td><td class="dt-due">31 Jul</td><td><span class="dt-status st-general">General</span></td></tr>
                </tbody>
            </table>
        </div>
    </div>
    
    <div class="text-center text-muted mt-4 pt-3 border-top" style="margin-top: 24px;">
        <p class="mb-0" style="font-size: 0.85rem;">WTCTW Digital Transformation · Internal Management Use Only</p>
    </div>
</div>

<button id="backToTop" class="back-to-top" title="回到頂部" aria-label="Back to top" onclick="window.scrollTo({ top: 0, behavior: 'smooth' });">
    <i class="bi bi-chevron-up"></i>
</button>

<div id="guidelineModal" class="guideline-modal">
    <div class="guideline-content">
        <div class="guideline-header">
            <button class="guideline-close" onclick="closeGuideline()"><i class="bi bi-x-lg"></i></button>
            <h2 class="guideline-title">Weekly Report Guideline</h2>
            <p class="guideline-subtitle">供 PM 團隊共同維護頁面時參考的標準規範。</p>
        </div>
        <div class="guideline-scroll">
            <div class="guideline-section">
                <h3 class="guideline-section-title">1. 專案狀態徽章 (Status Badges)</h3>
                <div class="guideline-grid">
                    <div class="guideline-item"><div class="color-swatch" style="background: #198754;"></div><span>On Track</span><span class="color-hex">#198754</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #d97706;"></div><span>Attention</span><span class="color-hex">#d97706</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #dc3545;"></div><span>Delayed</span><span class="color-hex">#dc3545</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #6f42c1;"></div><span>In Progress</span><span class="color-hex">#6f42c1</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #0dcaf0;"></div><span>Monitor</span><span class="color-hex">#0dcaf0</span></div>
                </div>
            </div>
            <div class="guideline-section">
                <h3 class="guideline-section-title">2. 決策追蹤狀態 (Decision Status)</h3>
                <div class="guideline-grid">
                    <div class="guideline-item"><div class="color-swatch" style="background: #dc3545;"></div><span>Urgent</span><span class="color-hex">#dc3545</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #d97706;"></div><span>General</span><span class="color-hex">#d97706</span></div>
                </div>
            </div>
            <div class="guideline-section">
                <h3 class="guideline-section-title">3. EC 頁面進度條顏色 (Progress Bars)</h3>
                <div class="guideline-grid">
                    <div class="guideline-item"><div class="color-swatch" style="background: linear-gradient(90deg, #00a99d, #008f85);"></div><span>SIT</span><span class="color-hex">#00a99d → #008f85</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: linear-gradient(90deg, #56ccf2, #2f80ed);"></div><span>UAT</span><span class="color-hex">#56ccf2 → #2f80ed</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: linear-gradient(90deg, #f2c94c, #f2994a);"></div><span>Pre-Prod</span><span class="color-hex">#f2c94c → #f2994a</span></div>
                </div>
            </div>
            <div class="guideline-section">
                <h3 class="guideline-section-title">4. 里程碑進度圓點 (Milestone Dots)</h3>
                <div class="guideline-grid">
                    <div class="guideline-item"><div class="color-swatch" style="background: #198754;"></div><span>Completed</span><span class="color-hex">#198754</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #d97706;"></div><span>Current (In Progress)</span><span class="color-hex">#d97706</span></div>
                    <div class="guideline-item"><div class="color-swatch" style="background: #adb5bd;"></div><span>Pending</span><span class="color-hex">#adb5bd</span></div>
                </div>
            </div>
            <div class="guideline-section">
                <h3 class="guideline-section-title">5. 專案紀錄標籤 (Note Tags)</h3>
                <ul class="guideline-text-list">
                    <li><code>#Completed</code> 已完成事項（綠色 #198754）</li>
                    <li><code>#In progress</code> 進行中事項（橘色 #d97706）</li>
                    <li><code>#In SIT</code> SIT 測試中（紫色 #6f42c1）</li>
                    <li><code>#Pending</code> 待處理／等待中（灰色 #6c757d）</li>
                    <li><code>#Other</code> 其他未分類事項（青色 #0dcaf0）</li>
                </ul>
            </div>
            <div class="guideline-section">
                <h3 class="guideline-section-title">6. 快捷鍵</h3>
                <ul class="guideline-text-list">
                    <li><code>Ctrl + Shift + D</code> 開啟此 Guideline 頁面</li>
                    <li><code>Shift + Ctrl + E</code> 開啟/關閉編輯模式</li>
                    <li><code>ESC</code> 關閉 Guideline 或 Lightbox 或退出編輯模式</li>
                </ul>
            </div>
        </div>
    </div>
</div>

<div id="lightbox" class="lightbox-modal">
    <div class="lightbox-content">
        <button class="lightbox-close" onclick="closeLightbox()"><i class="bi bi-x-lg"></i></button>
        <button class="lightbox-nav lightbox-prev" onclick="changeImage(-1)"><i class="bi bi-chevron-left"></i></button>
        <img id="lightbox-img" class="lightbox-img" src="" alt="Project Image">
        <button class="lightbox-nav lightbox-next" onclick="changeImage(1)"><i class="bi bi-chevron-right"></i></button>
        <div id="lightbox-counter" class="lightbox-counter"></div>
        <div id="lightbox-caption" class="lightbox-caption"></div>
    </div>
</div>

<!-- Image Manager Modal -->
<div id="imageManagerModal" class="guideline-modal">
    <div class="guideline-content" style="max-width: 800px;">
        <div class="guideline-header">
            <button class="guideline-close" onclick="closeImageManager()"><i class="bi bi-x-lg"></i></button>
            <h2 class="guideline-title">圖片管理</h2>
            <p class="guideline-subtitle" id="imageManagerProjectTitle">專案名稱</p>
        </div>
        <div class="guideline-scroll">
            <div id="imageManagerList" style="display: flex; flex-direction: column; gap: 16px;"></div>
            <div style="margin-top: 24px; padding-top: 24px; border-top: 1px solid #eef0f2;">
                <h3 class="guideline-section-title">新增圖片</h3>
                <div style="display: flex; flex-direction: column; gap: 12px;">
                    <div style="display: flex; gap: 12px; align-items: center;">
                        <input type="text" id="newImageUrl" placeholder="圖片 URL" style="flex: 1; padding: 10px; border: 1px solid #dfe3e6; border-radius: 6px; font-size: 0.9rem;">
                        <input type="text" id="newImageCaption" placeholder="圖片說明文字" style="flex: 1; padding: 10px; border: 1px solid #dfe3e6; border-radius: 6px; font-size: 0.9rem;">
                        <button class="edit-btn" onclick="uploadNewImage()" style="flex-shrink: 0;">
                            <i class="bi bi-upload"></i> 上傳
                        </button>
                    </div>
                </div>
            </div>
            <div style="margin-top: 24px; padding-top: 24px; border-top: 1px solid #eef0f2; display: flex; justify-content: flex-end; gap: 12px;">
                <button class="edit-btn" onclick="closeImageManager()" style="border-color: #6c757d; color: #6c757d;">取消</button>
                <button class="edit-btn" onclick="saveImageChanges()"><i class="bi bi-check-lg"></i> 保存</button>
            </div>
        </div>
    </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
<script>
    // 從 DOM 讀取初始圖片數據
    let projectImages = [];
    document.addEventListener('DOMContentLoaded', () => {
        const cards = document.querySelectorAll('.project-card');
        projectImages = Array.from(cards).map((card, index) => {
            const data = card.getAttribute('data-images');
            if (data) {
                try { return JSON.parse(data); } catch(e) {}
            }
            return [{ src: `https://picsum.photos/seed/project-${index}/800/600`, caption: 'Project Image' }];
        });
        // 初始化圖片按鈕顯示狀態
        updateAllImageButtons();
    });
    
    let currentProject = 0;
    let currentImageIndex = 0;
    let isEditMode = false;
    let projectCounter = 6;
    let originalECContent = '';
    let originalReportSummary = '';
    let originalReportPeriod = '';
    let originalReportScope = '';
    let currentManageProjectIndex = 0;
    
    // 更新所有圖片按鈕的顯示狀態
    function updateAllImageButtons() {
        document.querySelectorAll('.project-card').forEach((card, idx) => {
            const galleryBtn = card.querySelector('.gallery-btn-mini');
            const countBadge = card.querySelector('.image-count-mini');
            if (galleryBtn && countBadge) {
                const count = projectImages[idx]?.length || 0;
                countBadge.textContent = count;
                // 非編輯模式下，如果沒有圖片就隱藏按鈕
                if (!isEditMode && count === 0) {
                    galleryBtn.style.display = 'none';
                } else {
                    galleryBtn.style.display = 'inline-flex';
                }
            }
        });
    }
    
    function openLightbox(projectIndex) {
        if (isEditMode) {
            openImageManager(projectIndex);
            return;
        }
        currentProject = projectIndex;
        currentImageIndex = 0;
        updateLightboxImage();
        document.getElementById('lightbox').classList.add('active');
        document.body.style.overflow = 'hidden';
    }
    
    function closeLightbox() {
        document.getElementById('lightbox').classList.remove('active');
        document.body.style.overflow = '';
    }
    
    function changeImage(direction) {
        const images = projectImages[currentProject];
        currentImageIndex += direction;
        if (currentImageIndex < 0) currentImageIndex = images.length - 1;
        else if (currentImageIndex >= images.length) currentImageIndex = 0;
        updateLightboxImage();
    }
    
    function updateLightboxImage() {
        const images = projectImages[currentProject];
        const currentImage = images[currentImageIndex];
        document.getElementById('lightbox-img').src = currentImage.src;
        document.getElementById('lightbox-counter').textContent = `${currentImageIndex + 1} / ${images.length}`;
        document.getElementById('lightbox-caption').textContent = currentImage.caption;
    }
    
    document.getElementById('lightbox').addEventListener('click', function(e) {
        if (e.target === this) closeLightbox();
    });
    
    function openGuideline() {
        document.getElementById('guidelineModal').classList.add('active');
        document.body.style.overflow = 'hidden';
    }
    
    function closeGuideline() {
        document.getElementById('guidelineModal').classList.remove('active');
        document.body.style.overflow = '';
    }
    
    document.getElementById('guidelineModal').addEventListener('click', function(e) {
        if (e.target === this) closeGuideline();
    });
    
    // Image Manager Functions
    function openImageManager(projectIndex) {
        if (!isEditMode) return;
        currentManageProjectIndex = projectIndex;
        const projectTitle = document.querySelectorAll('.project-card')[projectIndex]?.querySelector('.project-title')?.textContent || 'Unknown Project';
        document.getElementById('imageManagerProjectTitle').textContent = projectTitle;
        renderImageManagerList();
        document.getElementById('imageManagerModal').classList.add('active');
        document.body.style.overflow = 'hidden';
    }
    
    function closeImageManager() {
        document.getElementById('imageManagerModal').classList.remove('active');
        document.body.style.overflow = '';
    }
    
    function renderImageManagerList() {
        const list = document.getElementById('imageManagerList');
        const images = projectImages[currentManageProjectIndex];
        list.innerHTML = '';
        
        images.forEach((img, idx) => {
            const item = document.createElement('div');
            item.style.cssText = 'display: flex; gap: 16px; align-items: center; padding: 12px; background: #f8f9fa; border-radius: 8px; border: 1px solid #eef0f2;';
            item.innerHTML = `
                <img src="${img.src}" style="width: 80px; height: 60px; object-fit: cover; border-radius: 6px; flex-shrink: 0;" onerror="this.src='data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%2280%22 height=%2260%22><rect fill=%22%23ddd%22 width=%2280%22 height=%2260%22/></svg>'">
                <div style="flex: 1; min-width: 0;">
                    <div style="font-size: 0.75rem; color: #6c757d; margin-bottom: 4px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap;">${img.src}</div>
                    <input type="text" value="${img.caption}" onchange="updateImageCaption(${idx}, this.value)" style="width: 100%; padding: 6px 8px; border: 1px solid #dfe3e6; border-radius: 4px; font-size: 0.85rem; box-sizing: border-box;">
                </div>
                <button class="edit-btn danger" onclick="deleteImage(${idx})" style="flex-shrink: 0;">
                    <i class="bi bi-trash"></i>
                </button>
            `;
            list.appendChild(item);
        });
        
        if (images.length === 0) {
            list.innerHTML = '<div style="text-align: center; color: #6c757d; padding: 24px;">尚無圖片</div>';
        }
        
        updateImageCountDisplay();
    }
    
    function updateImageCaption(idx, value) {
        projectImages[currentManageProjectIndex][idx].caption = value;
    }
    
    function deleteImage(idx) {
        projectImages[currentManageProjectIndex].splice(idx, 1);
        renderImageManagerList();
    }
    
    function uploadNewImage() {
        const url = document.getElementById('newImageUrl').value.trim();
        const caption = document.getElementById('newImageCaption').value.trim();
        if (!url) {
            alert('請輸入圖片 URL');
            return;
        }
        projectImages[currentManageProjectIndex].push({ src: url, caption: caption || 'New Image' });
        document.getElementById('newImageUrl').value = '';
        document.getElementById('newImageCaption').value = '';
        renderImageManagerList();
    }
    
    function saveImageChanges() {
        const card = document.querySelectorAll('.project-card')[currentManageProjectIndex];
        if (card) {
            card.setAttribute('data-images', JSON.stringify(projectImages[currentManageProjectIndex]));
        }
        updateImageCountDisplay();
        closeImageManager();
    }
    
    function updateImageCountDisplay() {
        document.querySelectorAll('.project-card').forEach((card, idx) => {
            const countBadge = card.querySelector('.image-count-mini');
            if (countBadge) {
                countBadge.textContent = projectImages[idx]?.length || 0;
            }
        });
    }
    
    document.getElementById('imageManagerModal').addEventListener('click', function(e) {
        if (e.target === this) closeImageManager();
    });
    
    function toggleEditMode() {
        isEditMode = !isEditMode;
        if (isEditMode) {
            originalECContent = document.getElementById('ec-content').innerHTML;
            originalReportSummary = document.getElementById('reportSummary').textContent;
            originalReportPeriod = document.getElementById('reportPeriod').textContent;
            originalReportScope = document.getElementById('reportScope').textContent;
            document.body.classList.add('edit-mode');
            document.getElementById('editHint').classList.add('show');
            document.getElementById('addProjectBtn').style.display = 'inline-flex';
            enableEditing();
            setTimeout(applyMasonry, 200);
        } else {
            exitEditModeOnly();
        }
    }
    
    function cancelEditing() {
        if (!isEditMode) return;
        document.getElementById('ec-content').innerHTML = originalECContent;
        document.getElementById('reportSummary').textContent = originalReportSummary;
        document.getElementById('reportPeriod').textContent = originalReportPeriod;
        document.getElementById('reportScope').textContent = originalReportScope;
        isEditMode = false;
        document.body.classList.remove('edit-mode');
        document.getElementById('editHint').classList.remove('show');
        document.getElementById('addProjectBtn').style.display = 'none';
        // 重新從 DOM 讀取圖片數據
        const cards = document.querySelectorAll('.project-card');
        projectImages = Array.from(cards).map((card, index) => {
            const data = card.getAttribute('data-images');
            if (data) {
                try { return JSON.parse(data); } catch(e) {}
            }
            return [{ src: `https://picsum.photos/seed/project-${index}/800/600`, caption: 'Project Image' }];
        });
        updateAllImageButtons();
        setTimeout(applyMasonry, 100);
    }
    
    function exitEditModeOnly() {
        if (!isEditMode) return;
        isEditMode = false;
        document.body.classList.remove('edit-mode');
        document.getElementById('editHint').classList.remove('show');
        document.getElementById('addProjectBtn').style.display = 'none';
        disableEditing();
        updateAllImageButtons();
    }
    
    function saveAndDownload() {
        exitEditModeOnly();
        setTimeout(() => {
            downloadHTML();
        }, 300);
    }
    
    function createProgressEditRow(name, pct) {
        const row = document.createElement('div');
        row.className = 'progress-row-edit';
        row.innerHTML = `
            <select class="progress-name-select">
                <option value="SIT">SIT</option>
                <option value="UAT">UAT</option>
                <option value="Pre-Prod">Pre-Prod</option>
            </select>
            <input type="number" class="progress-percent-input" min="0" max="100" value="${pct}">
            <span class="progress-unit">%</span>
            <button type="button" class="edit-btn danger progress-del-btn"><i class="bi bi-trash"></i></button>
        `;
        const select = row.querySelector('.progress-name-select');
        select.value = name;
        row.querySelector('.progress-del-btn').addEventListener('click', () => {
            const container = row.parentElement;
            if (container.querySelectorAll('.progress-row-edit').length <= 1) {
                alert('至少需要保留一條進度條');
                return;
            }
            row.remove();
            applyMasonry();
        });
        return row;
    }
    
    function enterProgressEditing(container) {
        if (container.dataset.editing === 'true') return;
        const pairs = [];
        const kids = Array.from(container.children);
        for (let i = 0; i < kids.length; i++) {
            if (kids[i].classList.contains('progress-label')) {
                const name = kids[i].textContent.trim();
                const bar = kids[i + 1];
                let pct = 0;
                if (bar) {
                    pct = parseInt((bar.style.getPropertyValue('--p') || '0'), 10);
                    if (isNaN(pct)) pct = 0;
                }
                pairs.push([name, pct]);
            }
        }
        container.innerHTML = '';
        container.classList.add('progress-editing');
        container.dataset.editing = 'true';
        pairs.forEach(p => container.appendChild(createProgressEditRow(p[0], p[1])));
    }
    
    function exitProgressEditing(container) {
        if (container.dataset.editing !== 'true') return;
        const rowsData = Array.from(container.querySelectorAll('.progress-row-edit')).map(row => {
            const select = row.querySelector('.progress-name-select');
            const pctInput = row.querySelector('.progress-percent-input');
            let name = select.value;
            let pct = parseInt(pctInput.value, 10);
            if (isNaN(pct)) pct = 0;
            pct = Math.max(0, Math.min(100, pct));
            return { name, pct };
        });
        container.classList.remove('progress-editing');
        container.dataset.editing = 'false';
        container.innerHTML = '';
        rowsData.forEach(r => {
            const label = document.createElement('span');
            label.className = 'progress-label';
            label.textContent = r.name;
            const bar = document.createElement('div');
            bar.className = 'progress-bar-custom';
            bar.style.setProperty('--p', r.pct + '%');
            let fillClass = '';
            let pctClass = '';
            if (r.name === 'UAT') { fillClass = ' fill-uat'; pctClass = ' pc-uat'; }
            else if (r.name === 'Pre-Prod') { fillClass = ' fill-preprod'; pctClass = ' pc-preprod'; }
            bar.innerHTML = `<div class="progress-fill${fillClass}"></div><span class="progress-percent${pctClass}">${r.pct}%</span>`;
            container.appendChild(label);
            container.appendChild(bar);
        });
    }
    
    function makeDescEditable(li, container) {
        li.contentEditable = true;
        li.classList.add('editable-field');
        if (li.querySelector('.desc-del-btn')) return;
        const del = document.createElement('button');
        del.type = 'button';
        del.className = 'desc-del-btn';
        del.setAttribute('contenteditable', 'false');
        del.innerHTML = '<i class="bi bi-x-lg"></i>';
        del.addEventListener('click', function(e) {
            e.preventDefault();
            e.stopPropagation();
            if (container.querySelectorAll('li').length <= 1) {
                alert('至少需要保留一條描述');
                return;
            }
            li.remove();
            applyMasonry();
        });
        li.appendChild(del);
    }
    
    function addTimelineItem(btn) {
        const editControls = btn.closest('.edit-controls');
        const container = editControls.previousElementSibling;
        
        if (!container || !container.hasAttribute('data-timeline-container')) {
            console.error('找不到 timeline container');
            return;
        }
        
        const newItem = document.createElement('li');
        newItem.className = 'timeline-item-edit';
        newItem.innerHTML = `
            <div class="timeline-edit-row">
                <select class="timeline-marker-select">
                    <option value="completed">Completed (綠色)</option>
                    <option value="current" selected>Current (橘色)</option>
                    <option value="pending">Pending (灰色)</option>
                </select>
                <input type="text" class="timeline-date-input" placeholder="時間 (例如: 8/15)">
                <input type="text" class="timeline-title-input" placeholder="里程碑標題">
            </div>
            <div class="timeline-edit-row">
                <input type="text" class="timeline-desc-input" placeholder="描述（選填）" style="flex: 1;">
                <button type="button" class="edit-btn danger timeline-item-del-btn"><i class="bi bi-trash"></i></button>
            </div>
        `;
        
        newItem.querySelector('.timeline-item-del-btn').addEventListener('click', function() {
            const items = container.querySelectorAll('.timeline-item-edit, .timeline-item');
            if (items.length <= 1) {
                alert('至少需要保留一個里程碑');
                return;
            }
            newItem.remove();
            applyMasonry();
        });
        
        container.appendChild(newItem);
        applyMasonry();
    }
    
    function exitTimelineEditing(container) {
        const editItems = container.querySelectorAll('.timeline-item-edit');
        editItems.forEach(item => {
            const markerSelect = item.querySelector('.timeline-marker-select');
            const dateInput = item.querySelector('.timeline-date-input');
            const titleInput = item.querySelector('.timeline-title-input');
            const descInput = item.querySelector('.timeline-desc-input');
            
            const markerState = markerSelect.value;
            const dateText = dateInput.value || 'TBC';
            const titleText = titleInput.value || 'New Milestone';
            const descText = descInput.value || '';
            
            const newLi = document.createElement('li');
            newLi.className = 'timeline-item';
            newLi.setAttribute('data-marker-state', markerState);
            
            const hasLine = true;
            newLi.innerHTML = `
                <div class="timeline-marker">
                    <div class="marker-dot ${markerState}"></div>
                    ${hasLine ? '<div class="marker-line"></div>' : ''}
                </div>
                <div class="timeline-content">
                    <span class="timeline-date-top">${dateText}</span>
                    <div class="timeline-header"><h6 class="timeline-title">${titleText}</h6></div>
                    ${descText ? `<p class="timeline-desc">${descText}</p>` : '<p class="timeline-desc"></p>'}
                </div>
            `;
            
            item.replaceWith(newLi);
        });
    }
    
    function enableEditing() {
        const ecContent = document.getElementById('ec-content');
        const periodField = document.querySelector('#reportPeriod');
        if (periodField) periodField.contentEditable = true;
        
        ecContent.querySelectorAll('.editable-field').forEach(f => f.contentEditable = true);
        
        ecContent.querySelectorAll('.project-card').forEach(card => {
            const badge = card.querySelector('.status-badge');
            const select = card.querySelector('.status-select');
            if (badge && select) {
                const cur = badge.className.split(' ').find(c => c.startsWith('status-'));
                if (cur) select.value = cur.replace('status-', '');
                badge.style.display = 'none';
                select.style.display = 'inline-block';
            }
            const pc = card.querySelector('[data-progress-container="true"]');
            if (pc) enterProgressEditing(pc);
            card.querySelectorAll('[data-desc-container="true"] li, [data-risk-desc-container="true"] li, [data-plan-desc-container="true"] li').forEach(li => {
                makeDescEditable(li, li.parentElement);
            });
            card.querySelectorAll('[data-note-container="true"] li').forEach(li => {
                makeDescEditable(li, li.parentElement);
            });
            
            card.querySelectorAll('.note-group').forEach(group => {
                const tag = group.querySelector('.note-tag');
                if (tag) {
                    const currentTag = tag.textContent.trim();
                    const select = document.createElement('select');
                    select.className = 'note-tag-select';
                    select.innerHTML = `
                        <option value="#Completed" ${currentTag === '#Completed' ? 'selected' : ''}>#Completed</option>
                        <option value="#In progress" ${currentTag === '#In progress' ? 'selected' : ''}>#In progress</option>
                        <option value="#In SIT" ${currentTag === '#In SIT' ? 'selected' : ''}>#In SIT</option>
                        <option value="#Pending" ${currentTag === '#Pending' ? 'selected' : ''}>#Pending</option>
                        <option value="#Other" ${currentTag === '#Other' ? 'selected' : ''}>#Other</option>
                    `;
                    tag.replaceWith(select);
                }
                
                const delBtn = group.querySelector('.note-group-del-btn');
                if (delBtn) {
                    delBtn.style.display = 'inline-flex';
                }
            });
            
            card.querySelectorAll('[data-timeline-container="true"]').forEach(container => {
                const items = container.querySelectorAll('.timeline-item');
                items.forEach(item => {
                    const markerState = item.getAttribute('data-marker-state') || 'pending';
                    const dateText = item.querySelector('.timeline-date-top')?.textContent || '';
                    const titleText = item.querySelector('.timeline-title')?.textContent || '';
                    const descText = item.querySelector('.timeline-desc')?.textContent || '';
                    
                    const editItem = document.createElement('li');
                    editItem.className = 'timeline-item-edit';
                    editItem.innerHTML = `
                        <div class="timeline-edit-row">
                            <select class="timeline-marker-select">
                                <option value="completed" ${markerState === 'completed' ? 'selected' : ''}>Completed (綠色)</option>
                                <option value="current" ${markerState === 'current' ? 'selected' : ''}>Current (橘色)</option>
                                <option value="pending" ${markerState === 'pending' ? 'selected' : ''}>Pending (灰色)</option>
                            </select>
                            <input type="text" class="timeline-date-input" placeholder="時間" value="${dateText}">
                            <input type="text" class="timeline-title-input" placeholder="標題" value="${titleText}">
                        </div>
                        <div class="timeline-edit-row">
                            <input type="text" class="timeline-desc-input" placeholder="描述（選填）" value="${descText}" style="flex: 1;">
                            <button type="button" class="edit-btn danger timeline-item-del-btn"><i class="bi bi-trash"></i></button>
                        </div>
                    `;
                    
                    editItem.querySelector('.timeline-item-del-btn').addEventListener('click', function() {
                        const allItems = container.querySelectorAll('.timeline-item-edit, .timeline-item');
                        if (allItems.length <= 1) {
                            alert('至少需要保留一個里程碑');
                            return;
                        }
                        editItem.remove();
                        applyMasonry();
                    });
                    
                    item.replaceWith(editItem);
                });
            });
        });
        
        setupTitleObserver();
        updateReportSummary();
    }
    
    function disableEditing() {
        document.querySelectorAll('[data-progress-container="true"]').forEach(c => exitProgressEditing(c));
        document.querySelectorAll('[data-timeline-container="true"]').forEach(c => exitTimelineEditing(c));
        
        document.querySelectorAll('.desc-del-btn').forEach(b => b.remove());
        document.querySelectorAll('.note-group-del-btn').forEach(b => b.style.display = 'none');
        document.querySelectorAll('[contenteditable="true"]').forEach(el => el.removeAttribute('contenteditable'));
        document.querySelectorAll('.editable-field').forEach(el => el.classList.remove('editable-field'));
        
        document.querySelectorAll('.note-tag-select').forEach(select => {
            const val = select.value;
            const span = document.createElement('span');
            span.className = 'note-tag';
            span.textContent = val;
            const classMap = {
                '#Completed': 'tag-completed',
                '#In progress': 'tag-inprogress',
                '#In SIT': 'tag-insit',
                '#Pending': 'tag-pending',
                '#Other': 'tag-other'
            };
            span.classList.add(classMap[val] || 'tag-other');
            select.replaceWith(span);
        });
        
        document.querySelectorAll('.status-select').forEach(select => {
            const badge = select.parentElement.querySelector('.status-badge');
            if (badge) {
                const selectedOption = select.querySelector(`option[value="${select.value}"]`);
                if (selectedOption) {
                    badge.className = 'status-badge ' + selectedOption.dataset.class;
                    badge.textContent = selectedOption.textContent;
                }
                select.style.display = 'none';
                badge.style.display = 'inline-flex';
            }
        });
        
        // 重置按鈕文字
        document.querySelectorAll('[data-toggle-type="risk"]').forEach(btn => {
            const cardSection = btn.closest('.card-section');
            const riskCard = cardSection.querySelector('.risk-card');
            if (riskCard && riskCard.style.display === 'none') {
                btn.innerHTML = '<i class="bi bi-eye"></i> 顯示 Risk & Issue';
            } else {
                btn.innerHTML = '<i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue';
            }
        });
        
        document.querySelectorAll('[data-toggle-type="plan"]').forEach(btn => {
            const planSection = btn.closest('.plan-section');
            const title = planSection.querySelector('.card-section-title');
            if (title && title.style.display === 'none') {
                btn.innerHTML = '<i class="bi bi-eye"></i> 顯示預計執行';
            } else {
                btn.innerHTML = '<i class="bi bi-eye-slash"></i> 隱藏預計執行';
            }
        });
        
        setTimeout(() => {
            updateReportSummary();
            applyMasonry();
        }, 100);
    }
    
    function setupTitleObserver() {
        const ecContent = document.getElementById('ec-content');
        const observer = new MutationObserver(() => updateReportSummary());
        ecContent.querySelectorAll('.project-title').forEach(title => {
            observer.observe(title, { childList: true, subtree: true, characterData: true });
        });
    }
    
    function updateReportSummary() {
        const ecContent = document.getElementById('ec-content');
        const titles = [];
        const cards = ecContent.querySelectorAll('.project-card');
        cards.forEach(card => {
            titles.push(card.querySelector('.project-title').textContent.trim());
        });
        const reportSummary = document.getElementById('reportSummary');
        const reportScope = document.getElementById('reportScope');
        if (reportSummary) reportSummary.textContent = titles.join(' · ');
        if (reportScope) reportScope.textContent = `${cards.length} Workstreams`;
    }
    
    function addProjectCard() {
        projectCounter++;
        const projectsList = document.getElementById('projectsList');
        const newCard = document.createElement('div');
        newCard.className = 'project-card';
        newCard.id = `project-${projectCounter}`;
        
        const defaultImages = [{ src: `https://picsum.photos/seed/new-project-${projectCounter}/800/600`, caption: 'New Project Image' }];
        newCard.setAttribute('data-images', JSON.stringify(defaultImages));
        projectImages.push(defaultImages);
        
        newCard.innerHTML = `
            <div class="project-header">
                <div class="project-header-left">
                    <div class="project-title-row">
                        <h3 class="project-title editable-field" data-field="title" contenteditable="true">New Project</h3>
                        <select class="edit-select status-select" data-project="${projectCounter}" style="display: inline-block;">
                            <option value="ontrack" data-class="status-ontrack">On Track</option>
                            <option value="attention" data-class="status-attention">Attention</option>
                            <option value="delayed" data-class="status-delayed">Delayed</option>
                            <option value="wip" data-class="status-wip" selected>In Progress</option>
                            <option value="monitor" data-class="status-monitor">Monitor</option>
                        </select>
                        <span class="status-badge status-wip" style="display: none;">In Progress</span>
                    </div>
                    <div class="project-tags editable-field" data-field="tags" contenteditable="true">Tags · Here</div>
                </div>
                <button class="gallery-btn-mini" onclick="openLightbox(${projectImages.length - 1})">
                    <i class="bi bi-images"></i> 圖片 <span class="image-count-mini">1</span>
                </button>
            </div>
            <div class="card-section gap-16">
                <div class="progress-head">
                    <h4 class="card-section-title">進度</h4>
                    <p class="progress-text editable-field" data-field="progress-text" contenteditable="true">Description here</p>
                </div>
                <div class="progress-layout" data-progress-container="true"></div>
                <div class="edit-controls" data-progress-controls="true">
                    <button class="edit-btn" onclick="addProgressRow(this)"><i class="bi bi-plus-lg"></i> 新增進度條</button>
                </div>
                <ul class="key-points" data-desc-container="true">
                    <li>First description</li>
                </ul>
                <div class="edit-controls" data-desc-controls="true">
                    <button class="edit-btn" onclick="addDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                </div>
            </div>
            <div class="card-section" data-risk-section="true">
                <div class="risk-card">
                    <h5 class="risk-title">Risk &amp; Issue</h5>
                    <ul class="key-points" data-risk-desc-container="true">
                        <li>Risk description here</li>
                    </ul>
                </div>
                <div class="edit-controls" data-risk-controls="true">
                    <button class="edit-btn" data-toggle-type="risk" onclick="toggleRiskSection(this)"><i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue</button>
                    <button class="edit-btn" onclick="addRiskDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                </div>
            </div>
            <div class="card-section plan-section" data-plan-section="true">
                <h4 class="card-section-title">預計執行</h4>
                <ul class="key-points" data-plan-desc-container="true">
                    <li>Plan item</li>
                </ul>
                <div class="edit-controls" data-plan-controls="true">
                    <button class="edit-btn" data-toggle-type="plan" onclick="togglePlanSection(this)"><i class="bi bi-eye-slash"></i> 隱藏預計執行</button>
                    <button class="edit-btn" onclick="addPlanDescRow(this)"><i class="bi bi-plus-lg"></i> 新增描述</button>
                </div>
            </div>
            <div class="note-collapse-wrapper">
                <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                    <h4 class="timeline-collapse-title note-title">專案紀錄</h4>
                    <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                </div>
                <div class="timeline-collapse-body">
                    <div class="note-group">
                        <span class="note-tag tag-completed">#Completed</span>
                        <button type="button" class="edit-btn danger note-group-del-btn" style="display:none; margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
                        <ul class="note-list" data-note-container="true">
                            <li contenteditable="true" class="editable-field">Completed note</li>
                        </ul>
                    </div>
                    <div class="edit-controls" data-note-group-controls="true" style="margin-top: 12px;">
                        <button class="edit-btn" onclick="addNoteGroup(this)"><i class="bi bi-plus-lg"></i> 新增標籤群組</button>
                    </div>
                </div>
            </div>
            <div class="timeline-collapse-wrapper">
                <div class="timeline-collapse-header" onclick="toggleTimeline(this)">
                    <h4 class="timeline-collapse-title">里程碑</h4>
                    <div class="timeline-collapse-toggle"><i class="bi bi-plus-lg"></i></div>
                </div>
                <div class="timeline-collapse-body">
                    <ul class="iq-timeline" data-timeline-container="true">
                        <li class="timeline-item" data-marker-state="current">
                            <div class="timeline-marker"><div class="marker-dot current"></div></div>
                            <div class="timeline-content">
                                <span class="timeline-date-top">TBC</span>
                                <div class="timeline-header"><h6 class="timeline-title">New Milestone</h6></div>
                                <p class="timeline-desc">Description</p>
                            </div>
                        </li>
                    </ul>
                    <div class="edit-controls" data-timeline-controls="true">
                        <button class="edit-btn" onclick="addTimelineItem(this)"><i class="bi bi-plus-lg"></i> 新增里程碑</button>
                    </div>
                </div>
            </div>
            <div class="edit-controls delete-project-controls">
                <button class="edit-btn danger" onclick="deleteProjectCard(this)"><i class="bi bi-trash"></i> 刪除此專案卡片</button>
            </div>
        `;
        projectsList.appendChild(newCard);
        
        const pc = newCard.querySelector('[data-progress-container="true"]');
        enterProgressEditing(pc);
        newCard.querySelectorAll('[data-desc-container="true"] li, [data-plan-desc-container="true"] li, [data-note-container="true"] li').forEach(li => makeDescEditable(li, li.parentElement));
        
        updateReportSummary();
        applyMasonry();
    }
    
    function deleteProjectCard(btn) {
        const card = btn.closest('.project-card');
        const cards = document.getElementById('projectsList').querySelectorAll('.project-card');
        if (cards.length <= 1) {
            alert('至少需要保留一個專案卡片');
            return;
        }
        if (confirm('確定要刪除此專案卡片嗎？')) {
            const index = Array.from(cards).indexOf(card);
            if (index > -1) {
                projectImages.splice(index, 1);
            }
            card.remove();
            updateReportSummary();
            applyMasonry();
        }
    }
    
    function addProgressRow(btn) {
        const container = btn.closest('.card-section').querySelector('[data-progress-container="true"]');
        if (container.dataset.editing !== 'true') enterProgressEditing(container);
        container.appendChild(createProgressEditRow('SIT', 50));
        applyMasonry();
    }
    
    function addDescRow(btn) {
        const container = btn.closest('.card-section').querySelector('[data-desc-container="true"]');
        const li = document.createElement('li');
        li.textContent = 'New description';
        makeDescEditable(li, container);
        container.appendChild(li);
        applyMasonry();
        li.focus();
    }
    
    function addRiskDescRow(btn) {
        const container = btn.closest('[data-risk-section="true"]').querySelector('[data-risk-desc-container="true"]');
        const li = document.createElement('li');
        li.textContent = 'New risk description';
        makeDescEditable(li, container);
        container.appendChild(li);
        applyMasonry();
        li.focus();
    }
    
    function addPlanDescRow(btn) {
        const container = btn.closest('.plan-section').querySelector('[data-plan-desc-container="true"]');
        const li = document.createElement('li');
        li.textContent = 'New plan item';
        makeDescEditable(li, container);
        container.appendChild(li);
        applyMasonry();
        li.focus();
    }
    
    function addNoteRow(btn) {
        const container = btn.closest('.note-group').querySelector('[data-note-container="true"]');
        const li = document.createElement('li');
        li.textContent = 'New note';
        makeDescEditable(li, container);
        container.appendChild(li);
        applyMasonry();
        li.focus();
    }
    
    function deleteNoteGroup(btn) {
        const noteBody = btn.closest('.timeline-collapse-body');
        const groups = noteBody.querySelectorAll('.note-group');
        if (groups.length <= 1) {
            alert('至少需要保留一個標籤群組');
            return;
        }
        const group = btn.closest('.note-group');
        group.remove();
        applyMasonry();
    }
    
    function addNoteGroup(btn) {
        const noteBody = btn.closest('.timeline-collapse-body');
        const controlsDiv = btn.closest('.edit-controls');
        const newGroup = document.createElement('div');
        newGroup.className = 'note-group';
        newGroup.innerHTML = `
            <select class="note-tag-select">
                <option value="#Completed">#Completed</option>
                <option value="#In progress">#In progress</option>
                <option value="#In SIT">#In SIT</option>
                <option value="#Pending">#Pending</option>
                <option value="#Other" selected>#Other</option>
            </select>
            <button type="button" class="edit-btn danger note-group-del-btn" style="margin-left: 8px;" onclick="deleteNoteGroup(this)"><i class="bi bi-trash"></i></button>
            <ul class="note-list" data-note-container="true">
                <li contenteditable="true" class="editable-field">New note<button type="button" class="desc-del-btn" contenteditable="false"><i class="bi bi-x-lg"></i></button></li>
            </ul>
        `;
        noteBody.insertBefore(newGroup, controlsDiv);
        
        const newLi = newGroup.querySelector('li');
        makeDescEditable(newLi, newGroup.querySelector('ul'));
        
        applyMasonry();
    }
    
    function toggleRiskSection(btn) {
        const cardSection = btn.closest('.card-section');
        if (cardSection.classList.contains('hidden-section')) {
            cardSection.classList.remove('hidden-section');
            btn.innerHTML = '<i class="bi bi-eye-slash"></i> 隱藏 Risk & Issue';
        } else {
            cardSection.classList.add('hidden-section');
            btn.innerHTML = '<i class="bi bi-eye"></i> 顯示 Risk & Issue';
        }
        applyMasonry();
    }
    
    function togglePlanSection(btn) {
        const cardSection = btn.closest('.card-section');
        if (cardSection.classList.contains('hidden-section')) {
            cardSection.classList.remove('hidden-section');
            btn.innerHTML = '<i class="bi bi-eye-slash"></i> 隱藏預計執行';
        } else {
            cardSection.classList.add('hidden-section');
            btn.innerHTML = '<i class="bi bi-eye"></i> 顯示預計執行';
        }
        applyMasonry();
    }
    
    function downloadHTML() {
        let htmlContent = document.documentElement.outerHTML;
        // 替換 projectImages 的定義
        const regex = /let projectImages = \[\];[\s\S]*?document\.addEventListener\('DOMContentLoaded', \(\) => \{[\s\S]*?\}\);/;
        const newDefinition = `let projectImages = ${JSON.stringify(projectImages, null, 2)};\n    document.addEventListener('DOMContentLoaded', () => {\n        updateAllImageButtons();\n    });`;
        if (regex.test(htmlContent)) {
            htmlContent = htmlContent.replace(regex, newDefinition);
        }
        
        const blob = new Blob([htmlContent], { type: 'text/html' });
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = 'weekly-executive-report.html';
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
        URL.revokeObjectURL(url);
    }
    
    let masonryTimer = null;
    document.addEventListener('input', function() {
        if (!isEditMode) return;
        clearTimeout(masonryTimer);
        masonryTimer = setTimeout(applyMasonry, 150);
    });
    
    document.addEventListener('keydown', function(e) {
        if (e.key === 'Enter' && e.target.isContentEditable) {
            e.preventDefault();
            e.target.blur();
        }
    });
    
    document.addEventListener('keydown', function(e) {
        if (e.shiftKey && e.ctrlKey && (e.key === 'e' || e.key === 'E')) {
            e.preventDefault();
            toggleEditMode();
            return;
        }
        
        if (e.ctrlKey && e.shiftKey && (e.key === 'd' || e.key === 'D')) {
            e.preventDefault();
            openGuideline();
            return;
        }
        
        if (e.key === 'Escape') {
            if (isEditMode) {
                cancelEditing();
            } else if (document.getElementById('guidelineModal').classList.contains('active')) {
                closeGuideline();
            } else if (document.getElementById('lightbox').classList.contains('active')) {
                closeLightbox();
            } else if (document.getElementById('imageManagerModal').classList.contains('active')) {
                closeImageManager();
            }
        }
        
        if (!document.getElementById('lightbox').classList.contains('active')) return;
        if (e.key === 'ArrowLeft') changeImage(-1);
        else if (e.key === 'ArrowRight') changeImage(1);
    });
    
    function _toggleTimeline(header) {
        const body = header.nextElementSibling;
        const icon = header.querySelector('.timeline-collapse-toggle i');
        
        if (body.classList.contains('show')) {
            body.classList.remove('show');
            icon.className = 'bi bi-plus-lg';
        } else {
            body.classList.add('show');
            icon.className = 'bi bi-dash-lg';
        }
    }
    
    function applyMasonry() {
        const allLists = document.querySelectorAll('.projects-list');
        let container = null;
        
        allLists.forEach(list => {
            if (list.offsetParent !== null) container = list;
        });
        
        if (!container) return;
        
        const cards = Array.from(container.querySelectorAll('.project-card'));
        
        if (window.innerWidth <= 992) {
            container.style.display = 'grid';
            container.style.gridTemplateColumns = '1fr';
            container.style.position = 'static';
            container.style.height = 'auto';
            cards.forEach(card => {
                card.style.position = 'static';
                card.style.width = '100%';
                card.style.left = 'auto';
                card.style.top = 'auto';
            });
            return;
        }
        
        container.style.display = 'block';
        container.style.position = 'relative';
        const gap = 24;
        const colWidth = (container.offsetWidth - gap) / 2;
        const colHeights = [0, 0];
        
        cards.forEach((card) => {
            card.style.position = 'absolute';
            card.style.width = `${colWidth}px`;
            
            const shorterCol = colHeights[0] <= colHeights[1] ? 0 : 1;
            card.style.left = shorterCol === 0 ? 0 : `${colWidth + gap}px`;
            card.style.top = `${colHeights[shorterCol]}px`;
            
            card.offsetHeight;
            colHeights[shorterCol] += card.offsetHeight + gap;
        });
        
        container.style.height = `${Math.max(...colHeights)}px`;
    }
    
    window.toggleTimeline = function(header) {
        _toggleTimeline(header);
        setTimeout(() => {
            applyMasonry();
        }, 350);
    };
    
    window.addEventListener('load', function() {
        window.scrollTo(0, 0);
        applyMasonry();
    });
    
    let resizeTimer;
    window.addEventListener('resize', () => {
        clearTimeout(resizeTimer);
        resizeTimer = setTimeout(applyMasonry, 100);
    });
    
    function switchTab(tab) {
        const ecContent = document.getElementById('ec-content');
        const storeContent = document.getElementById('store-content');
        const decisionContent = document.getElementById('decision-content');
        const backToTop = document.getElementById('backToTop');
        const reportSummary = document.getElementById('reportSummary');
        const reportScope = document.getElementById('reportScope');
        
        window.scrollTo(0, 0);
        
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        document.querySelector(`.tab-btn[data-tab="${tab}"]`).classList.add('active');
        
        ecContent.style.display = (tab === 'ec') ? 'block' : 'none';
        storeContent.style.display = (tab === 'store') ? 'block' : 'none';
        decisionContent.style.display = (tab === 'decision') ? 'block' : 'none';
        
        backToTop.style.display = (tab === 'decision') ? 'none' : 'inline-flex';
        
        if (tab === 'ec') {
            reportSummary.textContent = 'Group Supplier Portal · Group Seller Center · New DS · AIMAS O+O coupon · Oracle PRIME HCM · OMM x Shopee Integration';
            reportScope.textContent = '6 Workstreams';
        } else if (tab === 'store') {
            reportSummary.textContent = 'TW mPOS · Store CEE';
            reportScope.textContent = '2 Workstreams';
        } else {
            reportSummary.textContent = 'Group Supplier Portal · Group Seller Center · New DS · AIMAS O+O coupon · Oracle PRIME HCM · OMM x Shopee Integration · TW mPOS · Store CEE';
            reportScope.textContent = '8 Workstreams';
        }
        
        setTimeout(applyMasonry, 100);
    }
    
    document.querySelectorAll('.tab-btn').forEach(btn => {
        btn.addEventListener('click', function() {
            switchTab(this.dataset.tab);
        });
    });
</script>

</body>
</html>
