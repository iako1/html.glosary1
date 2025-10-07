[deepseek_html_20251007_45915a (11).html](https://github.com/user-attachments/files/22754637/deepseek_html_20251007_45915a.11.html)
<!DOCTYPE html>
<html lang="ka">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UI ელემენტების გლოსარი ბაგ რეპორტებისთვის</title>
    <style>
        :root {
            --primary-color: #4a00e0;
            --secondary-color: #8e2de2;
            --accent-color: #00ffcc;
            --text-color: #fff;
            --bg-dark: rgba(0,0,0,0.7);
            --bg-light: rgba(255,255,255,0.1);
            --border-color: rgba(255,255,255,0.2);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background: linear-gradient(270deg, #ff00cc, #3333ff, #00ffcc, #ffcc00);
            background-size: 800% 800%;
            animation: gradientBG 120s ease infinite;
            color: var(--text-color);
            min-height: 100vh;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            padding: 20px;
            background-color: var(--bg-dark);
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            color: var(--text-color);
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 20px;
        }

        .search-container {
            max-width: 500px;
            margin: 0 auto 20px;
            position: relative;
        }

        #searchInput {
            width: 100%;
            padding: 12px 20px;
            border-radius: 30px;
            border: none;
            background-color: rgba(255,255,255,0.15);
            color: var(--text-color);
            font-size: 1rem;
            backdrop-filter: blur(5px);
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
        }

        #searchInput:focus {
            outline: none;
            background-color: rgba(255,255,255,0.25);
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        #searchInput::placeholder {
            color: rgba(255,255,255,0.7);
        }

        .controls {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .filter-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .filter-btn {
            padding: 8px 16px;
            border-radius: 20px;
            border: 1px solid var(--border-color);
            background-color: var(--bg-light);
            color: var(--text-color);
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .filter-btn:hover, .filter-btn.active {
            background-color: var(--accent-color);
            color: #000;
            border-color: var(--accent-color);
        }

        .sort-options {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        select {
            padding: 8px 12px;
            border-radius: 5px;
            border: 1px solid var(--border-color);
            background-color: var(--bg-light);
            color: var(--text-color);
            cursor: pointer;
        }

        select:focus {
            outline: none;
            border-color: var(--accent-color);
        }

        .table-container {
            overflow-x: auto;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            background-color: var(--bg-dark);
            margin-bottom: 30px;
            max-height: 70vh;
            overflow-y: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            animation: tableFadeIn 1.5s ease forwards;
        }

        @keyframes tableFadeIn {
            0% { opacity: 0; transform: translateY(20px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid var(--border-color);
            transition: all 0.3s ease;
        }

        th {
            background-color: rgba(0,255,255,0.2);
            font-weight: bold;
            position: sticky;
            top: 0;
            cursor: pointer;
            user-select: none;
        }

        th:hover {
            background-color: rgba(0,255,255,0.3);
        }

        tr {
            transition: all 0.3s ease;
        }

        tr:hover {
            background-color: var(--bg-light);
            transform: scale(1.01);
        }

        /* Limited colors for terms */
        tbody tr:nth-child(2n+1) td:first-child { color: #FFD700; font-weight: 600; }
        tbody tr:nth-child(2n) td:first-child { color: #87CEEB; font-weight: 600; }

        a {
            color: var(--accent-color);
            text-decoration: none;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }

        a:hover {
            text-decoration: underline;
            color: #fff;
        }

        .external-icon {
            font-size: 0.8rem;
        }

        .results-info {
            text-align: center;
            margin-bottom: 20px;
            font-size: 1.1rem;
        }

        .no-results {
            text-align: center;
            padding: 40px;
            font-size: 1.2rem;
            color: rgba(255,255,255,0.7);
        }

        footer {
            text-align: center;
            padding: 20px;
            margin-top: 30px;
            border-top: 1px solid var(--border-color);
            font-size: 0.9rem;
            color: rgba(255,255,255,0.7);
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .controls {
                flex-direction: column;
            }
            
            .filter-buttons, .sort-options {
                width: 100%;
                justify-content: center;
            }
            
            table, thead, tbody, th, td, tr {
                display: block;
            }
            
            thead tr {
                position: absolute;
                top: -9999px;
                left: -9999px;
            }
            
            tr {
                border: 1px solid var(--border-color);
                margin-bottom: 10px;
                border-radius: 5px;
            }
            
            td {
                border: none;
                position: relative;
                padding-left: 50%;
            }
            
            td:before {
                position: absolute;
                top: 15px;
                left: 15px;
                width: 45%;
                padding-right: 10px;
                white-space: nowrap;
                font-weight: bold;
            }
            
            td:nth-of-type(1):before { content: "ტერმინი"; }
            td:nth-of-type(2):before { content: "განმარტება (ინგლისური)"; }
            td:nth-of-type(3):before { content: "განმარტება (ქართული)"; }
            td:nth-of-type(4):before { content: "ვიზუალური მაგალითი"; }
        }

        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            td {
                padding-left: 40%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>UI ელემენტების გლოსარი ბაგ რეპორტებისთვის</h1>
            <p class="subtitle">ყოვლისმომცველი საცნობარო UI/UX ტერმინებისთვის</p>
            
            <div class="search-container">
                <input type="text" id="searchInput" placeholder="მოძებნეთ ტერმინი...">
            </div>
        </header>
        
        <div class="controls">
            <div class="filter-buttons">
                <button class="filter-btn active" data-filter="all">ყველა</button>
                <button class="filter-btn" data-filter="ui">UI ელემენტები</button>
                <button class="filter-btn" data-filter="ux">UX კონცეფციები</button>
                <button class="filter-btn" data-filter="design">დიზაინის პრინციპები</button>
                <button class="filter-btn" data-filter="development">დეველოპმენტი</button>
            </div>
            
            <div class="sort-options">
                <label for="sortSelect">დალაგება:</label>
                <select id="sortSelect">
                    <option value="name-asc">სახელი (ა-ჰ)</option>
                    <option value="name-desc">სახელი (ჰ-ა)</option>
                    <option value="category">კატეგორია</option>
                </select>
            </div>
        </div>
        
        <div class="results-info" id="resultsInfo"></div>
        
        <div class="table-container">
            <table>
                <thead>
                    <tr>
                        <th data-sort="name">ტერმინი</th>
                        <th data-sort="description">განმარტება (ინგლისური)</th>
                        <th>განმარტება (ქართული)</th>
                        <th>ვიზუალური მაგალითი</th>
                    </tr>
                </thead>
                <tbody id="glossaryTable">
                    <!-- Data will be populated by JavaScript -->
                </tbody>
            </table>
        </div>
        
        <div class="no-results" id="noResults" style="display: none;">
            მოძებნილ ტერმინებთან დაკავშირებით შედეგები ვერ მოიძებნა. სცადეთ სხვა საკვანძო სიტყვა.
        </div>
        
        <footer>
            <p>UI ელემენტების გლოსარი &copy; 2023 - შექმნილია დეველოპერებისა და დიზაინერებისთვის</p>
        </footer>
    </div>

    <script>
        // Glossary data with all terms and Georgian translations
        const glossaryData = [
            { term: "Accordion", definition: "A UI element that expands in place to expose hidden information.", georgian: "UI ელემენტი, რომელიც ადგილზე ვრცელდება ფარული ინფორმაციის გამოსავლენად.", category: "ui", link: "https://dribbble.com/tags/accordion" },
            { term: "Anchor Link", definition: "A link allowing navigation within the same page.", georgian: "ბმული, რომელიც საშუალებას იძლევა ნავიგაცია იმავე გვერდის შიგნით.", category: "ui", link: "https://dribbble.com/tags/anchor-link" },
            { term: "Avatar", definition: "A graphical representation of a user, typically displayed as a circular image.", georgian: "მომხმარებლის გრაფიკული წარმოდგენა, ჩვეულებრივ წრიული სურათის სახით.", category: "ui", link: "https://dribbble.com/tags/avatar" },
            { term: "Back-to-Top Button", definition: "A button that takes users back to the top of the page.", georgian: "ღილაკი, რომელიც მომხმარებლებს უბრუნდება გვერდის ზედა ნაწილში.", category: "ui", link: "https://dribbble.com/tags/back-to-top" },
            { term: "Bento Menu", definition: "A bento menu, named after bento boxes, represents a menu with grid items.", georgian: "ბენტოს მენიუ, ბენტოს ყუთების სახელწოდებით, წარმოადგენს მენიუს ბადის ელემენტებით.", category: "ui", link: "https://dribbble.com/tags/bento-menu" },
            { term: "Breadcrumb", definition: "These little trails of links help users figure out where they are within a website.", georgian: "ეს პატარა ბმულების კვალი ეხმარება მომხმარებლებს გაარკვიონ სად არიან ვებგვერდში.", category: "ui", link: "https://dribbble.com/tags/breadcrumb" },
            { term: "Button", definition: "Traditionally displayed as shapes with a label, buttons are a vital user element.", georgian: "ჩვეულებრივ ფორმებად ეტიკეტით წარმოდგენილი, ღილაკები მნიშვნელოვანი მომხმარებლის ელემენტია.", category: "ui", link: "https://dribbble.com/tags/button" },
            { term: "Card", definition: "Super popular these days, cards are small rectangular or square modules.", georgian: "ამ დღეებში უმაღლესად პოპულარულია, ბარათები პატარა მართკუთხა ან კვადრატული მოდულებია.", category: "ui", link: "https://dribbble.com/tags/card" },
            { term: "Carousel", definition: "Carousels allow users to browse through sets of content, like images or cards.", georgian: "კარუსელები საშუალებას აძლევს მომხმარებლებს გადაამოწმონ კონტენტის ნაკრები, როგორიცაა სურათები ან ბარათები.", category: "ui", link: "https://dribbble.com/tags/carousel" },
            { term: "Checkbox", definition: "In UI design, a checkbox appears exactly as the name suggests: a little square box.", georgian: "UI დიზაინში, ჩეკბოქსი ზუსტად იმას წარმოადგენს რასაც სახელი მიუთითებს: პატარა კვადრატული ყუთი.", category: "ui", link: "https://dribbble.com/tags/checkbox" },
            { term: "Comment", definition: "Pretty common around interfaces today, comments display content users input.", georgian: "დღეს ინტერფეისებში საკმაოდ გავრცელებულია, კომენტარები აჩვენებენ მომხმარებლის შეყვანილ კონტენტს.", category: "ui", link: "https://dribbble.com/tags/comment" },
            { term: "Döner Menu", definition: "A döner menu is a variation of the more well-known hamburger menu.", georgian: "დონერის მენიუ არის უფრო კარგად ცნობილი ჰამბურგერის მენიუს ვარიაცია.", category: "ui", link: "https://dribbble.com/tags/doner-menu" },
            { term: "Dropdown", definition: "This controversial UI element allows users to select an item from a list.", georgian: "ეს კონტროვერსიული UI ელემენტი საშუალებას აძლევს მომხმარებლებს აირჩიონ ელემენტი სიიდან.", category: "ui", link: "https://dribbble.com/tags/dropdown" },
            { term: "Feed", definition: "Feeds display user activity in chronological order.", georgian: "ფიდები აჩვენებენ მომხმარებლის აქტივობას ქრონოლოგიური თანმიმდევრობით.", category: "ui", link: "https://dribbble.com/tags/feed" },
            { term: "Form", definition: "Forms help users input sets of related information into the system.", georgian: "ფორმები ეხმარება მომხმარებლებს შეყვანენ დაკავშირებული ინფორმაციის ნაკრებს სისტემაში.", category: "ui", link: "https://dribbble.com/tags/form" },
            { term: "Hamburger Menu", definition: "These three little horizontal lines look slightly like America's quintessential meal.", georgian: "ეს სამი პატარა ჰორიზონტალური ხაზი ოდნავ ჰგავს ამერიკის კლასიკურ კერძს.", category: "ui", link: "https://dribbble.com/tags/hamburger-menu" },
            { term: "Icon", definition: "Icons are images used to communicate a variety of things to users.", georgian: "იკონები არის სურათები, რომლებიც გამოიყენება მომხმარებლებთან სხვადასხვა საგნის კომუნიკაციისთვის.", category: "ui", link: "https://dribbble.com/tags/icon" },
            { term: "Input Field", definition: "Input fields are, quite simply, a place for users to enter content.", georgian: "შეყვანის ველები, მარტივად რომ ვთქვათ, ადგილია მომხმარებლისთვის კონტენტის შესატანად.", category: "ui", link: "https://dribbble.com/tags/input-field" },
            { term: "Kebab Menu", definition: "Consisting of three vertical dots, the kebab menu represents a set of grouped options.", georgian: "სამი ვერტიკალური წერტილისგან შედგება, კებაბის მენიუ წარმოადგენს დაჯგუფებული ვარიანტების ნაკრებს.", category: "ui", link: "https://dribbble.com/tags/kebab-menu" },
            { term: "Loader", definition: "Loaders are designed to let users know the system is completing an action.", georgian: "ლოდერები შექმნილია იმისთვის, რომ მომხმარებლებს აცნობონ სისტემა ასრულებს ქმედებას.", category: "ui", link: "https://dribbble.com/tags/loader" },
            { term: "Meatballs Menu", definition: "Yet another member of the menu family is the meatballs menu—a set of three horizontal dots.", georgian: "მენიუს ოჯახის კიდევ ერთი წევრია მიტბოლის მენიუ—სამი ჰორიზონტალური წერტილის ნაკრები.", category: "ui", link: "https://dribbble.com/tags/meatballs-menu" },
            { term: "Modal", definition: "A modal window is a small box containing content or a message.", georgian: "მოდალური ფანჯარა არის პატარა ყუთი კონტენტის ან შეტყობინების შეკვებით.", category: "ui", link: "https://dribbble.com/tags/modal" },
            { term: "Notification", definition: "They let us know there is something new, like a message.", georgian: "ისინი გვაცნობენ ახალი რაღაცის შესახებ, როგორიცაა შეტყობინება.", category: "ui", link: "https://dribbble.com/tags/notification" },
            { term: "Pagination", definition: "Typically found near the bottom of a page, pagination organizes content into pages.", georgian: "ჩვეულებრივ გვერდის ძირის სიახლოვეს მდებარეობს, პაგინაცია აწყობს კონტენტს გვერდებად.", category: "ui", link: "https://dribbble.com/tags/pagination" },
            { term: "Picker", definition: "Date and time pickers let users pick dates and times.", georgian: "თარიღის და დროის პიკერები საშუალებას აძლევს მომხმარებლებს აირჩიონ თარიღები და დროები.", category: "ui", link: "https://dribbble.com/tags/picker" },
            { term: "Progress Bar", definition: "Progress bars help users visualize where they are in a series of steps.", georgian: "პროგრესის ზოლები ეხმარება მომხმარებლებს წარმოიდგინონ სად არიან ნაბიჯების სერიაში.", category: "ui", link: "https://dribbble.com/tags/progress-bar" },
            { term: "Radio Buttons", definition: "Often confused with checkboxes, radio buttons are small circular elements.", georgian: "ხშირად ადგილს უთმობს ჩეკბოქსებს, რადიო ღილაკები პატარა წრიული ელემენტებია.", category: "ui", link: "https://dribbble.com/tags/radio-buttons" },
            { term: "Search Field", definition: "Commonly represented as an input field with a little magnifying glass.", georgian: "ჩვეულებრივ წარმოდგენილია შეყვანის ველად პატარა გამძრავლის ყვავილით.", category: "ui", link: "https://dribbble.com/tags/search-field" },
            { term: "Sidebar", definition: "A sidebar displays a group of navigational actions or content.", georgian: "საიდბარი აჩვენებს ნავიგაციის ქმედებების ან კონტენტის ჯგუფს.", category: "ui", link: "https://dribbble.com/tags/sidebar" },
            { term: "Slider Controls", definition: "Sliders are a common UI element used for selecting a value or a range of values.", georgian: "სლაიდერები ჩვეულებრივი UI ელემენტია მნიშვნელობის ან მნიშვნელობების დიაპაზონის შერჩევისთვის.", category: "ui", link: "https://dribbble.com/tags/slider-controls" },
            { term: "Stepper", definition: "Steppers are two-segment controls that also let users adjust a value.", georgian: "სტეპერები ორ-სეგმენტიანი კონტროლებია, რომლებიც საშუალებას აძლევს მომხმარებლებს შეცვალონ მნიშვნელობა.", category: "ui", link: "https://dribbble.com/tags/stepper" },
            { term: "Tag", definition: "In UI design, tags are essentially labels which help to mark and categorize content.", georgian: "UI დიზაინში, ტეგები ძირითადად ეტიკეტებია, რომლებიც ეხმარება კონტენტის მონიშვნას და კატეგორიზაციას.", category: "ui", link: "https://dribbble.com/tags/tag" },
            { term: "Tab Bar", definition: "Tab bars appear at the bottom of a mobile app.", georgian: "ტაბ ბარები გამოჩნდება მობილური აპლიკაციის ძირის ნაწილში.", category: "ui", link: "https://dribbble.com/tags/tab-bar" },
            { term: "Tooltip", definition: "Tooltips provide little hints that help users understand a part or process.", georgian: "ტულტიპები უზრუნველყოფს პატარა მინიშნებებს, რომლებიც ეხმარება მომხმარებლებს გაიაზრონ ნაწილი ან პროცესი.", category: "ui", link: "https://dribbble.com/tags/tooltip" },
            { term: "Toggle", definition: "Think of toggles as on and off switches.", georgian: "გაიაზრეთ ტოგლები როგორც ჩართვა-გამორთვის გადამრთველები.", category: "ui", link: "https://dribbble.com/tags/toggle" },
            { term: "Badge", definition: "Indicates a notification or an item count. A badge usually appears on top of an icon.", georgian: "მიუთითებს შეტყობინებაზე ან ელემენტის რაოდენობაზე. ბეჯი ჩვეულებრივ იკონის ზედა ნაწილში გამოჩნდება.", category: "ui", link: "https://dribbble.com/tags/badge" },
            { term: "Bottom Sheet", definition: "An overlay that is anchored to the bottom edge of a mobile device's screen.", georgian: "ოვერლეი, რომელიც მიბმულია მობილური მოწყობილობის ეკრანის ქვედა კიდეზე.", category: "ui", link: "https://dribbble.com/tags/bottom-sheet" },
            { term: "Calendar Picker", definition: "A special type of date-input control that allows users to select a date from a calendar.", georgian: "სპეციალური ტიპის თარიღის შეყვანის კონტროლი, რომელიც საშუალებას აძლევს მომხმარებლებს აირჩიონ თარიღი კალენდრიდან.", category: "ui", link: "https://dribbble.com/tags/calendar-picker" },
            { term: "Dialog", definition: "A small window appears in front of the main application window to provide critical information.", georgian: "პატარა ფანჯარა გამოჩნდება მთავარი აპლიკაციის ფანჯრის წინ კრიტიკული ინფორმაციის მისაღებად.", category: "ui", link: "https://dribbble.com/tags/dialog" },
            { term: "Drawer Menu", definition: "A menu that appears in a side sheet, sliding out from the left or right side.", georgian: "მენიუ, რომელიც გამოჩნდება გვერდით ფურცელში, გადახტომით მარცხნიდან ან მარჯვნიდან.", category: "ui", link: "https://dribbble.com/tags/drawer-menu" },
            { term: "Floating Button", definition: "A button that hovers over the content of a page.", georgian: "ღილაკი, რომელიც ჰუვერავს გვერდის კონტენტზე.", category: "ui", link: "https://dribbble.com/tags/floating-button" },
            { term: "Listbox", definition: "A type of input control that displays a list of selectable items in a container.", georgian: "შეყვანის კონტროლის ტიპი, რომელიც აჩვენებს შერჩევადი ელემენტების სიას კონტეინერში.", category: "ui", link: "https://dribbble.com/tags/listbox" },
            { term: "Megamenu", definition: "An expandable menu in which the collection of options is displayed in a rectangle.", georgian: "გაშლადი მენიუ, რომელშიც ვარიანტების კოლექცია გამოჩნდება მართკუთხედში.", category: "ui", link: "https://dribbble.com/tags/megamenu" },
            { term: "Overlay", definition: "A UI element used to display content on top of existing page content.", georgian: "UI ელემენტი, რომელიც გამოიყენება კონტენტის გამოსატანად არსებული გვერდის კონტენტის ზემოთ.", category: "ui", link: "https://dribbble.com/tags/overlay" },
            { term: "Progress Indicator", definition: "A UI element that provides visual feedback on the completion status of an ongoing process.", georgian: "UI ელემენტი, რომელიც უზრუნველყოფს ვიზუალურ უკუკავშირს მიმდინარე პროცესის დასრულების სტატუსზე.", category: "ui", link: "https://dribbble.com/tags/progress-indicator" },
            { term: "Scrollbar", definition: "An element used to indicate and control the portion of a container or page that is visible.", georgian: "ელემენტი, რომელიც გამოიყენება კონტეინერის ან გვერდის ხილული ნაწილის მონიშვნისა და კონტროლისთვის.", category: "ui", link: "https://dribbble.com/tags/scrollbar" },
            { term: "Segmented Button", definition: "A user-interface element that displays a group of connected buttons laid out in a horizontal row.", georgian: "მომხმარებლის ინტერფეისის ელემენტი, რომელიც აჩვენებს დაკავშირებული ღილაკების ჯგუფს ჰორიზონტალურ რიგში.", category: "ui", link: "https://dribbble.com/tags/segmented-button" },
            { term: "Skeleton Screen", definition: "A specific type of progress indicator used exclusively for full-page loads.", georgian: "სპეციფიკური ტიპის პროგრესის ინდიკატორი, რომელიც გამოიყენება მხოლოდ სრული გვერდის ჩატვირთვისთვის.", category: "ui", link: "https://dribbble.com/tags/skeleton-screen" },
            { term: "Snackbar", definition: "A transient nonmodal dialog that usually informs the user about the status of a process.", georgian: "დროებითი არამოდალური დიალოგი, რომელიც ჩვეულებრივ აცნობს მომხმარებელს პროცესის სტატუსის შესახებ.", category: "ui", link: "https://dribbble.com/tags/snackbar" },
            { term: "Spinner", definition: "A type of progress indicator used to signify that a process is ongoing.", georgian: "პროგრესის ინდიკატორის ტიპი, რომელიც მიუთითებს მიმდინარე პროცესზე.", category: "ui", link: "https://dribbble.com/tags/spinner" },
            { term: "Textbox", definition: "An input control that allows users to type text within a defined rectangular area.", georgian: "შეყვანის კონტროლი, რომელიც საშუალებას აძლევს მომხმარებლებს შეიტანონ ტექსტი განსაზღვრულ მართკუთხა არეში.", category: "ui", link: "https://dribbble.com/tags/textbox" },
            { term: "Combo Box", definition: "An input control that combines the features of a dropdown list and a textbox.", georgian: "შეყვანის კონტროლი, რომელიც აერთიანებს დროპდაუნ სიის და ტექსტბოქსის მახასიათებლებს.", category: "ui", link: "https://dribbble.com/tags/combo-box" },
            { term: "Contextual Menu", definition: "A type of menu that appears on demand and contains a small set of relevant actions.", georgian: "მენიუს ტიპი, რომელიც გამოჩნდება მოთხოვნის მიხედვით და შეიცავს მცირე რაოდენობის შესაბამის ქმედებებს.", category: "ui", link: "https://dribbble.com/tags/contextual-menu" },
            { term: "Date Picker", definition: "A date-input control that allows users to select a date.", georgian: "თარიღის შეყვანის კონტროლი, რომელიც საშუალებას აძლევს მომხმარებლებს აირჩიონ თარიღი.", category: "ui", link: "https://dribbble.com/tags/date-picker" },
            { term: "Expandable Menu", definition: "A menu in which the collection of options is expandable.", georgian: "მენიუ, რომელშიც ვარიანტების კოლექცია გაშლადია.", category: "ui", link: "https://dribbble.com/tags/expandable-menu" },
            { term: "Knob", definition: "A type of range control in which the available values are displayed on a circle.", georgian: "დიაპაზონის კონტროლის ტიპი, რომელშიც ხელმისაწვდომი მნიშვნელობები წრეში გამოჩნდება.", category: "ui", link: "https://dribbble.com/tags/knob" },
            { term: "Lightbox", definition: "An overlay that does not occupy the full screen.", georgian: "ოვერლეი, რომელიც არ იკავებს მთელ ეკრანს.", category: "ui", link: "https://dribbble.com/tags/lightbox" },
            { term: "Hyperlink", definition: "A UI element that allows users to jump from one location to another.", georgian: "UI ელემენტი, რომელიც საშუალებას აძლევს მომხმარებლებს გადახტომას ერთი ადგილიდან მეორეზე.", category: "ui", link: "https://dribbble.com/tags/hyperlink" },
            { term: "Menu Bar", definition: "A type of menu in which the collection of options is visible at all times.", georgian: "მენიუს ტიპი, რომელშიც ვარიანტების კოლექცია ყოველთვის ხილულია.", category: "ui", link: "https://dribbble.com/tags/menu-bar" },
            { term: "Navigation Bar", definition: "A type of navigation menu implemented as a menu bar hosting navigation categories.", georgian: "ნავიგაციის მენიუს ტიპი, რომელიც განხორციელებულია მენიუს ბარად ნავიგაციის კატეგორიების მასპინძლობლობით.", category: "ui", link: "https://dribbble.com/tags/navigation-bar" },
            { term: "Pie Menu", definition: "A type of expandable menu in which all the menu options are placed on a circle.", georgian: "გაშლადი მენიუს ტიპი, რომელშიც ყველა მენიუს ვარიანტი წრეზეა განთავსებული.", category: "ui", link: "https://dribbble.com/tags/pie-menu" },
            { term: "Popover", definition: "An overlay that does not occupy the whole screen.", georgian: "ოვერლეი, რომელიც არ იკავებს მთელ ეკრანს.", category: "ui", link: "https://dribbble.com/tags/popover" },
            { term: "Popup Tip", definition: "A small overlay displaying a brief, informative message.", georgian: "პატარა ოვერლეი მოკლე, ინფორმაციული შეტყობინების გამოსატანად.", category: "ui", link: "https://dribbble.com/tags/popup-tip" },
            { term: "Ribbon", definition: "A UI element that presents various controls and tools grouped into a set of tabs.", georgian: "UI ელემენტი, რომელიც წარმოადგენს სხვადასხვა კონტროლებს და ინსტრუმენტებს ტაბების ნაკრებში.", category: "ui", link: "https://dribbble.com/tags/ribbon" },
            { term: "Split Button", definition: "A hybrid between a menu and a button.", georgian: "ჰიბრიდი მენიუსა და ღილაკს შორის.", category: "ui", link: "https://dribbble.com/tags/split-button" },
            { term: "Submenu", definition: "A secondary menu that appears as part of a larger menu.", georgian: "მეორადი მენიუ, რომელიც გამოჩნდება უფრო დიდი მენიუს ნაწილად.", category: "ui", link: "https://dribbble.com/tags/submenu" },
            { term: "Wheel Picker", definition: "An iOS-specific picker that displays the options available for selection using a wheel-like interface.", georgian: "iOS-სპეციფიკური პიკერი, რომელიც აჩვენებს შერჩევისთვის ხელმისაწვდომ ვარიანტებს რადიოს მსგავსი ინტერფეისით.", category: "ui", link: "https://dribbble.com/tags/wheel-picker" },
            { term: "2D Matrix Input Control", definition: "A specialized input control used primarily in complex applications to modify multiple parameters.", georgian: "სპეციალიზებული შეყვანის კონტროლი, რომელიც ძირითადად გამოიყენება კომპლექსურ აპლიკაციებში მრავალ პარამეტრის შესაცვლელად.", category: "ui", link: "https://dribbble.com/tags/2d-matrix-input-control" },
            { term: "Input Stepper", definition: "A UI input control used to incrementally increase or decrease a default numeric value.", georgian: "UI შეყვანის კონტროლი, რომელიც გამოიყენება ნაგულისხმევი რიცხვითი მნიშვნელობის თანდათანობით გაზრდის ან შემცირებისთვის.", category: "ui", link: "https://dribbble.com/tags/input-stepper" },
            { term: "State Switch Control", definition: "A control designed to move the system between two mutually exclusive states.", georgian: "კონტროლი, რომელიც შექმნილია სისტემის გადატანისთვის ორ ურთიერთგამომრიცხავ სტატუსს შორის.", category: "ui", link: "https://dribbble.com/tags/state-switch-control" },
            { term: "Call to Action", definition: "A call-to-action button encourages users to take a specific action.", georgian: "მოქმედების მოწოდების ღილაკი მომხმარებლებს უბიძგებს კონკრეტული ქმედებისკენ.", category: "ui", link: "https://dribbble.com/tags/call-to-action" },
            { term: "Dropdown Button", definition: "The clickable button used in a dropdown list to reveal a list of items.", georgian: "დაკლიკებადი ღილაკი დროპდაუნ სიაში ელემენტების სიის გამოსავლენად.", category: "ui", link: "https://dribbble.com/tags/dropdown-button" },
            { term: "Plus Button", definition: "Usually shaped like a plus sign, the plus button indicates that new content can be added.", georgian: "ჩვეულებრივ პლუსის ნიშნის ფორმისაა, პლუსის ღილაკი მიუთითებს ახალი კონტენტის დამატების შესაძლებლობაზე.", category: "ui", link: "https://dribbble.com/tags/plus-button" },
            { term: "Primary Button", definition: "The primary button lets us know which action is the most important.", georgian: "პრიმარული ღილაკი გვაცნობს რომელი ქმედებაა ყველაზე მნიშვნელოვანი.", category: "ui", link: "https://dribbble.com/tags/primary-button" },
            { term: "Secondary Button", definition: "The secondary button is still an important CTA but less important than the primary.", georgian: "სეკონდარული ღილაკი კვლავ მნიშვნელოვანი CTA-ია, მაგრამ ნაკლებად მნიშვნელოვანი ვიდრე პრიმარული.", category: "ui", link: "https://dribbble.com/tags/secondary-button" },
            { term: "Share Button", definition: "The share button is used to share a page or a product externally.", georgian: "გაზიარების ღილაკი გამოიყენება გვერდის ან პროდუქტის გარე გაზიარებისთვის.", category: "ui", link: "https://dribbble.com/tags/share-button" },
            { term: "Message Box", definition: "A small window that pops up, providing information to users.", georgian: "პატარა ფანჯარა, რომელიც გამოდის და აწვდის ინფორმაციას მომხმარებლებს.", category: "ui", link: "https://dribbble.com/tags/message-box" },
            { term: "Grid", definition: "In UI design, a grid is a layout constraint that determines where UI elements will sit.", georgian: "UI დიზაინში, ბადე არის განლაგების შეზღუდვა, რომელიც განსაზღვრავს სად იჯდება UI ელემენტები.", category: "ui", link: "https://dribbble.com/tags/grid" },
            { term: "Gutter", definition: "Gutters are the vertical strips between columns in grids.", georgian: "გუტერები არის ვერტიკალური ზოლები ბადის სვეტებს შორის.", category: "ui", link: "https://dribbble.com/tags/gutter" },
            { term: "Logo", definition: "A logo is a symbol or a small design used by companies to identify their products.", georgian: "ლოგო არის სიმბოლო ან პატარა დიზაინი, რომელსაც კომპანიები იყენებენ პროდუქტების იდენტიფიკაციისთვის.", category: "ui", link: "https://dribbble.com/tags/logo" },
            { term: "Menu", definition: "A collection of options or commands presented to the user.", georgian: "ვარიანტების ან ბრძანებების კოლექცია მომხმარებლისთვის.", category: "ui", link: "https://dribbble.com/tags/menu" },
            { term: "Navigation Menu", definition: "A menu that hosts navigation options.", georgian: "მენიუ, რომელიც მასპინძლობს ნავიგაციის ვარიანტებს.", category: "ui", link: "https://dribbble.com/tags/navigation-menu" },
            { term: "Range Control", definition: "A type of picker that allows the selection of any possible value within a predefined range.", georgian: "პიკერის ტიპი, რომელიც საშუალებას აძლევს აირჩიოს ნებისმიერი შესაძლო მნიშვნელობა წინასწარ განსაზღვრულ დიაპაზონში.", category: "ui", link: "https://dribbble.com/tags/range-control" },
            { term: "Side Sheet", definition: "A type of overlay that slides out from the left or right edge of the screen.", georgian: "ოვერლეის ტიპი, რომელიც გადახტება ეკრანის მარცხენა ან მარჯვენა კიდიდან.", category: "ui", link: "https://dribbble.com/tags/side-sheet" },
            { term: "Wheel Style Date Picker", definition: "An iOS-specific date picker that lets users select date and time values using a rotating wheel.", georgian: "iOS-სპეციფიკური თარიღის პიკერი, რომელიც საშუალებას აძლევს მომხმარებლებს აირჩიონ თარიღის და დროის მნიშვნელობები ბრუნავა როტაციის გამოყენებით.", category: "ui", link: "https://dribbble.com/tags/wheel-style-date-picker" },
            { term: "Control", definition: "Any interactive UI element that allows users to perform an action or input data.", georgian: "ნებისმიერი ინტერაქტიული UI ელემენტი, რომელიც საშუალებას აძლევს მომხმარებლებს შეასრულონ ქმედება ან შეიტანონ მონაცემები.", category: "ui", link: "https://dribbble.com/tags/control" },
            { term: "Input Control", definition: "Any UI component that allows users to input information into a system.", georgian: "ნებისმიერი UI კომპონენტი, რომელიც საშუალებას აძლევს მომხმარებლებს შეიტანონ ინფორმაცია სისტემაში.", category: "ui", link: "https://dribbble.com/tags/input-control" },
            { term: "Accessible Design", definition: "Accessibility or accessible design helps users of all abilities to interact with a product.", georgian: "ხელმისაწვდომობა ან ხელმისაწვდომი დიზაინი ეხმარება ყველა შესაძლებლობის მომხმარებლებს პროდუქტთან ურთიერთობაში.", category: "design", link: "https://dribbble.com/tags/accessible-design" },
            { term: "Alignment", definition: "Alignment is the design principle that is used to create structure and readability.", georgian: "მიბმა არის დიზაინის პრინციპი, რომელიც გამოიყენება სტრუქტურისა და წაკითხვადობის შესაქმნელად.", category: "design", link: "https://dribbble.com/tags/alignment" },
            { term: "Baseline", definition: "The baseline is the invisible line where text sits on a page.", georgian: "ბეისლაინი არის უხილავი ხაზი, სადაც ტექსტი ზის გვერდზე.", category: "design", link: "https://dribbble.com/tags/baseline" },
            { term: "Breakpoints", definition: "A breakpoint is the predetermined ranges in screen sizes that require changes in layouts.", georgian: "ბრეიქპოინტი არის წინასწარ განსაზღვრული დიაპაზონები ეკრანის ზომებში, რომლებიც მოითხოვს განლაგების ცვლილებებს.", category: "design", link: "https://dribbble.com/tags/breakpoints" },
            { term: "Chunking", definition: "Chunking is used by designers to break down large chunks of information into smaller ones.", georgian: "ჩანკინგი გამოიყენება დიზაინერების მიერ დიდი ინფორმაციის ნაჭრების პატარა ნაჭრებად დაყოფისთვის.", category: "design", link: "https://dribbble.com/tags/chunking" },
            { term: "Color Palette", definition: "A color palette is a small combination of colors for a new design.", georgian: "ფერის პალიტრა არის პატარა კომბინაცია ფერების ახალი დიზაინისთვის.", category: "design", link: "https://dribbble.com/tags/color-palette" },
            { term: "Color Models", definition: "A color model is a system that helps to describe colors using numbers or letters.", georgian: "ფერის მოდელი არის სისტემა, რომელიც ეხმარება ფერების აღწერაში რიცხვებით ან ასოებით.", category: "design", link: "https://dribbble.com/tags/color-models" },
            { term: "Counters", definition: "In typography, a counter is the area of a letter that is enclosed by a letter or symbol.", georgian: "ტიპოგრაფიაში, კაუნტერი არის ასოების ან სიმბოლოების მიერ შეკრული ასოს არე.", category: "design", link: "https://dribbble.com/tags/counters" },
            { term: "Date Time Picker", definition: "A date or time picker allows users to select a date and/or time from a digital calendar.", georgian: "თარიღის ან დროის პიკერი საშუალებას აძლევს მომხმარებლებს აირჩიონ თარიღი და/ან დრო ციფრული კალენდრიდან.", category: "design", link: "https://dribbble.com/tags/date-time-picker" },
            { term: "Descenders", definition: "In typography, descenders are the letters that fall under the x-height and below the baseline.", georgian: "ტიპოგრაფიაში, დესენდერები არის ასოები, რომლებიც ეცემა x-სიმაღლის ქვემოთ და ბეისლაინის ქვემოთ.", category: "design", link: "https://dribbble.com/tags/descenders" },
            { term: "Design Patterns", definition: "UX and UI design patterns are repeatable, reusable design components.", georgian: "UX და UI დიზაინის პატერნები არის განმეორებადი, ხელახლა გამოყენებადი დიზაინის კომპონენტები.", category: "design", link: "https://dribbble.com/tags/design-patterns" },
            { term: "Design Systems", definition: "A design system is a universal source of truth for the design team.", georgian: "დიზაინის სისტემა არის უნივერსალური სიმართლის წყარო დიზაინის გუნდისთვის.", category: "design", link: "https://dribbble.com/tags/design-systems" },
            { term: "Easing", definition: "Easing refers to the movement of the animation and how it gradually begins to move.", georgian: "იუზინგი მიუთითებს ანიმაციის მოძრაობაზე და როგორ იწყება ის თანდათანობით.", category: "design", link: "https://dribbble.com/tags/easing" },
            { term: "Font", definition: "Font is the name given to the particular size, weight and style of a typeface.", georgian: "შრიფტი არის სახელი, რომელიც მიენიჭება ტიპოგრაფიის კონკრეტულ ზომას, წონას და სტილს.", category: "design", link: "https://dribbble.com/tags/font" },
            { term: "Form Field States", definition: "Digital forms should change their state or appearance so that users know what to do.", georgian: "ციფრული ფორმები უნდა შეცვალონ თავიანთი სტატუსი ან გარეგნობა, რათა მომხმარებლები იცოდნენ რა უნდა გააკეთონ.", category: "design", link: "https://dribbble.com/tags/form-field-states" },
            { term: "Gestalt Principles", definition: "The Gestalt principles are a set of psychology laws that describe how our minds organise visual data.", georgian: "გეშტალტის პრინციპები არის ფსიქოლოგიის კანონების ნაკრები, რომლებიც აღწერს როგორ აწყობს ჩვენი გონება ვიზუალურ მონაცემებს.", category: "design", link: "https://dribbble.com/tags/gestalt-principles" },
            { term: "Hierarchy", definition: "Hierarchy is a UI design principle used to present information with different levels of emphasis.", georgian: "ჰიერარქია არის UI დიზაინის პრინციპი, რომელიც გამოიყენება ინფორმაციის წარდგენისთვის სხვადასხვა დონის ხაზგასმით.", category: "design", link: "https://dribbble.com/tags/hierarchy" },
            { term: "Line Height", definition: "Line height is the distance above and below lines of text.", georgian: "ხაზის სიმაღლე არის მანძილი ტექსტის ხაზებს ზემოთ და ქვემოთ.", category: "design", link: "https://dribbble.com/tags/line-height" },
            { term: "Margin", definition: "Margins are the areas sitting left and right of a grid.", georgian: "მარჯინები არის არეები ბადის მარცხენა და მარჯვენა მხარეს.", category: "design", link: "https://dribbble.com/tags/margin" },
            { term: "Moodboard", definition: "Moodboards are a collage of images, text and samples of objects in a design composition.", georgian: "მუდბორდები არის კოლაჟი სურათების, ტექსტის და ობიექტების ნიმუშების დიზაინის კომპოზიციაში.", category: "design", link: "https://dribbble.com/tags/moodboard" },
            { term: "Padding", definition: "Padding is the spacing inside grid columns.", georgian: "პედინგი არის სივრცე ბადის სვეტებს შიგნით.", category: "design", link: "https://dribbble.com/tags/padding" },
            { term: "Prototype", definition: "A prototype is a simulation or model of what the final product will look like.", georgian: "პროტოტიპი არის სიმულაცია ან მოდელი იმისა, თუ როგორი იქნება საბოლოო პროდუქტი.", category: "design", link: "https://dribbble.com/tags/prototype" },
            { term: "Responsive Design", definition: "Responsive design ensures that designs display accurately on different screen sizes.", georgian: "რესპონსიული დიზაინი უზრუნველყოფს, რომ დიზაინები სწორად გამოჩნდეს სხვადასხვა ეკრანის ზომებზე.", category: "design", link: "https://dribbble.com/tags/responsive-design" },
            { term: "Scanning Patterns", definition: "Designers must choose the placement of important text or images to accommodate scanning styles.", georgian: "დიზაინერებმა უნდა აირჩიონ მნიშვნელოვანი ტექსტის ან სურათების განთავსება სკანირების სტილების მოსაგებად.", category: "design", link: "https://dribbble.com/tags/scanning-patterns" },
            { term: "Text Field", definition: "Text fields allow users to enter text. Used in forms or questionnaires.", georgian: "ტექსტური ველები საშუალებას აძლევს მომხმარებლებს შეიტანონ ტექსტი. გამოიყენება ფორმებში ან კითხვარებში.", category: "design", link: "https://dribbble.com/tags/text-field" },
            { term: "Type", definition: "Type is the very basic description of any text or lettering on a screen.", georgian: "ტიპი არის ძირითადი აღწერა ნებისმიერი ტექსტის ან ასოების ეკრანზე.", category: "design", link: "https://dribbble.com/tags/type" },
            { term: "Typeface", definition: "Typeface is the design set of lettering.", georgian: "ტიპფეისი არის ასოების დიზაინის ნაკრები.", category: "design", link: "https://dribbble.com/tags/typeface" },
            { term: "Typography", definition: "Typography is the art of lettering itself.", georgian: "ტიპოგრაფია არის ასოების ხელოვნება თავისთავად.", category: "design", link: "https://dribbble.com/tags/typography" },
            { term: "Wireframes", definition: "A wireframe depicts the 'bare bones' of a website or app.", georgian: "ვაიერფრეიმი წარმოადგენს ვებგვერდის ან აპლიკაციის 'ჩონჩხს'.", category: "design", link: "https://dribbble.com/tags/wireframes" },
            { term: "X-Height", definition: "Designers use the height of a lowercase x to determine the height of all lowercase letters.", georgian: "დიზაინერები იყენებენ პატარა x-ის სიმაღლეს ყველა პატარა ასოს სიმაღლის განსასაზღვრად.", category: "design", link: "https://dribbble.com/tags/x-height" },
            { term: "Adaptive", definition: "An adaptive interface is a set of layouts designed specifically for different devices.", georgian: "ადაპტური ინტერფეისი არის განლაგებების ნაკრები, რომელიც სპეციალურად შექმნილია სხვადასხვა მოწყობილობებისთვის.", category: "design", link: "https://dribbble.com/tags/adaptive" },
            { term: "Affinity Map", definition: "Affinity mapping is a method used to interpret and group insights from a user research exercise.", georgian: "აფინიტის მაპინგი არის მეთოდი, რომელიც გამოიყენება მომხმარებლის კვლევის შედეგების ინტერპრეტაციისა და ჯგუფირებისთვის.", category: "ux", link: "https://dribbble.com/tags/affinity-map" },
            { term: "Affordance", definition: "Affordances are clues that tell us what an element can do to us.", georgian: "აფორდანსები არის მინიშნებები, რომლებიც გვეუბნება რას შეუძლია ელემენტს ჩვენთან.", category: "ux", link: "https://dribbble.com/tags/affordance" },
            { term: "Agile", definition: "Agile is a process by which a team can manage a project by breaking it up into several stages.", georgian: "აჯაილი არის პროცესი, რომლის მეშვეობით გუნდი მართავს პროექტს მის რამდენიმე ეტაპად დაყოფით.", category: "ux", link: "https://dribbble.com/tags/agile" },
            { term: "API", definition: "Application Programming Interfaces are pieces of software that help different applications communicate.", georgian: "აპლიკაციის პროგრამირების ინტერფეისები არის პროგრამული უზრუნველყოფის ნაწილები, რომლებიც ეხმარება სხვადასხვა აპლიკაციებს კომუნიკაციაში.", category: "development", link: "https://dribbble.com/tags/api" },
            { term: "Artificial Intelligence", definition: "Artificial intelligence refers to the simulation of human intelligence in machines.", georgian: "ხელოვნური ინტელექტი მიუთითებს ადამიანის ინტელექტის სიმულაციაზე მანქანებში.", category: "development", link: "https://dribbble.com/tags/artificial-intelligence" },
            { term: "Back and Front-End Development", definition: "Back end development refers to the server-side of an application.", georgian: "ბექენდის განვითარება მიუთითებს აპლიკაციის სერვერულ მხარეზე.", category: "development", link: "https://dribbble.com/tags/back-and-front-end-development" },
            { term: "Backlog", definition: "A backlog is a list of tasks required to support a larger strategic plan.", georgian: "ბეკლოგი არის ამოცანების სია, რომელიც საჭიროა უფრო დიდი სტრატეგიული გეგმის მხარდაჭერისთვის.", category: "development", link: "https://dribbble.com/tags/backlog" },
            { term: "Beta Testing", definition: "Beta testing is a soft launch of an unfinished product to a select group of users.", georgian: "ბეტა ტესტირება არის რბილი გაშვება დაუმთავრებელი პროდუქტის შერჩეული მომხმარებლების ჯგუფისთვის.", category: "development", link: "https://dribbble.com/tags/beta-testing" },
            { term: "Card Sorting", definition: "An exercise where participants are asked to sort a batch of cards into different categories.", georgian: "ვარჯიში, სადაც მონაწილეებს სთხოვენ დაალაგონ ბარათების პაკეტი სხვადასხვა კატეგორიებში.", category: "ux", link: "https://dribbble.com/tags/card-sorting" },
            { term: "Chatbot", definition: "Chatbots are a chat interface that allow the user to ask questions to the system.", georgian: "ჩატბოტები არის ჩატის ინტერფეისი, რომელიც საშუალებას აძლევს მომხმარებელს დაუსვას კითხვები სისტემას.", category: "ux", link: "https://dribbble.com/tags/chatbot" },
            { term: "Clickstream", definition: "Clickstream refers to the path of clicks taken by the user to accomplish a goal.", georgian: "კლიკსტრიმი მიუთითებს მომხმარებლის მიერ მიზნის მიღწევისთვის გადაცილებულ კლიკების გზაზე.", category: "ux", link: "https://dribbble.com/tags/clickstream" },
            { term: "Cognitive Load", definition: "Cognitive load is the amount of mental effort required to complete a certain task.", georgian: "კოგნიტური დატვირთვა არის გონებრივი ძალისხმევის რაოდენობა კონკრეტული ამოცანის შესასრულებლად.", category: "ux", link: "https://dribbble.com/tags/cognitive-load" },
            { term: "Consistency", definition: "Consistency is all about providing a consistent experience to the users.", georgian: "კონსისტენტობა ყველაფერია მომხმარებლებს თანმიმდევრული გამოცდილების მოწოდების შესახებ.", category: "ux", link: "https://dribbble.com/tags/consistency" },
            { term: "Contextual Enquiry", definition: "Contextual enquiry is a user research method that involves observing and interviewing users.", georgian: "კონტექსტუალური კვლევა არის მომხმარებლის კვლევის მეთოდი, რომელიც მოიცავს მომხმარებლების დაკვირვებას და ინტერვიუს.", category: "ux", link: "https://dribbble.com/tags/contextual-enquiry" },
            { term: "Customer Experience", definition: "Customer experience is the customers' holistic perception of their experience with a business.", georgian: "მომხმარებლის გამოცდილება არის მომხმარებლების ჰოლისტური აღქმა ბიზნესთან ურთიერთობის შესახებ.", category: "ux", link: "https://dribbble.com/tags/customer-experience" },
            { term: "Customer Journey Map", definition: "A customer journey map shows how a customer moves through an entire service.", georgian: "მომხმარებლის მოგზაურობის რუკა აჩვენებს როგორ მოძრაობს მომხმარებელი მთელ სერვისში.", category: "ux", link: "https://dribbble.com/tags/customer-journey-map" },
            { term: "Customer Relationship Management", definition: "CRM software systems help manage business processes like sales and customer interactions.", georgian: "CRM პროგრამული სისტემები ეხმარება ბიზნეს პროცესების მართვაში, როგორიცაა გაყიდვები და მომხმარებლის ურთიერთობები.", category: "ux", link: "https://dribbble.com/tags/customer-relationship-management" },
            { term: "Design Debt", definition: "Design debt is the natural decay that accrues as a project matures.", georgian: "დიზაინის დავალიანება არის ბუნებრივი დეგრადაცია, რომელიც გროვდება პროექტის მომწიფების შემდეგ.", category: "design", link: "https://dribbble.com/tags/design-debt" },
            { term: "Design Sprint", definition: "A design sprint is a collaborative methodology for rapidly identifying and solving a design problem.", georgian: "დიზაინის სპრინტი არის კოლაბორაციული მეთოდოლოგია დიზაინის პრობლემის სწრაფად იდენტიფიცირებისა და გადაჭრისთვის.", category: "ux", link: "https://dribbble.com/tags/design-sprint" },
            { term: "Empathy", definition: "Empathy is the ability to put yourself in someone else's shoes.", georgian: "ემპათია არის შესაძლებლობა დადგე სხვის ადგილზე.", category: "ux", link: "https://dribbble.com/tags/empathy" },
            { term: "Empathy Map", definition: "Empathy maps are collaborative tools that help visualize user behavior.", georgian: "ემპათიის რუკები არის კოლაბორაციული ინსტრუმენტები მომხმარებლის ქცევის ვიზუალიზაციისთვის.", category: "ux", link: "https://dribbble.com/tags/empathy-map" },
            { term: "End User", definition: "An end user is any user of an app or website.", georgian: "შეძლებული მომხმარებელი არის აპლიკაციის ან ვებგვერდის ნებისმიერი მომხმარებელი.", category: "ux", link: "https://dribbble.com/tags/end-user" },
            { term: "Eye Tracking", definition: "An advanced method for assessing the visual hierarchy of information on a screen.", georgian: "განსხვავებული მეთოდი ეკრანზე ინფორმაციის ვიზუალური ჰიერარქიის შეფასებისთვის.", category: "ux", link: "https://dribbble.com/tags/eye-tracking" },
            { term: "Fidelity", definition: "A concept in both wireframing and prototyping.", georgian: "კონცეფცია როგორც ვაიერფრეიმინგში, ასევე პროტოტიპინგში.", category: "ux", link: "https://dribbble.com/tags/fidelity" },
            { term: "Flat Design", definition: "Flat design is a user interface design style that uses simple, two-dimensional elements.", georgian: "ფლატ დიზაინი არის მომხმარებლის ინტერფეისის დიზაინის სტილი, რომელიც იყენებს მარტივ, ორ-განზომილებიან ელემენტებს.", category: "design", link: "https://dribbble.com/tags/flat-design" },
            { term: "Flowchart", definition: "Flowcharts illustrate the steps a user can take to complete a task on a product.", georgian: "ფლოუჩარტები ასახავს ნაბიჯებს, რომლებიც მომხმარებელი შეუძლია გადადგას პროდუქტზე ამოცანის შესასრულებლად.", category: "ux", link: "https://dribbble.com/tags/flowchart" },
            { term: "Floating Action Button", definition: "A UI element that sits on top of a screen design, often in the bottom-right-hand corner.", georgian: "UI ელემენტი, რომელიც ზის ეკრანის დიზაინის ზედა ნაწილში, ხშირად ძირ-მარჯვენა კუთხეში.", category: "ui", link: "https://dribbble.com/tags/floating-action-button" },
            { term: "Focus Group", definition: "A focus group is a UX research method that involves a group of users to discuss issues.", georgian: "ფოკუს ჯგუფი არის UX კვლევის მეთოდი, რომელიც მოიცავს მომხმარებლების ჯგუფს საკითხების განსახილველად.", category: "ux", link: "https://dribbble.com/tags/focus-group" },
            { term: "Full Stack", definition: "Full-stack refers to a person who has both front-end and back-end development skills.", georgian: "ფულ-სტეკი მიუთითებს პირს, რომელსაც აქვს როგორც ფრონტ-ენდის, ასევე ბექ-ენდის განვითარების უნარები.", category: "development", link: "https://dribbble.com/tags/full-stack" },
            { term: "Gamification", definition: "Gamification is the process of integrating game-design elements into products.", georgian: "გეიმიფიკაცია არის პროცესი თამაშის დიზაინის ელემენტების პროდუქტებში ინტეგრაციის.", category: "ux", link: "https://dribbble.com/tags/gamification" },
            { term: "Graphical User Interface", definition: "A GUI is a system of interactive visual components for computer software.", georgian: "GUI არის ინტერაქტიული ვიზუალური კომპონენტების სისტემა კომპიუტერული პროგრამული უზრუნველყოფისთვის.", category: "ui", link: "https://dribbble.com/tags/graphical-user-interface" },
            { term: "Graphics Interchange Format", definition: "A legacy web graphics format that has frame-by-frame animation.", georgian: "მემკვიდრეობითი ვებ გრაფიკის ფორმატი, რომელსაც აქვს ჩარჩოთა მიხედვით ანიმაცია.", category: "design", link: "https://dribbble.com/tags/graphics-interchange-format" },
            { term: "Heat Map", definition: "A heat map is a graphical representation of the areas on your product that receive the most user attention.", georgian: "ჰიტ მაპი არის გრაფიკული წარმოდგენა პროდუქტის იმ არეებისა, რომლებიც იღებს ყველაზე მეტ მომხმარებლის ყურადღებას.", category: "ux", link: "https://dribbble.com/tags/heat-map" },
            { term: "Hamburger Button", definition: "A visual pattern of three horizontal lines that typically indicates a hidden menu.", georgian: "ვიზუალური პატერნი სამი ჰორიზონტალური ხაზის, რომელიც ჩვეულებრივ მიუთითებს ფარული მენიუზე.", category: "ui", link: "https://dribbble.com/tags/hamburger-button" },
            { term: "Heuristics", definition: "A heuristic is a mental shortcut that enables people to solve problems quickly.", georgian: "ჰეურისტიკა არის გონებრივი შოურტკატი, რომელიც საშუალებას აძლევს ადამიანებს სწრაფად გადაჭრან პრობლემები.", category: "ux", link: "https://dribbble.com/tags/heuristics" },
            { term: "HyperText Markup Language", definition: "A markup standard used for coding web pages.", georgian: "მარკაპის სტანდარტი, რომელიც გამოიყენება ვებგვერდების კოდირებისთვის.", category: "development", link: "https://dribbble.com/tags/hypertext-markup-language" },
            { term: "Human-Computer Interaction", definition: "HCI is a field of study concerned with the design and use of computer technology.", georgian: "ადამიან-კომპიუტერის ურთიერთქმედება არის კვლევის სფერო, რომელიც ეხება კომპიუტერული ტექნოლოგიის დიზაინს და გამოყენებას.", category: "ux", link: "https://dribbble.com/tags/human-computer-interaction" },
            { term: "Hybrid App", definition: "Hybrid mobile apps combine both native and web technologies.", georgian: "ჰიბრიდული მობილური აპლიკაციები აერთიანებს როგორც ნატიურ, ასევე ვებ ტექნოლოგიებს.", category: "development", link: "https://dribbble.com/tags/hybrid-app" },
            { term: "Information Architecture", definition: "The structure and organization of information in a website or app.", georgian: "ინფორმაციის სტრუქტურა და ორგანიზაცია ვებგვერდზე ან აპლიკაციაში.", category: "ux", link: "https://dribbble.com/tags/information-architecture" },
            { term: "Interaction Design", definition: "Interaction Design is the practice of designing interactive digital products.", georgian: "ინტერაქციის დიზაინი არის ინტერაქტიული ციფრული პროდუქტების შექმნის პრაქტიკა.", category: "ux", link: "https://dribbble.com/tags/interaction-design" },
            { term: "Intuitive UX Design", definition: "Intuitive UX design is the creation of products that are easy to understand without instruction.", georgian: "ინტუიტიური UX დიზაინი არის პროდუქტების შექმნა, რომლებიც ადვილად გასაგებია ინსტრუქციის გარეშე.", category: "ux", link: "https://dribbble.com/tags/intuitive-ux-design" },
            { term: "Iteration", definition: "The process of repeatedly gathering feedback on a design solution.", georgian: "პროცესი დიზაინის გადაწყვეტის შესახებ უკუკავშირის განმეორებით შეგროვების.", category: "ux", link: "https://dribbble.com/tags/iteration" },
            { term: "Javascript", definition: "Javascript defines how HTML and CSS should behave.", georgian: "JavaScript განსაზღვრავს როგორ უნდა იქცეს HTML და CSS.", category: "development", link: "https://dribbble.com/tags/javascript" },
            { term: "KPI", definition: "KPIs are measurable values that help track how well a product is doing.", georgian: "KPI-ები არის გაზომვადი მნიშვნელობები, რომლებიც ეხმარება პროდუქტის შედეგების თვალყურის დევნებაში.", category: "ux", link: "https://dribbble.com/tags/kpi" },
            { term: "Lean UX", definition: "Lean UX is a collaborative user-centric approach that prioritizes learning loops.", georgian: "Lean UX არის კოლაბორაციული მომხმარებელ-ცენტრული მიდგომა, რომელიც პრიორიტეტს ანიჭებს სწავლის ლუპებს.", category: "ux", link: "https://dribbble.com/tags/lean-ux" },
            { term: "Material Design", definition: "Material Design is a design language developed by Google used in Android devices.", georgian: "მატერიალ დიზაინი არის დიზაინის ენა, რომელიც შექმნილია Google-ის მიერ Android მოწყობილობებისთვის.", category: "design", link: "https://dribbble.com/tags/material-design" },
            { term: "Mental Model", definition: "A mental model represents what the user believes to be true about a product's functionality.", georgian: "გონებრივი მოდელი წარმოადგენს იმას, რასაც მომხმარებელი თვლის ჭეშმარიტად პროდუქტის ფუნქციონალის შესახებ.", category: "ux", link: "https://dribbble.com/tags/mental-model" },
            { term: "Microcopy", definition: "Microcopy refers to the tiny tidbits of copy found on websites and products.", georgian: "მიკროკოპი მიუთითებს პატარა ტექსტის ნაწილაკებზე ვებგვერდებზე და პროდუქტებზე.", category: "ux", link: "https://dribbble.com/tags/microcopy" },
            { term: "Minimum Viable Product", definition: "An MVP is a basic version of a product designed for early release to test marketability.", georgian: "MVP არის პროდუქტის ძირითადი ვერსია, შექმნილი ადრეული გაშვებისთვის ბაზრის შესამოწმებლად.", category: "development", link: "https://dribbble.com/tags/minimum-viable-product" },
            { term: "Mobile Web", definition: "The mobile web refers to browser-based services accessed from handheld devices.", georgian: "მობილური ვებ მიუთითებს ბრაუზერზე დაფუძნებულ სერვისებზე, რომლებიც ხელში მოსაკრავი მოწყობილობებიდანაა ხელმისაწვდომი.", category: "development", link: "https://dribbble.com/tags/mobile-web" },
            { term: "Mockup", definition: "Mockups are static representations of a product.", georgian: "მოკაპები არის პროდუქტის სტატიკური წარმოდგენები.", category: "design", link: "https://dribbble.com/tags/mockup" },
            { term: "Near Field Communication", definition: "A technology that allows two physical devices in close proximity to share information.", georgian: "ტექნოლოგია, რომელიც საშუალებას აძლევს ორ ფიზიკურ მოწყობილობას ახლომდებარედ ინფორმაციის გაზიარებას.", category: "development", link: "https://dribbble.com/tags/near-field-communication" },
            { term: "Onboarding", definition: "Onboarding refers to the steps a user goes through when they first open up an app.", georgian: "ონბორდინგი მიუთითებს ნაბიჯებზე, რომლებიც მომხმარებელი გადის აპლიკაციის პირველ გახსნის დროს.", category: "ux", link: "https://dribbble.com/tags/onboarding" },
            { term: "Pain Points", definition: "Pain points refer to the issues or frustrations a user encounters during an experience.", georgian: "პეინ პოინტები მიუთითებს იმ პრობლემებზე ან იმედგაცრუებებზე, რომლებსაც მომხმარებელი ხვდება გამოცდილების დროს.", category: "ux", link: "https://dribbble.com/tags/pain-points" },
            { term: "Paper Prototyping", definition: "The creation of a product prototype using roughly sketched interfaces on pieces of paper.", georgian: "პროდუქტის პროტოტიპის შექმნა ნახევრად ხელნაწერული ინტერფეისების გამოყენებით ქაღალდის ნაწილებზე.", category: "ux", link: "https://dribbble.com/tags/paper-prototyping" },
            { term: "Persona", definition: "A persona is a document that synthesizes user research data into an archetype.", georgian: "პერსონა არის დოკუმენტი, რომელიც აერთიანებს მომხმარებლის კვლევის მონაცემებს არქეტიპში.", category: "ux", link: "https://dribbble.com/tags/persona" },
            { term: "Pixel", definition: "Pixels are tiny squares used to construct the images seen on device displays.", georgian: "პიქსელები არის პატარა კვადრატები, რომლებიც გამოიყენება მოწყობილობის დისპლეებზე ხილული სურათების შესაქმნელად.", category: "design", link: "https://dribbble.com/tags/pixel" },
            { term: "Problem Statement", definition: "A problem statement is a concise description of a user's pain point or need.", georgian: "პრობლემის განცხადება არის მოკლე აღწერა მომხმარებლის პეინ პოინტის ან საჭიროების შესახებ.", category: "ux", link: "https://dribbble.com/tags/problem-statement" },
            { term: "Product Roadmap", definition: "A product roadmap is a high-level plan that outlines a product's vision and goals.", georgian: "პროდუქტის როუდმაპი არის მაღალი დონის გეგმა, რომელიც ორიენტირებულია პროდუქტის ხედვასა და მიზნებზე.", category: "development", link: "https://dribbble.com/tags/product-roadmap" },
            { term: "Progressive Enhancement", definition: "The practice of adding functionality as technical constraints are removed.", georgian: "პრაქტიკა ფუნქციონალის დამატების ტექნიკური შეზღუდვების მოხსნის შემდეგ.", category: "development", link: "https://dribbble.com/tags/progressive-enhancement" },
            { term: "Qualitative UX Research", definition: "Qualitative UX research gathers insights into user experiences through in-depth exploration.", georgian: "კვალიტატიური UX კვლევა შეგროვებს შეხედულებებს მომხმარებლის გამოცდილებებზე ღრმა კვლევის მეშვეობით.", category: "ux", link: "https://dribbble.com/tags/qualitative-ux-research" },
            { term: "Quantitative UX Research", definition: "Quantitative UX research gathers numerical data about user experiences.", georgian: "კვანტიტატიური UX კვლევა შეგროვებს რიცხვით მონაცემებს მომხმარებლის გამოცდილებებზე.", category: "ux", link: "https://dribbble.com/tags/quantitative-ux-research" },
            { term: "Refactoring", definition: "Refactoring is the process of cleaning up code without affecting functionality.", georgian: "რეფაქტორინგი არის კოდის გაწმენდის პროცესი ფუნქციონალის გავლენის გარეშე.", category: "development", link: "https://dribbble.com/tags/refactoring" },
            { term: "SaaS", definition: "Software as a Service is a software distribution model licensed on a subscription basis.", georgian: "პროგრამული უზრუნველყოფა როგორც სერვისი არის პროგრამული დისტრიბუციის მოდელი სუბსკრიფციის საფუძველზე.", category: "development", link: "https://dribbble.com/tags/saas" },
            { term: "Scalable Vector Graphics", definition: "An SVG can be resized infinitely without losing quality.", georgian: "SVG შეიძლება გადიდდეს უსასრულოდ ხარისხის დაკარგვის გარეშე.", category: "design", link: "https://dribbble.com/tags/scalable-vector-graphics" },
            { term: "Scrum", definition: "A set of project management practices emphasizing daily communication and flexible planning.", georgian: "პროექტის მართვის პრაქტიკების ნაკრები, რომელიც ხაზს უსვამს ყოველდღიურ კომუნიკაციას და მოქნილ დაგეგმვას.", category: "development", link: "https://dribbble.com/tags/scrum" },
            { term: "Stakeholders", definition: "Stakeholders are individuals or organizations affected by the success of a product.", georgian: "სტეიკჰოლდერები არის ინდივიდუალები ან ორგანიზაციები, რომლებზეც იმოქმედებს პროდუქტის წარმატება.", category: "ux", link: "https://dribbble.com/tags/stakeholders" },
            { term: "Storyboard", definition: "Storyboards are a visual representation of a user's experience with a product.", georgian: "სტორიბორდები არის ვიზუალური წარმოდგენა მომხმარებლის გამოცდილების პროდუქტთან.", category: "ux", link: "https://dribbble.com/tags/storyboard" },
            { term: "Style Guide", definition: "A style guide defines the visual language and interaction patterns of a product.", georgian: "სტილის სახელმძღვანელო განსაზღვრავს პროდუქტის ვიზუალურ ენას და ინტერაქციის პატერნებს.", category: "design", link: "https://dribbble.com/tags/style-guide" },
            { term: "Task Analysis", definition: "Task analysis is the process of listing tasks a user takes to complete a goal.", georgian: "ამოცანის ანალიზი არის პროცესი მომხმარებლის მიერ მიზნის შესასრულებლად გადადგმული ამოცანების ჩამონათვალის შედგენის.", category: "ux", link: "https://dribbble.com/tags/task-analysis" },
            { term: "Technical Debt", definition: "Technical debt accrues when an easy but messy development solution is favored.", georgian: "ტექნიკური დავალიანება გროვდება, როდესაც ურჩევნია მარტივი, მაგრამ კოჭული განვითარების გადაწყვეტა.", category: "development", link: "https://dribbble.com/tags/technical-debt" },
            { term: "Unit Testing", definition: "The process of testing parts of an application to ensure they're working properly.", georgian: "აპლიკაციის ნაწილების ტესტირების პროცესი იმის უზრუნველსაყოფად, რომ ისინი სწორად მუშაობენ.", category: "development", link: "https://dribbble.com/tags/unit-testing" },
            { term: "Usability Testing", definition: "Usability testing evaluates how easy a product is to use by testing on users.", georgian: "გამოყენებადობის ტესტირება შეფასებს რამდენად ადვილია პროდუქტის გამოყენება მომხმარებლებზე ტესტირებით.", category: "ux", link: "https://dribbble.com/tags/usability-testing" },
            { term: "User-Centered Design", definition: "User-centered design is an iterative design framework where users are at the center.", georgian: "მომხმარებელ-ცენტრული დიზაინი არის იტერაციული დიზაინის ჩარჩო, სადაც მომხმარებლები ცენტრშია.", category: "ux", link: "https://dribbble.com/tags/user-centered-design" },
            { term: "User Experience", definition: "The user experience refers to a user's emotions and perceptions about a product.", georgian: "მომხმარებლის გამოცდილება მიუთითებს მომხმარებლის ემოციებსა და აღქმებებზე პროდუქტის შესახებ.", category: "ux", link: "https://dribbble.com/tags/user-experience" },
            { term: "User Interface", definition: "User interface is the front-end of an app or website that the user interacts with.", georgian: "მომხმარებლის ინტერფეისი არის აპლიკაციის ან ვებგვერდის ფრონტ-ენდი, რომელთანაც მომხმარებელი ურთიერთქმედებს.", category: "ui", link: "https://dribbble.com/tags/user-interface" },
            { term: "UI Pattern", definition: "UI patterns are reusable solutions to common usability problems.", georgian: "UI პატერნები არის ხელახლა გამოყენებადი გადაწყვეტილებები ჩვეულებრივი გამოყენებადობის პრობლემებისთვის.", category: "ui", link: "https://dribbble.com/tags/ui-pattern" },
            { term: "User Flow", definition: "A user flow describes the intended series of steps a user needs to complete a goal.", georgian: "მომხმარებლის ფლოუ აღწერს მომხმარებლის მიერ მიზნის შესასრულებლად საჭირო ნაბიჯების თანმიმდევრობას.", category: "ux", link: "https://dribbble.com/tags/user-flow" },
            { term: "User Journey", definition: "A user journey is a description of the steps a user will go through when using a product.", georgian: "მომხმარებლის მოგზაურობა არის აღწერა მომხმარებლის მიერ პროდუქტის გამოყენების დროს გადადგმული ნაბიჯების.", category: "ux", link: "https://dribbble.com/tags/user-journey" },
            { term: "User Research", definition: "User research is the methodic study of target users including their needs and pain points.", georgian: "მომხმარებლის კვლევა არის მეთოდური შესწავლა სამიზნე მომხმარებლების, მათი საჭიროებებისა და პეინ პოინტების შეტანით.", category: "ux", link: "https://dribbble.com/tags/user-research" },
            { term: "User Scenario", definition: "A story-like description of a specific situation in which a user might interact with a product.", georgian: "სტორი-სგავსი აღწერა კონკრეტული სიტუაციის, სადაც მომხმარებელი შესაძლოა ურთიერთქმედებდეს პროდუქტთან.", category: "ux", link: "https://dribbble.com/tags/user-scenario" },
            { term: "User Stories", definition: "User Stories share actions different kinds of users can take in a product.", georgian: "მომხმარებლის სტორიები იზიარებს ქმედებებს, რომლებიც სხვადასხვა ტიპის მომხმარებლები შეუძლიათ განახორციელონ პროდუქტში.", category: "ux", link: "https://dribbble.com/tags/user-stories" },
            { term: "Waterfall", definition: "In software waterfall development, each phase must be completed before the next.", georgian: "პროგრამული უზრუნველყოფის უოტერფოლ განვითარებაში, თითოეული ფაზა უნდა დასრულდეს შემდეგის წინ.", category: "development", link: "https://dribbble.com/tags/waterfall" },
            { term: "White Space", definition: "White or negative space refers to the unoccupied or blank space on a page.", georgian: "თეთრი ან უარყოფითი სივრცე მიუთითებს გვერდზე შეუკავებელ ან ცარიელ სივრცეზე.", category: "design", link: "https://dribbble.com/tags/white-space" },
            { term: "Wireframe", definition: "A wireframe is a rough version of a screen design that allows exploration of layout.", georgian: "ვაიერფრეიმი არის ეკრანის დიზაინის ნახევრად მკაცრი ვერსია განლაგების კვლევის საშუალებით.", category: "design", link: "https://dribbble.com/tags/wireframe" },
            { term: "Adobe XD", definition: "Adobe XD is a vector-based design tool used for creating wireframes and prototypes.", georgian: "Adobe XD არის ვექტორზე დაფუძნებული დიზაინის ინსტრუმენტი ვაიერფრეიმების და პროტოტიპების შესაქმნელად.", category: "design", link: "https://dribbble.com/tags/adobe-xd" },
            { term: "Animation", definition: "In UI terms, animation is the act of adding motion to any UI element.", georgian: "UI ტერმინებში, ანიმაცია არის მოძრაობის დამატების ქმედება ნებისმიერ UI ელემენტზე.", category: "design", link: "https://dribbble.com/tags/animation" },
            { term: "Ascenders", definition: "In typography, ascenders are letters that reach above the x-height.", georgian: "ტიპოგრაფიაში, ასენდერები არის ასოები, რომლებიც აღწევს x-სიმაღლის ზემოთ.", category: "design", link: "https://dribbble.com/tags/ascenders" },
            { term: "Call-to-action", definition: "A CTA encourages users to take a specific action on a website or application.", georgian: "CTA უბიძგებს მომხმარებლებს კონკრეტული ქმედებისკენ ვებგვერდზე ან აპლიკაციაში.", category: "ui", link: "https://dribbble.com/tags/call-to-action" },
            { term: "Containers", definition: "A container is a UI element designed to contain page elements to a certain width.", georgian: "კონტეინერი არის UI ელემენტი, შექმნილი გვერდის ელემენტების გარკვეული სიგანის შეკუმშვისთვის.", category: "ui", link: "https://dribbble.com/tags/containers" },
            { term: "Critique", definition: "Critiques allow designers to provide constructive criticism to improve a product.", georgian: "კრიტიკები საშუალებას აძლევს დიზაინერებს მოუწოდონ კონსტრუქციული კრიტიკა პროდუქტის გაუმჯობესებისთვის.", category: "design", link: "https://dribbble.com/tags/critique" },
            { term: "Design Thinking", definition: "Design thinking is a process comprising five phases: Empathise, Define, Ideate, Prototype, Test.", georgian: "დიზაინ თინკინგი არის პროცესი, რომელიც შედგება ხუთი ფაზისგან: ემპათია, განსაზღვრა, იდეაცია, პროტოტიპი, ტესტი.", category: "ux", link: "https://dribbble.com/tags/design-thinking" },
            { term: "Dribbble", definition: "Dribbble is a social media platform that focuses on building a community of designers.", georgian: "Dribbble არის სოციალური მედიის პლატფორმა, რომელიც ფოკუსირებულია დიზაინერების თემის შექმნაზე.", category: "design", link: "https://dribbble.com/tags/dribbble" },
            { term: "Dropdown Buttons", definition: "The dropdown button is the clickable button used in a dropdown list.", georgian: "დროპდაუნ ღილაკი არის დაკლიკებადი ღილაკი დროპდაუნ სიაში.", category: "ui", link: "https://dribbble.com/tags/dropdown-buttons" },
            { term: "Figma", definition: "Figma is a browser-based interface design tool for fast design and prototyping.", georgian: "Figma არის ბრაუზერზე დაფუძნებული ინტერფეისის დიზაინის ინსტრუმენტი სწრაფი დიზაინისა და პროტოტიპინგისთვის.", category: "design", link: "https://dribbble.com/tags/figma" },
            { term: "Fluid UI", definition: "Fluid UI is a prototyping and wireframing software tool for mobile touch interfaces.", georgian: "Fluid UI არის პროტოტიპინგისა და ვაიერფრეიმინგის პროგრამული ინსტრუმენტი მობილური ტაჩ ინტერფეისებისთვის.", category: "design", link: "https://dribbble.com/tags/fluid-ui" },
            { term: "Full-stack Designer", definition: "A full-stack designer has skills to take on all layers of the product design process.", georgian: "ფულ-სტეკ დიზაინერი აქვს უნარები პროდუქტის დიზაინის პროცესის ყველა ფენის ასაღებლად.", category: "design", link: "https://dribbble.com/tags/full-stack-designer" },
            { term: "Grids", definition: "Grids bring order to a layout using columns and rows.", georgian: "ბადეები მოაქვთ წესრიგი განლაგებაში სვეტებისა და რიგების გამოყენებით.", category: "design", link: "https://dribbble.com/tags/grids" },
            { term: "Informational Components", definition: "Informational components tell users what's going on.", georgian: "ინფორმაციული კომპონენტები ეუბნება მომხმარებლებს რა ხდება.", category: "ui", link: "https://dribbble.com/tags/informational-components" },
            { term: "InVision Studio", definition: "InVision Studio includes features for drawing, wireframing, prototyping and animating.", georgian: "InVision Studio შეიცავს ფუნქციებს ხაზვის, ვაიერფრეიმინგის, პროტოტიპინგისა და ანიმაციისთვის.", category: "design", link: "https://dribbble.com/tags/invision-studio" },
            { term: "Marvel", definition: "Marvel provides core functionality for designing and building digital products.", georgian: "Marvel უზრუნველყოფს ძირითად ფუნქციონალს ციფრული პროდუქტების დიზაინისა და შექმნისთვის.", category: "design", link: "https://dribbble.com/tags/marvel" },
            { term: "Navigational Components", definition: "Navigational components allow the user to interact with and use your product.", georgian: "ნავიგაციური კომპონენტები საშუალებას აძლევს მომხმარებელს ურთიერთქმედებდეს და გამოიყენოს შენი პროდუქტი.", category: "ui", link: "https://dribbble.com/tags/navigational-components" },
            { term: "Origami Studio", definition: "Origami Studio is a free design tool created by Facebook for prototyping.", georgian: "Origami Studio არის უფასო დიზაინის ინსტრუმენტი, შექმნილი Facebook-ის მიერ პროტოტიპინგისთვის.", category: "design", link: "https://dribbble.com/tags/origami-studio" },
            { term: "Principle", definition: "Principle for Mac is an easy-to-use design software for creating animations.", georgian: "Principle Mac-ისთვის არის მარტივი გამოყენების დიზაინის პროგრამა ანიმაციების შესაქმნელად.", category: "design", link: "https://dribbble.com/tags/principle" },
            { term: "ProtoPie", definition: "ProtoPie is a flexible prototyping tool with an easy-to-use interface.", georgian: "ProtoPie არის მოქნილი პროტოტიპინგის ინსტრუმენტი მარტივი გამოყენების ინტერფეისით.", category: "design", link: "https://dribbble.com/tags/protopie" },
            { term: "Sketch", definition: "Sketch is a vector graphics editor used for drawing and wireframing.", georgian: "Sketch არის ვექტორული გრაფიკის რედაქტორი, რომელიც გამოიყენება ხაზვისა და ვაიერფრეიმინგისთვის.", category: "design", link: "https://dribbble.com/tags/sketch" },
            { term: "Thumb Reachability", definition: "Thumb reachability considers the placement of interactive elements for mobile use.", georgian: "ბუმბის მისაწვდომობა განიხილავს ინტერაქტიული ელემენტების განთავსებას მობილური გამოყენებისთვის.", category: "ui", link: "https://dribbble.com/tags/thumb-reachability" },
            { term: "Uizard", definition: "Uizard is a UI design platform for creating digital products without advanced expertise.", georgian: "Uizard არის UI დიზაინის პლატფორმა ციფრული პროდუქტების შესაქმნელად მოწინავე ექსპერტიზის გარეშე.", category: "design", link: "https://dribbble.com/tags/uizard" },
            { term: "UX Design", definition: "UX design is the process of designing user experiences.", georgian: "UX დიზაინი არის მომხმარებლის გამოცდილების შექმნის პროცესი.", category: "ux", link: "https://dribbble.com/tags/ux-design" },
            { term: "UXPin", definition: "UXPin is an end-to-end platform for delivering interactive prototypes.", georgian: "UXPin არის დასაწყისი-დამთავრებითი პლატფორმა ინტერაქტიული პროტოტიპების მოწოდებისთვის.", category: "design", link: "https://dribbble.com/tags/uxpin" },
            { term: "Visual Design", definition: "Visual design considers the aesthetics of an app or website.", georgian: "ვიზუალური დიზაინი განიხილავს აპლიკაციის ან ვებგვერდის ესთეტიკას.", category: "design", link: "https://dribbble.com/tags/visual-design" },
            { term: "Zeplin", definition: "Zeplin bridges the gap between UI designers and front-end developers.", georgian: "Zeplin აკავშირებს ხიდს UI დიზაინერებსა და ფრონტ-ენდ დეველოპერებს შორის.", category: "design", link: "https://dribbble.com/tags/zeplin" },
            { term: "Accessibility", definition: "Accessibility helps differently-enabled users interact with a product.", georgian: "ხელმისაწვდომობა ეხმარება სხვადასხვა შესაძლებლობის მომხმარებლებს პროდუქტთან ურთიერთობაში.", category: "ux", link: "https://dribbble.com/tags/accessibility" },
            { term: "Diary Study", definition: "A diary study collects qualitative data about user behaviors over time.", georgian: "დღიურის კვლევა შეგროვებს კვალიტატიურ მონაცემებს მომხმარებლის ქცევებზე დროთა განმავლობაში.", category: "ux", link: "https://dribbble.com/tags/diary-study" },
            { term: "Bug", definition: "Bugs are mistakes in software that cause a product to malfunction.", georgian: "ბაგები არის შეცდომები პროგრამულ უზრუნველყოფაში, რომლებიც იწვევს პროდუქტის დამახინჯებას.", category: "development", link: "https://dribbble.com/tags/bug" },
            { term: "Frontend Development", definition: "Frontend development focuses on the design and functionality of the user interface (UI) by using coding languages like HTML, CSS, and JavaScript.", georgian: "ფრონტ-ენდის განვითარება ფოკუსირებულია მომხმარებლის ინტერფეისის (UI) დიზაინსა და ფუნქციონალზე კოდირების ენების გამოყენებით, როგორიცაა HTML, CSS და JavaScript.", category: "development", link: "https://dribbble.com/tags/frontend-development" },
            { term: "UI (User Interface)", definition: "The user interface in front-end development refers to the visual elements and design of a website or application that users interact with.", georgian: "მომხმარებლის ინტერფეისი ფრონტ-ენდის განვითარებაში მიუთითებს ვიზუალურ ელემენტებსა და დიზაინზე ვებგვერდის ან აპლიკაციის, რომელთანაც მომხმარებლები ურთიერთქმედებენ.", category: "ui", link: "https://dribbble.com/tags/user-interface" },
            { term: "UX (User Experience)", definition: "UX covers the broader user journey, flow, and satisfaction in product interactions.", georgian: "UX მოიცავს მომხმარებლის უფრო ფართო მოგზაურობას, ნაკადს და კმაყოფილებას პროდუქტის ურთიერთქმედებებში.", category: "ux", link: "https://dribbble.com/tags/user-experience" },
            { term: "CSS Grid", definition: "CSS Grid is a two-dimensional layout system for designing complex web layouts.", georgian: "CSS Grid არის ორ-განზომილებიანი განლაგების სისტემა კომპლექსური ვებ განლაგებების შესაქმნელად.", category: "development", link: "https://dribbble.com/tags/css-grid" },
            { term: "Flexbox", definition: "Flexbox is a one-dimensional layout model for distributing space between items in a container.", georgian: "Flexbox არის ერთ-განზომილებიანი განლაგების მოდელი სივრცის განაწილებისთვის ელემენტებს შორის კონტეინერში.", category: "development", link: "https://dribbble.com/tags/flexbox" },
            { term: "JavaScript", definition: "JavaScript is a programming language that enables interactive web pages.", georgian: "JavaScript არის პროგრამირების ენა, რომელიც საშუალებას აძლევს ინტერაქტიული ვებგვერდებს.", category: "development", link: "https://dribbble.com/tags/javascript" },
            { term: "HTML", definition: "HTML (HyperText Markup Language) is the standard markup language for creating web pages.", georgian: "HTML (HyperText Markup Language) არის სტანდარტული მარკაპის ენა ვებგვერდების შესაქმნელად.", category: "development", link: "https://dribbble.com/tags/html" },
            { term: "DOM (Document Object Model)", definition: "The DOM is a programming interface for web documents representing the page structure.", georgian: "DOM (Document Object Model) არის პროგრამირების ინტერფეისი ვებ დოკუმენტებისთვის გვერდის სტრუქტურის წარმოდგენისთვის.", category: "development", link: "https://dribbble.com/tags/dom" },
            { term: "AJAX", definition: "AJAX (Asynchronous JavaScript and XML) allows web pages to update content without reloading.", georgian: "AJAX (Asynchronous JavaScript and XML) საშუალებას აძლევს ვებგვერდებს განაახლონ კონტენტი გადატვირთვის გარეშე.", category: "development", link: "https://dribbble.com/tags/ajax" },
            { term: "Bootstrap", definition: "Bootstrap is a free CSS framework for responsive, mobile-first front-end development.", georgian: "Bootstrap არის უფასო CSS ფრეიმვორკი რესპონსიული, მობილური-პირველი ფრონტ-ენდის განვითარებისთვის.", category: "development", link: "https://dribbble.com/tags/bootstrap" },
            { term: "React", definition: "React is a JavaScript library for building user interfaces with reusable components.", georgian: "React არის JavaScript ბიბლიოთეკა მომხმარებლის ინტერფეისების შესაქმნელად ხელახლა გამოყენებადი კომპონენტებით.", category: "development", link: "https://dribbble.com/tags/react" },
            { term: "Angular", definition: "Angular is a platform for building mobile and desktop web applications.", georgian: "Angular არის პლატფორმა მობილური და დესკტოპ ვებ აპლიკაციების შესაქმნელად.", category: "development", link: "https://dribbble.com/tags/angular" },
            { term: "Vue.js", definition: "Vue.js is a progressive JavaScript framework for building UIs.", georgian: "Vue.js არის პროგრესული JavaScript ფრეიმვორკი UI-ების შესაქმნელად.", category: "development", link: "https://dribbble.com/tags/vuejs" },
            { term: "Semantic HTML", definition: "Semantic HTML uses tags that clearly describe the meaning of the content.", georgian: "სემანტიკური HTML იყენებს ტეგებს, რომლებიც მკაფიოდ აღწერს კონტენტის მნიშვნელობას.", category: "development", link: "https://dribbble.com/tags/semantic-html" },
            { term: "Media Queries", definition: "Media queries allow CSS to apply different styles based on device characteristics.", georgian: "მედია კუერიები საშუალებას აძლევს CSS-ს გამოიყენოს სხვადასხვა სტილები მოწყობილობის მახასიათებლების მიხედვით.", category: "development", link: "https://dribbble.com/tags/media-queries" },
            { term: "Pseudo-classes", definition: "Pseudo-classes in CSS select elements based on their state, like :hover or :active.", georgian: "CSS-ის პსევდო-კლასები ირჩევს ელემენტებს მათი სტატუსის მიხედვით, როგორიცაა :hover ან :active.", category: "development", link: "https://dribbble.com/tags/pseudo-classes" },
            { term: "Transitions", definition: "CSS transitions smoothly change property values over a specified duration.", georgian: "CSS ტრანზიციები უმშვიდესად ცვლის თვისებების მნიშვნელობებს მითითებულ დროში.", category: "development", link: "https://dribbble.com/tags/transitions" },
            { term: "Animations", definition: "CSS animations create complex movement effects using keyframes.", georgian: "CSS ანიმაციები ქმნის კომპლექსურ მოძრაობის ეფექტებს კეიფრეიმების გამოყენებით.", category: "development", link: "https://dribbble.com/tags/animations" },
            { term: "DOM Manipulation", definition: "DOM manipulation involves changing the structure, style, or content of a document using JavaScript.", georgian: "DOM მანიპულაცია მოიცავს დოკუმენტის სტრუქტურის, სტილის ან კონტენტის შეცვლას JavaScript-ის გამოყენებით.", category: "development", link: "https://dribbble.com/tags/dom-manipulation" },
            { term: "Event Handling", definition: "Event handling in JavaScript responds to user actions like clicks or key presses.", georgian: "ივენთ ჰენდლინგი JavaScript-ში რეაგირებს მომხმარებლის ქმედებებზე, როგორიცაა კლიკი ან ღილაკის ნაწაპება.", category: "development", link: "https://dribbble.com/tags/event-handling" },
            { term: "Single Page Application (SPA)", definition: "An SPA is a web app that loads a single HTML page and dynamically updates content.", georgian: "ერთგვერდიანი აპლიკაცია (SPA) არის ვებ აპლიკაცია, რომელიც ჩატვირთავს ერთ HTML გვერდს და დინამიურად განაახლებს კონტენტს.", category: "development", link: "https://dribbble.com/tags/single-page-application" },
            { term: "Component-Based Architecture", definition: "Component-based architecture builds UIs from reusable, independent components.", georgian: "კომპონენტებზე დაფუძნებული არქიტექტურა აშენებს UI-ებს ხელახლა გამოყენებადი, დამოუკიდებელი კომპონენტებიდან.", category: "development", link: "https://dribbble.com/tags/component-based-architecture" },
            { term: "State Management", definition: "State management handles the data and UI state across a front-end application.", georgian: "სტეიტ მენეჯმენტი მართავს მონაცემებს და UI სტატუსს ფრონტ-ენდ აპლიკაციის გავლენით.", category: "development", link: "https://dribbble.com/tags/state-management" },
            { term: "Progressive Web App (PWA)", definition: "A PWA is a web app that works offline and loads like a native app.", georgian: "პროგრესული ვებ აპლიკაცია (PWA) არის ვებ აპლიკაცია, რომელიც მუშაობს ოფლაინ რეჟიმში და იტვირთება როგორც ნატიური აპლიკაცია.", category: "development", link: "https://dribbble.com/tags/progressive-web-app" },
            { term: "Version Control (Git)", definition: "Version control like Git tracks changes in code over time.", georgian: "ვერსიის კონტროლი (Git) თვალყურს ადევნებს კოდის ცვლილებებს დროთა განმავლობაში.", category: "development", link: "https://dribbble.com/tags/git" },
            { term: "Build Tools (Webpack)", definition: "Build tools like Webpack bundle and optimize front-end code for production.", georgian: "შედგენის ინსტრუმენტები როგორიცაა Webpack აერთიანებს და ოპტიმიზაციას უკეთებს ფრონტ-ენდ კოდს პროდაქშენისთვის.", category: "development", link: "https://dribbble.com/tags/webpack" },
            { term: "Linting (ESLint)", definition: "Linting tools like ESLint detect errors and enforce code style in JavaScript.", georgian: "ლინტინგის ინსტრუმენტები როგორიცაა ESLint აღმოაჩენს შეცდომებს და აძალებს კოდის სტილს JavaScript-ში.", category: "development", link: "https://dribbble.com/tags/eslint" },
            { term: "Cross-Browser Compatibility", definition: "Cross-browser compatibility ensures a site works consistently across different browsers.", georgian: "კროს-ბრაუზერ თავსებადობა უზრუნველყოფს საიტის თანმიმდევრულ მუშაობას სხვადასხვა ბრაუზერებში.", category: "development", link: "https://dribbble.com/tags/cross-browser-compatibility" }
        ];

        // DOM elements
        const glossaryTable = document.getElementById('glossaryTable');
        const searchInput = document.getElementById('searchInput');
        const filterButtons = document.querySelectorAll('.filter-btn');
        const sortSelect = document.getElementById('sortSelect');
        const resultsInfo = document.getElementById('resultsInfo');
        const noResults = document.getElementById('noResults');
        const tableHeaders = document.querySelectorAll('th[data-sort]');

        // Initialize
        let currentFilter = 'all';
        let currentSort = 'name-asc';
        let currentData = [...glossaryData];

        // Render table
        function renderTable(data) {
            glossaryTable.innerHTML = '';
            
            if (data.length === 0) {
                noResults.style.display = 'block';
                resultsInfo.textContent = '0 შედეგი';
                return;
            }
            
            noResults.style.display = 'none';
            resultsInfo.textContent = `${data.length} შედეგი`;
            
            data.forEach(item => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${item.term}</td>
                    <td>${item.definition}</td>
                    <td>${item.georgian}</td>
                    <td><a href="${item.link}" target="_blank">მაგალითები <span class="external-icon">↗</span></a></td>
                `;
                glossaryTable.appendChild(row);
            });
        }

        // Filter data
        function filterData() {
            let filteredData = [...glossaryData];
            
            // Apply category filter
            if (currentFilter !== 'all') {
                filteredData = filteredData.filter(item => item.category === currentFilter);
            }
            
            // Apply search filter
            const searchTerm = searchInput.value.toLowerCase().trim();
            if (searchTerm) {
                filteredData = filteredData.filter(item => 
                    item.term.toLowerCase().includes(searchTerm) || 
                    item.definition.toLowerCase().includes(searchTerm) ||
                    item.georgian.toLowerCase().includes(searchTerm)
                );
            }
            
            // Apply sorting
            filteredData = sortData(filteredData);
            
            currentData = filteredData;
            renderTable(currentData);
        }

        // Sort data
        function sortData(data) {
            const [field, direction] = currentSort.split('-');
            
            return data.sort((a, b) => {
                let aValue, bValue;
                
                if (field === 'name') {
                    aValue = a.term.toLowerCase();
                    bValue = b.term.toLowerCase();
                } else if (field === 'description') {
                    aValue = a.definition.toLowerCase();
                    bValue = b.definition.toLowerCase();
                } else if (field === 'category') {
                    aValue = a.category;
                    bValue = b.category;
                }
                
                if (aValue < bValue) return direction === 'asc' ? -1 : 1;
                if (aValue > bValue) return direction === 'asc' ? 1 : -1;
                return 0;
            });
        }

        // Event listeners
        searchInput.addEventListener('input', filterData);

        filterButtons.forEach(button => {
            button.addEventListener('click', () => {
                filterButtons.forEach(btn => btn.classList.remove('active'));
                button.classList.add('active');
                currentFilter = button.dataset.filter;
                filterData();
            });
        });

        sortSelect.addEventListener('change', () => {
            currentSort = sortSelect.value;
            filterData();
        });

        tableHeaders.forEach(header => {
            header.addEventListener('click', () => {
                const field = header.dataset.sort;
                let direction = 'asc';
                
                if (currentSort.startsWith(field)) {
                    direction = currentSort.endsWith('asc') ? 'desc' : 'asc';
                }
                
                currentSort = `${field}-${direction}`;
                sortSelect.value = currentSort;
                filterData();
            });
        });

        // Initial render
        renderTable(currentData);
    </script>
</body>
</html>
