javascript:(function() {
    /* === [ 1. НАСТРОЙКИ ДЛЯ ЗАПОЛНЕНИЯ ] === */
    let GLOBAL_PHONE = "9136210498"; /* БЕЗ 7!!!!!! */
    let GLOBAL_TELEGRAM = "@SharovaKRD";
    let SHOW_WA = true;
    let SHOW_TG = true;
 
    /* ШАНСЫ ВЫПАДЕНИЯ ГРУПП (1.0 = всегда, 0.0 = никогда) */
    let CHANCE_GROUP_1 = 0.3;
    let CHANCE_GROUP_2 = 0.3;
    /* Короткие фразы для анонса */
    const GLOBAL_MIN_DESCRIPTIONS = [
        "Улыбка с секретом… хочешь узнать каким? 😉✨.",
        "Чуть дерзкая, но очень милая — рискнёшь? 💋🔥.",
        "В моих глазах прячется маленькое чудо ✨👀.",
        "Лёгкая загадка с ароматом нежности 🌸😉.",
        "Ты ещё не знаешь, но я уже нравлюсь 😌💫.",
        "Играю взглядом и немного твоим вниманием 😉🔥.",
        "Сегодня я — твоя самая приятная случайность 💖✨.",
        "Давай добавим искру в этот вечер ✨😌.",
        "Я умею удивлять — проверим? 😏✨.",
        "В этом взгляде спрятано больше, чем кажется 👀💖.",
        "Настроение: флирт и немного магии 😉✨.",
        "Секунда со мной — и день уже не такой обычный 😉✨.",
        "Смотри осторожно… могу остаться в мыслях 😌💖.",
        "Настроение: нравиться и немного дразнить 😏🔥.",
        "Чуть тепла и капля безумия для тебя 😉🔥.",
        "Я умею превращать «просто день» в «вау» 😏💖.",
        "Я как музыка — хочется включить ещё 😌🎶.",
        "Улыбка, которая цепляет надолго 😉💫.",
        "Взгляд, в котором легко потеряться 😏👀.",
        "Время со мной летит быстрее 😏💫.",
        "Просто улыбнись… и всё станет интереснее 😉🌟.",
        "Я как кофе — сначала горько, потом любовь ☕💘.",
        "Немного магии, немного меня — идеально ✨😉.",
        "Моя улыбка умеет творить чудеса 😏💖.",
        "Осторожно, вызываю лёгкую зависимость 😌🔥.",
        "Хочешь настроение лучше? Я рядом 😉✨.",
        "Я — причина твоей улыбки сегодня 😏💫.",
        "Нежность с характером — редкое сочетание 💋🌸.",
        "Твоя новая привычка начинается здесь 😉🔥."
    ];
    /* Полные описания */
    const GLOBAL_DESCRIPTIONS = [
        "Готов ли ты позволить себе чуть больше, чем обычно? 😏 Со мной всё начинается с улыбки и заканчивается желанием повторить. Я не обещаю спокойствия — только эмоции. Сделай первый шаг, я уже жду 🔥 ",
        "Иногда стоит рискнуть ради правильного настроения… ✨ Я умею быть разной: мягкой, дерзкой, загадочной. Всё зависит от тебя. Хочешь проверить? Напиши — и начнём эту игру 💋",
       "Ты уверен, что сможешь меня забыть после знакомства? 😉 Я бы не рассчитывала. Лучше проверь сам — напиши мне 💌",
       "Хочешь узнать, как я умею сводить мужчин с ума одним только голосом? 🔥 Представь, как я шепчу тебе все свои самые пошлые желания… медленно, жарко, дерзко. Я буду твоей тайной страстью, которая не знает слова «нет». Буду ласкать тебя так, что тело будет гореть, а разум — плавиться.Не выдержишь? Отлично. Пиши мне сейчас — и давай воплотим всё, о чём ты стесняешься мечтать! 😈💋",
       "😉 Я люблю быть твоей самой смелой фантазией. Буду нежной, страстной, дерзкой — какой захочешь. Главное, чтобы тебе было так хорошо, что ты не захочешь меня отпускать.Хватит фантазировать в одиночку. Пиши мне прямо сейчас и забери меня! 💦😏",
       "Хочешь, чтобы я рассказала тебе, что сделаю с тобой, когда мы останемся наедине? 😈 Мои губы, мой голос, мои движения — всё будет только для твоего удовольствия. Я умею любить так горячо, что воздух вокруг закипает. Буду твоей личной искрой, которая разожжёт настоящий пожар.Не медли. Пиши мне СЕЙЧАС — и давай устроим взрыв! 🔥💋",
       "Что если я скажу, что готова выполнить любое твоё желание… и даже то, о котором ты стесняешься сказать? 🔥 Я — та, кто умеет читать мысли и исполнять их в сто раз жарче. Буду нежной и дерзкой, сладкой и очень-очень мокрой.Не думай. Пиши мне сейчас — и начнём нашу горячую историю! 💋Напиши мне в ТГ",
       "Готов ли ты к тому, что я сделаю тебя зависимым от моих ласк? 🔥 Я умею любить так, что ты будешь возвращаться ко мне снова и снова. Пиши мне СЕЙЧАС, и мы начнём самую горячую игру! 💋",
       "Хочешь узнать, как я умею превращать обычный вечер в самую горячую ночь в твоей жизни? 🔥 Я — твоя личная искра. Пиши мне прямо сейчас и давай зажжём! 💦😏",
        "Что если я скажу, что хочу почувствовать тебя всем своим телом, каждой клеточкой? 🔥 Хочу, чтобы ты взял меня так, как давно мечтал. Я буду твоей самой послушной и самой дерзкой одновременно.Пиши сейчас — давай сделаем это реальностью! 😏💋",
        "Ты правда думаешь, что готов к встрече со мной? 😉 Я — удовольствие, которое не спешит раскрываться сразу. Со мной время теряет значение, а желания становятся громче. Напиши, если хочешь испытать нечто по-настоящему особенное 💌",
        "Скучаешь по эмоциям, которые сложно забыть? ✨ Я умею создавать моменты, о которых думают снова и снова. Лёгкий флирт, искренний интерес и немного магии между нами… рискнёшь? Напиши мне сейчас 💋"
    ];
    /* Имена */
    const NAMES = [
        "Саша", "Анастасия", "София", "Виктория", "Елизавета", "Милана", "Арина", "Кристина", "Полина", "Валерия", "Алиса", "Мария", "Дарья", "Екатерина", "Ольга", "Анна", "Вероника", "Юлия", "Алина", "Ксения", "Светлана", "Надежда", "Любовь", "Ирина", "Татьяна", "Евгения", "Маргарита", "Наталья", "Ярослава", "Мирослава", "Злата", "Лилия", "Розалия", "Снежана", "Диана", "Камилла", "Эмилия", "Сабрина", "Василиса", "Агата", "Белла", "Аврора", "Серафима", "Анжелика", "Влада", "Милослава", "Эвелина", "Лидия", "Вера", "Агния", "Селена", "Луна", "Ариадна", "Фиона", "Жасмин", "Изабелла", "Шарлотта", "Оливия", "Эмма", "Ава", "Мия", "Амелия", "Харпер", "Ева", "Скарлетт", "Грейс", "Хлоя", "Зоя", "Ника", "Лия", "Мира", "Элеонора", "Клара", "Сильвия", "Джульетта", "Авелина", "Мелания", "Рафаэлла", "Аделина", "Вивьен", "Моника", "Лаура", "Алессия", "Селестия", "Аурелия", "Флора", "Иветта", "Жаклин", "Матильда", "Кассандра", "Афина", "Эсмеральда", "Сапфира", "Руби", "Лаванда", "Аметист", "Селеста", "Валентина", "Александра",  "Серафима", "Софья", "Ульяна", "Кристина", "Эвелина", "Эмилия", "Юлиана", "Яна", "Аделина", "Азалия", "Амалия", "Анфиса", "Афродита", "Жанна", "Калерия", "Карина", "Мелания", "Аня", "Вика", "Ева", "Катя", "Маша", "Полина", "Юля", "Лера "
    ];
    /* === [ 2. ТЕХНИЧЕСКИЙ БЛОК ] === */
    const BASE_SERVICES = ["service1", "service7", "service8", "service9", "service11", "service14", "service18", "service19", "service20", "service35", "service52"];
    const SERVICE_DATA = {
        "секс": [{id: "service2", price: "5000"}, {id: "service4", price: "5000"}, {id: "service5", price: "5000"}, {id: "service6", price: "5000"}, {id: "service7", price: ""}],
        "ласки_клиенту": [{id: "service10", price: "3000"}, {id: "service11", price: ""}, {id: "service12", price: "5000"}, {id: "service13", price: "5000"}, {id: "service56", price: "3000"}],
        "ласки_путане": [{id: "service15", price: "5000"}, {id: "service16", price: "5000"}, {id: "service17", price: "5000"}],
        "окончание": [{id: "service18", price: "5000"}],
        "bdsm": [{id: "service21", price: "5000"}, {id: "service22", price: "5000"}, {id: "service23", price: "5000"}, {id: "service24", price: "5000"}, {id: "service25", price: "5000"}, {id: "service26", price: "5000"}, {id: "service27", price: "5000"}, {id: "service28", price: "5000"}, {id: "service29", price: "5000"}, {id: "service55", price: "5000"}, {id: "service30", price: "5000"}, {id: "service31", price: "5000"}, {id: "service34", price: "5000"}],
        "массаж": [{id: "service36", price: ""}, {id: "service37", price: ""}, {id: "service38", price: "0"}, {id: "service39", price: "5000"}, {id: "service40", price: "5000"}],
        "шоу": [{id: "service41", price: "5000"}, {id: "service42", price: ""}, {id: "service43", price: "3000"}, {id: "service44", price: "3000"}, {id: "service45", price: "5000"}],
        "вирт": [{id: "service46", price: "3000"}, {id: "service47", price: "3000"}, {id: "service48", price: "5000"}, {id: "service49", price: "1000"}],
        "позвать": [{id: "service50", price: "5000"}],
        "дополнительно": [{id: "service53", price: "10000"}, {id: "service54", price: "5000"}]
    };
    function getNextUnique(key, array) {
        if (!array || array.length === 0) return "";
        let currentArrayStr = JSON.stringify(array);
        let savedArrayStr = localStorage.getItem('eva_array_' + key);
        let indices = [];
        if (savedArrayStr !== currentArrayStr) {
            indices = Array.from(array.keys()).sort(() => Math.random() - 0.5);
            localStorage.setItem('eva_array_' + key, currentArrayStr);
            localStorage.setItem('eva_indices_' + key, JSON.stringify(indices));
        } else {
            try { indices = JSON.parse(localStorage.getItem('eva_indices_' + key) || "[]"); } catch(e) { indices = []; }
        }
     
        if (indices.length === 0) {
            indices = Array.from(array.keys()).sort(() => Math.random() - 0.5);
            localStorage.setItem('eva_array_' + key, currentArrayStr);
            localStorage.setItem('eva_indices_' + key, JSON.stringify(indices));
        }
     
        const nextIdx = indices.pop();
        localStorage.setItem('eva_indices_' + key, JSON.stringify(indices));
        return array[nextIdx] || "";
    }
    function fillField(selector, v) {
        const el = document.querySelector(selector);
        if (el) {
            if (el.focus) el.focus();
            el.value = v;
            el.dispatchEvent(new Event('input', { bubbles: true }));
            el.dispatchEvent(new Event('keyup', { bubbles: true }));
            el.dispatchEvent(new Event('change', { bubbles: true }));
            if (el.blur) el.blur();
            if (typeof window.jQuery !== 'undefined') {
                window.jQuery(el).trigger('input').trigger('change');
            }
        }
    }
    function syncDescription(fullText, showWA, showTG, tgUser, isMin = false) {
        if (!fullText) return "";
        let cleanText = fullText.replace(/@[\w\d_]+/g, "").replace(/\s+/g, " ").trim().replace(/[.!?, ]+$/g, "");
        if (isMin) return cleanText;
        if (!tgUser || tgUser === "@Ваша собачка") return cleanText;
        return cleanText + " Мой телеграм: " + tgUser;
    }
    function getPhotoPrice() {
        const prices = [10000,11000,12000,13000,14000,15000,16000,17000,18000,19000,20000];
        const boosted = new Set([14000,15000,16000]);
        const weights = prices.map(p => boosted.has(p) ? 1.3 : 1.0);
        const total = weights.reduce((a,b) => a+b, 0);
        let r = Math.random() * total;
        for (let i = 0; i < prices.length; i++) { r -= weights[i]; if (r <= 0) return String(prices[i]); }
        return '14000';
    }
    function applyAdvancedServices(isCreation = false) {
        if (!isCreation) return;
     
        document.querySelectorAll('.prof_form_service input[type="checkbox"]').forEach(c => {
            if (c.checked) {
                c.click();
            }
        });
        let finalIDs = new Set(BASE_SERVICES);
        const limits = { "ласки_путане": 3, "массаж": 4, "шоу": 2, "вирт": 2, "позвать": 1 };
        const currentCatCount = {};
        const always4142 = Math.random() < 0.5 ? "service41" : "service42";
        finalIDs.add(always4142);
        const blockedIDs = new Set(["service51", "service32", "service33", (always4142 === "service41" ? "service42" : "service41")]);
        const isLucky1 = Math.random() < CHANCE_GROUP_1;
        const group1 = ["service2", "service26", "service16", "service13"];
     
        const isLucky2 = Math.random() < CHANCE_GROUP_2;
        const group2 = ["service4", "service5", "service39", "service50"];
        const links = {
            "service2": ["service26", "service16", "service13"], "service26": ["service2", "service16", "service13"],
            "service16": ["service2", "service26", "service13"], "service13": ["service2", "service26", "service16"],
            "service4": ["service5", "service39", "service50"], "service5": ["service4", "service39", "service50"],
            "service39": ["service4", "service5", "service50"], "service50": ["service4", "service5", "service39"],
            "service22": ["service6", "service21", "service24", "service29"],
            "service3": ["service47", "service48", "service53"],
            "service28": ["service29", "service27", "service23", "service12"]
        };
        const tryAdd = (item) => {
            if (group1.includes(item.id) && !isLucky1) return false;
            if (group2.includes(item.id) && !isLucky2) return false;
            if (finalIDs.size >= 30 || finalIDs.has(item.id)) return false;
            let limit = limits[item.cat] || 99;
            currentCatCount[item.cat] = currentCatCount[item.cat] || 0;
            if (currentCatCount[item.cat] < limit) { finalIDs.add(item.id); currentCatCount[item.cat]++; return true; }
            return false;
        };
        if (isLucky1) group1.forEach(id => { let item = Object.values(SERVICE_DATA).flat().find(i => i.id === id); if (item) tryAdd({...item, cat: "спец"}); });
        if (isLucky2) group2.forEach(id => { let item = Object.values(SERVICE_DATA).flat().find(i => i.id === id); if (item) tryAdd({...item, cat: "спец"}); });
        const triggerIDs = Object.keys(links).sort(() => Math.random() - 0.5);
        const selectedTriggers = triggerIDs.slice(0, 2);
        const allItemsFlat = [];
        Object.keys(SERVICE_DATA).forEach(cat => {
            SERVICE_DATA[cat].forEach(item => {
                if(!finalIDs.has(item.id) && !blockedIDs.has(item.id)) allItemsFlat.push({...item, cat});
            });
        });
        selectedTriggers.forEach(tId => {
            const triggerItem = allItemsFlat.find(i => i.id === tId);
            if (triggerItem && tryAdd(triggerItem)) {
                links[tId].forEach(reqId => { let reqItem = allItemsFlat.find(i => i.id === reqId); if (reqItem) tryAdd(reqItem); });
            }
        });
        allItemsFlat.sort(() => Math.random() - 0.5).forEach(item => { if (finalIDs.size < 30) tryAdd(item); });
        finalIDs.forEach(id => {
            const cb = document.getElementById(id);
            if (cb) {
                if (!cb.checked) {
                    cb.click();
                }
                let priceValue = "";
                Object.values(SERVICE_DATA).forEach(cat => { let f = cat.find(i => i.id === id); if(f) priceValue = f.price; });
                if (id === 'service53') priceValue = getPhotoPrice();
                if (priceValue) {
                    setTimeout(() => {
                        const pInp = document.querySelector(`input[name="Item[service_price][${cb.value}]"]`);
                        if (pInp) {
                            pInp.disabled = false;
                            pInp.readOnly = false;
                            let parentDiv = pInp.parentElement;
                            if (parentDiv) {
                                parentDiv.style.display = 'block';
                                parentDiv.classList.remove('hidden', 'hide', 'd-none');
                                if (parentDiv.parentElement) {
                                    parentDiv.parentElement.style.display = 'block';
                                    parentDiv.parentElement.classList.remove('hidden', 'hide', 'd-none');
                                }
                            }
                            fillField(`input[name="Item[service_price][${cb.value}]"]`, priceValue);
                        }
                    }, 250);
                }
            }
        });
    }
    function parseData(text) {
        const res = { age: '', height: '', weight: '', boobs: '', hair: '' };
        const lines = text.split('\n');
     
        lines.forEach(line => {
            const l = line.toLowerCase().trim();
            const getDigits = (str) => str.replace(/[^0-9]/g, '').trim();
         
            if (!res.age && /(age|возраст)/i.test(l)) { const d = getDigits(l).match(/(\d{2})/); if(d) res.age = d[1]; }
            if (!res.height && /(height|рост)/i.test(l)) { const d = getDigits(l).match(/(\d{3})/); if(d) res.height = d[1]; }
            if (!res.weight && /(weight|вес)/i.test(l)) { const d = getDigits(l).match(/(\d{2})/); if(d) res.weight = d[1]; }
         
            if (!res.boobs && /(груд|chest|bust|boobs|cup|чашк)/i.test(l)) {
                let m = l.match(/(?:\d{2}\s*|(?:cup|чашк[аи]|размер|size|chest|bust|boobs|груд[ьзи])\s*[-:]?\s*)([a-fавсдеф])(?:$|[\s,.])/i);
                if (m) {
                    let char = m[1].toLowerCase();
                    if (char === 'a' || char === 'а') res.boobs = '1';
                    else if (char === 'b' || char === 'в') res.boobs = '2';
                    else if (char === 'c' || char === 'с') res.boobs = '3';
                    else if (char === 'd' || char === 'д') res.boobs = '4';
                    else if (char === 'e' || char === 'е') res.boobs = '5';
                    else if (char === 'f' || char === 'ф') res.boobs = '6';
                }
                if (!res.boobs) {
                    let cleanLine = l.replace(/\d{2,}/g, '');
                    let d = cleanLine.match(/\d/);
                    if (d) res.boobs = d[0];
                }
            }
         
            if (!res.hair) {
                if (/(шатенк|шатен|коричн)/i.test(l)) res.hair = '3';
                else if (/(брюнетк|брюнет)/i.test(l)) res.hair = '2';
                else if (/(блондин)/i.test(l)) res.hair = '1';
                else if (/(рыжая|рыжие|рыжуля)/i.test(l)) res.hair = '4';
                else if (/(русая|русые|русый)/i.test(l)) res.hair = '5';
                else if (/(волос|цвет|hair)/i.test(l) && !/(глаз|кожи|eye|любим)/i.test(l)) {
                    if (/(рус|rus)/i.test(l)) res.hair = '5';
                    else if (/(шатен|каштан|brown|chestnut|коричн)/i.test(l)) res.hair = '3';
                    else if (/(брюнет|черн|черный|black|brunet|темн)/i.test(l)) res.hair = '2';
                    else if (/(блон|бел|свет|white|blonde|blond)/i.test(l)) res.hair = '1';
                    else if (/(рыж|red|ging)/i.test(l)) res.hair = '4';
                }
            }
        });
        return res;
    }

    /* === [ 3. ТИРЫ: СТРАШНАЯ / ОБЫЧНАЯ / ВИП ] === */
    /* Услуги и цены — одинаковые для всех трёх тиров */
    const TIER_SERVICES = [
        {id: "service1",  price: ""},     /* Классический */
        {id: "service7",  price: ""},     /* В авто */
        {id: "service8",  price: ""},     /* Минет в презервативе */
        {id: "service9",  price: ""},     /* Минет без презерватива */
        {id: "service11", price: ""},     /* Минет в авто */
        {id: "service14", price: ""},     /* Куннилингус */
        {id: "service19", price: ""},     /* На грудь */
        {id: "service20", price: ""},     /* На лицо */
        {id: "service2",  price: "8000"}, /* Анальный */
        {id: "service4",  price: "6000"}, /* Групповой МЖМ */
        {id: "service5",  price: "5000"}, /* Групповой ЖМЖ */
        {id: "service6",  price: "4000"}, /* С игрушками */
        {id: "service10", price: ""},     /* Глубокий минет (входит) */
        {id: "service12", price: "7000"}, /* Анилингус (ласки клиенту) */
        {id: "service13", price: "5000"}, /* Фистинг */
        {id: "service56", price: "4000"}, /* Поцелуи */
        {id: "service15", price: "6000"}, /* Анилингус (ласки путане) */
        {id: "service16", price: "7000"}, /* Фистинг анальный */
        {id: "service17", price: "7000"}, /* Фистинг вагинальный */
        {id: "service18", price: "5000"}, /* В рот */
        {id: "service21", price: "5000"}, /* Лёгкая доминация */
        {id: "service22", price: "5000"}, /* Госпожа */
        {id: "service23", price: "5000"}, /* Порка */
        {id: "service24", price: "5000"}, /* Трамплинг */
        {id: "service25", price: ""},     /* Фейсситтинг (входит) */
        {id: "service26", price: "8000"}, /* Страпон */
        {id: "service27", price: "5000"}, /* Бондаж */
        {id: "service28", price: "4000"}, /* Рабыня */
        {id: "service29", price: "5000"}, /* Ролевые игры */
        {id: "service55", price: "5000"}, /* Фут-фетиш */
        {id: "service30", price: "7000"}, /* Зол. дождь выдача */
        {id: "service31", price: "8000"}, /* Зол. дождь приём */
        {id: "service32", price: "7000"}, /* Копро выдача */
        {id: "service33", price: "8000"}, /* Копро приём */
        {id: "service34", price: "5000"}, /* Клизма */
        {id: "service35", price: ""},     /* Расслабляющий (входит) */
        {id: "service36", price: ""},     /* Профессиональный (входит) */
        {id: "service37", price: ""},     /* Массаж телом (входит) */
        {id: "service38", price: ""},     /* Массаж лингама (входит) */
        {id: "service39", price: "4000"}, /* В четыре руки */
        {id: "service40", price: "4000"}, /* Урологический */
        {id: "service41", price: "5000"}, /* Стриптиз профи */
        {id: "service42", price: ""},     /* Стриптиз любительский (входит) */
        {id: "service43", price: ""},     /* Танец живота (входит) */
        {id: "service44", price: ""},     /* Тверк (входит) */
        {id: "service45", price: "5000"}, /* Женское шоу */
        {id: "service46", price: "3000"}, /* Секс чат */
        {id: "service47", price: "4000"}, /* Секс по телефону */
        {id: "service48", price: "5000"}, /* Секс по видео */
        {id: "service49", price: "2000"}, /* Отправка фото/видео */
        {id: "service50", price: "5000"}, /* Подругу */
        {id: "service52", price: ""},     /* Эскорт (входит) */
        {id: "service53", price: "4000"}, /* Фотосъёмка */
        {id: "service54", price: "4000"}  /* Сквирт */
        /* service51 (Друга) — НИКОГДА не ставить */
    ];

    /* Диапазоны цен для каждого тира: [min, max, step] */
    const TIER_PRICES = {
        "страшная": { p1: [13000, 15000, 1000], p2: [26000, 30000, 1000] },
        "обычная":  { p1: [15000, 18000, 1000], p2: [30000, 36000, 1000] },
        "вип":      { p1: [20000, 25000, 1000], p2: [40000, 50000, 1000] }
    };

    function getRandomInRange(min, max, step) {
        const steps = [];
        for (let v = min; v <= max; v += step) steps.push(v);
        return String(steps[Math.floor(Math.random() * steps.length)]);
    }

    function applyTierServices() {
        document.querySelectorAll('.prof_form_service input[type="checkbox"]').forEach(c => {
            if (c.checked) c.click();
        });

        /* Таблица цен из TIER_SERVICES */
        const tierPriceMap = {};
        TIER_SERVICES.forEach(item => { tierPriceMap[item.id] = item.price; });

        /* Начинаем с базовых услуг */
        let finalIDs = new Set(BASE_SERVICES);

        /* Всегда один из service41/service42 */
        const always4142 = Math.random() < 0.5 ? "service41" : "service42";
        finalIDs.add(always4142);
        const blocked4142 = always4142 === "service41" ? "service42" : "service41";
        const blocked = new Set(["service51", "service3", blocked4142]);

        /* Группы с шансами — как в оригинале */
        const isLucky1 = Math.random() < CHANCE_GROUP_1;
        const isLucky2 = Math.random() < CHANCE_GROUP_2;
        const group1 = ["service2", "service26", "service16", "service13"];
        const group2 = ["service4", "service5", "service39", "service50"];
        if (isLucky1) group1.forEach(id => { if (!blocked.has(id) && finalIDs.size < 30) finalIDs.add(id); });
        if (isLucky2) group2.forEach(id => { if (!blocked.has(id) && finalIDs.size < 30) finalIDs.add(id); });

        /* Связанные услуги (триггеры) */
        const links = {
            "service2":  ["service26", "service16", "service13"],
            "service26": ["service2",  "service16", "service13"],
            "service16": ["service2",  "service26", "service13"],
            "service13": ["service2",  "service26", "service16"],
            "service4":  ["service5",  "service39", "service50"],
            "service5":  ["service4",  "service39", "service50"],
            "service39": ["service4",  "service5",  "service50"],
            "service50": ["service4",  "service5",  "service39"],
            "service22": ["service6",  "service21", "service24", "service29"],
            "service28": ["service29", "service27", "service23", "service12"]
        };
        const tierIDs = new Set(TIER_SERVICES.map(s => s.id));
        const triggerIDs = Object.keys(links)
            .filter(id => tierIDs.has(id) && !blocked.has(id))
            .sort(() => Math.random() - 0.5)
            .slice(0, 2);
        triggerIDs.forEach(tId => {
            if (finalIDs.size < 30) {
                finalIDs.add(tId);
                links[tId].forEach(reqId => {
                    if (tierIDs.has(reqId) && !blocked.has(reqId) && finalIDs.size < 30) finalIDs.add(reqId);
                });
            }
        });

        /* Заполняем оставшиеся места случайными услугами из тира */
        TIER_SERVICES
            .map(s => s.id)
            .filter(id => !finalIDs.has(id) && !blocked.has(id))
            .sort(() => Math.random() - 0.5)
            .forEach(id => { if (finalIDs.size < 30) finalIDs.add(id); });

        /* Ставим галочки и цены */
        finalIDs.forEach(id => {
            const cb = document.getElementById(id);
            if (cb) {
                if (!cb.checked) cb.click();
                const priceValue = tierPriceMap[id] || "";
                if (priceValue) {
                    setTimeout(() => {
                        const pInp = document.querySelector(`input[name="Item[service_price][${cb.value}]"]`);
                        if (pInp) {
                            pInp.disabled = false;
                            pInp.readOnly = false;
                            let parentDiv = pInp.parentElement;
                            if (parentDiv) {
                                parentDiv.style.display = 'block';
                                parentDiv.classList.remove('hidden', 'hide', 'd-none');
                                if (parentDiv.parentElement) {
                                    parentDiv.parentElement.style.display = 'block';
                                    parentDiv.parentElement.classList.remove('hidden', 'hide', 'd-none');
                                }
                            }
                            fillField(`input[name="Item[service_price][${cb.value}]"]`, priceValue);
                        }
                    }, 250);
                }
            }
        });
    }

    const TIER_LABELS = {
        "страшная": { text: "😈 СТРАШНАЯ", color: "#7b2d2d", range: "13–15К / 26–30К" },
        "обычная":  { text: "⭐ ОБЫЧНАЯ",  color: "#2d5a7b", range: "15–18К / 30–36К" },
        "вип":      { text: "👑 ВИП",      color: "#7b6b2d", range: "20–25К / 40–50К" }
    };

    const renderTierCreate = (tier) => {
        const randomName = getNextUnique('names', NAMES) || "Анна";
        const lbl = TIER_LABELS[tier];

        panel.innerHTML = `<div class="ui-close" style="position:absolute; top:12px; right:15px; cursor:pointer; opacity:0.3; font-weight:bold; font-size:18px; z-index:10;">✕</div>
            <div id="go-back" style="position:absolute; top:12px; left:15px; cursor:pointer; opacity:0.5; font-size:11px;">← НАЗАД</div>
            <div style="font-size:15px; font-weight:bold; color:#7ecfbe; margin-bottom:4px; margin-top:5px;">скриптонит залив.</div>
            <div style="display:inline-block; padding:3px 12px; border-radius:8px; background:${lbl.color}; color:#fff; font-size:11px; font-weight:bold; margin-bottom:8px;">${lbl.text} &nbsp;·&nbsp; ${lbl.range}</div>
            ${getMonitorHTML()}
            <textarea id="ui-parser" placeholder="Вставь данные анкеты..." style="${FIELD_CSS} height:110px!important; resize:none; padding:10px;"></textarea>
            <div style="display:grid; grid-template-columns: 1fr 1fr; gap: 8px; text-align:left;">
                <div style="grid-column: span 2;"><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Имя</label><input id="ui-name" style="${FIELD_CSS}" value="${randomName}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Возраст</label><input id="ui-age" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Рост</label><input id="ui-height" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Вес</label><input id="ui-weight" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Грудь</label><input id="ui-boobs" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Волосы</label><select id="ui-hair" style="${FIELD_CSS}"><option value="1">Блонд</option><option value="2">Брюнетка</option><option value="3">Шатенка</option><option value="4">Рыжая</option><option value="5">Другой</option></select></div>
            </div>
            <div style="display:flex; gap:8px; margin-top:10px;"><button id="toggle-wa" data-on="0" style="flex:1; padding:10px; border:1px solid rgba(61,158,138,0.35); border-radius:10px; background:rgba(0,40,35,0.4); color:rgba(232,244,242,0.45); font-size:12px; font-weight:bold; cursor:pointer; transition:0.2s;">WhatsApp</button><button id="toggle-tg" data-on="0" style="flex:1; padding:10px; border:1px solid rgba(61,158,138,0.35); border-radius:10px; background:rgba(0,40,35,0.4); color:rgba(232,244,242,0.45); font-size:12px; font-weight:bold; cursor:pointer; transition:0.2s;">Telegram</button></div>
            <button id="ui-apply-tier" style="${BTN_STYLE} background:${lbl.color}; color:#fff; margin-top:10px;">ПРИМЕНИТЬ</button>`;

        panel.querySelector('.ui-close').onclick = () => panel.remove();
        panel.querySelector('#go-back').onclick = renderMainMenu;

        const toggleStyle = (btn) => {
            const on = btn.dataset.on === '1';
            btn.dataset.on = on ? '0' : '1';
            btn.style.background = !on ? 'rgba(61,158,138,0.55)' : 'rgba(0,40,35,0.4)';
            btn.style.color = !on ? '#e8f4f2' : 'rgba(232,244,242,0.45)';
            btn.style.borderColor = !on ? '#3d9e8a' : 'rgba(61,158,138,0.35)';
        };
        panel.querySelector('#toggle-wa').onclick = function() { toggleStyle(this); };
        panel.querySelector('#toggle-tg').onclick = function() { toggleStyle(this); };

        const parser = panel.querySelector('#ui-parser');
        parser.oninput = () => {
            const data = parseData(parser.value);
            if(data.age) panel.querySelector('#ui-age').value = data.age;
            if(data.height) panel.querySelector('#ui-height').value = data.height;
            if(data.weight) panel.querySelector('#ui-weight').value = data.weight;
            if(data.boobs) panel.querySelector('#ui-boobs').value = data.boobs;
            if(data.hair) panel.querySelector('#ui-hair').value = data.hair;
        };

        panel.querySelector('#ui-apply-tier').onclick = function() {
            const tp = TIER_PRICES[tier];
            const p1 = getRandomInRange(tp.p1[0], tp.p1[1], tp.p1[2]);
            const p2 = getRandomInRange(tp.p2[0], tp.p2[1], tp.p2[2]);

            fillField('#item-name', panel.querySelector('#ui-name').value);
            fillField('#item-age', panel.querySelector('#ui-age').value);
            fillField('#item-height', panel.querySelector('#ui-height').value);
            fillField('#item-weight', panel.querySelector('#ui-weight').value);
            fillField('#item-boobs', panel.querySelector('#ui-boobs').value);
            fillField('#item-color_hair', panel.querySelector('#ui-hair').value);

            const phoneClean = GLOBAL_PHONE.replace(/\D/g, '');
            if (phoneClean) fillField('#item-phone', phoneClean);

            fillField('#item-price', "1");
            const p3 = String(parseInt(p1) * 5);
            fillField('#item-price_a_0', "");
            fillField('#item-price_b_0', "");
            fillField('#item-price_a_1', p1);
            fillField('#item-price_b_1', p1);
            fillField('#item-price_a_2', p2);
            fillField('#item-price_b_2', p2);
            fillField('#item-price_a_3', p3);
            fillField('#item-price_b_3', p3);

            const dist = document.querySelector('#item-district');
            if(dist) { const opts = Array.from(dist.options).map(o => o.value).filter(v => v); fillField('#item-district', opts[Math.floor(Math.random() * opts.length)]); }
            const metro = document.querySelector('#item-metro');
            if(metro) { const opts = Array.from(metro.options).map(o => o.value).filter(v => v); if(opts.length > 0) { fillField('#item-metro', opts[Math.floor(Math.random() * opts.length)]); } }
            const map = document.getElementById('leaflet_coordinates');
            if(map) { const r = map.getBoundingClientRect(); map.dispatchEvent(new MouseEvent('click', { bubbles: true, clientX: r.left + r.width/2 + (Math.random()*40-20), clientY: r.top + r.height/2 + (Math.random()*40-20) })); }
            const work24 = document.getElementById('work_time24');
            if(work24) { work24.checked = true; work24.dispatchEvent(new Event('change', { bubbles: true })); if(typeof window.work_time_24 === 'function') window.work_time_24(); }

            const useWA = panel.querySelector('#toggle-wa').dataset.on === '1';
            const useTG = panel.querySelector('#toggle-tg').dataset.on === '1';
            if(useWA) { const wa = document.getElementById('messengers1'); if(wa) { wa.checked = true; wa.dispatchEvent(new Event('change', {bubbles:true})); } }
            else { const wa = document.getElementById('messengers1'); if(wa) { wa.checked = false; wa.dispatchEvent(new Event('change', {bubbles:true})); } }
            if(useTG) { const tg = document.getElementById('messengers2'); if(tg) { tg.checked = true; tg.dispatchEvent(new Event('change', {bubbles:true})); } }
            else { const tg = document.getElementById('messengers2'); if(tg) { tg.checked = false; tg.dispatchEvent(new Event('change', {bubbles:true})); } }

            ['where_to_go1', 'where_to_go2', 'where_to_go3', 'where_to_go4'].forEach(id => { const cb = document.getElementById(id); if(cb) { cb.checked = true; cb.dispatchEvent(new Event('change', {bubbles:true})); } });
            fillField('#item-neighbors', "1"); fillField('#item-haircut', "1"); fillField('#item-smoking', "1"); fillField('#item-nationality', "1");

            if (GLOBAL_TELEGRAM && GLOBAL_TELEGRAM !== "@Ваша собачка") fillField('#item-messengers_telegram_username', GLOBAL_TELEGRAM.replace('@', ''));

            fillField('#item-max_ejaculation', "6");
            setTimeout(() => {
                const rawDesc = getNextUnique('main', GLOBAL_DESCRIPTIONS);
                const rawMinDesc = getNextUnique('min', GLOBAL_MIN_DESCRIPTIONS);
                const dInp = document.querySelector('#item-description');
                if (dInp && rawDesc) {
                    const finalDesc = syncDescription(rawDesc, SHOW_WA, SHOW_TG, GLOBAL_TELEGRAM, false);
                    dInp.value = finalDesc;
                    dInp.dispatchEvent(new Event('input', { bubbles: true }));
                    setTimeout(() => { dInp.value = finalDesc; dInp.dispatchEvent(new Event('change', { bubbles: true })); dInp.dispatchEvent(new Event('blur', { bubbles: true })); }, 100);
                }
                const mInp = document.querySelector('#item-min_description');
                if (mInp && rawMinDesc) {
                    const finalMinDesc = syncDescription(rawMinDesc, false, false, GLOBAL_TELEGRAM, true);
                    mInp.value = finalMinDesc;
                    mInp.dispatchEvent(new Event('input', { bubbles: true }));
                    setTimeout(() => { mInp.value = finalMinDesc; mInp.dispatchEvent(new Event('change', { bubbles: true })); mInp.dispatchEvent(new Event('blur', { bubbles: true })); }, 100);
                }
            }, 600);

            applyTierServices();
            this.textContent = 'ГОТОВО ✓';
        };
    };

    /* ====================== ЦВЕТА + АНИМАЦИЯ ====================== */
    const COLOR_RED = "#3d9e8a";
    const COLOR_TITLE = "#7ecfbe";
    const COLOR_TEXT = "#e8f4f2";
    const COLOR_MUTED = "rgba(232,244,242,0.55)";
    const TOGGLE_STYLE = `.eva-switch { position: relative; display: inline-block; width: 34px; height: 18px; margin-right: 8px; } .eva-switch input { opacity: 0; width: 0; height: 0; } .eva-slider { position: absolute; cursor: pointer; top: 0; left: 0; right: 0; bottom: 0; background-color: rgba(238,238,245,0.08); transition: .4s; border-radius: 18px; border: 1px solid rgba(61,158,138,0.4); } .eva-slider:before { position: absolute; content: ""; height: 12px; width: 12px; left: 2px; bottom: 2px; background-color: #b0d8d0; transition: .4s; border-radius: 50%; } input:checked + .eva-slider { background-color: ${COLOR_RED}; } input:checked + .eva-slider:before { transform: translateX(16px); background-color: #e8f4f2; }`;
    const PANEL_STYLE = `position:fixed!important; top:50%!important; left:50%!important; transform:translate(-50%,-50%)!important; z-index:99999!important; background:rgba(0,30,26,0.97)!important; color:#e8f4f2!important; padding:10px 14px 14px 14px!important; border-radius:18px!important; border:1px solid rgba(61,158,138,0.5)!important; box-shadow:0 12px 50px rgba(0,20,20,0.85),0 0 0 1px rgba(126,207,190,0.08)!important; width:270px!important; font-family: 'Segoe UI', sans-serif!important; backdrop-filter:blur(20px)!important; text-align:center!important; cursor:grab!important; opacity:0; animation: panelPop 0.45s forwards;`;
    const styleSheet = document.createElement("style");
    styleSheet.innerText = TOGGLE_STYLE + `
        @keyframes panelPop {
            from { opacity: 0; transform: translate(-50%, -50%) scale(0.7); }
            to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        }
    `;
    document.head.appendChild(styleSheet);
    const panel = document.createElement('div');
    panel.style.cssText = PANEL_STYLE;
    panel.style.backgroundImage = 'linear-gradient(rgba(0,30,26,0.80),rgba(0,40,34,0.85)),url("data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjL/wAARCAJYAZADASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwDxwyKsuCTFKvR16Gt/StShMMltervsp+J0/wCebdnHt61z8wEsauB8w7UkcjW0geMlom5APb2rQ5rXR6toGvTaFcRaRq0vmWj8Wd6TwR2Rj6+h/wDrV3gYMMjpXiuk6vbNZmxvlE+nPxzyYf8A638q6zT9U1Dw3CpbzNU0XHyyJ800C+/99R+YqZIqE7aM6LU9J6zW68dWQdvpXPyxkcjPHWuy07U7LVrRbqwuY54j3Q9PYjqD9apalpgfdNAvPVkHf3FJS6Myq0r+9E5dXwc9fUeopHUq2Acg8g+op88Rhkx/C3IpAcptPVelWcpLa31xaMPLc7R/Cen/ANatu3v47tNyt5cg5ZT0/wA+4rnSOaVGZHDKcEdxQONRx0NW40+M5ELralzloZRugkPqOwP0/Kh7jxNZxfubWW5AHyhZllX2+982PxqOC9dVIz8p+8vUfketWorgA/ugUP8A0xYr/wCOnIoNlUOaudb8apP5klvNbr/cWzJT+p/WtTSvHz7hBq1qEPQyQ5IH1Q/MPwzWuur3EZ4l3D/aX/Cia+tb9dl9ZQzD1IBI/Pn9aLDVTszZtb2OaFZ7WVZrc8goc7fp/hWrHIJFBBzn071w8WkpbTG50G7aCX+K3kJKP7c8/wA62tN1jfL5FxEba5H3om6N7qalo3hU7nQ5w2ex4qUGq8brKm5TkfyqVSQOelQbElKaaDS5oAxfE2g2/iPRpbC4wrfehlxkxSDo307EdwTXiMPnWd3Po2pRlJ4mMZVvbtnv6g9xX0KwzXEeOvBY8QwreWW2PVYFwjE4EyjopPYjse3Tp0qMraGc4cyPIbq0kspR8zGMnKP/AJ71PKv9qwAggXkY6f8APQVZhv8AbJJp+rRNBcRnY4lXGD/tDt9adLpRQia3faOqkHI/OtDmb77mdZXRjk8mcEMPl+buPQ1dkh8yJ4GYlWXCkn8vxFLNbLeJi5Ty5h0lXkN9agDz2REd2CY/4ZhyB9aZD11W5qeFJiLWS3c4kjkO4fWt2SUjgHk1yiu9rdrfW/zBhiVB/EPUe9b8dylxEk0TZU/pVpmM1rc2LWEBcnlu5q6oYVTtZQ0YINXUBb+LFJmY1olbqtQyWMUikEcHqCMirmGHUZFGFb60XCxzV54UsLgEiDy2P8UJ2n8ulc3e6Ff6YfNgdp41544dfw716Oy4qGWFZF5H40ylOSOG0zXFmKw3DYJ4V/f3pb6ObSbtb+1JVC3zAdj/AIVJ4j0IfvLq2TEyjc6DpIvr9ak0iYatorwync6gxsT34+U/59KC9Lcy26m2jwa7pZfA3Y+YD+E+orlZ7aW0uCpJVh0Yd6s+E7xoL0wMeN2xh9f/AK9buuWKtzjAblT6GpYfC7HOpdMRiYbh/fXrVa5sFkUywHcvfb1H4UxmeNyp4IODTo7plfIU7vVetItJrYqBmXAkJIHAdeq//W9qilQxsGHAPdeh9xWo6xXXzAiKb1xgH6iqewqzRMu1u69j9PSg0TEilwQxzg8MP5/40XNpuR5YiRLF8zY/jU9GHofWmIm1yh6NwKu2bEzRZ6kMjUwbtqi9p9yb/TwznLp8j/X1/GqEyS2VyssBIIPH19KsaOgjmukA+XKn8cVNfIpBB6EVXQyvaTS2N3Tb4XdusnRujD0NW7h8Qnmuc8OsQsq9g1a19NthwOvpSMmrSsYcuZZ5ZM8uwiT8ev6VTuVNxqGP+WcXAHvVxHBugAcpbqWY/wC1S2MG5fNfgE7yTSZutDk1JGQas/Zt9i1zHyqtiZB1X0Ye3qKieLuvWtOzeLTlhui5eGXCTrjpnv8Ah/WoOlsxVke3l3xtg+3Qiul8P+JZ7CULEV2n79tI2Fb3U/wmsvXNIbTZVmh+ezmOY2HIU9cfTuPasmkPRq56jDZ2mpztqXhu+bTNUXmWA/KG/wB5f6jIrofD3im4u71tJ1m3FrqaDII+5KPUf5xXlWj3rySBZGczQ/PFIrYcDuAfX/JrrZdRN7Bb3shX7fpcys7qMeZC3cexBzjsQaGiU2mdrrWnBomliX3wOx/+vXOqc13QxcQ7T/EOv9a4q8gNreyRkYAOR9KS7GVeFnzIiYc0qgE805xxmmCqOZ7koBQBhyueCPWpo3D5AO1iPzqKN9pzgEEYZT3FLLHsw6EmM9D3HsfegPQeSQe4NAdh3/OgN5y4/wCWo/8AHh/jUYNAiwk2CP4TV37VHcoIrxSwH3ZB95ay809WK+4plRm0dBbX1xY4Z2M8HaZBkgf7Q7/zrftdQguYhIjqVP8AEpyv59voa4mC6eJsxuVPp61dikikl82OR7K5/wCesP3W/wB5ehFS4nTTrdDtOKX8TXOR6jc2qj7XEwj/AOfiz+ZPqUOcfhV+GVryLfbaoXT1REOPrxx+NQ0dKmmae3/ab86jaJj0f8xVP7Lf9U1SQ/70KEfyqWP+0Iz+8a3nHqAYz/UUirmL4k8HWHiSEfbINtwoxHcwkCRfbn7w9j+leX6n4J8TeHXZ7LfeWw53W4JOP9qM8/lmvcg7EfMhX2yDSkg9QfxFNSaE4pnzkmvurlLq1HmLwxjJRh9QavRanZXA2eaozxslXafz6GvatV8P6PrSFdQsYJz2Zlw4+jDkfnXn+ufCJSrTaHekHr9mujkH2Dj+o/GrUzGVHscq1j5Z3Wh2558puh+lNglkt5WMakN/y0hbgn3FZcw1Xw7etZ3kEkLryYJh8pHqPb3FbNvc22qQ7lVi6clM/vI/cHuKtMwlFrc07LUBtDxtuQ9R3Fb9tdK4BBBBrimjlgkEsRDE9CvSUfTs1adlfDYJUPyH7y/3TVbmMoW1R2SSZFPKhhkdazLefcoOeKvRydKTRCYuTna1MYYpZT0NNZvlpoTMvWBshinH8MgU/RuP54rl/D0f2fVdVt14RGUgenJ/xrpNcfNikQ+9LNGo/wC+s/0rC0Qq93rF7/A0wQH2Uc0MuPwszdOymv3YHZmI/Bwa7zUo/NtWGORyK4fw7GbzUpZsf62QD823H9BXY6zqsGmxbpFLu33UHehlS+KxxmpJi43dMjke9Z8hkUkBjgenFaN7c/bJPMaOOJv7gJP51W3FTkop9yM1JrEqrcyp0ckejcip2mW4jDEbXXim3KRtF5iLtI6gdKrK2Ao9c0FJX1LT5O1u+cGp7Y4uXYdEyahUhIfMPPPA9T2q3Z25kQIf4sPIf9nsPxP6CmJ7al7T7dkt3nYYEj5z7YwP0FVb2XcxI79Kt3NwFTaOg4FVbaAzyiRx8g6e9V0Mk/tM0NKh+z2+Twzcmq2p3p3iKLmVunsPWpby+FtGI0G6V+EQf56VTggaJyzAS3j8kHonuf8ACk2KKu+ZgtuUiW0X/WS4aQ/3V/8Ar1Lfy+Tb/Z4vvEc47UquINwjPmTMcvIemf8APas68uY7dGZ2yx6k9TUmq1ZlAspwwOR19anicYZCA8T8Onr7+xqpHdsG8q7Vty8biPmX2I71YMQcB4nAJ6EdDUm70L1temytHsruI3elvwD/ABRe3+fwqpf6VZraG7068Esa8tG5G4D2pqXb274mVkPTcOhqVrWzvBuXEbH+KPp+VIL2Mu0uDbXMcy/wnOPUdx+VdO1wltJHOWzbyIYZD/0zflT+DZ/OsCfSriFSyATIDnKdfyq5pN0k9ubCYBiARGG/jU9U/qKYSs9Ue1eHLwXmi277gZI1EUnP8S8fqMH8ah8RWJdFu4xnbw+PT1rzfw34jn8KaisV0Wl02X5d/cDtn3FewwzQXlqk0LpLbyrlWHIYGoejuVZTjZnEj5o/pTAOa0b+xOn3ZQA+S/KH29Pwqi67WIPXNUcE4tPUQcVLHLtyGG5G4Yf571Ec4+lANMi9iSSPYwwcqeVb1FO4k5bh/X1pYmyuxunUU/yxnigdyEoy9RQDVkAjimlEJ5GD7UxEQNPViOhyPSgxkcjkU2gC9a6hLbtwSR6d60E+xXp85gYZh1ngYoy/72P/AK4rBB9amjleNw6MVYdCKTNYVGtGdGH1mzAaJ4tRh9GPly4+o+U/iBU9v4lsmlEFyXs5z/yyuV2H8D0NZ9hfsPmiXJHMkA/iH95Pf2rbMVnqdoBJHHPA44Drkf8A1qh26nZBt/Cy2kySLuVgw9QcinhvQ1zU3hAREyaTfz2b9RGWLJ/iKozX3ibRDm7gW7gH/LRRn+XIo5U9ivaOPxI7TKng4/GmmJT0yp9q57S/FthqTCJybeY9FkPB+hroFfHB6VNrFxkpK6MvW9CsNdsTZ6nbrLH1Rxw8Z9VPY/5Oa8O8SeGtQ8Gasn7wvbuSba6AwHHdWHZh3H4ivokjcKx9e0S117SJ9Nux+7lGVfHMbj7rj3B/TIpxlYJRTR4za3kd7a+eBhScTIP4W/vCmS7rK5E4GUY4lA6H3/Gs6xjn0fX59NvF2uHaGVe24dD+P9a15k32ciNy0Xyn3Hb9K3OKS5XY2tMlGwoDlRgqf9k9K2IpORXKaDKdmwnlAyfgDkfzroUkxTOaSsy7I+SBUMs4A64A6msm+1eK2bZkvKeiLyTWFf6qzqRcuFT/AJ4IeW/3j/SiwKLZNrOrhg1yh/dxgpb/AO254L/QDgVXnJ0rwpHB0nuOvrluT+lUtOik1vVFklGLeHBI7AdhU1zI2u68scXzQRHauOhPc0zW1tDf8KWS21l9pkGMA4+p/wDrVhavfG91GScnKJwg/lXQ6zdLp2mJZQn5yMHFcZI3YdB+pqWOmrvmBnPrTlkPrxUVKG2+59KRrYkmbERQHlv0FV4V81xjhR0J9O5qN5DOdqn5M/M394+g9qvW0DSkIFJBOMD+I+n0Hc0D+FEsELXUyYTKDhEPf3Pt61qSMtvGUVtzE5Zv7xo+W0iKgjzD95h29hVTPmNkgn0H+NXYwbcvQfFCZ33Pnb6VNJeBV22+0443n7i/4n6VAqS3AIXDRjqc4jH1Pel3KhxCfMkHWVh8q/7opNjUb7goS2BkkZhJJ1dhmR/90dhTgXaMlv3EH93PzN9T/QVUurmLTvncGa7cZCsenu3+FYNxeXN85eec7R17KPYVFzaNNy1Nm71SOMeVBg9gFrCubgvJukIZ+y9lqF5wMrCCB3c9T/hUI96TOiNNRNhLwXaiK6T7RjhSTiUfRv4voaI7SQFpNPl88D70TDDj6r3/AArPIqZZt5Xe5SRfuTDqPY+o9+tAi9FdpLmORdrdCj0j2ZVvMtJDG390nj86adRDsIdVthNxxMnDgeoI6iraWUjRedp04vIO6Hh1oJtbYhh1J4HEd2jRt2cD+lXJ7SC9USZCSHlJk6GqwkSYGKRDkdY5BgimxLLYuXt8yQn78Df0oIa7aMuRzBybPUFAZurdm9GH9fQ/Wuj8H6xN4b1RdPuZS2lXTYUt0ic9G9h2I/GsF44NQtFw2Ub7j90PvSWM5nWTTb0fvk4z/eHY0NAnbVHteoWYvLR4sfOvzIfeuTlU4Vj1IwfqK1vCGrNqOkJHO2bq2PkyE9WwPlb8R/I03UbQLdTRgcOPMX69/wCtStNBVo8y5kYppO9OYEHBpMc1RwiqcHNWlbcKq1JGe1AFpSKcUBFRA81YTlaBkGCpxQyBqmdc9KjX070xEBUg4NAODVgqCMGoWXBxSGSI7IyuhIIOQR2rf069LMZIhmU8ywjgSf7S+je3eucXg/WpopGhkDKxXnII7H1oaua06nKzvoJkniWSNtyt3qbAIweRWBY35ZGukXLL/wAfMS/xD++o9fX1rdjkWRFdGDIwyCOhFZtWPQhNSOZ8QeD7e+RrixUQ3I52jhX/AMKzfDevT29z/ZOplgwO2N36g/3T/Su8rj/GmjCSEalAuJU/1mO47H8Kad9GZzhyPngdSjfw/lQ4yM1j+HNSOp6THK5/fRny5PqO/wCNbJ6VNrG0XdXR4r8WLD7D4ns9TjGBdRAsR/fjOP8A0ErVRcNLJ6SRBv8AP511nxhthJ4dsLjHMV2Uz7Mh/qorjrIlo4HP/PsM/pW0HdHLXVmO0b5JpvQEfyq5quqfYrYBCPNfgZ7D1qrp42LO/wDekwPwAFc9q14bq8dgcqPlX6Cruc6hzTI5b+Q7gjFd33mz8zfU1DbW8t7crDGMux/L3pkcTzSCONSzN0AreR49Dg8qECXUJR252Ukat8ukdx+pTx6XZLpVkczOP3jjrz1rX0LT00qyNzNgSFc89hVLR9GFuW1DUmzIfmw3b603VtY875V+4Puj19zTMd/dRT1S9a5uGkJ5PCj0FZvQUFi7FmOSabI6xx736dAO5NSbpW0FLBVLMQFHc1XLPcsFVWEZPCj7z/X2/QU5YXndS65Y/dj7KPU1o21oXcRRAO7Dlj0I9T6L7d6Nx3USK1s2kZVA3MRwF4GPb0Hv37VsAR2SbVwZCMEgfoPQUrtFp8RjjO+Vvvuep+v+FVBHJMd0jbEb16n6DvVLQybct9h2WnfAUt7Dp+Jq6lkqpvuWG0fwL0/+vTFZbKPO3aewblj/AEFVTeXF5cJGrkbjgAdAKQJdie4dpyF6RDhEXgf/AF6SeSOws2nbnb90f3m7flUkrK9yxT5UHf0Arndd1AyyiCEElegAzsH+JpM0px5nYy7i4aSd5ZjvlY5I7f59qru7SEbjwOgHQUmxh94Y+tKql2CqCzHsKk7NhOKdgxospPLfcH9aHCR8Eh39B90fj3pjOztuY5NAy3SEVMVSRN0eQ4+8h5/EHv8AT+dQ0GRLFIhXybgEwk8EfejPqP6jvTHW5026BjlKNgMkkZ4dT0I9RTTWnpkI1S2k05yBIgMlu5/hPcfQ8fzoC9ie3122u1WHV7cN6TxjDL74/wAPyq1LamJFlimE9s33JV/kf8a5YgqSrDDA4IPY1d07UpdPkIHzwPxJEejD+hoFKHY2Im+zymQcRucSr/7NS6ojIkd7H/rrcgMR/Eh/z+tWPLiliWWBt8TjKn1HofcU+3QTRNBJyCDG2fQjg/y/KmZX1ub/AIY1IW2qQXKnEN0oRxnvng/gePxrvNTx59tIO+R/WvINAdmtpLRyRJC5X6Z/+uK9Stro6jpOm3B+83Df7w4P6ik+5XRop31t5cm5R8vUfSqZ4OO9dTNZ+bDtI+YfrWJcQCKMbl53EE0HPVp2d0UcUqnBFKy7Tim0HOywpyKsRtVRD2qZGxQBYPWox9807cGFIBg0AOxTJEyKkFB6UxlQg05eRg0915zTOjUgRc0+7ezuklGSFOGHqpro4LlNOvI4Sf8AQrs5gbsjnnb9D1H41yg6g9uhrbsY11bRp9NlbDrzG/dT1BH0NJo6aUnsjqhUdzClxbSQuMq6lTWT4d1OS9s2huhtu7ZjFMv+0O/41tk8Vm9GdsZKUbnBeFGay1u/05u3IHup/wADXbfw1x4j8j4iHaMCSMk/98//AFq68fcOaqRFHSNuzOD+K2D4M5/5/Isf+PVwluPJtRn+CJF/TNdj8Vpt+m6TYD71xeFyPZVx/Nq5GQZVU7O5P4D/APVWkNjHEPVFW8nNlpgUH94w/U9TXPxQPPKqRrlm4FXdRmN3qDIPuR8VLbQPLIbaE7cjM0o/hH90e9WZr3YklrE0bG309Q8/SW4I+VPYe9XolstGyzk3F2eTznn1J7VOQtpaeVbKEAGFx61nxaWZPnu5SM8lVP8AM0WM7p77EN7rE123zNx2UfdH+NZ5Yscsck1oX/8AZkERjhjLTeqscD61lhs1JtFaaIkLAAknAHWmKpkkWV1yTxFHQq7sM3CDke/vVqM+XEbiThmGEHovrTQ9iWKJi4hjG+WQ4/3j3+iitIyLYx+RAd87cu/v/noO1V7fdaWokxi5uBkf9M4x0/OpbS1WXc0udg65PX60zORFDHJM5EK+Y/eRvur/AI1YM0doDszLN/FKf6elWLm4iih28JGOiDjNUYre4v2+QbIvWkLfcqSSS3MuOWYngCtC2tvscRkkIErDH+6O9XFgt9OgZyQoH3nPJJ9Pr7VzWsax+8MYALj/AJZ9Qn+96n26Dvmk2XFOei2Jr2/xHiIP5ZPVRlpPp7e9Yjrdy7iQIY89GYIB+fJqu13O5JaRmJ65OajLlupqbnXGCitCYxW0eS8xlI6iJf6mo5LkshjiRYoz1VeS31Pf+VR54IBxnqKTbjrxQUJSgUUZxSGWqeu2RwGcJnq5Bx+OKZSGmZ2LE1pcQxiRoyYj0kQ7kP4iprG5TTrqC6WVZD/GgB4B4Iz61Vt7u4tHL28rRk9dp4P1Hery31jdcX9kFc/8trc7D+I6UXJkn1KeoKpvZZYjmKRi6n681WrYbRDOhk025S6j7ocK4+o6VmTW8tvKYpo3jkHVWGDQOLT6mjod99nuPs0rfuZTxn+FuxrfZDFcA4+98p+tcYK6+0uPtulRz9ZFG1/95f8AGhGdRdSG3P2XxPMo4WZBIPrxn+teieEnMlnJbsf9Revj6EZrzq9/d61psw6ODGfx/wD1133g1v8AiYX8fq0cn5rigSeqO+Me5fftWPq1nviLqOetbqDiobmIMp46j9R/9aoT1Npw5lY4eRcCoav6hB5E7L2PSs+rPNkrOw9TipgagHFPVqZmThsdKeHzUANO3UWAsg06qysRU6tmgYjDIqFhxVhhULDmkA5BuGPUVe0i48nUUJPyv8p/H/69UIzg/Q0/lJsr25FBrB2aZtzD+z/FsE68RX8ZRx/00TofxH8q6bORXNa4wfT7O7HWK4jcH2PB/nXQRtujU+1RI76ejaOZ8vzfHjOOfLgOa6Vzti+tYmjp5+r6jekcFhEp+lWdc1eDRtKudRuD+7t03bf77dFUe5OBQwp7NnmXji9/tHx0lshzHpsGw/8AXRuT/MD8KxbuUQGVh0hj2j6n/Ipukiacz6hdNunupGmdj3Ocn9f5VUvX81UQ/wDLVzI30/zitoqyOWb5plCFTFDvIzK54HqTW1bolhahScueWPdmNUINpujK/wByAf8Ajxq+hGfNnIA9+gqiJu+hA0svnrJKCF6AdlqPUZnWHcDkHgD3q215ZzDZ5yDtVK5tCiFkbdH1wDQwja+pkBSx/rVq2tklYKcnHJ9KjJGMYwKuW37u3llPXG0VJtJ6EGwXFwYxwnVj6KKmt4v7RvsN8tug3MeyoOp/z3qN/wBzahOkk/J9lq+sJht4rFABNcYkmP8AdX+FaBN2HAveTsyJy3Rf7qjgD8qnLeSmzeGx1PbP/wBapJiLaIW8XygAF27kmiysGvJBuH7sdvX/AOtTMmyOzsX1CcSyAiIcqD39zW1IY7aHauEVRkn0HrU0hjtIdqgcfqa53XL/AOzWrsTkjGR/ec9B9B1pExTm7GPr2ru02yMlXA+Uf88we/8AvH9BXN052ZnZnJLMcsT60zocHrUPU9GEVFWQtFJmikULn0p8X7wmPuwO369R/hUVCsUcMvBByDQMSlFSXEe1hIo/dyfMv9R+FRA0wLec0hNOZCjYP4EdxTTSIEpKKKAJIJ5baUSwyMjjoRXTQ3EHiSxNtOqx3sYyjDv7j+orlalt55LW4jnhbDodwoJcbhLG8MjJIu10O1h6Gtvw1N891bE8MgkA9xwf0NM15I7jyNRgGI7lBkejD/JH4VW0CTZrNv6PuQ/iKYnrE1NXOyHT37xzgfqK77wkMa5MB/FEv6Zrgdd/484R6XArv/CQJ11j/wBMh/I0zJdD0VaSXGwH0YU4dKSUfu/xH86xOvoc3rUGbdZQOUYoa54j5q7O5gE5u7Y9WAdfxH+Irj5VKsQRgg4NaI8/ERs7jRSgYpq1KuM80zmsANKKVk2nFJVAOBqWNsNioR0p6nkGkItdRUT9RUimopDzSGIvQ/Snk/vV96jHQ1IvMw9qC4m1cnzPDKg9TsA+oatueb7Lp7yn+CPj64rGK7rDT7bvI6kj2HNaV+POkhtf4WO5/wDdFTY74PQbpkBtdOjTB8x/mb6mvMfG+rv4j11dEs5M2Fi+Z5FPDy9D+C8ge+a6/wAceIJdJ0+OxsG/4md9lIiOsSdGf69h75PauFs7GOwtFt4uWP327se5q4xuZ1aiguVENxthsyEG0EBEA7DoKxJGDTO/8K/IPoOTWhq10FmCKciJc/j0FZc48uNY++0Z/Hk1oYwWg+1x5eX4C/vH+p6Vm3l69xKecIPurVu6cw2CJ0eX5m+lZwiPVztz27/lUs0gluxu41s2EhbTpAxyAcCs57dViEiPuGcHjGK0FX7PYrGfvN8xFCCdmkU25cjsKvCPdFHEeEHzOfbqaqqmXUd2NTX8nlQrCD80n3vZRQD1aQWQW91Bp5eIUG9vZB2rU0vNxLcajMMBiW+ijoKyyDBpqQD/AFt0dzj0QdBW7IgsdOjg/ixub+n600RNlYBrq7CdydzY9f8APFdPDCLW3CgDdjmsjQLffKZHGcHOfp/9ete8k2j9aGzKT1sZl1NumZjykYz9TXEa/e+bfCEMCtufm7hpD1/Lp+FdTez/AGezab+7uk/IZH64rz5yScsck8knvUSOnDx6gXJJ7ZOcDgUeY2MN8w9G5pvWkqTsHhY5CAD5Z/2iSP8AGmFSrYZWBHYjFNNSi4YoI5P3iDoD1X6Ht/KgBmR6frSZPSlIBPykkeh60mKAJY5C0D27fdY7l9mH+I4/KocY61YjikMDzxZIhIL4H3QTgH8+Kc8cdxGrQ5EwzvjPf3U/0piL9xDuHTbnoPQ+n0NUCOcdD05rprq3WQNxjPB+tYVzEQdx+8Dhvr60NGMJXRUpcUU5RxSLExRin8GkIwaAuaVlL5+lXVm3Jj/fR/1H+fWodJGNXtT6TCmafKIb+Fm+4W2P/ung/wA6nsY2i1qGM9VmCn8DTJ2ua2tLuFvH3aZK9C8Ij/iduR/zxP8AQf1rgtTX/idWURGdmHI+i5r0Dwev/E0lPpB/Nh/hQ9jOO6O/HQUkn3VH+0KCcAU4jOz/AHv6VkdRQvD5F/bTH7rgxN/MVja5ppSY3CL+7fr7H/69dFf2v2m0aMfe6qfQjpVe0mS8tzFKAWA2upq0zGcFJuL6nDMpRsMMU9a3NU0jyclcmI/dbup9DWFtKOVYYIqjgnBwdmWfvxA9xxUB4qaI9vWmOMEg0yWhFpV6kU0Uo4agktRn+VRueadGeD9KZ1akAq8DP41NbxmRsDqxC/nUQ5wvrV6D90u5Rlhwnux70GkFqa1mBPqRk/5ZWybVPbNTvcRW0FzqNy+yFFLE+iD/ABptvAYbVLcfff5pDXL+MNRF3cro0B/cQEPdEdC38Kfh1P4UJXZ183LG7OckuJtT1G41i7GJp+I0/wCeUY+6o/D+tRXVwtrbPM57cVM7rgu3CKK5bVNQN3N1/dIflHqfWtUrHKk5yuyrJIzl5ZDyTuP17CrbSW0kSSSHnAB9eKpSqTaRsP4mJNRRxlhz0FFzeyZJIWupjLg+ij0p4sWxuat/StMUQrLIvJ6A9qq65ciM/ZoAN5IXj1P+AosZ+0vLlRmWsaM7l/8AVR8sfpUUs5mkLHvzj0FJdOII1tIznbzIfVvT8KgQnOak1S6mjbRBrtfZcmoGX7ZqhXtu2/gKu6f/AK6Rj2Qfyqro53XEsh6hM/jmglPdlmyAvvEA7xocKPZf/r1panJm4YejY/If4msnw44XVUB/iUj8a0dT4uXH+2/6gGhESXvWOh0SIR2G7uQo/rUeoMcuPYCpdFkEmmrj0B/pUd8uZWHqBSMupz+vKTpbIvVoz+rLXBsc/N+FehawpNhKw6iFx/WuCkVUhhHQugbP0JFJndh/hIaDQQR1/CipNxKTFLRQAmKUGiigDe8PajptnHcwXyuBcAKz43KV9COo57iobvR2tt1zZSLeWXd4juKD0YdvrWPU9rdT2U6z28rRyDoy/wAj6imJrW6O1u49kv8AstWPfQjzAT91/lP17Gt68HmQ7u4rKvF32jHuBmqZxU2c46lWKkdKUdKmvB+9Vx0cA1AvcVJ17oKXqMflSUCkIXqK2LL99rVnN/z0ZWP1xz+uayOp+ta+h/Nd2uf+Wc2PwPP+NNCexsamP+KncH+GLj8lH9a73wg2dUuv+uSf+hNXDawhXxEj9pbZiPqB/wDY113hC4UaueeJYAR/wFv/ALKh7GcfiR6BdSiG2aQ8BcGrKHcUqhqcbXGl3MSfeeIhfrjijQ75dQ0u2uV/iUbh6HoR+dZnTfWxrbcism/s5Y5ftVt97+JR3rXHSgjNJOwSipKxl2t1HexmKRQJMYZD3rm9d05rOVZVyYm4B9PY11V1YK58yP5JByGFRSxLf2cltOMMRg+x7EVSdjGpTc42e5xMbdPapp1+YMOjDNVyjwXDwyDDoxUj3FXSN9nG/cEqa0ODoU6X+IUEYNA7UEE68Rk/hTKd/wAsx7mm4LHApASxLk57nv6Vs6fACRMw+VeEHrWbbQmaZYx07/St9pobC0a4mO2OMcAdT7D3NB00o9WV9a1T+yLHMeGvp/lhX0Pr9BXAuvljytxd2JaRz1YnqTWlfXcl1NLqFxw7/LGvZF9BWXGRtad+gG7n07VcURUnzPTYx9dvPKQWyHDHl8VzTtU97cNcXUkrH7xqoxqzWEbInhvGijMZVXXORntVjT0e8vkTHGcYFZnQ103ha3DTNKf4V4+ppBO0Vc6KV0srOSUj5Y0zj+QriTMxuJ7qQ5aMED/fPU/59K6nxBJssFTszjP0AJ/pXGyMRYoO7yEn8v8A69DIox0uQE5OTyaeOKjp2ag6DX05svJ7oP8ACqulN5d68TfxKy/iD/8AWpdNlCzgE8H5T9D/APXplwrW2oGQdc7x/WmZ21aFs3+x6tG3ZJP0NdFrEJ8zzF7gMPqP/rYrCv4wzJcx/dcc4roLKUanpSgYM0fA9yO34ihET6Mn8OXQXMJPGePoa0tQjKkOO3WuXXfZ3IZM8cgeq9xXU2t1HqVoMEFwOR60PQykuqMueNZ4th6NlT+IxXnd1bvFut5B89sxU+6k9f8APrXpUsRicofun7p96wdf0Z7pBfWi/v0HzqB1FJm1CoovU4pc4K4yD+lNK4NWAFJYqCGIwU9Dnt7VGQP/AK9Sd1yLFGKf17Z+lJx6GgBuKKdx70cHoRSAbg0oB9KU5HOKTJ70wPQn5Hs3BrLZcwyIevIq2k4lthIh4IyKglx5z46MAwqjgic/djNtE3oSKqA81duv+PQ/7L1R7ipZ1x2HUUUUALnj6Vo6PMIr5c9Nyt+R5/Qms4VNaMBcxZOATtP48f1oQNaHba+BHHZXx5FtLtk/3G+U1PpN22nSxTkk/ZJPnx3jPDfpzQ4GoaWsTji6hwf97HP6g1l6LdGW0jkfl4/9HuAfUcA/iMD6igy6XPcLaZZ4EdWDKQCCOhHY1haTu0XxLc6Yx/0a7JubY9gf4l/rXPeG9eOjTR6desTZSHFvKf4P9g/0rsdUsjf20U1uR9rt2E1u2epHb6EcVLVmac3Mk1ujoFPFOBqpZ3KXdpFOmQrrnB6j1B9weKsqeag3Wo4iq8sWG3r1FWaQjNAM4vxRa+VdRXijiUbW/wB4f/W/lVSD57GXHYhq6fXbM3OkXCKMug8xPqOf5ZrldLbzIp4++zIrSL0OCrC1T1IG60L1p2OD7U0dao5SU8Kv0ojHJJpG6L9KlgTeyIP4mApDSNnS7fbFvYfM/OfasbV706leLEh/0eM4X/aPdv8ACtnVJ/smnGOM4eU+WuOw7n8s/nXP2qDzj6DgU13N6jsuRGVq0ga5S1XgDCn+Z/T+dU9TfytKlI4LcU++bHiFwf7zf0qLWVL6U2Oxq0YvdHDufnpp6Usv3zTD0pnUhpOAa7LwoAbZz/u/yrimzXV+D5xl4ieccfhSTJrL3C/4jUm2z6bv/QTXIH95aEDrG2fwIrutZi8yB+M7cN+HQ/zrhEJtbllcEhSUceooZNF+6JDE0pwgJbsBWhNod3HCJQqvxkqp5H4VFYuthqkLOcxEghvUGuu851vJIXcNnDRgjhlNJIKk2nocMNyP3BHWtB/9Otwy8TR9R61t6lo0dx++h+UnvjofQ1iPY3NrJuZWQ/3uoNOwKalr1G2sisht5eI26f7JqaxuJNJvzvB8s8OPUeoqB13ncRsc/kamSRZkEFxlWX7jdx/9apKep0V5bpcxC4iOUb5tw7H1+hrMjeayl86LKkH5gO1FhdTaW3lTAtbN3HIH0rWe2imUSwP8p6Edv/rU7mTVie3v7fU4tsgCSd8dDTHSW0bcwLxn+Jf61QfTMtuXKN/ej/wpUn1O0yA4njHXPP596BWXQg1Hw9Y6tmaFhDOedy9CfcVzF74f1OyY74DMg/jTnj+f5115vYJGzPayQv8A34uP0qeOZmH7i+jf/ZmG00mjWFSUDzV1VTiRSh9HUj9RSCMN91gfo4P88V6VNFLMv7/Toph6rg1mzaZpUhxNpzRN7cUrGyxHdHDNA6jJQge6kVEV9j+BzXZP4f00829zPAfqaqT6BdqCyNFdp7j5vzHNKxarRZy4yOhpwOeGGD6ir89iVbCqyP8A3JP6N3/GqTxsrFWBVh1BFBopJnQaZc7CYGPB5X/Crm7hc9Y22n6HpWHkqQQcEdDWnBOJdpJwXGxvY9jTTOWUbO5n3i4guF9JAazz1Na99GWjl45Zf1FY560mbQ2H0ZpKKRVhc80vOT+YpmaePWgDttJu/P0hmHL27iYD/ZPJ/Xd+dZs0g0fxVKGG60vAGx2Of/r5/Sq3h3UFtL5FlP7pso/+63+B5rV8RaW0+kyqBm405sj1aI/4Y/SqM7WlZm5HCjxm2mAmhdQVJ/iXsfYitXQdfn0S9j0zUJGls5f+Peduq/7J9/59a4/wrrAvrf7FO+J4+Y2PeuhvrP8AtDT3iHyzD5oz3Vx0pGV3CVj060KxzOqkbJf3q46Z7/nwfzq+hyT9a4XwVrRv9LjSY4mt2AIPYdCPw5H5V3EZ+dhWbVmdlN3ROKWmg06kWMdc9s+3rXB+R/ZXiJrdv9WWwpPdG6f59q74jNc/4m0try1FxApNxAOg6svcfUdR+NVF6nPXhdXW6OeljMU8sR6qSKrelaEjfbrKK+j5cDbKB6iqbKOo6HkVSOCcbMTPA+tW7AgXUJPQPVMZ5Bp8blWB7g5piiy9r0mZLVc8BC361TjGyb2wKtaoPtFnDcrz5eVf2B7/AJ1XjAkhB6sowfcdjQi5/Fc5rxEjWusx3OPkfn+hqdkW5tWTsw4rX1GwTU7IwMQJF5jY1zVlNJZXBsroFHBwM1cWRJX1RymoWj287Ky96pdDXf6npSXsZZR81cfeaZNbMcqStUa06iaszPdB1HSrWk3hsNQjkJ+XPNV+QcUx07jpUm26sz06XbPAsq4ZSPzFcTruntbTi4QZQ8H3FX/DOuhMWN02FPEbn+RrfvbRJIzHIuYn6H0qtzlV6cjz5XXy/LfJiPKt3Q1r2eor5cdrfNgL/qblecD0PtVXUtHnsJG2AvC3Q/571QSRo8rjK91bpU7HRZTR3drdlABcEEHgTLyr/WtERwyrjoD6ciuAtb14D+4laPPVG5U1rW+stHjzEMfuh4P4VRjKmzZvdDilBZAo/wB3j9K5y6sXtn8twGXsG/zxW4mtRsvMqH6gg1m6lfx3HCDOO9Sxw5kU4p7i1IVW3xn/AJZyHPHsa3dKiF2SbVZYZB95QMrXOwIJbmJHfaruFLHsCetejhFtLm3022Xybfy9x29X5xyaVipFA211EP3lvv8A9pOD+VMItZfllXn0kWuoFnDs5z+dc74ivLPToRuhMsjHCqTwPqe1FyeUqm0s15VEx7EioXtbbr9nH/fWD/OpbbSZrzY7h8soITzCFUH6cn8TWsvhj7NA9xJGuEUthF5/M80xW7GAsMeflguF9w/FPOxRzc3Kf7xDD9RUcl9cPcLBbxoGboqqOnuTU7pcxYE+oWkbn+Buf6UAVzAkv3Z4ZPqm0/mtQSWLJyu5T6g7h+nP6VZMDS9BZXHvGcN+mDULRyRn5WmjI7H94B/Jh+VIZTniMiEXEayr03d/z/xrIudMjkUiPLqOinhl+lb5mdRukUFf+ekZyPx7j8ajkjhlXMi8dpI+CPqKCoyaOXgt0lOGfBqy9hLCm9PmAHOOv1qnGxU5HUVvWUolgB70kaTbjqZkh86HzB35I9x1rCddkhX0OP8ACulng8mY7eEk5Hs3/wBesW9i5DgY7EehpM0pyKeaDQT3oNI1DNOU8803FAoETK+xw/p1HqK73StQW40+C8fDNbYguQf4oj0Y/hj8jXn4ORW14d1FbK92z820o8mYH+4eh/A/oTTIkroq67p03hvxAwhJEZPmQN6r6fh0rvtF1NNUsEuEI80Abx7+tU9S0o65oUlgxDX9g2InPVhjK/gy4H1Fcb4b1d9G1QCXcIWO2VT29aAkueN+qPQtNnGk+KnGdtvdr5g9s8N+Rwa9Ss5vMjjbPJG0/UV5ZrUBNkl7D8z2recuP4oz94flzXY+FtUW7tli35YgMh9eP8B+hpSV0FKVnY7AU8VFG+5Q3rUorM6QxTWFPoIoA5TU7A6RcyahboWsZf8Aj6iA/wBX/tj29fT6VnXVqsY82I77d+QR2ruitcvfaRcaUzT6bC09i3Mlmoy8XqYx/Ev+x1Hb0q4s5atG+xhld2AevY+tN2EHpg1dWGG7hFxYOssTfwA/n/8Aq61ADg7TkEfwtVHE4tbhb3RgYo43RtwQabJayW5821k3RHkA9vY05kRxg8Gmq09rnZ8yHqp5BoBPoxEukLhJV8mQ9A33W+hqLUdNttSi2XKfMPuyDhh/jU5ktblSjYQnqkgyp/GmGynhGbeQhOyON6fgeo/OmMwWh1PRx8yG+tB0dPvqPcd6SO5sNUU7JFD9Cp4I+orYaeWE5lhkjx/HHmRP05H4iqlxBp2pHdNHbzSf89EYK4/Ec1SZLVzn7/w4j5aMbW9ulc7dabdWhIZDt9R0rvBp01uP9GvpAv8AzzuV3j/voYNRyJPtIns9692gO8fl1p6FRnKOm55yVwc46etdJonifyVFpqWXhPCydx9f8auz6LZ3wZoDhh1xwR9QaxLvQ5YASVZlH8S8/pRY15ozVpHatbpLB5kRW4tmHbnH1rGufDlvc5a3cKf7r9Pz61zdpeX2lyB7O5dcHlex/CugtvGME2BqdgN/eWA7T+IouR7OUdYmZc+G723yfJdl9YyGFZ4S4tmwrY9VYY/Q13lvqemXAzbap5Z/uXCY/UVae0a7XmG2u19Y2Vv/AK9Gg+eS3R568jvhjGF9QBxTck12Fzodnk7rea2b2BA/WqD+Hd5/c3aMPRhj+VBSnE58Zb8BW/pfiWVRFb3sbTJGf3UqH95H7c8MPY00eGrs8B4cf7+P6VbtPC7Ruryzx8cgJSE5RaOzstShvrXzI5FcDgsOMH0IPIP1rlvGNqWsjKvJRt34Hitaygt7CR5Q/wA7Jsbn7w96zNfvYjYyQ53SSjaiDkkmkSnsdNol3BKbS6xmMpnAGeCBzj2IxXXfupIcqVZGH4GuC8O6ZNYaLbm+cQKgLEucYyc1NqnjS2trdo7FjKwGPMPSk1c0py5dGYGriHTPGAVSBAW2+y5HH6mruhQx/ZWZ0BuBIyylhk7ga4+/uZbzzJ5mLO7Zrp9Gui8cc5PLBY5vc4+Vv6GqMprqbslrBKMPDG31UVVk08EYUZUdA3OP8KuiRQMk1RuNXjSUwwRtNKPvAdF+ppEFC40/YSxDI397/wCv/jWXNbNA25VxnsOA309DXQrfyuP3sOB7HNV54o5EZkXK/wASf4UFJnByQI/T5TT7NjDIY34DdKI5op+BgP8A3TSshHHWg1fZluVQ6FH6Hof61lXUW4Etxn5W9m7GtCOUMPLc8jpUc6DncOMYbHcev4Ugg7M5qVCjYx/+umdq0LyAhmHVuoI7/wD6xWfUnWndAKcOtNFO7UAGcU9W2sD2PBplKvoaYjuNC1UG3juJW+e2AguSe8RPyP8A8BPX2z61R8caD5cv9rWyYVzi4Ufwt2b8eh9/rWLpd+dPu1mK74xmOaM9HQ8EV3+lzQ3FtJpdwRPGIwYmb/ltAeFP1H3T9AaBfC7op+CNXGoaabKZgbi2GBn+KP8A+t0q1YPLomrNYqWCj99akdWjzyo91P8AT1rjrm3uvBviSKaLc8Od0TH/AJaR91Pv2P4GvQb+0TXtIgurCRfOUefayH+93U+x6H/61BLVnod/pOqR31uJFI3YG9R+jD2P/wBbtWwpz9K8k0LW24uY8xOjFZo2HMT/AMQI9D3H4jvXoum6pFeIACFlAyYyc59we4qJLqawnfR7mzRUaSBhxUgqTUXGaaRT6MZoEYeo+HoLyd7u1kayvW5aaMZWQ/7adG+vB96wrz7RZqRrNkfLHH2u3y6fieq/8CGPeu4K0m38KaZEqcZbnBJapOoeyuo5kPIG4ZpjxXUP3oHH4V0974V0m8dpPs32eZusts3lkn1IHB/EVly+F9Wt/wDkH62SvZLqPP6qR/Kq5jmlhuxiSSqeJYB+PFQ+ZDGcxyTRH/ZatdrPxfCcNbWNyvqtwBn8GT+tAj8Sn72hWxPr58VPmRm6DMkagwP/AB9q3++gz+dNku4Zv9alrL/vJn+ea21s/ErnjSbCP/euF/opqVdJ8RuOf7Mi/wCBs38kFPmQ/YSOXYWZ6WkI942Zf5VCwiU5R7iP6Shv/Qs12H9heID/AMvunj/tm/8AhTH0PxAB/rNOl9juX+amjmQ/YyOMmXzSC7RykdGYGNx/wIZqMtJGMO6unpcfL+Ugyv54rqbjSNSGftOhRzDu1tIpP5ZB/SsuTT7NpfLSW4sbg/8ALK4Urn88GqUkS6bW6OcvNMtJsNIjWzv90yDCt9HHyn8DWTdaBcQ8hd6+4rqrjTtQ03e6RNsb7z254b/eXofxFUor2IHBjCH/AKdyIz+MbZQ/htpiV1scdJatG3KshojluYWzG5/A127rb3J2NDHcMf4UHlTf9+3Pzf8AAWb6VnvodrdyOlnOBMv3oJFKSL9VPP6UFc7W6M618V6xZgBbqXaOz/MP1rRj8aSy8XNjZT+5Taf0qlNoN5AeYnI9QM0LodzMMpbZUd3GKNRc0GaqeJbB/wDWaQyn1inIH60/+2tNccWuoIf9mVG/nXOXGlXdrlmtpUUfxJ8wqqCScCX/AL6FIEovY6s39k/S31Rh6b0X9cUkesJYOZLHTbS2l/573MvnSD/CuXEUrfdKt9DThazf3D+VFgsjTv8AVpL5993dS3b54B+VB+FUS5l5Y9OijoKaLSf+5+oqRYSp+c8+i8mmGgOP3IB7mt3RDgLE33ZIiD+ByP51mRWUs7AsuxB6+lblhbbXDr9xFKg+pNBE2rWJr68kgspHzmRflH+90FWrOzisrTdM4VIxukc9z3Puc1k6vIBvHZGjkf6BxXW6bAlzrul28uDF58krKejFELKD+OD+FJihG9kW7Lw3e3kCzSLFZRsMqkqGSUj1YAgL9OTUk/hKdRuiuoXYeqFM/qRXWySBFLMeO5NZsupxZIG4+4FZ3bOx0qaWp8/yC3ueVZQ3bHFME08HDjen61nxxtIcKpNW1iuYhjcuP7rMKsyaS0Laywzjg4Pp3p+/A2yHI7N6VQdM8vGyH+8vIp8czJhZCGQ8BqLi5RbmM42n7y8qfUVjzx+XKQPun5hW6BnER78xn39Ky7yPMeQMbfmH07j8KTNabKA604elNPFOU9DSNGFLQetHagRIDghvwNbWj38qmO2SQJPCxe0dugJ+8h/2TWEpzwehqQEkdSGB6jsfWmJnprw2fi3QjG48twSORloJR2P9fUVieFdWn8O6nLoWrfu4y/yMx4Rj0Of7rev0PrVHR9bkt7j7aoLSqoW8hX/lsg6SL/tD9a67V9Fs/FmlRz28iC4CZt5+zD+63t/I/jQLyH67o9ylw2saSubwDFxb9rlR/wCzj9aZoutw3cCyW7ttQ8p0eFvT2rM8NeJ5tOuP7D17dDLEdkcsp+76Kx9PRvz45rX17wtJcXB1XRZRbamOXXok/wBe2f0P60EtHYWHiHaFW8Py9p1HH/Ah2+vSukhukkVTuBBGQwOQa8c0jxCJbg2N6hsdSjO1oZOAx9v8P510tpeTWj/6NL5DE5aJxuiY/wC72+q4/GpcSo1WtJHo4YU4GuWs/EsQKpeKbRzwGY7om+j9vo2K3kvFKgnoehHIP41NmbqSZcpahSZG6MD+NSBqQx20UbaTdS5oAaVo2mnbqN1ADdlLsFLu9qM/WgBNgpdg96N1KGoAQp+NQ3FrFcxGKeJJYz1V1DD8jVjNLxQBzNx4b8ol9MnMB/54yZeM/h1X8PyrmtU06xeTytYs/sUzHCzKfkc+zdPwODXpRUGobi1huoHhniSWJxhkdQQR7iqUmjKVJS2PIL7wrf2sZazkW7g6+Wwz+lY7Xh+W3vYshOFjuAWC/wC62dyf8BNelXfhG709jN4fvPKXqbO4JaI/Q9V/UVhXs9hdyrZeItPfTrtuFeTGxz/sydDWilc5pU3ExLXUXhAKXO6P/nndvkfRZgMj6OPxrXhvoZ5Vgfdb3LDKwzDBb3U9HHupNZl/4Pv7HM2my/aIuu3+LH071ix3JjDWsyCIZy0EiboyfXYeh91waaZm4p7nbGAH76gH2qpc6HZXYJlgRj6lefz61lW2p3VuB5E6PGOPIu3LJ9Em+8v0cEe9a9vrtk8qQXayafct92O6AAf/AHXHysPoaLkOm1qjHn8IQcmIyL9Gz+hrPk8OTRH5boD/AH1K133lnAI6Hv601ogeqgii5PNI4JdHvM8XUWP94mrsGkyrzJclvZFH9a6h7GCT70S/lUDaPan+Aj6Madw5mzKWygj5cZx/fbioLvVLa3QqjLI4HCpyBWu2g2b/AHlc/jSw6DYRMGEG4j+8cj8qA9TC03T5tQsr+aYEG4jMaE9/f88Vq6PqO2HRdTbjZIhl9usUn6HP4VtJFjaAAAOgFcvbIo0q5iB+RNSmhH+6zY/maW5pB63PTNSkPEX4n8KqxRDHqfWqtreG9s7W4Y/M8K7vrjn9c1p26ZGaz2Ote9K588p+5twV4Zuh9B3NVHkGTtH/AAJuSaszN/oie4I/WqOeatkQXUcJXU5VyD7VYhuFkbZKACf4sYB+v+NVaMUimkzTCM0Dx5w6dD6elV5ZBMizgD5xuK/7Q4Yf59at6e3nbSeWxtb8On6VlQOVWWP+428D9DTJhuypKnlyMvUDofUdqYPSrN0vCsO3y/h1H9aqHipNlqSg5FFNVu9LjmgQvQ+xqQNnn+IdfcVH14oBIPuP1piLMcjxSJPC2HXkGuk8P+Ijo8/mYLafK376IcmBz/Eo9D6Vy6sBz/CevtUqMYX3D7pGGHYigR6xrWgaf4s06OZJFWcLmC6Tnj0Pqv8AL9K5rSvEOp+EbxdI1+GRrYcRyD5io9VP8S+3UfpWV4a8TSaDciGUs9hIclepjPqP6j+tenz2+neINMWO4jjubaQbkIPT/aU9qBeTKepaNpHi3T45WZXyP3N1CfmX8e49j+lcxM+u+FP3epwHUtMHC3Uf3kHv6fQ/nRceHtc8IzveaDO91ZHl4GGWA91/i+o5rd0Px3pmqAQXZFlcn5Ssh+Rj6Z7fQ0E/kN0vWbXUEDafdpNxzC5w4/D/APXWxb3QhOIvNt37rG20H8Pun8qztW8B6RqbfaLYNYXJ+ZZrb7pPqV6fiMViS2fjTQQQFj1i0XowG5gPp94frQTbsztxrVxGPnO//rpb5/VT/Sl/4SqOP76oPpJIn81rgYfHtvFJ5d/p9xbSDghTnH4HBrWt/GOiXHA1Exn0lUrRZD5po6oeMrX++R9LpP6inHxlaj/lrJ/3+hP9aw49S0+5GY72zkz/ALSGpgsTchIGHtEDS5UHtpGm3jeyXrcS/wDf2L/69QP45tDwn2qT6TH/ANlSqwCr0jQfSKnfaNg5faP93FPlQvasG8XyP/q9JupB6kzH/Co/+Equwcnw/c49t/8A8XUcmrWUX+svoV+sqD+tV/8AhItIBwdUt/8Av8tFkHPI0U8cQQn/AEmz1O19/nI/UEVs6d4vsL7i31GGQ/3ZRtP5jj8xXPQapY3PEGoQSE9lmU/1pt3pVpd/NPaRO3Zwuxx9GFKyGqskehxahGVUyAxhujEgqfow4q2rgjIOR6ivKrZdV0pidL1BpE72t53HoG/xBrf0nxXFJOttcxtp94f+WMvCP/ut0P8AnpScextGsnudyDS1ShvFdfm4I6n0+o7VaDAjIORUGydxxGar3djbX1u9vdwRzwuMMkihgfwNWQaKAOLn8I3uksZfDt5tiHP2C7YtF9Eb7yfqPasy7j07WHWx1myfT9QP3FmwNx/6ZyD5XH059q9HxUF3Y2t/btBdQRzRN95JFDKfwNUpGcqaZ5Ff+C9Qstz2MvnoP4G4asUXM9oHtLqLbGT88E0e+Nvqp/mK9TutB1HSv3mjTefbjrY3Lk4H/TOQ8r9GyPcVn+bpeuBrW8t/KuV4eCddrqfY1akc0qdmcJaXK23NheT6d/sDNxbH6qfmT9a3LfX76OLzL3TPtUA63Wlv5yj3KfeFO1LwLLGWl02Ut38tjhvwPeuXmhvtMuv3kcsM4/iGY3/Pv+tPRkO6+JHaWWv6NqJ222oQeZ/zzkPluPwbFafknGcHHrXnkmrC7ATUra0vf+vuEB/++1wafAulrzay6tpbf9Olz5sY/wCAnmizJ5Ynf+XQE7AVxyXWpYxb+M4mHpd2mG/kaWRNSuFxd+NEWM9VtIsE/kBSsw5V3NnX9eg0SDy0xNqUnywWy8sWPQkdh/OsMW0mmaXpunTvm6km+03BJ+7ht7E/y/Cktzomg7prRHnvGHN1dtz+Hf8ALn3qnbpeeItRMMIciUjzpmGCVH8IH8K+3U00h26Hc+Gi82i2bEEFlLAegLEj+ddZDFsjAqtpempZ20aAYCKFUegFX2ZVIXIzjOM81m2ddONlqfMTbvsrIwIaNsEHtVWrdvMLqJg/M8afP/00j9fqv6j6VAq7Ax4LA7QatkJW0GUYpS3sPqaTd6qPwpDL2kyhL0Kejc1Tmja2vZScYEzKR3/zg0iuY3WReqnNX9UiFzCupQjcpULOo7Hs34/0pk7S9SgV3q0XqNo/mKoHkVcByvB5HT3FQzqMiQfdbr7H/PNBoiBDg4NSioDwalU5FIpodQaKKZIoPcfiPWpY5ABg/d/lUPfilHJyOD6etAFkqMEHlT+la/h/xNeeHpggzNZMctETjHup7H9DWHHJt45x6dxUuAwyuCp7UCPcNJ1e01ezW5tJhIh6joVPoR2NUNb8H6Xrm6VozDcn/lvDwfxHQ15Npup3mi3gurKQqw4ZT0YehHcfyr1nw74qtNcgzGwjuFH7yBjyPceo96CWranK/YfGHhAlrKVr2xU5wo3rj3Q8j8K09N+J9lIRHqllLbuODJB865/3TyP1ruFdX5Bwaz9S8O6Tq2Te2MMrn/loBtf/AL6HNBPqMi1Hw34jjEYubC9z/wAs5sB/ybBqle/Dfw9c5ZbSe0J7wSkD8jkVj3vwt06YlrO+uLc9lkUSAfyNVE8F+LtK50rXwVHRRM6focigNOjJ7n4SW7c2mryL7TQBv1BFZsvwo1mMn7PqFlIPdnQ/yrQ/tD4lad/rLZL1R38qOTP/AHyQaT/hZeuWJxqfh5Vx1OJIv55FGpV2Y7/DTxOvAaB/926/xqFvhv4o72sbf9vCn+tdZafFnSpCBdafdw+pjZZAP5VuWnj7wxeMFXVFhY9riNo/1xj9aQanmTfD3xHH97T3I/2HU/1qnP4T1m3z5llOuPWP/Cve7eWK6iE1tLHPEed8Thx+Yp/NFxXZ83S6ZdRE+ZCwI9VNS2t9qensPsl7PFj+FZDj8jX0HPY2tzkTW0b/AFUViX3gvR70H90Yie68gfgaBXZ5paeO9Tgwl9BFdKO+PLf8xx+ldFaeKNG1iIW8ziMt/wAsbsY59m6fypNR+HFxEpaxnjmX+43B/Xj+Vcff6HNZOY7yylhb1UcH8Oh/CmL3Wen2eoX+klRE0l3ajpEzfvYx/sN/EPY11+la5bX8IlgmGAdrcY2t6Op+6a8C07UdT0sgWF0J4QebeTp+R6fhXU6Z4ltr+5Vld7DU1G3J6sPQg8OvsaGkylJxPbknH8Qx7jpUwbPIriNG8SlnS2uVWOVjhVBykn/XMnof9g8+ma6yCVJV3xNj1+vuKhqxvGaZeBparrKR98Y9x0qUNxUlj6ydY0G01aMGVNsyD5JU4ZfofT2rVBpaBNJqzOEaTVdBfy7tDdWo4Eq9QPf0q/He6dqsPlSeXID/AMs5VH9a6iSJJFIYAg9a57UfCVtcEyWrGCT/AGen5Val3MXTkttTEv8AwPp10CbctAT/AAj5l/I/0rnbr4fX0RLQFHA/uNj9DW9OniHQyT5L3MI7xfNx9OtFr49s87LpTGwODkYI/Cqu+hjaPXQ5B/Dmq25xJbSMKauh3jnH2S4H0Nel2/ivRpxxexD2Y1b/ALd0kDd9rgx/vUczH7NdGee2Hgie5cNJbug7ljXe6RodppFuFjjUHqTVS78a6PbHZHcefKeFjhG5ifYVc0+C+1QC51FPs8B5S1zkn3c9/p09c0m31KhCKemrLLPc3vyWr+TD/FcEZJ9kH/sx49M06LSLKE7vIDyZyZZDukJ9dx5/KtAKAMAcCgioOix8kQzPbypLG210O5W9D/hWlMiOqXMK7YJui5/1bDqv4Z49iKdcRxXkT39nEiSoM3NsFyo/20H931HaqdjdJAzQz5NrNgPjkoezj3H6gkVoZ77C0VLcwPbztG+CQAcqchlPRh7GohQSKOD04qxZ3cllJ2aNuCrfdYHqp9j+lVxTgSOmMHqDQJq5PfaesUX22xJa0J+ZT96E+h/xqgCGBB+43X2PrWrp92La4DIQpYbWR+UkX0PpTdV0pbYC8tATauSCh6xN1Kn8OQe4+lAJ62ZhSIQxU9RSx+lTSrvTcOo/lUA4IpG17olooopksKXrSUtAhevXr2NPRiGweD+hpq4JwT+NOZCnyuMigCcYcejU1GmtZ0ngkaKZDlXQ4INRhipG45Xs1TbuMHBB70hbHc6D4/V9tvq+IpOguFHyN/vD+H6jj6V3cF+rKrBgykZBByCPY14O8XdfyrS0XxFe6K4WNjLa5+aBjwPp6GmQ4dYnuSTo46/rUufSuR03V4NTtFurOXcp4ZT1Q+hHY1qQ6g64DH86LGPPbRm1kd1p2QRgk49D0qpFeo/DcGrIKnkGkUmmUrrQdIv8/adOtJSe5iAP5jBrn9Q+Gmh3QJt/Ps37eW+9fyb/ABrr80ok20xrQ8nuPh/4h0SY3OjXZmI6NbSGKT8sjP5mox4t8daafKuWuWK9rmzDH89v9a9c82Jv4gD9aZJLFGuWmVV93xQVzHli/EHxc3SCA/8Abkanj+IXidOZrC0ce9vIn9a9BN/A3+qeSU/9M1LD8+lVbjU1gGZV8pfWadE/rQTzHLW/xNcEC+0dl9Wgm/owH862YPFnh7WE8mS4SMtx5V2mz9Tx+tJLrWlz/JJLYSezXMR/nWfPouh6mpK2YUn+O3IYf+OE0Bfuh2q+DLC7Hm237pjyCDx+BrjNU0K9sfkuYDcwr0cD519wa6KLRtS0kltE1JmjHJgc7l/FT0/Q1bg8SRSH7LrVt9kkPG/kxE/Xqv48e9Aehyena1cWke2Um+sujEjLoP8AaHevQ9A8VDykcTNc22B84O6WMeh/vj6/MPU9K53WPDKO32uyby5CMiROc/UfxD3rmFFzZXu6Mi0vfb/VTf8A16Y0+qPoay1GC7jjZJEIkGUZTlXHsf6dauhccqdv8q8V0HxSwnaDAgujzLaSn93N7qex9xXo2jeIlu12IWkZfv28hxKn0/vCocexvGp0Z0wc9GGKeDVe3uYblN0ThvUdCPqKeysOUOD6HpUGtyfNLVQ3Plf66NkH94Dcv6dPxqaOVJU3xurr6qcigCQqGGCM1k6l4b0rVR/pllFI39/GGH4jmtUNS5oE0nucFd/CvSJSTBc3UPtuDAfmKpp8JbMNmTUrll9AqivSCaaWquZmfso9jn9F8HaRoZD21uDL/wA9X+Zv/rVukhRUVzdw20LSzSpHGoyWY4ArItLqXxD+9tneLTAcecPla49dnov+11Pb1paspJR0RpTajaQuUedQ4/hHJ/Ic1CNb04uEa8jRj0EmUz/31irsNvDaxiOCNY1HZRj/APXSyIkqFJFDoequMg/gaLIep8mwTzWc6zRMQyHIP+f5VavLaK4tjqFmoEZOJoh/yyY9x/snt6dKgZMcEfgadZ3L2Fz5qrujYFZIz0dT1BrQxv1Rbsc39g1n1urZTLbH+8nV4/8A2YfjVYAOgdeh/SpbhDpd5b39mxa3ZhJC3p6qf5VNfwxw32+H/j2ulE0XtnqKYPuiByAdigBR7daYCMHill7H1FR5pCQ481qaPckzmzmbMM67Mnsf4T+B/qO9ZYqRCyESqeUYGgGhl7bmzusbcI2cD0IOGX8D+mKoyJtY46dq6jWbcXduZYxkyJ56f7wGGH4jH5VzZ+eMHuKGVCV0RjpSjoRTcYNOoLYDmnYpFHFOAoIYmKsQssg8qQ4z91vSoaQii4mPkjaByjjihWMZweVNXLdlu4vs8v3x9xu9UpEaCRo5B06/4igE76EwPGRypprxbvmXrUasUPXIPQ+tTqQ3I4NAx2m6ldaTeC5tH2t0dD91x6EV6TpGt2utW3mQHZMo/eQsfmT/ABHvXmbxh/8AZb1pIJ57G5SeCRopkOVdf5e49qCJwU0ewRSlTjNaVvcMOhrjdF16PWIscR3iDLw54b3X1Ht1FblteANhuKZyNODszpUfeMg4NIwkPAYj6CqcN0hUc4qdrpVXJakaJ3QjWStzK5/OsbW9Z0bw7CJLhVaZuY4gNzt74PQe5qPxJ4kj0TTDcsFaeXK20Lfxn+8f9kV5HLPPfXEl5eStLK5yzt1Y/wCHtQaQgmrnQap421jUyfLl+w238McJy5Hux/piueZ5LiQtgu/dn+dvzNOSIyHfJwvpT/Mz8sYAX17UGvoM8iY9SB9SKRYZ4mDxnDDoUYA1NsJ5Lt/KlCHs5oJuaNp4r1exKpcOLqMfwXI3EfR/vD866az8Q6TriC3uSIJm4EV0QVY/7Mn/AMV+dcQdwGDyPSo2hR84G0+nagHFM9BW1v8AQ3IsS0tt1azmPQeqH/DipHi07xBbSCNcSL/rIWGHjP0/qK5DSfEt9pIW3nH2uyH/ACxkblPdG6qfbpXWLHY63CNQ065dZov+WqDbLCfR17j9DQZyi0c3qWmPbr5V4rSQA/u7hfvJ+NPttautO8tb8vcW6/6q9hP7yP6+oro0vg8ostVjjiuH4SUf6m4+no3tWbf6FJbs72fAP34H5BoGpdGdXpPi1poklnb7bD0F5bHEq/7w7/jXZ6drv2qIPBIl9F3MeFlX6oev4V4ALeW2ujLYSvZXY6x5wG/ofxrWsfFnkXKrqsMlncjpdW4Iz9R/+uiyZpGTWx7/AG17bXeRDIC6/eQ8Mv1B5qO50q0umLsjxSn/AJawSGNx+KkfrXBWHiVrmBJJ1i1KAfduLdsSL+VdLp+tC5UfYr+O4x1huvlcf8CH9QalxNFUT3LL6Xrdv/x46/5ijpHqFssv/j6bW/nUD3XjC34bS9IvAP4obx4ifwdT/OtH+11i/wCPy2nt/wDbI3p/30vH54q5BeW9yu6GeOQeqsDU6l3Rzb634qHH/CIlj6rqERFV5Lvxze/Jb6Np2ng/8tLm78wj/gKiuzyDSZouFn3OOtfA8t5cJdeJtVl1R1OVtlXy4FP+71b8a65VWNFRFCqowqgYAHoKcWphai9wUUthSaTOaz7rVILeUwJuuLrtbw4Lf8C7KPdsVlXSvdOV1C4lZgM/ZLNyqIP9phgsfckD0FNITkkeNz6QsoPy81h3umTWuSVJT19K7xUB6iiWzSVSGUEH1rWx50arTOC02ZHD6dcH9xP9w/3H7EVKkcsmlXFnIP8ASdOk8xB6ofvD+tLr2lHT5xJGD5Tngj+E1NFdBzaaqcZB+y3Y+v3WNSdSd1dGe2HiyvI6j6VDVue3NneS2x+4DuT3U1WdCrEfkaGCAGlV8H2pAMimkj1oKOjspN+kRMeTby8/7p4P6EVzdxD9lv54D0ViB9O1bOiv5tneQnuuR+X/ANaqOtri9imH/LWFW/EcH+VMmGjaMxlwSPT+VIDUko5Vu3Q1HjBpGu44Hn60/pUftUg5HuKRLFFLSUUEgMqwYHBHOasTyC6hDEATJ19xUFIeKYeZGrbeCMqe1PBI5HzL/Kmt600EqeDSLLSTA8E/gafjIxjI9DVTzARhlp6OR91/wNMViZUaKRZIZGjdTlTnBB9jXRWXi+4hUJqVp9oxx50ZCP8Aj2P6VzomIHzIDT1ljP8AeWgmSUtzt4vGGjgZL30f+z5IP6hqZc+PrGJCLKyuLmX+FrkhUB/3RkmuO3If4x+IFGVH8f8A3zQQqcE9g1C7vNWvmvNQlLyNwB0wPQDsKjC8jI+i07IB+UY9zSFgnTljQaCud/yDp/F7+1IGJO2Jc+56CkRd/GeP4jUcs5Pyx/Kg7+tAichR/rZj9BxTd1t/z0f86pcepNJj2P50DsXwYz9y4x7NTiGA5UMPVazfxP405ZHQ5RiPoaLhYvghwcEGpLW6uNPukurOZ4Z06Ovp6H1Hsaprcq5AmXDdnXg1MSwXJIdD0df60Bsd5purWPiW3NncwxR3bD5rY/cl/wBqM9j7flUiy3Ojjy7rzLrTl4EpGZbf2b1HvXnvcFSQQQQQcEH1BrtdB8WpdlLLWZAk33Yrwjh/9mT/ABoM5Q7Gpd6XaalbrKpSSNhlJU5rnL/Tbi1Xy7iEXNv2J6j6GujuNJutMne40oiMn5pLVuY5Pcen1FS2WpWmpEwOv2e6/it5R1+nqPcUzPVbHAxWc1tN9o0e7eKQdU3bW+nofxrTt/GM8Ugi1mw8x1/5bQ/u5B+HQ/hiug1Hw3DMS6DyX7H+E/j2/GsC906+tV2XVst1D2z1/A0Gimnudjo3jPzNq6frMch/597v5H+nPX9a3G1y3Y7tR0gI5/5axjr+Iwa8Zl0+xnOI5mt5P+ec4yPz61LA2v6QN1pdXCxf9M5N6H8DkfpSK06M9tt9R02YAW+o3sB/uifdj8HBq6JJMZTX5wP+mlup/wAK8Ri8Zako23dhZXXqTEY2/NCP5Vdj8cW6/e0q5hP/AEwvSP5rSsP3j2EvI33vEb/8At0z/M014bZkJmutVvVA5DyeTH+JAQfma8n/AOE9gx/q9W+n20f4VUn8ZCU5g0nzH7Pd3DS4/DinZBr2PUbjW7O1ha3sUTaOTBYYwP8AflxtH4ZPvXDa14xt8NBJILjB/wCPS0O2FT/tt1c/XP0rlbu91jWI83lz5dr/AM81/dxD8B1/WptP0rcy+RGWPaR1/wDQV/qefagTa6l7+1LzRZlg1JftEB4juUHJHuPWty01OzvEzDOje2eaxdLmj13Q/IuTucfIx7hh0P4jn6g1y93aTafdtE+VYdGHGR6imYumpOz0Z2XiIRSadKGx0yPrXIaS6NcSWUxxDeJ5R9m/hP51A9xNIm15XYehOahOQQQcEcg0ma04cqsbojk1HTzGwP8AaNiSrL3df8j8x71RRklj9R/Krkty+LfXLYZcYjukHc//AF/8KvXGkJqKLqGmuAJfmZD0z6+x9aAehgSjHAqBsjrXT2vhS/nfMpjjX161YvvBlzHbM8E4mIGShXB/ChgppGN4ecC/dD0dMVHra/6PZN6K6fkRUOlSG31eMOCCCVIPar2vpixQj+C4dfzGf6U+g9pmJjdHj0qPt7ipU6/WmEYakaIZSg/nQRg+9JQDJetJTQ2OtOHNBI6kPNGaQmkIY1J1pTSUFIMD1o207gDJ/Kmgk9KYxRuXocfjThI49D9RTcHuaPxoAkEx/uD9acJm7KKj59QacM9z+VITH73PoKTd2X8TSAEj0X1qxbwCRtzfJEgyT/nvTE2En7q3VBwz/wAqgWLdgnp2FOnm8yUvjGeFHotEburjOcGgFdInSDtsP5VN9nQD5i2fSmRTOz8mrBu7ccMu498UyHcrNHCepI/AGoXtoz911/EEVe3WM3VSp+pprafE4zFIfzpWEpWMx7Z1GR0/MfnTI5ZIGyOPUHoavPZzRHcrH6ionXIxNHjP8S0WNFK4qGO4GYvlfun+FMboQwyOh4/nUEkLQkOrcdmFWYp1ucK5CTdm7N7GgLdTpvDni9tPRLHUy81h/wAs5Ry8H+K/55rsr7SbLVbRLkMksTjdHcxnj6nHQ+//AOqvJXiZGYbcMOqmtPQfEmoeHbgvaMHgY5ltpD8jfT+6fcfrRsTKClqjtRcaxoh2Sob+17ZP7wD2PRvxq/Z6npep/JBP5M38UMg2n/vk8H8Kt6LrGj+J4SLGYW91jMlnMP5DuPdfyqDVfCsM4zLb7SOjjnH0Yf1p3MpRa3RXvvD1vcAh7cfWMf8Asp/pWBL4WaF82l0Y2/u7ih/I1ppY63poxZ35kiHSO4G4fnU661qSDbeaSJV7tCwYflTEm1sc5NpGqof3iQTj/prGM/mKrNp12PvaTEf9yRh/WuvTVdJm4ltpbdv7rApUnm6Q/wB2eUe2+kPmZxi6fcE8aP8AnI3+NTJpl7n/AFFpaj+8Rub9c11xFgR8hlk9jJgUu+3tl3lYoh6jk/mf6UC52Ydp4eDOJZ3eZ+zydPwFbUcUVoyQQRNLcuMJGuNx/oo96txWl9eAsq/ZYOpmmHzY9Qp5/E4H1rltc8W2mmRS6f4fbzLiTie/J3E/Q9z+g7UXGoyluchouq/YtVZ5eILgkSAfw5OQR9D/AFrtL2wg1KHypwN45V16j3HtXmprsvC+rC6gFjM+J4h+7Yn7y+n4Uka1ofaRjajpVzpshEq5jJ+WRehrPIr0xkSeJopUDKRhlPeuI1vSv7Nux5eTbycxk9vUU2TCd9GQaXeJaXDRz82s42Sg9B6H8K2dIkfRda/s6Zs21wcxMT0Pb8/8K5kjIrXgP9raS1qSftdqN0R7so/w6flSLaueoWyh6fMGAO0VleGNT/tLTopmP7zbtkH+2OD+fX8a2JJNkqrtyGOKDC1tzzLxXaix16K7RcJP8x7fMOD/AENP1lfN0u4Ycj93MP5Guj8d2Am0Q3CL81u4f/gJ4P8AOudsiL7SEQnJKNA39KEaJ6JnNIeB9KcwyfrUSgrlWGGU4IqXqtBsyM9MGmn9akIyuajoAKAaKSgVh+6jNMzQTQKw4mm0UtA0L/CKO2BQOn40ooGAWpVhJGSMD1NPt492XYZA6D1qYAM7Mxyq0Etka24I4DH6DFPEDdo8/XmmvduSdgVR6nmozJIw+Z2P6CgWpY8pEOZW/DNRz3G9RGoAQdEHf61AT6UgBPT86B2FXg7jyxpyZZmdjwvJNIq9l69z2FSxRPLIsMKGRz91QP1NANiDIHTk9B6VatdPluDkISM8/wD6604tMs9NQS6nODK3IiXkn8Kiutauimyws3iQDAdk5/DsKpLuZubekSymjwwoGuHjQe//ANenr/ZsR+WaLP1rk7h55ZC1wzs5/vmoNue1F7D9k3uzs2jtZPuTID7GqdxZbOoGD37GuZXcnKsVPscVag1K7t+BJuXurcg0XQeya2ZcktzGSuOD2NZ1xbmI71HyH9DWrDqltOAkyeWfQnj8DU72oZCyYkjI5FKw1Jx3Mu2u0lAguTgjhJe6+x9RT54GRtrjDdiOhHr7iql5aNbtkfNE33W/oaltL8Igt7kFof4WHVPpSKa0vEbh45VdGaOVTlXU4IPse1djonxO1fS9sGoxrqEI43E7JQPr0P4j8a5i4gMShiRJC33ZB0P19DVYpkYI3D07igaaaPZ7Dxt4S1lR5lwtnOeqXI8o/wDfQ+U/nWwulafervtrrzFPQoyyD8xXz2Y+PlOR6d6agMbbkJRvVTg/pQJxiz6Cfw2e10B7MpFQt4XZjnz4Prgf4V4lDrWr24HkarfRgdluH/xqz/wlPiLGP7c1D/v+aLk+zR7MPDEaIWnvWVB1MYCgfjgYrBv/ABP4U8OM32MC/vhxmJvMIPvIchfw/KvKrq+vr7/j8vbm4/67Ssw/ImoAvHoKBqKRu694v1bxBuilkEFoT/x7wkhT/vHq348e1YqJsXcfwpyIDyelK+evr0pDuUadFI8MqSxMVkQ5Vh2qTarjKkH2JwaaY8HHIPoaZpc77RdYTVbYZwtzGPnX196n1m0F/pcqAfOo3r9RXAWlzLY3SXEJw6Hkeo9K9HsLuO9to5kIIcAn8aEzlqQ5XdHnNS2t01ldxXCdUOSPUdxU2q2/2TVLiEfdDZH0NU6DVao7jQZ107xI1ujf6LfoJ4D23dx+X8q7dhkq1eWWUslzoy+Sf9N02TzofUp1x/OvS9Jv4dT0+G5iPySqGHse4/A0ETXUde2yXtrNbSfdkQqfoRivLdF3295dabMcOMj/AIEpr1iXKOp9K828ZWjaT4nj1CIYjuQJOP7w4Yf59aAhrdGJqsHlag0gGEmG/Ho3Rh+f86qA4rd1SJbq1LR88ebHj6cj8v5Vgg7lDCg0Tuhejexpki4ORT+o2ntSr8wKnrQO5DRSuu04pP1oGJijFL2ooASloooAUdKXtQKF5Ye5oA0Yl2qo9ABTI+bZx7ZqXo2P9oVFbsBgHoRg0zIqnIbFObgAevJpZkKOVPVTSP0U+9IsbjP0p6IXOOgHWgLk4FTCNmdII/vv+nqTQkJsSGCS5mSC3TcXOFHr7n2Fbk9xbeHrcwwnfdN9+TuT7U7S1i0/SLjUyMFhsiJ6hR0/PrXLTTPczNLJ95v0HpV2sQlzvXYklv7mZ2feY93XaeT9T1NQEljlmLH1JzTTRuqWzdIXFFN3E0c0hj8UhFAVv7ppeR1U0CuMK1LbXk9o4MbnH909KZxQVBoG7Pc2orq21BSpUJKww0bH5X+noazL7T3tcumWhzjJHKn0aqpUqcj9K07LUzkRz4ORty3Rh6N/jT3M7ODvHYpWd/JaEoQJIW4aNuQRV9rMTwm409jJGBloCcsn09RTNQ0pVjN1ZgtDn5oz1jPpWbb3EtrKssLlWHoaPULKXvRLIdW6/K1KRnrg1sQfYdeQh8QXo/iX+P6jvWfeaXeWLNuTei9WTkD6jqKVhKSbt1K2F+lKB6U1XyPT9aduPoDQMXbntTsAdaQMcYCn86VUYnLDAoAlTHBbp6UnDybjwgpSMYLcDsPWm/fkWPOM8sfQUEruUmQg5Xg9xT0fI2sMjuD/AErrtR0221exF9ZY8xl3BgMb/UEetccwKtnGCDzQXF3HlcHHXuD6iul8J3LCG4hzxGwZfo3X9QK5onIHtXTeF7cCzmm/ikl2fgq5/rQiZ/DqQ+K4wuqJKo4kjBrCHNdLrkf2rTredeWjGD/KubxQxQd4lrTL06ffxz/wdHHqprq9K1BfDmrm2kbGl3h8yF88RMeo+n/1q4gjiug0iaHVtPbR7xtrrzBIeq//AKv5GgbR6rgTJjvWD4s0g6t4emRFzc2376L3x1H4jP6VheHPEM2jXQ0bWTtRTtimY8KOwJ7qex7fy9Ax0deo6+9IjZnjelXPm2Jjzl4DuX3Ws+5iFtevGPuMcr9DW1rth/wj/i2REGLWc+ZH6bG6j8DkVR1aAiNJB1jO0/TtT6F7S9TPIwc+lI2Qdwp33lB74oAyMUDHYWZPQ1XZCp5qRW8tueh61YKrKAG69moDYpD2pR7jFOkiaM4I/Gm5xQUGB6ilA9KBRmgAPpUtuhaZfSowpJq9CnlR7iPmPCigmTJVxncegJaqSHG3P0q3KfKg2/xNx+HeqTGgmKLsiC4gDj76cH3FVGHyH2qxBJtKnseGqOZNsjKfegI6Ow6ED5mPRRmp4I2Fk8v/AC2upPIjPoOrH+QqvEcwSfQVsafGJL7RIccCMyEe5Y/4CqQpOw/xWwtbGx02PhcZYew4FcqTx9TW/wCLZN+ule0cYH8654nAFDKpL3UKTSY9aB6mngc5qbGtxYoWkkVERmdjhVUZJNdNB4ds7CFZ9cvBDnpBGw3fief0/OoIXXw9arJtV9TnTKhhkQoe/wBT/n3xppJbiZpp5GkkbksxyTVWsZNuXodEbzwknyrp9xJ/tfN/VqjaXwrLwIr+3PqhJx+BJrDihaRwqgkmtq00FXAMxJP90HFUk2ZylGO7I20zSLj/AI9NchDHol5CU/8AHhUE/hvUY0Mkdt9oj/56WjiUfkOa2x4ZtHHMZH0Y1GPCphbzLO7mgcdCD/hinyshYiPc5MxEMVz8w6qeCPwNMaI9SpFddcwa2q7by3ttWiHTzVzIPoww36msmSKwZtqtcabN/wA8rgGSP/voDcPxBqWjaNRPYp2N/LbuAMNxtKk8MPT/AAqS+0+OaI3ljzGfvx91P0ptzZPEA00YVW+7NGwaNv8AgQ4/rTYZ5rSYMCMng5+649D7+9IrziZqO8UgkjYq46EV12ka9DfBLe8CrcLwrdN30PY+1Yt1aRXKNdWgxj/Wwn7yH/CswrjrU7A1GotTt7nR7adi3kqxPUr8rfjjg/lVFtBQN8jTL7Eg/wBKoaf4gntQEuQ00Y6OD86/410lrrlpcgbZ43P91+GFUrHPJVIFGLw6HGTIwHqTn9BWNeRy2F49vKiKy915yOxGa7O61a3s7GS4IVio4VepJ6VwdzdTX149xINzs2cDt6ChlUuaV+YXdvcu3QDvUlooLmSXhfvNn09KgI42Z92NWFUCPdIdqDkA9zUmz2saHhG/8u7ewkP7uf5kz2cf4j+VUvENr9l1OUAYWT5x/Wt/x34dbQNYTU7JdlrO+9do4ik6kfQ9R+NQa4i6vosOqQD5gMuo7HuKQ3pK5yoORXUeFbgGCe2/jjkEyj1BGDXKqeKuWF5JYXkdzHyUPK/3h3FMJxurHTXxNjdeXJzZ3PKN/db0/GsyfSiCTFyO1dPcQQatpnlKQY5l3wv6Hr/n8a5O11OezYwTrvCEqR3U0zCN/s7kFxZSQRb2qmrvDKssbFXQ5Uj1q/f6j9rwqKVQevU1QPJpGsb21OvRrXxLpQ8wBLiLjcOTGf6qa1vCGuT2d1/wj+qHEi8W0hOdw/u57j0/KuC06/fTb1Z0BK9JE/vLXV6tZrqWnpdWjkzwr5sLr1ZeuP6/UU9yX7rt0Nv4haV9r0Fb2Nf3tk2447xtwfyOD+dcQjC8sBu6su0/UV6T4f1WLxJ4fzcAM5UwXSe5GCfxBzXmUdvJpupXemT/AH4ZCv1x3/EYNJD6ehmx5GVPVTzTsYPHbmpLtPLu93Z+fx70xfmGO4oKGSL09D0pI5CnBGV9KlUBhtP4VCwKkg9aA8i4rK6Yb5k/ven1phs93MbAiq0bMjZViDVlJ1zloyD6ocfpQLVbDDZyD+A/hTlspD1wo9zU4niI/wBbIPqtO823x8zyN7dKBXY1Io4jgfvH9AKlIEQ8yU/N2A7VE12qjbDGFHrVV3Zzljk0gs2OkkaWTcfoB6VG3anKPkJ9KTq3sKCkPj5ytTXB3PE395AaiiGCWPQDJqSb5ViHdYxn+dUiepHEcQyH/ZA/Wug0hc+ItPX+5Zg/oT/WsALiAqOruEFdFpHPi+VR0igKfkFFNEVNn8zJ8TnOvT/7o/rWGecfStvxJzrs5/CsQ8YoZrT+FB7VqaNBHJdmacZt7WMzyj1A6D8SQKyh1rXgPleH7gr1uLhYv+AoNxH5lfyoQ57FaeeW7uZLidsySNuY0795PIoLM7YCjJzgDgD6VEorT0uEFzKw4XpTSuyJPlRqadYLAoJHzkZJParL6vbWzbY0MhHUjgVVurhtotovvN94+lWrDSwgDMqg+sn+FaehxPvIs2utpKwD2syj1UZFbcMkcqgo2fbGDVaK1hwMz5/3cCraW0XYk++aZjJroSeWD2FV7nT4LpCk8SSL6MM1dRMdCfxp22gnY4288LyW5eTS5zGW+9C/KP7c/wBc1zMw8qZoJ4fs0o+9G33D9PT9R9K9WaMGsvVdGtdTg8udMMPuSL95T7f4VMonRTxLWkjzkLJBIskLMpXoR1A/qKc6w3vZYZz2/gf6HsfapNQsbzRLnyZfmjPMb/wsPb0NQq0NyCD8jn8jWex3J31RVlgkgcq6kGo8A9QK0RLNbjbKomh9G5x9D1qRY9OuOQJYj6DDf/XpWHzPqZ6u6/clkA9KXzXc7S7sfTNaBsbFeWuZiPRYmz/KkM8UA2WUBRj/AMtZcFvwHQfjmgL32IhELcBpl+c8rEP5moZpjnc5y3ZR0FNll2E87pDySTn86ZFEGRp5iREDjjq59B/U9qLDS6nvup6daa3pMlpIwktblMxyKc47hgfbrXklg83h3WLnRdSUCJ22nP3QezD2Ir2OaAabc/KMWFw/QdIJSe3orH8m+tcz448MHW7D7Rbxj+0bVTtAH+tTuv17j8qhFSR5brWlNpd8QATbycxt/T6iqANdNpV5Fq9kdKv8lwP3bn73H9RWBfWE+m3TQTD3Vx0ceoqiU+jOj8K3heCewY/NH+9i9vUf59aoeI7cRaqZkGEuFEg+vQ/rWbpt8dP1CG6HIRvmHqp6j8q63XLMXenl4vmaE+YhH8SHrQZv3Z37nIpC8n3RSyQtGcMMVpWrokWTgAVWvZxK+AMBf1osCk27FEiul8LX5XdZufufPHn07j/PrXOVJa3DWl3FcL1Rsn3Hei5UldWOx0uf/hHPGbW5O2yvwMegz90/g2R9DSfEDTWtr+21iJflkxFNj+8Pun8RkfhTPE0AudHtbyPrE23cP7p5H6gfnXQ2U9v4r8KmG4I3SJ5cvqkg6N+eDTfcmL0ued3KC4g3LyfvLVBWwAw/GtAQzWF5Np90u2aFsfX3Ht3FVbmHypdwH7tzz7Gkyl2EIz8wpSBKvo1MVinX7p707HdeaAImjKnkUBanEmeGApSqHsRQBBz70lT+UD/F+lHkoOr/AJCkO5BT0jLcngU8eWvQZ+tBLN7CgQ1z0A6DpSBe1Lj06epp6ISM52p/ePU/Sgew+NQTt/hBy/8AhRMdzsSRkHJ+vpTiwiUKo2+g9Pc+9MQbmBxwD09TVC8y1YwiTUbKJvuqxkf6Dk1oeFXM+v3Ex6tGzfmwqjbN5Nlf3xP3l+yw+5P3jV3wniF767fiOOMDP45/pVIyn8L+4zdebdrE7f7ZFY7davX0hmuHc9ScmqTjmkzaGisMHWtUkf2Hbj0upM/iqVkjg1ownzNIuE7xTJJ+BBU/rihDmtiNRkgVtWmIoMnp941jR8sK2YiCIlPQsM/Qc1UTCrtYv2zRWg82XBmfkk9quxarbMcNzXOTymWY/Wt/SNHBCyzDJP8AD6VVznnFJXZqwC0uhkR/iOKtrZFOYZnX2anxpFCoAwKsJLH60zBkcck0fEqZH95asoyyLlSDTlZD0NBhUnI4PqKRIhX0ppGaX50+8Mj1FKNrDKkUwM3UtNg1G1e3nTKt0PcH1Hoa801bSbjSLrypQSjcxyAcMP8AH2r1wqD1GKp6hpsF/bNBcRh42/Q+oPY1LVzejWcHZ7Hk0d26DDDctTCW2k5ZcGrut+G7rSWMgBlte0qj7vsw7fyrFxUWPQTjJXReL2yjjJ9qgkuNwwg2iohG7dEJ+nNO8ll5l+Qenc/hSGkhsaByWckRr94jqfYe5rvfDnhcP5WoarENwH7i1P3Y17Fh3PfH4mo/CnhdiY9S1CLai828Df8AobV24HNUkctev9mJ10sMc8LxSoHjdSrqehBrGjMltc/2fcMWmVS1vK3/AC3jHb/eXv8Age9b2Kp6lpy6jaGEuYpVYPDMv3onHRh/UdxWCO9nknxB8Pf2fdprdipSGZ/3oTjy5OzD0z/P61UtJrfxLpjQXIAuYvvY6/7w/rXpiCPXNPu9O1GERzcwXcQ/gfHDL/snhga8TuYrvw14glhPE1rIVPo6/wCBFWjKUbla/sZtPuTDMMjqrjowrpfDOpefbCzkOZYR+7z/ABJ6fhWnc2trrmlpIozHIu5GHVT/AIjp71xMsVzpF+DnbJGco46MKZF+dW6mvrWnm0k82IH7PIcj/ZPpWPXa2l3b6vpxcqCrDbNH/dPrXM6npkmnT4+/C33H/ofehkwl0Zn0EU7FJig0Ov0Z/wC0/Cl1Zk5kiUqPw5X+WKx9C1mTRL8vgtbycSoP5j3FS+FL0WureS5wlwu3n+8OR/UVV1a0NnqU8OMANlf908imQlq0dXrumQeIbKO+sZEN0g/dyA8OP7p/p6VxwYtvt7iMpKvDxsMEU6y1C706TfbSlQfvKeVb6itOfUtO1dV/tCF7a4HC3EXOP64/OkFmjAkiMJ5+aP19PrTQpHKH8DWtLYTxqXhZLyH/AJ6QckD3XrVDyo3yY2we4H+FBSZDvP8AElKGT/aH608xyDsGpNp7x0gAFf736Ubo/Vj9BijZ/wBM6Xbjk4AoGN3D+FPxPNKqO3J4HqelTx20jIHwsaH+OTgH6ev4U5jBH/emb1bgflTsK5FHFuOVG7H8TcKKHkVT8rb3/vnoPpSSSSTfePHZR0FIqgHPDMO3YfWgVu43YcZY8nnnsPU1JHHJK8cUK5kkO2MfzJoIGwySE7M9O7mpp2ayRoQM30w2yY/5Yqf4B/tHv6dPWqQXI72VZZILG0y8MA2Jj/lo5+834n9K0rp00zTF06JgZCd9ww/vdl/CqcONNQlCDeEYLdoh6D/aqjLIWPWmTy39CNjuJJqJ1zUoHFNIpGiKzCrumOv2kwOcJcIYiT2J+6fzAqs60wcUti3qi4m5WKsMMpwR6GtOKTiM+hxVK6bzTFer0mGJB6SDr+fB/GnRP8pUH6Va0MZq6uW9NjE2pKrdF5ruov3UPFcNpL7dZX0dTiu4B3Q1S2OSt8Q63iad8nmtiGyQAZGTUWnwhYwa1FGBSbMUQC3UfwikMA7cfSrVIcUXHZFMow96haJWORw361oFc1E8Qai5LRS/eIMEbhSq6HjO0+hqcqy9eRTSqMOQD9aYiJoVYEEcHg9wa52/8FabeMXhD2kh/wCeXKn/AICf6YrpvLVehI/GlzjqfzpFRlKOsWcEfh7Nu+XUYdvqYmB/nW5pPg7TdNdZpc3U6nIMigIp9Qvf8c10JYe1HXoKLFutUatcDknJPNHQc0hIX3PpTljLHLflTMzr4Zop4UmhdXjcblZTkEfWn1w2o+Dbyyhkk8M6tdae4yy2okJhY+gB+7/KuIsvib4kspDHdNDdbDhlljweOoyuK5uW+x7XN3PVtatTBPHrEC/vIV8u5Qf8tYc/zXqPxFebfFXTAl5Z6pGAVmTynYdyOVP5Gu/8M+LrDxPZlof3dwgxNbsclf8AFT61W8WaF/a3hi5sYlzLABJB+HQflxVLTcl90eZ+Cr3e02myN94ebF7EdR/X8K2dV0hL+BlZPnHI9QfUV5/bXE1hex3ERKTQvkZ9R1Br1TSdY0zXrdSjiO5A+eEnDKfb1HuKZjOOt0edQS3Xh3UwWBMZOGHZx/jXYKbW8tBuxJaTDKn+7WrqnhuHUoGVsFscOByK5G1ju/Dd79hvx/okx/dy/wAOf6e4pomS5tepU1TSJdPlzjfC33XFZhU13QdP+PW5AeCThCe3tXNarprafcbeWiblG9qVhwn0ZlKSjBlJVgcgjsa6ecr4h01LiID7dANssY6uPb+Y/EVzjJnkc063nmtJ1mgkKOO4oKavqhCpU4PSlCZbHrWsZrTVTufbbXh6k/ckPr7Gqs1jNbN+8QqOzdQfoaA5u5WWJo33RybXHcHBqw07SY+1wJP/ALZG1/8Avof1pFh9hinmJlPA/KgTYzyrV/uTTRezqHH5jB/SkNqna9i/79tTigPVfxXj9KPLT+8w+q0xXGeRAv37qR/aOPH6k/0pQ8cXMFuFP9+U72/XgflThEn/AD0P4LThFH2BJ+lAXKzsZHLSyMzHv/8AXpuFzwM/SrwhLdI2/wC+aX7Ow/5Zt+PFFg5kUREz9sD0p/lLGu6QgKOcCpZDt+9JHHj/AGsn8hTRbm4KliYbUHLzSDG76Dv7CgL3BHNtCuoOB57kraRnkJjrIfcdB7/Sqqn7OCQczH7znnb9Pepbu5FzcmWNSkSKI4UP8Kjp+PU/U1UZuMdqZSV1qIzZ4HSm4q48tmumxwxQM12zbpp5D90DoqAdu5J56DoOavGKChDTDUnFBHpQBARUbLg1YIqJhQNMsWDq5e0kICT42k/wuPun+n40IWRijAh1OCDVMjtV92NzbC8XmRCEmHr6N+P86F2FJD0mMFxHOv8AyzYN+HevQLaVZYFZTkMMg152GyBjkV0vhu++U2bnlBlM91/+tVp9Dlrwurroeg2nES/SrQbAqhZvmBT7VYeTAosclybfSGSsS91fyWKRgFh1J6Cs5dXmmk2h2Y+1A9WdZ5gpwYNWLbPMwBZmrTj3YoBE5UGmmMHsKcuadg0h2IDCvpSGFfSpyKY3AouKxFsUdhUZYk4QfjTypc+1SJGBTCwyOILyeT6mpAKdik71Iy34our2y8N311p+PtEUe5cjOB3P1AyayvhxoFvZ+HYtSmjSW9vsytI4BKqTwB/M/WugtrmO5iKNggjBU9xT9EgWwsk05fu242R5/uZ+X9OPwrHZHrqzYl94c029lS5WEWt7H/q7q2ASRfr2YexBBpkclxbSJDfBd5O1J0GEl9sfwt/sn8Ca2BSSRpNE0UqK8bjDKwyCKVyrHlXjnwA1y8uqaPHmU/NNbr/F7r7+1eW/NG/O5XU/Qg19KuraeQsrs9qThJWPzR+zn09G/P1PLeLfh/ba8HvLPbbah1LYwkv+8Ox96pMlo8v0vxfq+mOoM5uYR1imOePY9RXosL6f4t0MtszHIMMp+8jf4ivKdQ0270q7e1vYGhmXqrd/cHuK6TwBqotNUksZGxHcDK5/vD/61UZyWlyaBZbea40e9YmWD/Vuf407H6irWoYuNAczf6yLofcf41f8aWLQyW+rQr80Jw+O696x9QmEmjOYzlXZTn1FMxa1OdNHB69acRTSPzpGiE2/lV+z1Ge1GzPmRd435qmvOAKdigl67nSRWtrfw+db/u37gDofcVTuLWS1YFl/dmmaM8i367Putw/uK6cKjyGF1DBhyp7imZN8rscwIkl5Vh9Cal+xqq7ncAegNaF94fYHzLU/L3Q9ayJre6txloXVP74GR+dMa12ZPvgjH3WOPWoZNRxxHCo9yM1SaUn7pJPqTTkjnf7r9fegrlXUWTULhushUeg4/lVR5i5y+X/H/wDXWilucbZXxnuRmpJdEkFqZ4ZI5UAyQOCKQ04oyPOZOUVEPqBlvzOaidnlbc7Mx9WOTUgUE46elBRByzAAds5JoNNCGTKgAdCM1EamkbdlvTgD0qAnAJNMaAtjqaA4NR570daAJu1ANRBmU8VIGDdODQA4jNMK8VID2oIzQIqyLjp+NS2M629yPMGYpBskHsf8OtK65qswxxS8ylqrMuyRG2uHgY5weD6iprad4JkljP7yM7h7juKRv9K06OYHMsPyN7jtUAfowqiN1qep6HfR3dkrocgjcKu3Eu2Mn0FcD4W1T7HqAtnP7mY5T2buK7e5O6JsHqKs8+pDllY5K+nd5liXlpGrWsYUtUXK7m74rKt49+rsW/5ZpkVfu9RjskAxuY9FFA5a2SNuK+ResTD6Vft72CXhXGfQ8GuAbX7vdlRGo9Nuaswa/uwLiAN/tRnn8jQHs5I9EVgadmuY0/VxIP3MolUdUbhhW3BeRzD5Ww3908GpaJuW2NRkZ60bs0A0gFC0UtKBmi4CGmdKkxTDSAVo3s5QVJ2djWpa3Il2sP8AWL+tZ9vcJcxFG59R6VGm6CYrnkdDUHoJ8uq2OqRw6hh0NPrNs7oMAeiscH2NaQqGjqTurgQGUggEEYIIyCKy5g+kKZVDSWA5ZQMtAPUdyn6j3HTVFKMg5FIDndb8P6X4n08JcKrgjMU8ZGVz3B/yDXiviDw5qPhLVEEhym7db3KjhsfyPtXsGplvCVz/AGhEpOhzPi5hUZ+yOT99R/cJ6jsenWtLVNMsfEejvaXG2SCZdySLztPZlNUtDNo5DR9Qh8S6B84G/GyRD2auPuLOTTZ5tKmz5UgLWzn/ANB/Co9Pe78E+LJNPvTiMsFcjoyn7rj/AD612fiTSxqmmF4secnzxsOzj/Hp+VWYyR5qVIJB65oxU0n7395jBb7w9GHWmKuTg0AIqE1JsxV22t4nQFgSO/NTNa256Haf94GmQ5K5LokTictsPlkfePY1vTIzFXjwJk7dNwrJtZzAoQ5dB6HNbdrJazx7S+T9eRTMZb3Kza+kPySx7WHXNRx6zaSzAl0Qk49jRq+nSXNu3ksDKvKkdWHpXFknJHPB59qC4RUkd5qGiW99B5yKofGdy8H/AOvWJDpMkchDsCo7iq+najeLGsNvcOh9M/L+RrTt3uA5890fPocGgeq0uZ9/Yy2sfmhgYie55BqlDcsj7GKncMcHNbmvAXOlBEYeZC4fb3I6f1rlWhAtBOrHcr4YenpQVHVakUxDSMQPlzxUVPJJzkdaaQaDZDGqJ+wqc1G33jQBDSgGlxmnYoAbgelG09qkCmgr7UCuIrdj1qSoiKVWx97p60Ax5qCVO4qxTWGRg0CTsw02ZUn8pziOYbG9j2NEkZimeMjHPFVXXa3tV6Rzc2yzD/Wpw/v7/jQipb3GIW6KcOp3KfQivQtE1NdU0tWPEqDa6+hrznPRhWno+ptpl+s+f3Mnyyj+tUmYVqfNHTc6Vo/J1eTP8ceR+dZGqOWumJ7cCuh1AKyRXcfzBTkkd1PWsDV49su8dHGQapmFPdFCCKS5uEhiXc7HAFdtYeFLSKIG4LSyd+cAVheD0V9TlZvvIvFd/HjFIVWb5uUzD4csDgrG6MOhVzkU8aZcREbJlmUdBKNrD/gQ/wAK1s0oouZFOPzIxh1cfX5h+Yqyjg9CDUvamtGjdVB+tK47C07OBUJhIHyuy/jkfrSFZh0ZD9VIpASlqrXV3FawPNNKscajLOxwBQ8V0/CzRR+4jLH9TUK6VCZlmnL3My8q8xyF/wB1eg/AZpD9RkcjRSBl6jr71pswmgWVeo6/SsYPujR/XrWhp8mS8J6EZH9alo6acujNG2lCOM/cfg1r2t1+8+zSH94BlCf4h/iK59P4kNXZUlurAPbsBdw/PEf9odj7Hp+NJo6KcrHQg06s7RdVh1rSob6AFQ4IdD1jccMp9wa0BWbR0DJ4IrmCSCeNZIZVKSI3RlIwRXn/AIcuLjwz4nn8JXkjSWrZksJW67TyB+Iz+IPrXolcv4v0wSzaRrEYxNYXaB2HXynYA/kcH8TVR7EyXUw/ifoK6hoI1SJM3NjyxA+9Eeo/A8/nWf4K1T+0tEEMrZlh/dNnr/sn8v5V6PcW8dxbzW8q7opVZGHqCMGvC9Knk8J+LJrK4JEW8wufbPyt/L86qO1jOaLXiPTjp+rOVXENz86+gcfeH9fxrFHDV6brmlrrelMIiBKBvjb0YdP8K81ZW3FXQpIpKuh6qw6g0zIXzmK7dx2+lJuNMxSHIOD1FMCdXI5zVmO6lQghvzqipzVi2wznf0AJxQSzdsNULuFkOD2JrF1hE/tSRkAAk+YgevemSykEEE57Y7VBKzM+5iS3vTCKtqNDPCA6sRzjirY1CR0Bc/MOMjv9apy5CbfXk1GMop96CrXRoPdF1O48AcVUW6iQsCrbXGGHUEVBuJG2omBB5obGooedgJAYle3HNKFDDHfsfWoehqVD7/8A1qRTGEYqN1O0nBxnGatONw3d+9VpeGApiTIx0p6jikp/SgbHAUu0UgNGcUEAyComUipd1ITkUDVyEEr06elSAhhxTSvNGMUDEdNw96bbyeVJgjIPBHqKlpkke7kdRQCfRg6+XIV/hblTQDg4PINOQ+dGY24YcimjurdRQPyOk8P6rsxp9y2UP+qY+n92r19ab4Wtu4G6E+o9K45TjgkjuCOoNdPpeqC+iFndPsuF5jk9fQj+tUn0OapCz5kVNAvfsGtx7zhZPkOexr0uNwV4rzTV7Fiz3CLtkXmZF7ejj2rp/DGti+tfs8zf6REMH/aHY0Izqx5vfR05fmmRXccszxISxj4cgcA+n1qGVyFJHpVDw22/SUlP35ZJHY+p3EfyAoMraXN8GlFRinikA7NFJRmkAtLTc0uaAOesn82yH0zVq2mMcqOOqnP+NZukN/omPQEfkatxnDGg2WjN58CQkdOCKv6e3Lj0IIrKjbfBE2egKn8K0dMOZG+gqWdMH7xi6Rc/2B8Q77SGO201QC5tx2EmOQPrhh+ArvBXnPxLtJobbTdctflnspgpYdgTlT/30P1rudH1OLWNJtdQg+5PGHx/dPcfgcioe1zpj2L9Q3UK3NrLAwBWRSpqbtSGpKK8ZLRKT1IGa8t+JXh1phLqsCEvAcTAd0PQ/h/I+1epqNjsn/Ah9DVS7tknaRJFDJIm1ge/aqTsyJR0PKfBvioOi2F4/wC9XhCf4x/j6j8fWtLxLoAv1OqaaoefH76Jf+WoHcf7Q/X61xPivw5ceHNWdArC2Zt0Eo9PTPqK0/DnjKW3kWG+fk8CVuFf2b0P+1+frVmTXVGYRkBlJz69P8mojXc6xoUeqxNqOlqPtJ5mgPHmH+je/euNaMHJOQQdpyMEH0YdjQQQA+lTxnCk9zxUZQA805WUetMTB2GcEZphIPI/CnOu45HWhUwOeKAIj7HPqahdueufep2HFRmMGgpMiHrS7gRg0MpFNwaLjuLtB6UgUjNSDgelLuycNimFxYzkgHoflNQXC7ZMenFSgFWI/EU26H7zPrzQJblcUpNNHQ0Dk0FDg1LuphIFJnNAWJN1JuzTc0tAWHUYoA4paQhOlO25HFJSjimIjdDncOGHQ07idCw+WReWH9R7U8/MMd6iIZHDKdrryCKBphjdkEYYdqVW6Akgg5Vh1BqUBLiPcvyOv3l/u+/+7/KonUgkEYamF7m7Zar54SC6cJOvEc3Y+x9qZJDLaXf2uzHlTQnLxjnb7j1U1iK24bTye2e9XrW+kBRWchkP7tz1X2PqKdzNwtsd/perRarZiRflkXiSP+6f8KXw83lRXlmettdOAP8AZb51/nXHx3LWE8ep2g2ozbJ4uyt3H09K6jTrmN9fMsR/d3toJB/vI2D+jD8qDnlCydjp1NPzUCHipc0jIfk0maSlwaQxMmjd607tTSAfegLHL6Z8vmJ6Mwq8g+6ex4rPsGBmkIPDYYfiKuxvmNl9DTNDVs2zble6kGtTSjmdx7Vi2Tf6weorW0lv9Kb3FQzopbo1NV06PV9JutPlwEuIym4/wt1B/A4NcJ8N9Um03U7rw3f5R97PCpPRx99R9cZH0NekLyK43xf4Yku5Bq2lgxapbsJo2TrIR2+vp68ioT6M62up3Y6UtYHhPxNB4l0oTKBHdxfJcwd0b6eh7V0FJqxRDKhIDL94dPeoiA+GFWsVG0XJZeCeo9aQFS6sba9gaG5gjmibqkihgfzrz7xJ8K7W4R59DYW0/X7O5Jjf2B6r+o+lemAdiMUFaadhWPA9E1u+8NakdO1RJIhGdjLIOY/Y+q/y7V2WsaFBrUI1CxZI7sr94/dkH91/6Gui8X+EbTxNY4YCK9iH7mfHT/Zb1X+VefeFdZudD1V9B1ZTGVbYu7+E+nuPSrTuYzjbUxpYXjmkgliaKaM4eJ+q/T1HvVdlKnNel6/oMOsQrsYRXajNvP8A+yH1FefSRywzSW1zEYrmM4dD/nkVRkU80E1I8OeV/KosGgB20AZam7x/dzSvyaZmgBTtP8LCo2C9ifyp+RRxQMiNNwamxmmMuO1MLjWP3X9ODRcjKIfbFC4yVPQ04jMJU9VNA0UicLQvClyDjsaJeMike4kkt4YGdjHFu2LngEnJI+uB+VBaGAljz0p/8qYBTxyaAFAp4FIKcKQC0UUUEhSim5ozTEOpH5GR1FKMmmSOANo5NAxqu0ciypww/X2q+0azxqycBl3L7eoqhjitPT0JWJT0AZvwNNEzdtTLcFWPYjrTx8zcdx+tS3oC3DgdMZqvGfun0akXfS5sabKsrtbyf6u5TY3sw6GtDw/M8Wo6fFIfmiuJYD9GTP8ANawbZikuR1SQEVuwrs8UW4XjddRv/wCOHNMykt0egxHip1qvD0qdaRxEq+tDSUxjgVAzl2wKB3JGmA6VEZfc09Yc8tzUojAHAoA4fQrjzrG1kzkmLYfqpxV62n/0h0J6mub8K3O1JbVjzG+8D2PB/pWswcagyr1yCKFsbzjaTR01m+2Vc9DWpp8nlXfPTpWHBKGVXHHPPtWkj4ZXH41LHCVjsI2yKc6hl9xVGwuPMiGTyKvg1nsd6d1c4jX/AA5e2GpnxH4cJS+Xm4t1GROvfjufUd+3NbvhzxhY69HHG2Le9Yf6ljw5HXYe/wBOo9K2cYb61yXibwl9qd9S0yNftZO6a36LcY7j0f37/Wno9xO61R3Ap1cB4f8AF06R+Vc+bcxR/K6uP9Ihx1z/AHwP++vrXcWt1BeW6XFtKksLjKuhyDSaaKjNS2JioNMKmpKMUiiuy5rgviH4U/tWx/tKyQ/b7Zc4UcyIOcfUdRXoZUGoJUI6jj1ovYmSueYeD/EaaxYfYbx8XMYAznBPow/z/Or+t6DHrS+XKVh1GJcxTAcSL7+38j7VzXjvw9P4a1ldd0wFLaZ8uFHEbnqP90/zre8O+KLPX7RYZ38q5j56/Mh9R6itd9TnlGxw1xb3VjcSQXUZjkQ7WyOM+9Nyrj5gM16bqmm299Eq348t1G2K7jHGPQ57f7LfhXIaj4TvLXLxqDH1EsILIfqvVf1FMixzkkRJJHIqEjAq7JaXcYLNbM6j+OA7x+OORVYTRu23eu7+642mgCDBNPVfWpCgH+z9f8aNu04I5pgSROI+QgP1FSMYZhgqEaqpbn0pd5/iGRQJoimiMTYPTsaQHOG9flP1qxkMmCdy/qKqldjYJ+U8ZoGirOu01XHUVemQshz95eDVEjBoNYu6JB0pw4pgp2aAH5pc0zOKTNAEm6kzTCwHuaApb73PtSEHmegLH2o3yf3QKk2gDlgv0pwQH+KmGiIcynqaUR4GSasLCx6HP0xU0dmzH7v4k0A5JFeKIuw9K1ZGWxg+b/WuPujsOwppeDTUycSXB+6o/hrImuWkkLyNlj1x2p7EJOb8hk8peRuck8n/AAp0C5ZR75qEYJHGKuxR7LYynq/yr9O5pFy0Q+zjaacKoyzyAAe5NdPpkH23xPLMnMVu+A3qQAP6H86w9FxHM05/5YI8v4hTj9a7HwpaiHSo5CPnkG4n60GFWVkzoYxgVMpqIU/OFNI5Rsr9aIE7mozycVZGAtMCQUtNFOzigo8UsLv7HfQ3P8J+ST6GuzYgX9tNnKyDZn3xxXArySh6N/Ouo0e5a80hoCf39vjafpyP8KSOqrHqdREdkjIej8j696v28mRtJ9qzraRLu2jlX+IbgfQ1MshjlAI60zDY6XTLja2wnkVvxybhXG28/IYfeX9RXR2dyHQc81nJHXRndWNPqKXqKhV81Irc1B0HJ+LvDkkxOtaUCmowjdIif8t1H/sw/UVkeH/EMkeb6zXJyPtdoOBJ/tr6N/OvRfcda8x8Waa/hjXI9Zsoz9huXIljXojHqPoeSPfNXF30ZlONveR6lZ3kF9aR3Nu++KQZU/0PvVjNcHoWqpYSJPG+/TbrDNjnYf7w/qPxruVYMoZSCCMgjoalqxpCXMh9BAIwaQGlpFmbqOnQX1nLaXUYlt5l2sp9K8H8UeFNQ8I6kJY2ka0LZguU4x/st6H+dfRJAIxVS6sobm3eC4iSaBxhkcZBHuKadiGrniGj/EO/slEd5GLmPGNw4OPeupsPGPh67IKTSWEp67TtGfpyv6VJrPwmsrh2m0m5e0Y8+U/zx/h3H61w+qeAvEGl7mksTcRD/lpbnd+g5/MVadzNxsemfZrTUgJUktLsno+Nj/8AfS1n6l4YFxGfJjjlk6iC8AO72WQdPxzXk9vc3mny7reaSJwfujg/lXf+F/H6XLLY6xgMxAWbtn39DTIcTElsbD7U9p5k2mXinDW91yufY1Vu9PvbAgSwjZ2IOVP0PavS/EnhuDxLp/lkol/Euba4/vD+63qp/TrXltnrV9o80ljeRmSKNjHLby8lCOoHpTTFZ20I8rIDtzkdVPUf400bcYIOexFa9zY2uo2/2zTXPHJX+JD7juKxWZlY71w6/fX+opkrUftI+ZTyKY5DqeMeo9KcsoA4AIofa/zRjDDqvrQMgVsgg9UHPuv/ANaqtxHtbjoeQfWp2YqwkXt/nFBVZP3Xr80ZP8qZS01KYpw600gqcEcinCkWxTSZJ4FO60qjFAhFXFTL6Z+pPamgelNlOwbR1PWgTJPtfknECgN3dhlv/rUn9o3mc/aX/OnQ2y7S0nAHX/CtKFIYITK0aIg7kZNMiTiulzNGq3a9XRv95FP9KbJql1Iu3zQg/wCmahf5VoDWYx9y0LL6naKeNUspP9dYEe/lq38qQbfZMEsxzknn3pBxXRrcaE/WKFT6GJhU6XGlxc28cOfVIST+oosU6j7GPY6XJcATT5hthyXbgt7D1p93KJpv3a7YkG1F9BVu7nuLo4jilI9Wpltp5bJncJxwMjrQTfrIdpikrdRAcyWzgfXB/wAK7rw66yaNasvQoK5GG1e0ubdgwO5SmR03DkVv+F5gkM1nniF9yf7jcj8uR+FBjU1V0dOKUn5aYpzTjyKRzjU+9UxPFQKcNU2aAHB8d6UvULdKrvIB3pjPGypSXDDBU4IrR0q6+x6mjE4Rzsb8ehqHUwGvhMowlwqyj6nr+uaidPlPtgUj0H7y9TubCX7NfSWjHCS5li9j/EPz5/GtWXlMnqK5S2nfUNLWSM/6XbHI9yP8RW/puox6harKvU8OvoaZyyj1L8ExGD3HWti0utmCD8p/SsIAoxHX09xVu2l/h7Gk9RRk0zroLoMBk1cVwa5e3uWhODytatvdK2NrfhUOJ2Qqp7mwDmqmp2Fvqmnz2Vyu6GZdpx1HoR7g80qTetSCVTUmt0zyTTLubwtrU2iao2LYv8snZCejj/ZP6fnXo2mX76UBDcc2J6P18n3/ANw/+O/TpkeOvDo1jTPtVum67tgSABy6dSv9R/8AXrnvAfibfImh6hJhsYs5mPX/AGD/AE/Kr3Rlbleh68DkZBBHqKXdXPRS3GlcQQtNaj71sp+aP/rnngj/AGT+BHStGy1ax1EH7LdRu6nDxk7XQ+jIcEH6ioaNk7mhmjNVJ7u3tl3T3MMI9ZJFX+ZqgfEWj5wuoRyn0h3Sf+gg0gubW0Um2shfEGl93mQer2sqj8ytWrbVtPu22219BI/91ZBu/LrTsF0Udb8J6Pr8bC9s0809Jo/lcfiOv45rx3xd4Ev/AA4xuFY3NkThZ1GCPRXHY+h6H9K983EcGmTRQ3MDwzRpJFIpV0cZDA9iKabQmux5H4B8UPdRro95J+/jGbZ2PUd1NS/EPw+l5ZjxBZpiaMBbpQPvKON31HQ+30rD8beFZ/CGsxahYF/sMj7oX6mJ+u0n+R713mhapBrenIzgGK9jKyJ6SAYYfiOavzMbWZ41ZXs9lOJoXZSOuOhHvW3MY9Th+0wKEuUGWQdD7j2rvPhlYpYz+ILCRFMsNwqncM5TkD8P8ag8e+GIdNVPEGlxLAEcLdxRjC88BwO3PBHTkH1p31sKUb6o81YbMSoPkJwV/umkV/nxnHoa0bpEVvtSLmKTiVPT3qhc25typzugf7knp7GmJNMSQZ5x161DtLIY8/MPmQ/0qTftwD+NNdehU+4NA0MP+lIWH+uUfMP7w9RVcGpJMhvOT5SD8wHY+tS4W8BZAFnHVeze4oC9vQhBqwYoxaJKJ1MhYhosYK+h981U5BweCOoqVSCPekUSKf0pGGLvJ6feFNU44qTb5qYH315X39RTETT5QrH2AyfqauPG19o5WE5ljIyvc4qCdd5inX7kij8xT4llhkEsDbXHUdiPemZX0Rhy/fKnovAHpTASOnH0rdvLSPUSZIF8q7Ay8R/j9we9YbqyOUdSrDqD1FS0bwkmjd06CL+yftRUPKXKktztAqrcTPuIBI/Gk0e/S2d7ac/6PNwT/dPrUl/atBKc8j1HQj1o6GdrTdykSx/iNG4jqASKWkNSWbmnXwntzCzHzU+dM9yK2Y5fsV5FepnyWHz4/uHk/kfm+m6uJBKOGUkEdCK6jQNRW5j+xXJ/eDmNvWquZSjbXod3FIGUEHNTg5Fc/psr2jizl+5/ywbsR/d+o7e30rcR88joaZySjZjzwaeDxTTzSe1IkkbkGs25WdTmFgPYjrV8NkGoJmCgn0oGnY8nb9/pgP8AHbPj/gLf4EfrTQPMV1HVhuH1plnMsc+JP9U4KSD2Pf8ADrT9jQTNEx+aM8H1HrQd/kP06+eyuBIMlTw6+orUe6Om3i6jaNutpj+8X0NY3lbpsL/FyKuLZy+Q6q+QeGWgUkr3O4tbuO+tlmhYEHkex9DU6Pghl9fyNcHYXd3o0+7aWgJ+ZfauztbyG6hWeJt0Tj5vag55w5TajYSRhgeP5Gplm2H5jtPYjpWZDM1vLzyO49R61ortkTfHhlPagSNGG9dB1yKuR3qt14rACAH5GZD7f4VIrTLyMN7rwfypWLVSSOjEwIypry3x14cNheDVLFSsEr7jt/5ZSdfwB6/Wu3hvecN+PY1bdIby3eGVVlhkXa6NyCKWxqqnMUvBniRPEmlhJmA1G3AWUH+Mdm/H9K2bzRNN1Ug3tjBOy8BnT5l/Ec4/GvLdV0fUfB2rJrGlMz26twTzgd0f1Hv/AFr0jw34o07xNaCS3fyrpB+9gY/Oh9vUe9DXY1hK5btfDulWh3W+m2kbDowhBP5nmtIREDG5wPQHApQ7L94bh6r/AIVKrqw4Oai5ruQ/Zwf7/wD32ahudJtbxdtzCJR/00w386vg0tF2Fkc/JoF1bfNpGqXNqR0hm/fwn/gLHI/AiiLVdXsjt1bS96DrdWBMij3KH5x+Ga6HFGKLhYyb6207xNoc1pJIk1rcKVEiHO1uxHoQe1eR6I134V8QXGg6gfLJcNDIfu7x9xgfRhxXtEthE0xnj/dTt96RB97/AHh0b8efeuc8WeF4vEViEuNsV3ED5F0oyB/st32n07dRVRdiJxuZ1jMmneM4dS+7aatELeU9o5h93P1IxXa3VpDeWk1pcpvgnQxyIe6ng147b6rdaPNJoviO3JRuMtyGH94HuPcfzr0DRfEIS2WO5mNzbKMLdDl0H/TQDr/vj8QOtOSIjJLRnmGoaVPoOqXGlXWXEfMb/wDPWI9G+vr71nxyrZytbzgPbSeo4xXtXiHQLTxNp8f7xUnQb7a6T5gM9uOqmvJNX0i6sZ2sb+LyZhyh6q3up7iqi7mc42fkZ15pEkKGW1zNb9do5Zfp6is1JdoPRlrSstQm02XyZgTGD+K/StO60u01OP7RbssUzDIdfut9RTFzOOkjnfLST5oW+fHKN3qo8ZjbfHkYPTupqe4gmtLgxSoY5V5+vuKckn2kY4E4HHow9KC721EWSO9G2UiOfs/ZvrUDxvBIUdcMP1pk0WB5iAhc4IP8J9KsW92kii3vMmP+GTulA7W1WxHnODUisVYFTz1H1pLm2e0l2McqwyrDowpiHOV/KgFZo00uIk/dSZEMvzqw/gNWhH8oBIz/AAuDwayt6m3UP0yRn0pBcy2j7Yn+UgEjqDTuZuF9jRdQcCRM45BHBH0NRTxC4XEq+djo4wJF/o1MTVoyMS2/4ocfpUi3tjJ/y0eM/wC0v9RSFyyRk3Fm8WWU70HUgYI+o7Vas78CIW1ycxD7j9dnt7itMRiVd8TrMB3RuR/Ws64sEfLR/K3fA/mP8PypWsaKSkrSC4s2iO5fmQ8gjmqxUjqDT4Lu4sfkZQ8J/hJyD9DWgksFzHui+Yd1P3lpA7x3F0cRM0kUkaszYIJGaZ58HnEtDsdW4ePj9KamIpQ8fBByKjmUGYsOjcimTa7OrstUtr6MW8r5Y+vB9iPety1uGB8uU5cchv749fr61w1rpVyxWSPjHINddAG2Irn5sZB9GpowmktEbavkdafmqUMhZffuKshsigxFY45FRS/Oh+lSk1BINtAjyKSP5iV69xVpCbu3G3/j4gHH+2tQsFdQwO30P90+h9qjWV4pg/3JV7+v1qT0Grk6yBXjmH3QeR6etXrmeS2ulkQ/K6AH0bFVnCTRG5iHyn/XR/3T61LGPtVr9nJ/ex8xk/xCmJvqXorqG5X5SFbupplvdtplyZIBuiY/vIh0PuPesb5lYgggg/iKlE57nPvSDkO/tLyG4gRhIDE3+rk/un+6auxvJA/yna3oehrz2y1CWykLREFG+/G33W/wPvXU2GrrNF+6zLGv3omPzx/T1FMwlBo6ZL1GAE8WD6ipl8t+YZefQ81l29xFOuYn3jup+8KsrEjcrwfaixF2XGAl+WQbX7MP6GmLNPayf3gP1HtUYaRBhvnWpg4dMZJX9RQFy9DeQXkZjO07hho2HUfTvXIaz4KaG4/tHQpXt5kO7y1Ygg/7J6/hW48Csw4APZhT0ubu1wGPnR+jdR+NFi1UtuYWm/ELWdKAj1qxN1CvBuIuGH17H8cV1+m+N/D+qFRHfJDKeiT/ALtv14P51k3Nvp2qtvLNa3WMbxwT9exrn9Q8JSAM0titzH/z2tDtb6leh/L8amxtGserpcEAMCJEPcdf/r1ZikWRAyNkV4bZLrGjS7tC1J3Cn5rOUbSfbYTg/wDATmu28OeNotUn+zzKLLVBw0EmQk2OwzyD+o9xScTeNRM9AFLVe1uo7lCUyGU4dG+8p9D/AI96sVBoFRtKucZz64FOc/KaiY7I8j0oQmzO1bQ9M1y1NteQo69V7FD6qe1ea6t4Y1rwjI13p8kl1Yr8x2/6yMe4HUe4q3ffFdo9Skit9NjmtY3K7ncqzY4yPSup0Pxfp+vW5Nszb1GZLWX76j1U9xWiujGXKzmfDnjKOVwqyLDIx+Yf8s5D/tL2P+0Me+a7iSLTfEti9reW4fHJjY/Mh/vKw/mPxrynx/oUWj6nDqmnYW2usnavADDrx71u+Fdalns45g5863wcnuvv602riUraMz/FXgq70dDOha708dJwvzw/749Pfp9K5S0updNn/vQnllB4x/eFfRMUiXVqkqgbZF5U8/UGvJ/HfhNNJkGo6em2ykfDx9oJD0x/sN0x2P4Uoy1CdNJabGXeWlvrNko3DdjMUo7f/WrjJ4pbW4eKVSk0ZwR/Wt3Sbz7PIsecQSn5c/wN3FXdb04ahbefEv8ApEQ4A/jX0/wqzKL5HyvY5wyCSPztuc/LKnr71Tnh8p8A5RhlG9RT4JPKkIb7jDDCplj8zdatjcTuib/a9Pof54oZsvdZLbSfa9Mltn5khHmR/TuKpo2GBpbSY2t4kjDhThwfToRTp4vJnePOQp4PqOx/KgSVmyTO6GRe4w3+NRSHKo3quPypUfaQ350jpsGzPyMcxt7+lIpEeaTr3pDkHB60lIqw5WeJgyMyN2IOKvxaqWwl2u/0kXhh/jWeCQPb0NBUEZHTuPSi4nFPc154BLF5sTK6H+Neh9mFZe0pJuiYpIPQ/wAjRbXUtpJvjPB+8p6MPer9xBHdW32y1GF/5aR91NPcjWOj2I47wS/JMAkn97salV/nCP1zwaziQRhhketSJJ8oRzlf4W9KExuPY7DS5UYSSEbnDqiqTgAH/wDVWurklTgcHrXGWF4yOVY/NjDAfxDsR7iuihuBJtfdnimjlnGzN63fLZ7EkVcBqhZfMN2foKvjFBgx4Oaa3THWjoaXOaBHjyPtOcZU8MPWpHQEAMcofuv6exooqT0mMhllsp9yjkcFezCr7RhoVu7UkRZ/GM/4UUUEy2TFkQXql1XbcIPnT196plRjkEH6UUUCWjaI8EdM1JHNNBIskbMrr0K9qKKRZ0WnaxHeMqTHyLvosi9H/wA+ldBBqckTBLpfpIvQ0UVaOapFJ2RrxXCyIGBBH94VLjPzKcH1FFFIxFEg+7IMZ79jUgLp23p+o/xoooKQhhguFypAPpUXlXNqd0bsAPQ8UUUga6kdyIL9dl/bq57SqMMPxrB1fSdsatdbrm2GPLu4x++g9M+o9j+BBoopjpydzb8Oa7cpdQWF9cI1ywxZ3yglLhf7j+p/I59G6+g2l4t1Gfl2SpxJGTnafr3B7Hv+YoorOSO+m20WCciol5yh7fyooqTRni3jjwLd6TeTajYRtNYyMXZVGWizyeO4/lXIWdzPaXEdxbyPFMhyrqcEGiitUYTR1Ws66dc8KIJVCzwXALAdOVIyKTwPIRewwNnbLGykfhn+lFFV0M0eteFZWl0NCxyVdk/Lj+lWtUsYtQsZ7OcZinQxt7Z7/gcH8KKKye50L4UfPcsElrqM9lNw28ofZwcZ/T9a2tPvmKbZc714J/rRRWqOaauilrOjiUm5tlAY8so6H3rADHHlyggjgE9VoooHSbasySYG5Blx+/UfvAP4h/e/xoQ/aIgpH7xBx/tL/iP5UUUGnQjwVPIqVG2qUZd0Z6iiikMR4CVzH+8Uf99Cq5BB+6c+mKKKTCDuJ+BoGQciiigsGXjIHBqaxu2srkPgmNuHX1FFFArJqzLGoWgglDxjMMnzIR/KqXI7fhRRQ9zODbiTRsTjaSHX7prZsb07SSDgffUdvcUUUBJJnVaVeAqEY54yCP4l9a2VYHkUUVRxTWpIORTckGiikQf/2Q==")';
    const MONITOR_STYLE = `background:rgba(0,50,45,0.35); border:1px dashed ${COLOR_RED}; border-radius:10px; padding:6px; margin-bottom:10px; font-size:11px; color:#7ecfbe; display:flex; justify-content: space-around; pointer-events:none;`;
    const LABEL_CSS = "display:block!important; font-size:10px!important; color:rgba(232,244,242,0.5)!important; margin:0 0 3px 2px!important; text-align:left!important; text-transform:uppercase!important; font-weight:bold!important; letter-spacing:0.5px!important;";
    const FIELD_CSS = "width:100%!important; height:28px!important; padding:0 8px!important; background:rgba(0,40,35,0.45)!important; color:#e8f4f2!important; border-radius:8px!important; border:1px solid rgba(61,158,138,0.25)!important; outline:none!important; box-sizing:border-box!important; font-size:11px!important; display:block!important; margin-bottom:5px!important;";
    const BTN_STYLE = "width:100%; padding:9px; margin-top:4px; border:none; border-radius:9px; cursor:pointer; font-weight:bold; font-size:11px; transition:0.2s;";
    const getMonitorHTML = () => `<div style="${MONITOR_STYLE}"><span>📞 ${GLOBAL_PHONE || "Не указан"}</span><span>📲 ${GLOBAL_TELEGRAM || "Не указан"}</span></div>`;
    const renderMainMenu = () => {
        panel.innerHTML = `<div class="ui-close" style="position:absolute; top:12px; right:15px; cursor:pointer; opacity:0.3; font-weight:bold; font-size:18px; z-index:10;">✕</div>
            <div id="ui-reset" style="position:absolute; top:12px; left:15px; cursor:pointer; opacity:0.5; font-size:11px;" title="Сбросить память имен и текстов">🔄 АННИГИЛИРОВАТЬ </div>
            <div style="font-size:18px; font-weight:bold; color:#7ecfbe; margin-bottom:10px; margin-top:5px;">скриптонит залив.</div>
            ${getMonitorHTML()}
            <button id="go-create" style="${BTN_STYLE} background:${COLOR_RED}; color:#fff;">ЗАЛИТЬ</button>
            <div style="display:grid; grid-template-columns:1fr 1fr 1fr; gap:6px; margin-top:6px;">
                <button id="go-strashnaya" style="padding:10px; border:none; border-radius:10px; cursor:pointer; font-weight:bold; font-size:11px; transition:0.2s; background:#7b2d2d; color:#fff;">😈 СТРАШНАЯ</button>
                <button id="go-obychnaya" style="padding:10px; border:none; border-radius:10px; cursor:pointer; font-weight:bold; font-size:11px; transition:0.2s; background:#2d5a7b; color:#fff;">⭐ ОБЫЧНАЯ</button>
                <button id="go-vip" style="padding:10px; border:none; border-radius:10px; cursor:pointer; font-weight:bold; font-size:11px; transition:0.2s; background:#7b6b2d; color:#fff;">👑 ВИП</button>
            </div>`;
         
        panel.querySelector('#go-create').onclick = renderCreate;
        panel.querySelector('#go-strashnaya').onclick = () => renderTierCreate('страшная');
        panel.querySelector('#go-obychnaya').onclick = () => renderTierCreate('обычная');
        panel.querySelector('#go-vip').onclick = () => renderTierCreate('вип');
        panel.querySelector('.ui-close').onclick = () => panel.remove();
     
        panel.querySelector('#ui-reset').onclick = () => {
            if (confirm("Точно сбросить память? Все имена и тексты начнут выдаваться с самого начала.")) {
                ['names', 'main', 'min'].forEach(k => {
                    localStorage.removeItem('eva_array_' + k);
                    localStorage.removeItem('eva_indices_' + k);
                });
                alert("АЛЯ-УЛЮ! 🧹");
            }
        };
    };
    const renderEdit = () => {
        panel.innerHTML = `<div class="ui-close" style="position:absolute; top:12px; right:15px; cursor:pointer; opacity:0.3; font-weight:bold; font-size:18px; z-index:10;">✕</div>
            <div id="go-back" style="position:absolute; top:12px; left:15px; cursor:pointer; opacity:0.5; font-size:11px;">← НАЗАД</div>
            <div style="font-size:16px; font-weight:bold; color:#7ecfbe; margin-bottom:15px;">скриптонит залив.</div>
            <div style="text-align:left;">
                <label style="${LABEL_CSS}">НОМЕР ТЕЛЕФОНА</label>
                <input id="edit-phone" style="${FIELD_CSS}" value="${GLOBAL_PHONE}">
                <label style="${LABEL_CSS}">TELEGRAM USERNAME</label>
                <input id="edit-tg" style="${FIELD_CSS}" value="${GLOBAL_TELEGRAM}">
                <div style="display:flex; justify-content: space-between; margin: 10px 0 15px 0; padding: 0 5px;">
                    <div style="display:flex; align-items:center;"><label class="eva-switch"><input type="checkbox" id="check-wa" ${SHOW_WA ? 'checked' : ''}><span class="eva-slider"></span></label><span style="font-size:12px; color:rgba(232,244,242,0.7);">WhatsApp</span></div>
                    <div style="display:flex; align-items:center;"><label class="eva-switch"><input type="checkbox" id="check-tg" ${SHOW_TG ? 'checked' : ''}><span class="eva-slider"></span></label><span style="font-size:12px; color:rgba(232,244,242,0.7);">Telegram</span></div>
                </div>
            </div>
            <button id="edit-save" style="${BTN_STYLE} background:${COLOR_RED}; color:#fff;">СОХРАНИТЬ ИЗМЕНЕНИЯ</button>`;
     
        panel.querySelector('.ui-close').onclick = () => panel.remove();
        panel.querySelector('#go-back').onclick = renderMainMenu;
     
        panel.querySelector('#edit-save').onclick = function() {
            GLOBAL_PHONE = panel.querySelector('#edit-phone').value;
            GLOBAL_TELEGRAM = panel.querySelector('#edit-tg').value;
            SHOW_WA = panel.querySelector('#check-wa').checked;
            SHOW_TG = panel.querySelector('#check-tg').checked;
         
            const phoneClean = GLOBAL_PHONE.replace(/\D/g, '');
            if (phoneClean) fillField('#item-phone', phoneClean);
         
            if (GLOBAL_TELEGRAM && GLOBAL_TELEGRAM !== "@Ваша собачка") {
                fillField('#item-messengers_telegram_username', GLOBAL_TELEGRAM.replace('@', ''));
            }
            const wa = document.getElementById('messengers1');
            if(wa) { wa.checked = SHOW_WA; wa.dispatchEvent(new Event('change', {bubbles:true})); }
         
            const tg = document.getElementById('messengers2');
            if(tg) { tg.checked = SHOW_TG; tg.dispatchEvent(new Event('change', {bubbles:true})); }
         
            this.textContent = 'ГОТОВО';
            setTimeout(() => renderMainMenu(), 800);
        };
    };
    const renderCreate = () => {
        const randomName = getNextUnique('names', NAMES) || "Анна";
     
        panel.innerHTML = `<div class="ui-close" style="position:absolute; top:12px; right:15px; cursor:pointer; opacity:0.3; font-weight:bold; font-size:18px; z-index:10;">✕</div>
            <div id="go-back" style="position:absolute; top:12px; left:15px; cursor:pointer; opacity:0.5; font-size:11px;">← НАЗАД</div>
            <div style="font-size:16px; font-weight:bold; color:#7ecfbe; margin-bottom:10px;">скриптонит залив.</div>
            ${getMonitorHTML()}
            <textarea id="ui-parser" placeholder="Вставь данные анкеты..." style="${FIELD_CSS} height:110px!important; resize:none; padding:10px;"></textarea>
            <div style="display:grid; grid-template-columns: 1fr 1fr; gap: 8px; text-align:left;">
                <div style="grid-column: span 2;"><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Имя</label><input id="ui-name" style="${FIELD_CSS}" value="${randomName}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Возраст</label><input id="ui-age" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Рост</label><input id="ui-height" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Вес</label><input id="ui-weight" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Грудь</label><input id="ui-boobs" style="${FIELD_CSS}"></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Волосы</label><select id="ui-hair" style="${FIELD_CSS}"><option value="1">Блонд</option><option value="2">Брюнетка</option><option value="3">Шатенка</option><option value="4">Рыжая</option><option value="5">Другой</option></select></div>
                <div><label style="display:block; font-size:10px; color:rgba(232,244,242,0.5); margin-bottom:3px;">Цены</label><select id="ui-tariff" style="${FIELD_CSS}"><option value="p1">6 / 9 / 18 / 45</option><option value="p2">6 / 10 / 20 / 50</option></select></div>
            </div>
            <div style="display:flex; gap:8px; margin-top:10px;"><button id="toggle-wa" data-on="0" style="flex:1; padding:10px; border:1px solid rgba(61,158,138,0.35); border-radius:10px; background:rgba(0,40,35,0.4); color:rgba(232,244,242,0.45); font-size:12px; font-weight:bold; cursor:pointer; transition:0.2s;">WhatsApp</button><button id="toggle-tg" data-on="0" style="flex:1; padding:10px; border:1px solid rgba(61,158,138,0.35); border-radius:10px; background:rgba(0,40,35,0.4); color:rgba(232,244,242,0.45); font-size:12px; font-weight:bold; cursor:pointer; transition:0.2s;">Telegram</button></div><button id="ui-apply" style="${BTN_STYLE} background:${COLOR_RED}; color:#fff;">ПРИМЕНИТЬ</button>`;
     
        panel.querySelector('.ui-close').onclick = () => panel.remove();
        panel.querySelector('#go-back').onclick = renderMainMenu;

        const toggleStyle = (btn) => {
            const on = btn.dataset.on === '1';
            btn.dataset.on = on ? '0' : '1';
            btn.style.background = !on ? 'rgba(61,158,138,0.55)' : 'rgba(0,40,35,0.4)';
            btn.style.color = !on ? '#e8f4f2' : 'rgba(232,244,242,0.45)';
            btn.style.borderColor = !on ? '#3d9e8a' : 'rgba(61,158,138,0.35)';
        };
        panel.querySelector('#toggle-wa').onclick = function() { toggleStyle(this); };
        panel.querySelector('#toggle-tg').onclick = function() { toggleStyle(this); };

        const parser = panel.querySelector('#ui-parser');
        parser.oninput = () => {
            const data = parseData(parser.value);
            if(data.age) panel.querySelector('#ui-age').value = data.age;
            if(data.height) panel.querySelector('#ui-height').value = data.height;
            if(data.weight) panel.querySelector('#ui-weight').value = data.weight;
            if(data.boobs) panel.querySelector('#ui-boobs').value = data.boobs;
            if(data.hair) panel.querySelector('#ui-hair').value = data.hair;
        };
        panel.querySelector('#ui-apply').onclick = function() {
            const tariff = panel.querySelector('#ui-tariff').value;
            const prices = tariff === 'p1' ? { a: ["6000", "9000", "18000", "45000"], b: ["6000", "9000", "18000", "45000"] } : { a: ["6000", "10000", "20000", "50000"], b: ["6000", "10000", "20000", "50000"] };
            fillField('#item-name', panel.querySelector('#ui-name').value);
            fillField('#item-age', panel.querySelector('#ui-age').value);
            fillField('#item-height', panel.querySelector('#ui-height').value);
            fillField('#item-weight', panel.querySelector('#ui-weight').value);
            fillField('#item-boobs', panel.querySelector('#ui-boobs').value);
            fillField('#item-color_hair', panel.querySelector('#ui-hair').value);
         
            const phoneClean = GLOBAL_PHONE.replace(/\D/g, '');
            if (phoneClean) fillField('#item-phone', phoneClean);
         
            fillField('#item-price', "1");
            for(let i=0; i<4; i++) { fillField(`#item-price_a_${i}`, prices.a[i]); fillField(`#item-price_b_${i}`, prices.b[i]); }
            const dist = document.querySelector('#item-district');
            if(dist) { const opts = Array.from(dist.options).map(o => o.value).filter(v => v); fillField('#item-district', opts[Math.floor(Math.random() * opts.length)]); }
            const metro = document.querySelector('#item-metro');
            if(metro) { const opts = Array.from(metro.options).map(o => o.value).filter(v => v); if(opts.length > 0) { fillField('#item-metro', opts[Math.floor(Math.random() * opts.length)]); } }
            const map = document.getElementById('leaflet_coordinates');
            if(map) { const r = map.getBoundingClientRect(); map.dispatchEvent(new MouseEvent('click', { bubbles: true, clientX: r.left + r.width/2 + (Math.random()*40-20), clientY: r.top + r.height/2 + (Math.random()*40-20) })); }
            const work24 = document.getElementById('work_time24');
            if(work24) { work24.checked = true; work24.dispatchEvent(new Event('change', { bubbles: true })); if(typeof window.work_time_24 === 'function') window.work_time_24(); }
            const useWA = panel.querySelector('#toggle-wa').dataset.on === '1';
            const useTG = panel.querySelector('#toggle-tg').dataset.on === '1';
            if(useWA) { const wa = document.getElementById('messengers1'); if(wa) { wa.checked = true; wa.dispatchEvent(new Event('change', {bubbles:true})); } }
            else { const wa = document.getElementById('messengers1'); if(wa) { wa.checked = false; wa.dispatchEvent(new Event('change', {bubbles:true})); } }
            if(useTG) { const tg = document.getElementById('messengers2'); if(tg) { tg.checked = true; tg.dispatchEvent(new Event('change', {bubbles:true})); } }
            else { const tg = document.getElementById('messengers2'); if(tg) { tg.checked = false; tg.dispatchEvent(new Event('change', {bubbles:true})); } }
            ['where_to_go1', 'where_to_go2', 'where_to_go3', 'where_to_go4'].forEach(id => { const cb = document.getElementById(id); if(cb) { cb.checked = true; cb.dispatchEvent(new Event('change', {bubbles:true})); } });
            fillField('#item-neighbors', "1"); fillField('#item-haircut', "1"); fillField('#item-smoking', "1"); fillField('#item-nationality', "1");
         
            if (GLOBAL_TELEGRAM && GLOBAL_TELEGRAM !== "@Ваша собачка") fillField('#item-messengers_telegram_username', GLOBAL_TELEGRAM.replace('@', ''));
         
            fillField('#item-max_ejaculation', "6");
            setTimeout(() => {
                const rawDesc = getNextUnique('main', GLOBAL_DESCRIPTIONS);
                const rawMinDesc = getNextUnique('min', GLOBAL_MIN_DESCRIPTIONS);
                const dInp = document.querySelector('#item-description');
                if (dInp && rawDesc) {
                    const finalDesc = syncDescription(rawDesc, SHOW_WA, SHOW_TG, GLOBAL_TELEGRAM, false);
                    dInp.value = finalDesc;
                    dInp.dispatchEvent(new Event('input', { bubbles: true }));
                    setTimeout(() => { dInp.value = finalDesc; dInp.dispatchEvent(new Event('change', { bubbles: true })); dInp.dispatchEvent(new Event('blur', { bubbles: true })); }, 100);
                }
                const mInp = document.querySelector('#item-min_description');
                if (mInp && rawMinDesc) {
                    const finalMinDesc = syncDescription(rawMinDesc, false, false, GLOBAL_TELEGRAM, true);
                    mInp.value = finalMinDesc;
                    mInp.dispatchEvent(new Event('input', { bubbles: true }));
                    setTimeout(() => { mInp.value = finalMinDesc; mInp.dispatchEvent(new Event('change', { bubbles: true })); mInp.dispatchEvent(new Event('blur', { bubbles: true })); }, 100);
                }
            }, 600);
            applyAdvancedServices(true);
            this.textContent = 'ГОТОВО ✓';
        };
    };
    renderMainMenu();
    document.body.appendChild(panel);
    panel.onmousedown = (e) => {
        if (['INPUT', 'BUTTON', 'TEXTAREA', 'SELECT', 'SPAN'].includes(e.target.tagName)) return;
        let sx = e.clientX - panel.getBoundingClientRect().left, sy = e.clientY - panel.getBoundingClientRect().top;
        document.onmousemove = (e) => { panel.style.left = e.clientX - sx + 'px'; panel.style.top = e.clientY - sy + 'px'; panel.style.transform = 'none'; };
        document.onmouseup = () => document.onmousemove = null;
    };

    /* === [ АНИМАЦИЯ ] === */
    function showToast(msg, duration) {
        duration = duration || 2800;
        var toast = document.createElement('div');
        toast.style.cssText = 'position:fixed!important;bottom:30px!important;right:30px!important;z-index:999999!important;background:rgba(0,35,30,0.95)!important;color:#7ecfbe!important;border:1px solid rgba(61,158,138,0.55)!important;border-radius:14px!important;padding:12px 22px!important;font-family:\'Segoe UI\',sans-serif!important;font-size:13px!important;font-weight:bold!important;box-shadow:0 6px 30px rgba(0,20,18,0.6)!important;opacity:0!important;transition:opacity 0.35s ease,transform 0.35s ease!important;transform:translateY(18px)!important;pointer-events:none!important;';
        toast.textContent = msg;
        document.body.appendChild(toast);
        requestAnimationFrame(function() {
            requestAnimationFrame(function() {
                toast.style.opacity = '1';
                toast.style.transform = 'translateY(0)';
            });
        });
        setTimeout(function() {
            toast.style.opacity = '0';
            toast.style.transform = 'translateY(10px)';
            setTimeout(function() { if (toast.parentNode) toast.parentNode.removeChild(toast); }, 400);
        }, duration);
    }

    /* === [ МЕДЛЕННОЕ ЗАПОЛНЕНИЕ — СЧЁТЧИК + ПРОГРЕСС-БАР ] === */
    var _origFillField = fillField;
    var _fillQueue = [];
    var _fillTimer = null;
    var _fillTotal = 0;
    var _fillDone = 0;
    var _counterEl = null;
    var _overlayActive = false;
    var FILL_TARGET_MS = 3000; /* целевое время залива — 3 секунды */
    var FILL_STEP_MS = 150;    /* пересчитывается под кол-во полей  */
    var _batchPending = false;

    function _updateCounter() {
        if (_counterEl) _counterEl.textContent = _fillDone + ' / ' + _fillTotal;
    }

    function _runFillQueue() {
        if (_fillTimer !== null || _fillQueue.length === 0) return;
        function _next() {
            if (_fillQueue.length === 0) { _fillTimer = null; return; }
            var item = _fillQueue.shift();
            _origFillField(item.s, item.v);
            _fillDone++;
            _updateCounter();
            _fillTimer = setTimeout(_next, FILL_STEP_MS);
        }
        _fillTimer = setTimeout(_next, 0);
    }

    function _createProgressOverlay() {
        var existing = document.getElementById('eva-progress-wrap');
        if (existing) existing.parentNode.removeChild(existing);

        var rect = panel.getBoundingClientRect();
        var overlay = document.createElement('div');
        overlay.id = 'eva-progress-wrap';
        overlay.style.cssText = [
            'position:fixed!important',
            'left:' + rect.left + 'px!important',
            'top:' + (rect.bottom - 26) + 'px!important',
            'width:' + rect.width + 'px!important',
            'height:26px!important',
            'border-radius:0 0 24px 24px!important',
            'overflow:hidden!important',
            'background:rgba(0,28,24,0.93)!important',
            'z-index:2147483647!important',
            'display:flex!important',
            'align-items:center!important',
            'pointer-events:none!important',
            'box-shadow:0 6px 20px rgba(0,0,0,0.5)!important'
        ].join(';');

        var bar = document.createElement('div');
        bar.style.cssText = 'position:absolute!important;left:0!important;top:0!important;height:100%!important;width:0%!important;background:linear-gradient(90deg,#1d6b5e,#3d9e8a,#7ecfbe)!important;transition:width 0.15s linear!important;opacity:0.45!important;';

        var counter = document.createElement('div');
        counter.style.cssText = 'position:relative!important;z-index:2!important;width:100%!important;text-align:center!important;font-size:12px!important;font-weight:bold!important;color:#e8f4f2!important;letter-spacing:1.5px!important;font-family:\'Segoe UI\',sans-serif!important;text-shadow:0 1px 5px rgba(0,0,0,0.9)!important;line-height:26px!important;';
        counter.textContent = '0 / ' + _fillTotal;
        _counterEl = counter;

        overlay.appendChild(bar);
        overlay.appendChild(counter);
        document.body.appendChild(overlay);

        var _readyCount = 0;
        var _pollTimer = setInterval(function() {
            var r = panel.getBoundingClientRect();
            overlay.style.left  = r.left + 'px';
            overlay.style.top   = (r.bottom - 26) + 'px';
            overlay.style.width = r.width + 'px';

            var total = _fillTotal;
            var done  = _fillDone;
            if (total === 0) return;

            bar.style.width = Math.min((done / total) * 100, 100) + '%';

            if (done >= total) { _readyCount++; } else { _readyCount = 0; }

            if (_readyCount >= 3) {
                clearInterval(_pollTimer);
                bar.style.width = '100%';
                setTimeout(function() {
                    _counterEl = null;
                    _overlayActive = false;
                    overlay.style.cssText += 'opacity:0!important;transition:opacity 0.4s!important;';
                    setTimeout(function() {
                        if (overlay.parentNode) overlay.parentNode.removeChild(overlay);
                        panel.style.animation = 'none';
                        panel.style.opacity = '1';
                        void panel.offsetHeight;
                        panel.style.transition = 'opacity 1.2s ease, transform 1.2s ease';
                        panel.style.opacity = '0';
                        panel.style.transform = 'translate(-50%, -50%) scale(0.82)';
                        setTimeout(function() { if (panel.parentNode) panel.parentNode.removeChild(panel); }, 1300);
                    }, 420);
                }, 500);
            }
        }, 100);
    }

    fillField = function(selector, value) {
        var isNewBatch = _fillQueue.length === 0 && _fillTimer === null && !_batchPending;
        if (isNewBatch) {
            _fillDone = 0;
            _fillTotal = 0;
            _overlayActive = false;
            _batchPending = true;
            /* Ждём 80мс — за это время все синхронные fillField успеют встать в очередь.
               Потом пересчитываем шаг: FILL_STEP_MS = 3000 / кол-во_полей */
            setTimeout(function() {
                _batchPending = false;
                FILL_STEP_MS = _fillTotal > 0 ? Math.max(50, Math.floor(FILL_TARGET_MS / _fillTotal)) : 150;
                _runFillQueue();
            }, 80);
            _overlayActive = true;
            setTimeout(_createProgressOverlay, 0);
        }
        _fillTotal++;
        _updateCounter();
        _fillQueue.push({ s: selector, v: value });
        if (!isNewBatch && !_batchPending) {
            _runFillQueue();
        }
    };

    showToast('⚡ скриптонит запущен');
})();
