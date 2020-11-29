# Cool Tabs
 Cool Tabs using **Vanilla JavaScript**
***
#### HTML
```html
    <main class="container">

        <div id="btn_container">
            <button class="btn active" data-tab="app">APP</button>
            <button class="btn" data-tab="web">WEB</button>
            <button class="btn" data-tab="ui">UI</button>
            <button class="btn" data-tab="seo">SEO</button>
        </div>

        <div class="tab-container">
            <div class="tab-content current" id="app">
                <h2>What is an App?</h2>
                <p>An app, which is short for application, is a type of software that can be installed and run on a computer, tablet, smartphone or other electronic devices. An app most frequently refers to a mobile application or a piece of software that is installed and used on a computer. Most apps have a specific and narrow function.</p>
            </div>

            <div class="tab-content" id="web">
                <h2>What is Web?</h2>
                <p>The Web, or World Wide Web (W3), is basically a system of Internet servers that support specially formatted documents. The documents are formatted in a markup language called HTML (HyperText Markup Language) that supports links to other documents, as well as graphics, audio, and video files.</p>
            </div>

            <div class="tab-content" id="ui">
                <h2>What is UI?</h2>
                <p>The “UI” in UI design stands for “user interface.” The user interface is the graphical layout of an application. It consists of the buttons users click on, the text they read, the images, sliders, text entry fields, and all the rest of the items the user interacts with. This includes screen layout, transitions, interface animations and every single micro-interaction. Any sort of visual element, interaction, or animation must all be designed.</p>
            </div>

            <div class="tab-content" id="seo">
                <h2>What is SEO?</h2>
                <p>SEO stands for “search engine optimization.” In simple terms, it means the process of improving your site to increase its visibility for relevant searches. The better visibility your pages have in search results, the more likely you are to garner attention and attract prospective and existing customers to your business.</p>
            </div>

        </div>

    </main>
```
#### CSS
***
```css
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    body {
        font-family: 'Poppins', sans-serif;
        background-color: #262626;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    main.container {
        width: 70%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .btn {
        font-family: 'Poppins', sans-serif;
        font-size: 16px;
        color: #fff;
        line-height: 1.3;
        font-weight: 600;
        letter-spacing: 1px;
        background-color: #0278d5;
        border: none;
        border-radius: 3px;
        outline: none;
        margin: 0 10px;
        padding: 6px 20px;
        box-shadow: 0 0 12px rgba(0, 0, 0, .3);
        cursor: pointer;
        transition: all .5s ease;
    }

    .btn:hover {
        background-color: #fc1a6d;
    }

    .btn.active {
        background: #e80458;
        transition: all .3s ease;
        box-shadow: 0 0 12px rgba(0, 0, 0, .3);
        position: relative;
    }

    .btn.active::after {
        content: '';
        height: 0;
        width: 0;
        border: 8px solid transparent;
        border-color: #e80458 transparent transparent transparent;
        position: absolute;
        left: 0;
        right: 0;
        bottom: -16px;
        margin: 0 auto;
    }

    .tab-container {
        width: 60%;
        height: 235px;
        max-height: 250px;
        position: relative;
    }

    .tab-content {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        display: none;
        border-radius: 3px;
        background-color: #0278d5;
        margin-top: 30px;
        padding: 30px;
        box-shadow: 0 0 12px rgba(0, 0, 0, .3);
    }

    .tab-content.current {
        display: block;
    }

    .tab-content h2 {
        font-family: 'Poppins', sans-serif;
        font-size: 25px;
        color: #fff;
        line-height: 1.3;
        font-weight: 700;
        padding: 0;
        margin: 0 0 20px 0;
    }

    .tab-content p {
        font-family: 'Poppins', sans-serif;
        font-size: 16px;
        color: #fff;
        line-height: 1.5;
        font-weight: 400;
        padding: 0;
        margin: 0;
    }

```
#### Javascript
```javascript
    const TABS = (tabHolder, tabClass, tabContentClass) => {
        const container = document.querySelector(tabHolder);
        const btns = document.querySelectorAll(tabClass);

        //Hide all the Tab Contents
        let tabcontent = document.querySelectorAll(tabContentClass);


        // Display : Block / None according to Tab Data-Attribute
        btns.forEach((item) => {
            item.addEventListener("click", () => {

                let attr = item.getAttribute("data-tab");

                tabcontent.forEach(item => {
                    if (item.id === attr) {

                        item.style.display = "block";
                        item.classList.add("current");

                    } else {
                        item.style.display = "none";
                        item.classList.remove("current");
                    }
                })

            })
        })

        //Tab Buttons Active/Deactive Class Add/Remove
        btns.forEach((i) => {
            i.addEventListener("click", () => {

                btns.forEach(j => j.classList.remove("active"))

                i.classList.add("active");

            });
        });
    }

    // Call the function
    TABS("#btn_container", ".btn", ".tab-content");
```