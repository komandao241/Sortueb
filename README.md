#sortueb
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تسجيل حساب جديد</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 50px;
        }
        .form-container {
            max-width: 400px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #007BFF;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h1>تسجيل حساب جديد</h1>
        <form id="registerForm">
            <input type="text" id="name" placeholder="الاسم" required>
            <input type="email" id="email" placeholder="البريد الإلكتروني" required>
            <input type="password" id="password" placeholder="كلمة المرور" required>
            <select id="userType" required>
                <option value="">اختر نوع الحساب</option>
                <option value="doctor">طبيب</option>
                <option value="patient">مريض</option>
            </select>
            <div id="doctorFields" style="display: none;">
                <input type="text" id="licenseNumber" placeholder="رقم الرخصة">
                <input type="text" id="certificates" placeholder="الشهادات">
                <input type="number" id="price" placeholder="سعر الخدمة">
            </div>
            <div id="patientFields" style="display: none;">
                <input type="text" id="nationalId" placeholder="رقم البطاقة أو الباسبور">
            </div>
            <button type="submit">تسجيل الحساب</button>
        </form>
        <p>لديك حساب بالفعل؟ <a href="login.html">تسجيل الدخول</a></p>
    </div>

    <script>
        const userType = document.getElementById('userType');
        const doctorFields = document.getElementById('doctorFields');
        const patientFields = document.getElementById('patientFields');

        userType.addEventListener('change', function() {
            if (userType.value === 'doctor') {
                doctorFields.style.display = 'block';
                patientFields.style.display = 'none';
            } else if (userType.value === 'patient') {
                patientFields.style.display = 'block';
                doctorFields.style.display = 'none';
            } else {
                doctorFields.style.display = 'none';
                patientFields.style.display = 'none';
            }
        });

        document.getElementById('registerForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            const type = userType.value;

            if (type === 'doctor') {
                const licenseNumber = document.getElementById('licenseNumber').value;
                const certificates = document.getElementById('certificates').value;
                const price = document.getElementById('price').value;
                alert(`تم تسجيل الدكتور: ${name}\nالبريد: ${email}\nرقم الرخصة: ${licenseNumber}\nالسعر: ${price}`);
            } else if (type === 'patient') {
                const nationalId = document.getElementById('nationalId').value;
                alert(`تم تسجيل المريض: ${name}\nالبريد: ${email}\nرقم البطاقة: ${nationalId}`);
            }
        });
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تسجيل الدخول</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 50px;
        }
        .form-container {
            max-width: 400px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #007BFF;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h1>تسجيل الدخول</h1>
        <form id="loginForm">
            <input type="email" id="email" placeholder="البريد الإلكتروني" required>
            <input type="password" id="password" placeholder="كلمة المرور" required>
            <button type="submit">تسجيل الدخول</button>
        </form>
        <p>ليس لديك حساب؟ <a href="index.html">أنشئ حسابًا جديدًا</a></p>
    </div>

    <script>
        document.getElementById('loginForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;

            // فتح صفحة جديدة لعرض معلومات الأطباء
            window.open('doctors.html', '_blank');
        });
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معلومات الأطباء</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 50px;
        }
        .doctor-card {
            background: #fff;
            padding: 20px;
            margin: 20px auto;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
        }
    </style>
</head>
<body>
    <h1>قائمة الأطباء</h1>
    <div class="doctor-card">
        <h2>الدكتور أحمد</h2>
        <p>التخصص: طب عام</p>
        <p>سعر الكشف: 200 جنيه</p>
    </div>
    <div class="doctor-card">
        <h2>الدكتورة سارة</h2>
        <p>التخصص: أسنان</p>
        <p>سعر الكشف: 300 جنيه</p>
    </div>
</body>
</html>
