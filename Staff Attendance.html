<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Society Staff Attendance</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, sans-serif; max-width: 800px; margin: 0 auto; padding: 20px; background: #f4f4f4; }
        .container { background: white; padding: 30px; border-radius: 10px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
        h1 { text-align: center; color: #333; }
        select, input, button { padding: 12px; margin: 10px 5px; border: 1px solid #ddd; border-radius: 5px; font-size: 16px; }
        button { background: #28a745; color: white; cursor: pointer; width: 120px; }
        button:hover { background: #218838; }
        button:disabled { background: #ccc; cursor: not-allowed; }
        #status { padding: 15px; margin: 15px 0; border-radius: 5px; font-weight: bold; }
        .in { background: #d4edda; color: #155724; }
        .out { background: #f8d7da; color: #721c24; }
        #report { margin-top: 20px; }
        table { width: 100%; border-collapse: collapse; margin-top: 10px; }
        th, td { padding: 10px; text-align: left; border-bottom: 1px solid #ddd; }
        th { background: #007bff; color: white; }
        @media (max-width: 600px) { body { padding: 10px; } select, input, button { width: 100%; margin: 5px 0; } }
    </style>
</head>
<body>
    <div class="container">
        <h1>🏢 Society Staff Attendance</h1>
        <div>
            <label>Staff:</label>
            <select id="staffSelect">
                <option value="">Select Staff</option>
                <!-- Edit these for your society staff -->
                <option value="Guard1">Guard - Ram</option>
                <option value="Guard2">Guard - Shyam</option>
                <option value="Maid1">Maid - Sita</option>
                <option value="Maid2">Maid - Geeta</option>
                <option value="Admin">Admin - You</option>
            </select>
            <button id="addStaffBtn">Add Staff</button>
        </div>
        <div>
            <button id="punchBtn">Punch In</button>
            <button id="punchOutBtn" disabled>Punch Out</button>
            <div id="status">Select staff to start</div>
        </div>
        <div>
            <input type="date" id="dateFilter" onchange="filterReport()">
            <button id="reportBtn">Generate Report & Download CSV</button>
        </div>
        <div id="summary"></div>
        <div id="report"></div>
    </div>

    <script>
        const staffSelect = document.getElementById('staffSelect');
        const punchBtn = document.getElementById('punchBtn');
        const punchOutBtn = document.getElementById('punchOutBtn');
        const status = document.getElementById('status');
        const reportDiv = document.getElementById('report');
        const summaryDiv = document.getElementById('summary');
        const dateFilter = document.getElementById('dateFilter');
        const addStaffBtn = document.getElementById('addStaffBtn');
        const reportBtn = document.getElementById('reportBtn');

        let currentStaff = '';
        let attendance = JSON.parse(localStorage.getItem('attendance')) || {};
        let staffList = JSON.parse(localStorage.getItem('staffList')) || ['Guard1: Ram', 'Guard2: Shyam', 'Maid1: Sita', 'Maid2: Geeta', 'Admin: You'];

        // Load staff list
        function loadStaff() {
            staffSelect.innerHTML = '<option value="">Select Staff</option>';
            staffList.forEach(item => {
                const [id, name] = item.split(': ');
                const option = document.createElement('option');
                option.value = id;
                option.textContent = name;
                staffSelect.appendChild(option);
            });
        }
        loadStaff();

        addStaffBtn.onclick = () => {
            const newStaff = prompt('Enter new staff (ID: Name, e.g., Guard3: Mohan)');
            if (newStaff) {
                staffList.push(newStaff);
                localStorage.setItem('staffList', JSON.stringify(staffList));
                loadStaff();
            }
        };

        staffSelect.onchange = () => {
            currentStaff = staffSelect.value;
            if (currentStaff) {
                updateStatus();
            }
        };

        function updateStatus() {
            if (!currentStaff) return;
            const records = attendance[currentStaff] || [];
            const today = new Date().toISOString().split('T')[0];
            const todayRecords = records.filter(r => r.date === today);
            const punchedInToday = todayRecords.some(r => r.action === 'in');
            const punchedOutToday = todayRecords.some(r => r.action === 'out');

            punchBtn.disabled = punchedOutToday;
            punchOutBtn.disabled = !punchedInToday || punchedOutToday;
            status.textContent = `Today: ${punchedInToday ? (punchedOutToday ? 'Punched Out' : 'Punched In') : 'Not Punched'}`;
            status.className = punchedOutToday ? 'out' : punchedInToday ? 'in' : '';
            showSummary();
        }

        punchBtn.onclick = punchIn;
        function punchIn() {
            if (!currentStaff) return;
            addRecord('in');
            updateStatus();
        }

        punchOutBtn.onclick = () => {
            if (!currentStaff) return;
            addRecord('out');
            updateStatus();
        };

        function addRecord(action) {
            let records = attendance[currentStaff] || [];
            const today = new Date().toISOString().split('T')[0];
            // Prevent duplicate same day
            const todayRecords = records.filter(r => r.date === today);
            if (todayRecords.some(r => r.action === action)) {
                alert(`Already ${action} today!`);
                return;
            }
            records.push({action, time: new Date().toLocaleString('en-IN', {timeZone: 'Asia/Kolkata'}), date: today});
            attendance[currentStaff] = records;
            localStorage.setItem('attendance', JSON.stringify(attendance));
        }

        function showSummary() {
            if (!currentStaff) return;
            const records = attendance[currentStaff] || [];
            const totalDays = new Set(records.map(r => r.date)).size;
            summaryDiv.innerHTML = `<strong>Summary for ${staffSelect.selectedOptions[0]?.text}: ${records.length} punches over ${totalDays} days</strong>`;
        }

        function filterReport() {
            // Filtered view logic here if needed
            generateReport();
        }

        reportBtn.onclick = generateReport;
        function generateReport() {
            if (!currentStaff) return;
            let records = attendance[currentStaff] || [];
            const filterDate = dateFilter.value;
            if (filterDate) {
                records = records.filter(r => r.date === filterDate);
            }
            let tableHtml = '<table><tr><th>Date</th><th>Time</th><th>Action</th></tr>';
            let csv = 'Date,Time,Action
';
            records.forEach(r => {
                tableHtml += `<tr><td>${r.date}</td><td>${r.time}</td><td>${r.action.toUpperCase()}</td></tr>`;
                csv += `${r.date},${r.time},${r.action}
`;
            });
            tableHtml += '</table>';
            reportDiv.innerHTML = tableHtml + `<br><a href="data:text/csv;charset=utf-8,${encodeURIComponent(csv)}" download="attendance_${currentStaff}_${filterDate || 'all'}.csv" class="download-btn">📥 Download CSV</a>`;
        }

        // Initial load
        dateFilter.value = new Date().toISOString().split('T')[0];
        showSummary();
    </script>
</body>
</html>
