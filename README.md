<甯築衛浴>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>衛浴設備諮詢與服務預約</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Calm Harmony (Warm neutrals with teal accents) -->
    <!-- Application Structure Plan: A multi-step, wizard-style interactive form. This structure breaks down the inquiry process into manageable steps (Introduction, Service Selection, Details, Contact, Review), reducing user cognitive load and improving completion rates compared to a single long form. Navigation is handled by 'Next'/'Back' buttons with a progress bar for user orientation. -->
    <!-- Visualization & Content Choices: The source material is a form specification, not a data report. Therefore, the application focuses on interactive data collection, not data visualization. Key choices: Intro -> Goal: Build Trust -> Presentation: Icon-driven cards for key values -> Interaction: Static. Form -> Goal: Guide User & Collect Info -> Presentation: Wizard with progress bar, styled inputs (radios, checkboxes, file upload) -> Interaction: JS-driven step navigation, input validation. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Noto Sans TC', sans-serif;
        }
        .step-transition {
            transition: opacity 0.5s ease-in-out, transform 0.5s ease-in-out;
        }
        .step-hidden {
            opacity: 0;
            transform: translateX(20px);
            display: none;
        }
        .step-visible {
            opacity: 1;
            transform: translateX(0);
            display: block;
        }
        .form-radio:checked {
            background-color: #0d9488;
            border-color: #0d9488;
        }
        .form-checkbox:checked {
            background-color: #0d9488;
            border-color: #0d9488;
        }
        .progress-bar-fill {
            transition: width 0.4s ease-in-out;
        }
    </style>
</head>
<body class="bg-stone-50 text-gray-800">

    <div class="container mx-auto max-w-3xl p-4 sm:p-8">
        
        <header id="main-header" class="text-center mb-8">
            <h1 class="text-3xl sm:text-4xl font-bold text-teal-800 mb-2">衛浴設備諮詢與服務預約</h1>
            <p class="text-gray-600">讓我們為您打造理想的衛浴空間</p>
        </header>

        <main id="app-container" class="bg-white rounded-2xl shadow-lg p-6 sm:p-10">
            
            <!-- Progress Bar -->
            <div id="progress-bar-container" class="mb-8 hidden">
                <div class="w-full bg-gray-200 rounded-full h-2.5">
                    <div id="progress-bar-fill" class="bg-teal-600 h-2.5 rounded-full progress-bar-fill" style="width: 0%;"></div>
                </div>
                <div id="step-counter" class="text-center text-sm text-gray-500 mt-2"></div>
            </div>

            <!-- Step 1: Introduction -->
            <div id="step-1" class="step-visible">
                <div class="text-center">
                    <h2 class="text-2xl font-bold mb-4 text-gray-700">為您提供最完善的衛浴解決方案</h2>
                    <p class="text-gray-600 mb-8">我們深知一個完美的衛浴空間，來自於精準的規劃與專業的施工。請讓我們了解您的需求，開啟您的高品質衛浴體驗。</p>
                    <div class="grid md:grid-cols-2 gap-6 text-left mb-8">
                        <div class="bg-teal-50 border-l-4 border-teal-500 p-6 rounded-lg">
                            <h3 class="font-bold text-xl mb-2 text-teal-800">精準丈量</h3>
                            <p class="text-gray-700">由專業人員到府進行精準測量，確保所有設備完美契合您的空間，避免尺寸不符或安裝困難，節省您的寶貴時間與金錢。</p>
                        </div>
                        <div class="bg-amber-50 border-l-4 border-amber-500 p-6 rounded-lg">
                            <h3 class="font-bold text-xl mb-2 text-amber-800">責任施工</h3>
                            <p class="text-gray-700">從現場規劃、設備安裝到售後服務，我們提供專業且負責的一條龍服務，施工品質有保障，讓您安心無憂。</p>
                        </div>
                    </div>
                    <button onclick="startWizard()" class="w-full sm:w-auto bg-teal-600 text-white font-bold py-3 px-10 rounded-full hover:bg-teal-700 transition-colors shadow-md">開始諮詢</button>
                </div>
            </div>

            <!-- Form Steps Container -->
            <form id="consult-form" class="hidden">
                <!-- Step 2: Service Type -->
                <div id="step-2" class="step-hidden">
                    <h2 class="text-2xl font-bold mb-6 text-center">您的需求類型是？</h2>
                    <div class="space-y-4">
                        <label class="block border border-gray-200 rounded-lg p-4 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                            <input type="radio" name="serviceType" value="新安裝" class="form-radio mr-3 text-teal-600 focus:ring-teal-500">
                            <span class="font-medium">新安裝：</span><span class="text-gray-600">全新衛浴空間規劃與設備安裝</span>
                        </label>
                        <label class="block border border-gray-200 rounded-lg p-4 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                            <input type="radio" name="serviceType" value="舊換新" class="form-radio mr-3 text-teal-600 focus:ring-teal-500">
                            <span class="font-medium">舊換新：</span><span class="text-gray-600">既有衛浴設備汰換與升級</span>
                        </label>
                        <label class="block border border-gray-200 rounded-lg p-4 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                            <input type="radio" name="serviceType" value="設備規劃搭配" class="form-radio mr-3 text-teal-600 focus:ring-teal-500">
                             <span class="font-medium">設備規劃搭配：</span><span class="text-gray-600">僅需衛浴設備採購建議</span>
                        </label>
                        <label class="block border border-gray-200 rounded-lg p-4 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                            <input type="radio" name="serviceType" value="維修/檢測" class="form-radio mr-3 text-teal-600 focus:ring-teal-500">
                             <span class="font-medium">維修/檢測：</span><span class="text-gray-600">衛浴設備故障排除或定期檢查</span>
                        </label>
                    </div>
                    <p id="serviceType-error" class="text-red-500 text-sm mt-2 hidden">請選擇一項需求類型。</p>
                </div>
                
                <!-- Step 3: Space Details -->
                <div id="step-3" class="step-hidden">
                    <h2 class="text-2xl font-bold mb-6 text-center">您的衛浴空間細節</h2>
                    <div class="space-y-6">
                        <div>
                            <label class="font-medium text-gray-700">您希望諮詢的衛浴空間是？</label>
                            <div class="mt-2 space-y-2">
                                <label class="flex items-center">
                                    <input type="checkbox" name="space" value="主衛浴" class="form-checkbox h-5 w-5 text-teal-600 rounded focus:ring-teal-500">
                                    <span class="ml-3 text-gray-700">主衛浴</span>
                                </label>
                                <label class="flex items-center">
                                    <input type="checkbox" name="space" value="客用衛浴" class="form-checkbox h-5 w-5 text-teal-600 rounded focus:ring-teal-500">
                                    <span class="ml-3 text-gray-700">客用衛浴</span>
                                </label>
                                <label class="flex items-center">
                                     <input type="checkbox" name="space" value="其他" class="form-checkbox h-5 w-5 text-teal-600 rounded focus:ring-teal-500" onclick="toggleOtherInput(this, 'spaceOther')">
                                    <span class="ml-3 text-gray-700">其他</span>
                                    <input type="text" id="spaceOther" name="spaceOther" class="ml-2 w-full max-w-xs p-2 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500 hidden" placeholder="請註明">
                                </label>
                            </div>
                             <p id="space-error" class="text-red-500 text-sm mt-2 hidden">請至少選擇一個衛浴空間。</p>
                        </div>
                        <div>
                            <label for="preferences" class="font-medium text-gray-700">您對衛浴設備是否有特定的品牌、風格或功能偏好？ (選填)</label>
                            <textarea id="preferences" name="preferences" rows="4" class="mt-2 w-full p-3 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500" placeholder="例如：偏好日系免治馬桶、簡約風格、需要大容量收納櫃等"></textarea>
                        </div>
                        <div>
                             <label for="fileUpload" class="font-medium text-gray-700">您是否有衛浴空間的尺寸或現場照片可供參考？ (選填)</label>
                             <div class="mt-2 flex justify-center items-center w-full">
                                <label for="fileUpload" class="flex flex-col justify-center items-center w-full h-32 bg-gray-50 rounded-lg border-2 border-gray-300 border-dashed cursor-pointer hover:bg-gray-100">
                                    <div class="flex flex-col justify-center items-center pt-5 pb-6">
                                        <p class="mb-2 text-sm text-gray-500"><span class="font-semibold">點擊此處上傳</span> 或拖曳檔案至此</p>
                                        <p class="text-xs text-gray-500">照片或平面圖</p>
                                    </div>
                                    <input id="fileUpload" name="fileUpload" type="file" class="hidden" onchange="updateFileName(this)">
                                </label>
                            </div>
                            <p id="fileName" class="text-sm text-gray-500 mt-2 text-center"></p>
                        </div>
                    </div>
                </div>

                <!-- Step 4: Contact Info -->
                <div id="step-4" class="step-hidden">
                    <h2 class="text-2xl font-bold mb-6 text-center">如何與您聯繫？</h2>
                    <div class="space-y-4">
                        <div>
                            <label for="name" class="font-medium text-gray-700">您的姓名</label>
                            <input type="text" id="name" name="name" class="mt-1 w-full p-3 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500" required>
                            <p id="name-error" class="text-red-500 text-sm mt-1 hidden">請輸入您的姓名。</p>
                        </div>
                        <div>
                            <label for="phone" class="font-medium text-gray-700">聯絡電話</label>
                            <input type="tel" id="phone" name="phone" class="mt-1 w-full p-3 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500" required>
                             <p id="phone-error" class="text-red-500 text-sm mt-1 hidden">請輸入您的聯絡電話。</p>
                        </div>
                        <div>
                            <label for="email" class="font-medium text-gray-700">電子郵件</label>
                            <input type="email" id="email" name="email" class="mt-1 w-full p-3 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500" required>
                             <p id="email-error" class="text-red-500 text-sm mt-1 hidden">請輸入有效的電子郵件地址。</p>
                        </div>
                        <div>
                            <label class="font-medium text-gray-700">方便聯繫時段</label>
                            <div class="mt-2 grid grid-cols-1 sm:grid-cols-3 gap-2">
                                <label class="flex items-center border border-gray-200 rounded-lg p-3 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                                    <input type="checkbox" name="contactTime" value="上午" class="form-checkbox h-5 w-5 text-teal-600 rounded focus:ring-teal-500">
                                    <span class="ml-2">上午 (9-12時)</span>
                                </label>
                                <label class="flex items-center border border-gray-200 rounded-lg p-3 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                                    <input type="checkbox" name="contactTime" value="下午" class="form-checkbox h-5 w-5 text-teal-600 rounded focus:ring-teal-500">
                                    <span class="ml-2">下午 (13-17時)</span>
                                </label>
                                <label class="flex items-center border border-gray-200 rounded-lg p-3 cursor-pointer hover:bg-gray-50 has-[:checked]:bg-teal-50 has-[:checked]:border-teal-400 transition-all">
                                    <input type="checkbox" name="contactTime" value="晚上" class="form-checkbox h-5 w-5 text-teal-600 rounded focus:ring-teal-500">
                                    <span class="ml-2">晚上 (18-21時)</span>
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Step 5: Final Details -->
                 <div id="step-5" class="step-hidden">
                    <h2 class="text-2xl font-bold mb-6 text-center">預約與備註 (選填)</h2>
                    <div class="space-y-6">
                        <div>
                             <label for="preferredDate" class="font-medium text-gray-700">您希望我們到府丈量或現場諮詢的日期？</label>
                             <input type="date" id="preferredDate" name="preferredDate" class="mt-2 w-full p-3 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500">
                        </div>
                        <div>
                            <label for="notes" class="font-medium text-gray-700">您是否有其他需要特別告知的事項或疑問？</label>
                            <textarea id="notes" name="notes" rows="4" class="mt-2 w-full p-3 border border-gray-300 rounded-md focus:ring-teal-500 focus:border-teal-500" placeholder="例如：施工時間限制、特殊管線配置、預算考量等"></textarea>
                        </div>
                    </div>
                </div>

                <!-- Navigation Buttons -->
                <div id="navigation-buttons" class="mt-10 flex justify-between items-center">
                    <button type="button" id="prevBtn" onclick="navigate(-1)" class="text-gray-600 font-bold py-2 px-4 rounded-full hover:bg-gray-100 transition-colors">上一步</button>
                    <button type="button" id="nextBtn" onclick="navigate(1)" class="bg-teal-600 text-white font-bold py-3 px-10 rounded-full hover:bg-teal-700 transition-colors shadow-md">下一步</button>
                </div>
            </form>

            <!-- Confirmation Message -->
            <div id="confirmation" class="step-hidden text-center py-10">
                 <h2 class="text-2xl font-bold mb-4 text-teal-800">感謝您提交諮詢！</h2>
                 <p class="text-gray-600 mb-6">我們已收到您的需求，將在 2 個工作天內與您聯繫，確認丈量或諮詢細節。</p>
                 <p class="text-gray-600">若有緊急需求，請撥打我們的服務專線：<span class="font-bold text-gray-800">0800-123-456</span></p>
                 <button onclick="resetForm()" class="mt-8 bg-gray-200 text-gray-800 font-bold py-3 px-10 rounded-full hover:bg-gray-300 transition-colors">返回首頁</button>
            </div>

        </main>
    </div>

    <script>
        let currentStep = 1;
        const totalSteps = 5; 
        const formData = {};

        function startWizard() {
            document.getElementById('step-1').classList.add('step-hidden');
            document.getElementById('consult-form').classList.remove('hidden');
            document.getElementById('progress-bar-container').classList.remove('hidden');
            
            currentStep = 2; 
            showStep(currentStep);
        }

        function showStep(step) {
            for (let i = 2; i <= totalSteps + 1; i++) {
                const el = document.getElementById(`step-${i}`);
                if (el) {
                    el.classList.add('step-hidden');
                    el.classList.remove('step-visible');
                }
            }
            const currentEl = document.getElementById(`step-${step}`);
            if(currentEl){
                currentEl.classList.remove('step-hidden');
                currentEl.classList.add('step-visible');
            }
            
            updateProgressBar();
            updateNavigationButtons();
        }

        function updateProgressBar() {
            const progress = ((currentStep - 2) / (totalSteps-1)) * 100;
            document.getElementById('progress-bar-fill').style.width = `${progress}%`;
            document.getElementById('step-counter').innerText = `步驟 ${currentStep - 1} / ${totalSteps}`;
        }

        function updateNavigationButtons() {
            const prevBtn = document.getElementById('prevBtn');
            const nextBtn = document.getElementById('nextBtn');
            
            prevBtn.style.display = currentStep === 2 ? 'none' : 'inline-block';
            nextBtn.innerText = currentStep === totalSteps + 1 ? '提交表單' : '下一步';
        }
        
        function navigate(direction) {
            if (direction === 1 && !validateStep()) {
                return;
            }
            
            saveStepData();

            currentStep += direction;

            if (currentStep > totalSteps + 1) {
                submitForm();
                return;
            }
            
            showStep(currentStep);
        }

        function validateStep() {
            let isValid = true;
            // Clear previous errors
            document.querySelectorAll('[id$="-error"]').forEach(el => el.classList.add('hidden'));

            if (currentStep === 2) {
                const serviceType = document.querySelector('input[name="serviceType"]:checked');
                if (!serviceType) {
                    document.getElementById('serviceType-error').classList.remove('hidden');
                    isValid = false;
                }
            } else if (currentStep === 3) {
                const spaces = document.querySelectorAll('input[name="space"]:checked');
                 if (spaces.length === 0) {
                    document.getElementById('space-error').classList.remove('hidden');
                    isValid = false;
                }
            } else if (currentStep === 4) {
                const name = document.getElementById('name');
                const phone = document.getElementById('phone');
                const email = document.getElementById('email');

                if (name.value.trim() === '') {
                    document.getElementById('name-error').classList.remove('hidden');
                    isValid = false;
                }
                 if (phone.value.trim() === '') {
                    document.getElementById('phone-error').classList.remove('hidden');
                    isValid = false;
                }
                const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
                if (!emailRegex.test(email.value)) {
                    document.getElementById('email-error').innerText = '請輸入有效的電子郵件地址。';
                    document.getElementById('email-error').classList.remove('hidden');
                    isValid = false;
                }
            }

            return isValid;
        }

        function saveStepData() {
            const form = document.getElementById('consult-form');
            const stepData = new FormData(form);
            for (let [key, value] of stepData.entries()) {
                if(formData[key]){
                    if(Array.isArray(formData[key])){
                        if(!formData[key].includes(value)){
                           formData[key].push(value);
                        }
                    } else if (formData[key] !== value) {
                        formData[key] = [formData[key], value];
                    }
                } else {
                    formData[key] = value;
                }
            }
        }
        
        function submitForm() {
            document.getElementById('consult-form').classList.add('hidden');
            document.getElementById('progress-bar-container').classList.add('hidden');
            document.getElementById('confirmation').classList.remove('step-hidden');
            document.getElementById('confirmation').classList.add('step-visible');

            console.log("表單已提交，資料如下：", formData);
        }

        function resetForm() {
            location.reload();
        }

        function toggleOtherInput(checkbox, inputId) {
            document.getElementById(inputId).classList.toggle('hidden', !checkbox.checked);
        }

        function updateFileName(input) {
            const fileName = document.getElementById('fileName');
            if (input.files && input.files.length > 0) {
                fileName.textContent = `已選擇檔案：${input.files[0].name}`;
            } else {
                fileName.textContent = '';
            }
        }

    </script>
</body>
</html>
