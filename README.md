<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5, user-scalable=yes">
    <title>Daily Report · BrightPath</title>
    <!-- Google Font & Font Awesome for icons -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(145deg, #f6f9ff 0%, #e9f0fa 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px 16px 40px;
        }

        /* main card – glassmorphism + vibrant accents */
        .report-card {
            max-width: 880px;
            width: 100%;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(6px);
            -webkit-backdrop-filter: blur(6px);
            border-radius: 48px 48px 40px 40px;
            box-shadow: 0 25px 50px -12px rgba(0, 30, 80, 0.25), 0 4px 18px rgba(0, 71, 171, 0.08);
            padding: 28px 32px 20px;
            border: 1px solid rgba(255, 255, 255, 0.6);
            transition: all 0.2s ease;
        }

        /* ---------- HEADER with logo ---------- */
        .brand-header {
            display: flex;
            align-items: center;
            gap: 14px;
            flex-wrap: wrap;
            margin-bottom: 18px;
            padding-bottom: 16px;
            border-bottom: 2px dashed rgba(0, 71, 171, 0.15);
        }

        .logo-wrapper {
            display: flex;
            align-items: center;
            gap: 14px;
            flex: 1 1 auto;
        }

        /* actual logo image – replace src with your logo */
        .logo-img {
            width: 58px;
            height: 58px;
            object-fit: contain;
            border-radius: 16px;
            background: white;
            box-shadow: 0 6px 14px rgba(0, 71, 171, 0.12);
            padding: 4px;
            border: 1px solid rgba(0, 71, 171, 0.08);
        }

        .brand-text {
            display: flex;
            flex-direction: column;
        }

        .brand-text h1 {
            font-size: 22px;
            font-weight: 800;
            color: #0b1e3a;
            letter-spacing: -0.4px;
            line-height: 1.2;
            background: linear-gradient(135deg, #0b2a5c, #0047AB);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .brand-text span {
            font-size: 13px;
            font-weight: 500;
            color: #4f6a8f;
            letter-spacing: 0.4px;
            -webkit-text-fill-color: #4f6a8f;
        }

        .badge-ceo {
            margin-left: auto;
            background: linear-gradient(135deg, #0047AB, #2a6fd4);
            color: white;
            font-size: 13px;
            font-weight: 600;
            padding: 8px 18px;
            border-radius: 60px;
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 6px 14px rgba(0, 71, 171, 0.25);
            white-space: nowrap;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .badge-ceo i {
            font-size: 15px;
            color: #ffd966;
        }

        /* ---------- TITLE ---------- */
        .form-title {
            margin-bottom: 26px;
        }

        .form-title h2 {
            font-size: 28px;
            font-weight: 800;
            color: #0b1e3a;
            letter-spacing: -0.5px;
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .form-title h2 i {
            background: linear-gradient(145deg, #0047AB, #3b7fd4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-size: 32px;
        }

        .form-title p {
            color: #4f6a8f;
            font-size: 15px;
            margin-top: 4px;
            font-weight: 400;
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }

        .form-title p .pill {
            background: #eef4ff;
            padding: 2px 14px;
            border-radius: 40px;
            font-size: 12px;
            font-weight: 600;
            color: #0047AB;
        }

        /* ---------- GRID / FIELDS ---------- */
        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 18px 24px;
        }

        .full-width {
            grid-column: 1 / -1;
        }

        .field-group {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .field-group label {
            font-size: 14px;
            font-weight: 600;
            color: #1a2b4a;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .field-group label i {
            color: #0047AB;
            font-size: 16px;
            width: 20px;
            text-align: center;
        }

        .field-group label .required-star {
            color: #d14545;
            font-weight: 700;
            margin-left: 2px;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px 16px;
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            border: 1.5px solid #dce3ef;
            border-radius: 18px;
            background: #ffffff;
            transition: 0.2s ease;
            color: #0b1e3a;
            box-shadow: 0 2px 6px rgba(0, 20, 40, 0.02);
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #0047AB;
            box-shadow: 0 0 0 5px rgba(0, 71, 171, 0.12);
            background: #ffffff;
        }

        textarea {
            resize: vertical;
            min-height: 80px;
            border-radius: 20px;
        }

        .field-group .hint {
            font-size: 12px;
            color: #7a8aa5;
            margin-top: 2px;
            padding-left: 4px;
        }

        /* ----- section dividers (colorful) ----- */
        .section-divider {
            grid-column: 1 / -1;
            display: flex;
            align-items: center;
            gap: 12px;
            margin: 8px 0 2px;
        }

        .section-divider span {
            font-weight: 700;
            font-size: 17px;
            color: #0b1e3a;
            letter-spacing: -0.2px;
        }

        .section-divider .line {
            flex: 1;
            height: 3px;
            border-radius: 4px;
            background: linear-gradient(90deg, #0047AB, #8bb3f0, transparent);
        }

        .section-divider i {
            color: #0047AB;
            font-size: 20px;
            background: #e7efff;
            padding: 6px;
            border-radius: 40px;
            width: 34px;
            text-align: center;
        }

        /* ---------- SUBMIT BUTTON (vibrant) ---------- */
        .btn-submit {
            grid-column: 1 / -1;
            margin-top: 18px;
            background: linear-gradient(135deg, #0047AB, #1f65c9);
            color: white;
            border: none;
            padding: 18px 24px;
            border-radius: 60px;
            font-size: 18px;
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 14px;
            cursor: pointer;
            transition: 0.2s ease;
            box-shadow: 0 10px 28px rgba(0, 71, 171, 0.3);
            letter-spacing: 0.3px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .btn-submit i {
            font-size: 22px;
            color: #ffd966;
        }

        .btn-submit:hover {
            transform: translateY(-2px) scale(1.01);
            box-shadow: 0 16px 36px rgba(0, 71, 171, 0.4);
            background: linear-gradient(135deg, #003c92, #1a5dbd);
        }

        .btn-submit:active {
            transform: scale(0.97);
        }

        /* ---------- FOOTER ---------- */
        .footer-note {
            margin-top: 28px;
            text-align: center;
            font-size: 13px;
            color: #5e7290;
            border-top: 1px solid rgba(0, 71, 171, 0.08);
            padding-top: 22px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .footer-note i {
            color: #0047AB;
        }

        .footer-note .dot {
            color: #b3c7e5;
        }

        /* ---------- RESPONSIVE ---------- */
        @media (max-width: 780px) {
            .report-card {
                padding: 22px 18px;
                border-radius: 36px;
            }
            .form-grid {
                grid-template-columns: 1fr 1fr;
                gap: 14px;
            }
            .brand-header {
                flex-direction: row;
                flex-wrap: wrap;
            }
            .badge-ceo {
                margin-left: 0;
                width: auto;
                font-size: 12px;
                padding: 6px 16px;
            }
            .brand-text h1 {
                font-size: 19px;
            }
            .logo-img {
                width: 48px;
                height: 48px;
            }
            .form-title h2 {
                font-size: 24px;
            }
        }

        @media (max-width: 540px) {
            body {
                padding: 12px 10px 30px;
            }
            .report-card {
                padding: 18px 14px;
                border-radius: 28px;
                backdrop-filter: blur(4px);
            }
            .form-grid {
                grid-template-columns: 1fr;
                gap: 14px;
            }
            .brand-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 8px;
            }
            .logo-wrapper {
                width: 100%;
            }
            .badge-ceo {
                margin-left: 0;
                width: 100%;
                justify-content: center;
            }
            .brand-text h1 {
                font-size: 18px;
            }
            .form-title h2 {
                font-size: 22px;
            }
            .form-title h2 i {
                font-size: 26px;
            }
            .btn-submit {
                font-size: 16px;
                padding: 16px 18px;
            }
            .section-divider span {
                font-size: 15px;
            }
            input, select, textarea {
                padding: 11px 14px;
                font-size: 14px;
            }
            .footer-note {
                font-size: 12px;
                flex-direction: column;
                gap: 4px;
            }
        }

        /* small tablet fine-tune */
        @media (min-width: 541px) and (max-width: 780px) {
            .form-grid {
                grid-template-columns: 1fr 1fr;
            }
        }

        /* select arrow custom */
        select {
            appearance: none;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="%235e6f8d" stroke-width="2.5"><polyline points="6 9 12 15 18 9"/></svg>');
            background-repeat: no-repeat;
            background-position: right 16px center;
            background-size: 14px;
        }

        /* extra color accents */
        .field-group select:focus {
            border-color: #0047AB;
        }

        .field-group textarea::placeholder {
            color: #a7b8d0;
            font-weight: 400;
        }

        .field-group input::placeholder {
            color: #a7b8d0;
        }
    </style>
</head>
<body>

<div class="report-card">

    <!-- HEADER with logo image -->
    <div class="brand-header">
        <div class="logo-wrapper">
            <!-- replace "logo.png" with your actual logo file -->
            <img src="logo.png" alt="BrightPath logo" class="logo-img" id="companyLogo">
            <div class="brand-text">
                <h1>Bright Path Innovators</h1>
                <span>Pvt. Ltd. · Empowering futures</span>
            </div>
        </div>
        <div class="badge-ceo">
            <i class="fas fa-crown"></i> CEO report
        </div>
    </div>

    <!-- TITLE -->
    <div class="form-title">
        <h2>
            <i class="fas fa-clipboard-check"></i> Daily work report
        </h2>
        <p>
            <span>Share your daily progress with the CEO</span>
            <span class="pill"><i class="fas fa-asterisk" style="font-size:10px;color:#d14545;"></i> required</span>
        </p>
    </div>

    <!-- FORM -->
    <form id="reportForm">
        <div class="form-grid">

            <!-- Employee Name (dropdown) -->
            <div class="field-group">
                <label><i class="fas fa-user-circle"></i> Employee name <span class="required-star">*</span></label>
                <select id="name" required>
                    <option value="">— select —</option>
                    <option value="MUNESULA VEERESH">MUNESULA VEERESH</option>
                    <option value="HARIKRISHNA GANJI">HARIKRISHNA GANJI</option>
                    <option value="ESHWARAMMA GANJI">ESHWARAMMA GANJI</option>
                    <option value="RAMA CHANDAK">RAMA CHANDAK</option>
                    <option value="MOLUGU RAKSHITHA">MOLUGU RAKSHITHA</option>
                    <option value="RUPA KUMARI">RUPA KUMARI</option>
                    <option value="BANDARI PRANITHA">BANDARI PRANITHA</option>
                    <option value="RAMBATRI SWETHA">RAMBATRI SWETHA</option>
                    <option value="CHEEKOTI NIKHIL">CHEEKOTI NIKHIL</option>
                    <option value="KATAM DEVENDRA REDDY">KATAM DEVENDRA REDDY</option>
                    <option value="TEJAVATH DURGA PRASAD">TEJAVATH DURGA PRASAD</option>
                    <option value="MARKANDEYA GANJI">MARKANDEYA GANJI</option>
                </select>
            </div>

            <!-- Employee ID (dropdown) -->
            <div class="field-group">
                <label><i class="fas fa-id-card"></i> Employee ID <span class="required-star">*</span></label>
                <select id="empId" required>
                    <option value="">— select —</option>
                    <option value="BPI - 002">BPI - 002</option>
                    <option value="BPI - 003">BPI - 003</option>
                    <option value="BPI - 009">BPI - 009</option>
                    <option value="BPI - 006">BPI - 006</option>
                    <option value="BPI - 011">BPI - 011</option>
                    <option value="BPI - 019">BPI - 019</option>
                    <option value="BPI - 021">BPI - 021</option>
                    <option value="BPI - 020">BPI - 020</option>
                    <option value="BPI - 024">BPI - 024</option>
                    <option value="BPI - 023">BPI - 023</option>
                    <option value="BPI - 025">BPI - 025</option>
                </select>
            </div>

            <!-- Date -->
            <div class="field-group">
                <label><i class="fas fa-calendar-alt"></i> Date <span class="required-star">*</span></label>
                <input type="date" id="date" required value="2026-07-04">
            </div>

            <!-- Entry time -->
            <div class="field-group">
                <label><i class="fas fa-clock"></i> Entry time <span class="required-star">*</span></label>
                <input type="time" id="entry" required>
            </div>

            <!-- Exit time -->
            <div class="field-group">
                <label><i class="fas fa-clock"></i> Exit time <span class="required-star">*</span></label>
                <input type="time" id="exit" required>
            </div>

            <!-- ----- WORK DETAILS ----- -->
            <div class="section-divider full-width">
                <i class="fas fa-tasks"></i>
                <span>Work details</span>
                <div class="line"></div>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-check-circle" style="color:#2a7f2a;"></i> Tasks completed today <span class="required-star">*</span></label>
                <textarea id="completed" placeholder="What did you accomplish? (be specific)" required></textarea>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-hourglass-half" style="color:#b37b2e;"></i> Pending tasks (today)</label>
                <textarea id="pendingToday" placeholder="Any tasks left unfinished?"></textarea>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-calendar-plus" style="color:#1f6f8f;"></i> Planned for tomorrow</label>
                <textarea id="pendingTomorrow" placeholder="Your focus areas for next day"></textarea>
            </div>

            <!-- ----- ISSUES ----- -->
            <div class="section-divider full-width">
                <i class="fas fa-exclamation-circle" style="color:#c7433a;"></i>
                <span>Issues & blockers</span>
                <div class="line"></div>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-bug"></i> Issues faced</label>
                <textarea id="issues" placeholder="Describe any challenges or blockers"></textarea>
            </div>

            <div class="field-group">
                <label><i class="fas fa-check-double"></i> Resolved?</label>
                <select id="resolved">
                    <option value="">— select —</option>
                    <option value="Yes">Yes</option>
                    <option value="No">No</option>
                    <option value="In Progress">In Progress</option>
                </select>
            </div>

            <div class="field-group">
                <label><i class="fas fa-flag" style="color:#d97706;"></i> Priority</label>
                <select id="priority">
                    <option value="Low">Low</option>
                    <option value="Medium" selected>Medium</option>
                    <option value="High">High</option>
                    <option value="Critical">Critical</option>
                </select>
            </div>

            <!-- ----- FEEDBACK ----- -->
            <div class="section-divider full-width">
                <i class="fas fa-comment-dots" style="color:#2d6b9b;"></i>
                <span>Feedback & reflections</span>
                <div class="line"></div>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-smile-beam" style="color:#e68a2e;"></i> How was your day?</label>
                <textarea id="experience" placeholder="Share your overall experience"></textarea>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-pen-fancy"></i> Comments</label>
                <textarea id="comments" placeholder="Additional comments for the CEO"></textarea>
            </div>

            <div class="field-group full-width">
                <label><i class="fas fa-lightbulb" style="color:#f5b342;"></i> Suggestions</label>
                <textarea id="suggestions" placeholder="Ideas to improve processes or team"></textarea>
            </div>

            <!-- SUBMIT -->
            <button type="submit" class="btn-submit full-width">
                <i class="fas fa-paper-plane"></i> Send report to CEO
            </button>

        </div><!-- end form-grid -->
    </form>

    <div class="footer-note">
        <span><i class="fas fa-shield-alt"></i> Encrypted · direct to CEO</span>
        <span class="dot">•</span>
        <span><i class="fas fa-mobile-alt"></i> WhatsApp delivery</span>
        <span class="dot">•</span>
        <span>© 2026 BrightPath</span>
    </div>
</div>

<script>
    (function() {
        const form = document.getElementById('reportForm');

        // pre-fill date with today
        const dateInput = document.getElementById('date');
        if (dateInput) {
            const today = new Date().toISOString().split('T')[0];
            dateInput.value = today;
        }

        // If logo image fails, fallback text (optional)
        const logoImg = document.getElementById('companyLogo');
        if (logoImg) {
            logoImg.onerror = function() {
                this.style.display = 'none';
                // optionally show a text fallback
                const wrapper = this.closest('.logo-wrapper');
                if (wrapper) {
                    const fallback = document.createElement('div');
                    fallback.style.cssText = 'width:58px;height:58px;background:#0047AB;border-radius:16px;display:flex;align-items:center;justify-content:center;color:white;font-size:28px;font-weight:700;';
                    fallback.textContent = 'BP';
                    wrapper.prepend(fallback);
                }
            };
        }

        form.addEventListener('submit', function(e) {
            e.preventDefault();

            // gather values
            const name = document.getElementById('name').value;
            const empId = document.getElementById('empId').value;
            const date = document.getElementById('date').value;
            const entry = document.getElementById('entry').value;
            const exit = document.getElementById('exit').value;
            const completed = document.getElementById('completed').value.trim();
            const pendingToday = document.getElementById('pendingToday').value;
            const pendingTomorrow = document.getElementById('pendingTomorrow').value;
            const issues = document.getElementById('issues').value;
            const resolved = document.getElementById('resolved').value;
            const priority = document.getElementById('priority').value;
            const experience = document.getElementById('experience').value;
            const comments = document.getElementById('comments').value;
            const suggestions = document.getElementById('suggestions').value;

            // required validation
            if (!name || !empId || !date || !entry || !exit || !completed) {
                alert('Please fill in all required fields: Name, ID, Date, Entry, Exit, and Completed tasks.');
                return;
            }

            const data = {
                name, empId, date, entry, exit,
                completed, pendingToday, pendingTomorrow,
                issues, resolved, priority,
                experience, comments, suggestions
            };

            // POST to Google Apps Script (no-cors, silent)
            try {
                fetch('https://script.google.com/macros/s/AKfycbyyGXPAmVhWOsk4jt4Uz-uEEnva3UdatwN7t1k9PTZshAcVHJ4WrJgcn1AByaubXePA/exec', {
                    method: 'POST',
                    mode: 'no-cors',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(data)
                });
            } catch (_) {}

            // WhatsApp message
            const message = `📊 *Daily Report – BrightPath*
👤 *Name:* ${name}
🆔 *ID:* ${empId}
📅 *Date:* ${date}

⏰ *Entry:* ${entry}
⏰ *Exit:* ${exit}

✅ *Completed:* ${completed}

⏳ *Pending (today):* ${pendingToday || '—'}

📌 *Planned (tomorrow):* ${pendingTomorrow || '—'}

⚠️ *Issues:* ${issues || '—'}
🔹 *Resolved:* ${resolved || '—'}
🔸 *Priority:* ${priority}

😊 *Experience:* ${experience || '—'}
💬 *Comments:* ${comments || '—'}
💡 *Suggestions:* ${suggestions || '—'}`;

            const phone = '917794947709';
            window.location.href = `https://wa.me/${phone}?text=${encodeURIComponent(message)}`;
        });
    })();
</script>

</body>
</html>
