# Broski-foundation
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VoiceClass NG — Learning Has No Boundaries</title>
    <!-- Google Fonts: Plus Jakarta Sans & Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        :root {
            --primary-purple: #6C4CF1;
            --primary-purple-hover: #5a3cdb;
            --electric-blue: #3986FF;
            --turquoise: #21D4C2;
            --turquoise-hover: #1bc0b0;
            --pink: #FF6BA8;
            --soft-lavender: #F2EEFF;
            --white: #FFFFFF;
            --dark-navy: #171A35;
            --light-blue: #EAF4FF;
            --gray-bg: #F8FAFC;
            --gray-border: #E2E8F0;
            --text-main: #1E293B;
            --text-muted: #64748B;
            --success: #10B981;
            --danger: #EF4444;
            --warning: #F59E0B;
            --font-main: 'Plus Jakarta Sans', 'Inter', sans-serif;
            --shadow-sm: 0 1px 3px rgba(0,0,0,0.05), 0 1px 2px rgba(0,0,0,0.1);
            --shadow-md: 0 4px 6px -1px rgba(108, 76, 241, 0.08), 0 2px 4px -1px rgba(108, 76, 241, 0.04);
            --shadow-lg: 0 10px 25px -5px rgba(108, 76, 241, 0.15), 0 8px 10px -6px rgba(57, 134, 255, 0.1);
            --radius-sm: 8px;
            --radius-md: 12px;
            --radius-lg: 20px;
            --radius-full: 9999px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-main);
            color: var(--text-main);
            background-color: var(--gray-bg);
            line-height: 1.5;
            overflow-x: hidden;
            -webkit-tap-highlight-color: transparent;
        }

        /* Utility Classes */
        .gradient-text {
            background: linear-gradient(135deg, var(--primary-purple) 0%, var(--electric-blue) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gradient-bg {
            background: linear-gradient(135deg, var(--primary-purple) 0%, var(--electric-blue) 100%);
        }

        .gradient-turquoise {
            background: linear-gradient(135deg, var(--electric-blue) 0%, var(--turquoise) 100%);
        }

        /* App Views Container */
        .view-container {
            display: none;
            min-height: 100vh;
        }
        .view-container.active {
            display: flex;
            flex-direction: column;
        }

        /* Toast Notification */
        #toast-container {
            position: fixed;
            top: 24px;
            right: 24px;
            z-index: 9999;
            display: flex;
            flex-direction: column;
            gap: 12px;
            pointer-events: none;
        }
        .toast {
            background: var(--dark-navy);
            color: var(--white);
            padding: 14px 20px;
            border-radius: var(--radius-md);
            box-shadow: var(--shadow-lg);
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 14px;
            font-weight: 500;
            pointer-events: auto;
            animation: slideIn 0.3s cubic-bezier(0.16, 1, 0.3, 1) forwards;
            max-width: 360px;
            border-left: 4px solid var(--turquoise);
        }
        .toast.error { border-left-color: var(--danger); }
        .toast.success { border-left-color: var(--success); }
        @keyframes slideIn {
            from { opacity: 0; transform: translateY(-20px) scale(0.95); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        /* ================= 1. HOMEPAGE ================= */
        #home-view {
            background: linear-gradient(180deg, #F8F6FF 0%, #FFFFFF 100%);
        }
        nav.navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1280px;
            margin: 0 auto;
            padding: 24px 32px;
            width: 100%;
        }
        .nav-logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-weight: 800;
            font-size: 22px;
            color: var(--dark-navy);
            text-decoration: none;
        }
        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--primary-purple), var(--electric-blue));
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--white);
            box-shadow: var(--shadow-md);
        }
        .nav-actions {
            display: flex;
            gap: 16px;
        }
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            font-family: var(--font-main);
            font-weight: 600;
            font-size: 15px;
            padding: 12px 24px;
            border-radius: var(--radius-full);
            cursor: pointer;
            transition: all 0.2s ease;
            border: none;
            text-decoration: none;
        }
        .btn-primary {
            background: linear-gradient(135deg, var(--primary-purple), var(--electric-blue));
            color: var(--white);
            box-shadow: 0 4px 14px rgba(108, 76, 241, 0.35);
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(108, 76, 241, 0.45);
        }
        .btn-turquoise {
            background: var(--turquoise);
            color: var(--dark-navy);
            box-shadow: 0 4px 14px rgba(33, 212, 194, 0.35);
        }
        .btn-turquoise:hover {
            background: var(--turquoise-hover);
            transform: translateY(-2px);
        }
        .btn-outline {
            background: transparent;
            color: var(--primary-purple);
            border: 2px solid var(--primary-purple);
        }
        .btn-outline:hover {
            background: var(--soft-lavender);
        }
        .btn-white {
            background: var(--white);
            color: var(--dark-navy);
            box-shadow: var(--shadow-sm);
        }
        .btn-white:hover {
            background: var(--gray-bg);
            transform: translateY(-2px);
        }

        .hero-section {
            max-width: 1280px;
            margin: 40px auto 80px;
            padding: 0 32px;
            display: grid;
            grid-template-columns: 1.1fr 0.9fr;
            gap: 48px;
            align-items: center;
        }
        .hero-content h1 {
            font-size: clamp(40px, 5vw, 64px);
            font-weight: 800;
            line-height: 1.1;
            color: var(--dark-navy);
            margin-bottom: 24px;
        }
        .hero-content p {
            font-size: 18px;
            color: var(--text-muted);
            margin-bottom: 36px;
            max-width: 520px;
        }
        .hero-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
        }
        .hero-card-visual {
            background: linear-gradient(135deg, #6C4CF1 0%, #3986FF 100%);
            border-radius: var(--radius-lg);
            padding: 40px;
            color: var(--white);
            box-shadow: var(--shadow-lg);
            position: relative;
            overflow: hidden;
        }
        .hero-card-visual::before {
            content: '';
            position: absolute;
            top: -50px;
            right: -50px;
            width: 200px;
            height: 200px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
        }
        .classroom-mockup {
            background: rgba(23, 26, 53, 0.85);
            backdrop-filter: blur(10px);
            border-radius: var(--radius-md);
            padding: 24px;
            border: 1px solid rgba(255, 255, 255, 0.15);
        }
        .mockup-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        .live-badge {
            background: rgba(16, 185, 129, 0.2);
            color: #34D399;
            padding: 4px 12px;
            border-radius: var(--radius-full);
            font-size: 12px;
            font-weight: 700;
            display: inline-flex;
            align-items: center;
            gap: 6px;
        }
        .live-dot {
            width: 8px;
            height: 8px;
            background: #34D399;
            border-radius: 50%;
            animation: pulseDot 1.5s infinite;
        }
        @keyframes pulseDot {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(52, 211, 153, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 8px rgba(52, 211, 153, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(52, 211, 153, 0); }
        }
        .mockup-avatars {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin-bottom: 20px;
        }
        .mockup-avatar {
            background: rgba(255, 255, 255, 0.08);
            border-radius: var(--radius-md);
            padding: 16px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }
        .avatar-circle {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            margin: 0 auto 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 16px;
            color: var(--white);
        }

        .features-section {
            max-width: 1280px;
            margin: 0 auto 100px;
            padding: 0 32px;
        }
        .section-title {
            text-align: center;
            max-width: 600px;
            margin: 0 auto 60px;
        }
        .section-title h2 {
            font-size: 32px;
            font-weight: 800;
            color: var(--dark-navy);
            margin-bottom: 12px;
        }
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 24px;
        }
        .feature-card {
            background: var(--white);
            padding: 32px 24px;
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--gray-border);
            transition: all 0.3s ease;
        }
        .feature-card:hover {
            transform: translateY(-6px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary-purple);
        }
        .feature-icon {
            width: 56px;
            height: 56px;
            background: var(--soft-lavender);
            color: var(--primary-purple);
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }
        .feature-card h3 {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 8px;
            color: var(--dark-navy);
        }
        .feature-card p {
            font-size: 14px;
            color: var(--text-muted);
        }

        /* ================= 2. TEACHER DASHBOARD ================= */
        #teacher-dashboard-view {
            background: var(--gray-bg);
            flex-direction: row;
        }
        .sidebar {
            width: 280px;
            background: var(--dark-navy);
            color: var(--white);
            padding: 28px 20px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: fixed;
            height: 100vh;
            left: 0;
            top: 0;
            z-index: 100;
        }
        .sidebar-brand {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 20px;
            font-weight: 800;
            color: var(--white);
            margin-bottom: 40px;
            padding-left: 8px;
        }
        .sidebar-nav {
            display: flex;
            flex-direction: column;
            gap: 8px;
            flex: 1;
        }
        .sidebar-link {
            display: flex;
            align-items: center;
            gap: 14px;
            padding: 12px 16px;
            border-radius: var(--radius-md);
            color: #94A3B8;
            text-decoration: none;
            font-weight: 600;
            font-size: 15px;
            transition: all 0.2s ease;
        }
        .sidebar-link:hover, .sidebar-link.active {
            background: rgba(108, 76, 241, 0.2);
            color: var(--white);
        }
        .sidebar-link.active {
            border-left: 4px solid var(--primary-purple);
        }
        .sidebar-footer {
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            padding-top: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .teacher-profile-mini {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .mini-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--primary-purple);
            color: var(--white);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
        }

        .main-content {
            margin-left: 280px;
            flex: 1;
            padding: 36px 40px;
            min-height: 100vh;
        }
        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 32px;
        }
        .welcome-banner {
            background: linear-gradient(135deg, var(--soft-lavender) 0%, var(--light-blue) 100%);
            border-radius: var(--radius-lg);
            padding: 32px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 32px;
            border: 1px solid rgba(108, 76, 241, 0.15);
        }
        .welcome-banner h2 {
            font-size: 24px;
            font-weight: 800;
            color: var(--dark-navy);
            margin-bottom: 8px;
        }
        .welcome-banner p {
            color: var(--text-muted);
            font-size: 15px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }
        .stat-card {
            background: var(--white);
            padding: 24px;
            border-radius: var(--radius-md);
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--gray-border);
            display: flex;
            align-items: center;
            gap: 20px;
        }
        .stat-icon {
            width: 52px;
            height: 52px;
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .stat-info h4 {
            font-size: 13px;
            color: var(--text-muted);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 4px;
        }
        .stat-info .stat-value {
            font-size: 26px;
            font-weight: 800;
            color: var(--dark-navy);
        }

        .classes-section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
        }
        .classes-section-header h3 {
            font-size: 20px;
            font-weight: 800;
            color: var(--dark-navy);
        }
        .classes-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 24px;
        }
        .class-card {
            background: var(--white);
            border-radius: var(--radius-lg);
            padding: 24px;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--gray-border);
            transition: all 0.2s ease;
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }
        .class-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-md);
            border-color: var(--primary-purple);
        }
        .class-top {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 16px;
        }
        .class-badge {
            padding: 4px 10px;
            border-radius: var(--radius-full);
            font-size: 11px;
            font-weight: 700;
            text-transform: uppercase;
        }
        .class-badge.live {
            background: rgba(16, 185, 129, 0.15);
            color: var(--success);
            display: inline-flex;
            align-items: center;
            gap: 6px;
        }
        .class-badge.offline {
            background: var(--gray-border);
            color: var(--text-muted);
        }
        .class-card h4 {
            font-size: 18px;
            font-weight: 700;
            color: var(--dark-navy);
            margin-bottom: 4px;
        }
        .class-subject {
            font-size: 14px;
            color: var(--text-muted);
            margin-bottom: 16px;
            font-weight: 500;
        }
        .class-meta {
            background: var(--gray-bg);
            padding: 12px 16px;
            border-radius: var(--radius-sm);
            display: flex;
            justify-content: space-between;
            font-size: 13px;
            color: var(--text-muted);
            margin-bottom: 20px;
            font-weight: 600;
        }
        .class-actions {
            display: flex;
            gap: 12px;
        }

        /* ================= 3. STUDENT JOIN PAGE ================= */
        #student-join-view {
            background: var(--soft-lavender);
            align-items: center;
            justify-content: center;
            padding: 24px;
        }
        .join-card {
            background: var(--white);
            width: 100%;
            max-width: 440px;
            padding: 40px;
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow-lg);
            position: relative;
            border: 1px solid rgba(108, 76, 241, 0.1);
        }
        .join-header {
            text-align: center;
            margin-bottom: 32px;
        }
        .join-icon-box {
            width: 64px;
            height: 64px;
            background: var(--soft-lavender);
            color: var(--primary-purple);
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
            box-shadow: var(--shadow-sm);
        }
        .join-header h2 {
            font-size: 24px;
            font-weight: 800;
            color: var(--dark-navy);
            margin-bottom: 8px;
        }
        .join-header p {
            color: var(--text-muted);
            font-size: 14px;
        }
        .For connecting and learning 
