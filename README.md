# code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- OWASP A05: restrict what the page may load or submit to. No scripts are allowed at all. -->
    <meta http-equiv="Content-Security-Policy"
          content="default-src 'none'; img-src 'self'; style-src 'unsafe-inline'; form-action 'self'; base-uri 'none'">
    <!-- OWASP A01/A05: do not leak the page URL when visitors click outbound links -->
    <meta name="referrer" content="no-referrer">

    <title>My Personal Profile | Rabeya Akter</title>

    <style>
        /* Design improvement 1: readable, responsive, high-contrast styling */
        :root {
            --text: #1a1a1a;        /* on #ffffff = 17.4:1 */
            --bg: #ffffff;
            --accent: #12355b;      /* on #ffffff = 12.4:1 */
            --link: #0b4f9c;        /* on #ffffff = 8.0:1 */
            --soft: #eef3f9;
            --border: #5a6b7d;
        }
        * { box-sizing: border-box; }
        body {
            font-family: Arial, Helvetica, sans-serif;
            font-size: 1.05rem;
            line-height: 1.6;
            color: var(--text);
            background: var(--bg);
            margin: 0;
        }
        .skip-link {
            position: absolute;
            left: -999px;
            top: 0;
            background: var(--accent);
            color: #fff;
            padding: 0.6rem 1rem;
            z-index: 10;
        }
        .skip-link:focus { left: 0; }

        header {
            background: var(--accent);
            color: #fff;
            padding: 1.5rem 1rem;
            text-align: center;
        }
        header h1 { margin: 0 0 0.25rem; }
        header p { margin: 0; }

        nav { background: var(--soft); padding: 0.75rem 1rem; text-align: center; }
        nav a { margin: 0 0.6rem; display: inline-block; padding: 0.2rem 0; }

        main { max-width: 800px; margin: 0 auto; padding: 1rem; }
        section { margin: 2rem 0; }
        h2 { color: var(--accent); border-bottom: 2px solid var(--accent); padding-bottom: 0.25rem; }
        h3 { color: var(--accent); }

        a { color: var(--link); text-decoration: underline; }
        a:hover { color: var(--accent); }

        /* WCAG 2.4.7: clearly visible keyboard focus for every interactive element */
        a:focus, input:focus, textarea:focus, button:focus {
            outline: 3px solid #b35900;
            outline-offset: 2px;
        }

        .summary { font-style: italic; background: var(--soft); padding: 1rem; border-left: 5px solid var(--accent); }
        .about { display: flex; flex-wrap: wrap; gap: 1.5rem; align-items: center; }
        .about img { width: 180px; max-width: 100%; height: auto; border-radius: 8px; border: 2px solid var(--accent); }
        .about > div { flex: 1 1 260px; }

        table { border-collapse: collapse; width: 100%; }
        caption { text-align: left; font-weight: bold; padding-bottom: 0.4rem; }
        th, td { border: 1px solid var(--border); padding: 0.6rem; text-align: left; }
        th { background: var(--accent); color: #fff; }

        label { font-weight: bold; }
        input[type="text"], input[type="email"], textarea {
            width: 100%;
            max-width: 480px;
            padding: 0.5rem;
            border: 2px solid var(--border);
            border-radius: 4px;
            font: inherit;
        }
        .field { margin-bottom: 1rem; }
        .hint { font-size: 0.9rem; margin: 0.1rem 0 0.4rem; }
        input[type="submit"], input[type="reset"] {
            background: var(--accent);
            color: #fff;
            border: 2px solid var(--accent);
            padding: 0.6rem 1.2rem;
            font: inherit;
            border-radius: 4px;
            cursor: pointer;
        }
        input[type="reset"] { background: #fff; color: var(--accent); }

        footer { background: var(--soft); text-align: center; padding: 1rem; margin-top: 2rem; }
    </style>
</head>

<body>

    <a class="skip-link" href="#main-content">Skip to main content</a>

    <header>
        <h1>My Personal Profile</h1>
        <p>Welcome to my personal webpage!</p>
    </header>

    <!-- Design improvement 2: semantic landmarks + in-page navigation -->
    <nav aria-label="Page sections">
        <a href="#about">About</a>
        <a href="#education">Education</a>
        <a href="#skills">Skills</a>
        <a href="#hobbies">Hobbies</a>
        <a href="#contact">Contact</a>
    </nav>

    <main id="main-content">

        <!-- Personal Information and Photograph -->
        <section id="about" aria-labelledby="about-heading">
            <h2 id="about-heading">About Me</h2>

            <p class="summary">
                Dedicated professional committed to continuous learning and career growth.
                Strong work ethic with a focus on teamwork, time management, and achieving targets.
                Passionate about bringing value to the organization.
            </p>

            <div class="about">
                <!-- Relative path: keep rabeya.jpeg in the same folder as this file -->
                <img src="rabeya.jpeg"
                     alt="Photograph of Rabeya Akter"
                     width="180" height="180">

                <div>
                    <h3>Rabeya Akter</h3>
                    <p>
                        Hello! My name is Rabeya Akter.
                        I am a Computer Science and Engineering student.
                        I am interested in programming, web development,
                        learning new technologies and teaching.
                    </p>
                </div>
            </div>
        </section>

        <!-- Education Table -->
        <section id="education" aria-labelledby="education-heading">
            <h2 id="education-heading">My Education</h2>

            <table>
                <caption>Education summary</caption>
                <thead>
                    <tr>
                        <th scope="col">Level</th>
                        <th scope="col">Institution</th>
                        <th scope="col">Subject</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Undergraduate</td>
                        <td>University of Liberal Arts Bangladesh</td>
                        <td>Computer Science and Engineering</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Skills -->
        <section id="skills" aria-labelledby="skills-heading">
            <h2 id="skills-heading">My Skills</h2>
            <ul>
                <li>C programming</li>
                <li>Python</li>
                <li>Java programming</li>
                <li>Database management</li>
            </ul>
        </section>

        <!-- Hobbies -->
        <section id="hobbies" aria-labelledby="hobbies-heading">
            <h2 id="hobbies-heading">My Hobbies and Interests</h2>
            <ol>
                <li>Dancing</li>
                <li>Reading books</li>
                <li>Exploring the internet</li>
                <li>Cooking</li>
                <li>Travelling</li>
            </ol>
        </section>

        <!-- Contact Information -->
        <section id="contact" aria-labelledby="contact-heading">
            <h2 id="contact-heading">Contact Me</h2>

            <!--(OWASP A02 / data minimisation) -->
            <p>Email: <a href="mailto:rabeya.akter1.cse@ulab.edu.bd">rabeya.akter1.cse@ulab.edu.bd</a></p>
            <p>Phone: 01936391635</p>

            <h3>My Social Profiles</h3>
            <ul>
                <li>
                    <a href="https://www.facebook.com/share/1FUrRzor9v/"
                       target="_blank" rel="noopener noreferrer">Facebook</a>
                </li>
                <li>
                    <a href="https://instagram.com/rabeya8962"
                       target="_blank" rel="noopener noreferrer">Instagram</a>
                </li>
            </ul>
        </section>

        <!-- Contact Form -->
        <section id="message" aria-labelledby="message-heading">
            <h2 id="message-heading">Send Me a Message</h2>

            <!-- POST (not GET) so message text is never placed in the URL / browser history / server logs.
                 A real server endpoint must still validate and escape this data (see report, OWASP A03). -->
            <form action="#" method="post" autocomplete="on">

                <div class="field">
                    <label for="visitor-name">Your Name</label><br>
                    <input type="text" id="visitor-name" name="visitor-name"
                           autocomplete="name" minlength="2" maxlength="60" required>
                </div>

                <div class="field">
                    <label for="visitor-email">Your Email</label><br>
                    <input type="email" id="visitor-email" name="visitor-email"
                           autocomplete="email" maxlength="100" required>
                </div>

                <div class="field">
                    <label for="visitor-message">Your Message</label><br>
                    <p class="hint" id="message-hint">Up to 500 characters.</p>
                    <textarea id="visitor-message" name="visitor-message"
                              rows="5" cols="35" minlength="5" maxlength="500"
                              aria-describedby="message-hint" required></textarea>
                </div>

                <input type="submit" value="Send Message">
                <input type="reset" value="Clear">
            </form>
        </section>

    </main>

    <footer>
        <p>Thank you for visiting my portfolio!</p>
        <p>Copyright &copy; 2026 My Personal Profile</p>
    </footer>

</body>
</html>
