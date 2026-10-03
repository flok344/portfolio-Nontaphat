# portfol<!DOCTYPE html>
<html lang="th">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Nontaphat Prasom | Portfolio</title>

<!-- Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Kanit:wght@200;300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">

<!-- Devicon -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css">

<!-- GSAP -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollToPlugin.min.js"></script>

<style>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
    background: #050505;
}

body {
    background: #050505;
    color: #fff;
    font-family: "Kanit", sans-serif;
    font-weight: 300;
    overflow-x: hidden;
}

a {
    color: inherit;
    text-decoration: none;
}


/* =========================================================
   HACKER LOADING
========================================================= */

#loader {
    position: fixed;
    inset: 0;
    z-index: 999999;
    background: #020202;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
}

.loader-grid {
    position: absolute;
    inset: 0;
    background-image:
        linear-gradient(rgba(255,255,255,.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.025) 1px, transparent 1px);
    background-size: 40px 40px;
}

.loader-scanline {
    position: absolute;
    width: 100%;
    height: 2px;
    top: -5%;
    left: 0;
    background: rgba(255,255,255,.18);
    box-shadow:
        0 0 10px rgba(255,255,255,.3),
        0 0 30px rgba(255,255,255,.1);
    animation: loaderScan 2s linear infinite;
}

@keyframes loaderScan {
    from { top: -5%; }
    to { top: 105%; }
}

.loader-content {
    position: relative;
    z-index: 5;
    width: min(800px, 90%);
    font-family: "Space Mono", monospace;
}

.loader-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-bottom: 15px;
    margin-bottom: 25px;
    border-bottom: 1px solid #222;
    font-size: 10px;
    letter-spacing: 2px;
    color: #666;
}

.loader-status {
    color: #aaa;
}

.loader-terminal {
    position: relative;
    min-height: 240px;
    padding: 25px;
    border: 1px solid #242424;
    background: rgba(255,255,255,.015);
    box-shadow:
        inset 0 0 50px rgba(255,255,255,.015),
        0 0 80px rgba(0,0,0,.8);
}

.loader-line {
    font-size: 13px;
    line-height: 2;
    color: #777;
    opacity: 0;
    transform: translateX(-15px);
    transition:
        opacity .35s ease,
        transform .35s ease;
}

.loader-line.show {
    opacity: 1;
    transform: translateX(0);
}

.loader-line::before {
    content: "> ";
    color: #fff;
}

.loader-line.active {
    color: #fff;
}

.loader-cursor {
    display: inline-block;
    width: 7px;
    height: 15px;
    margin-left: 5px;
    vertical-align: middle;
    background: #fff;
    animation: loaderCursor .55s infinite;
}

@keyframes loaderCursor {
    0%,45% { opacity: 1; }
    46%,100% { opacity: 0; }
}

.loader-title {
    margin: 30px 0 25px;
    font-size: clamp(38px, 8vw, 75px);
    line-height: .9;
    font-weight: 700;
    letter-spacing: -4px;
    color: #fff;
}

.loader-title.glitch {
    animation: loaderGlitch .12s infinite;
}

@keyframes loaderGlitch {
    0% { transform: translate(0); opacity: 1; }
    20% { transform: translate(-5px, 2px); opacity: .75; }
    40% { transform: translate(4px, -1px); opacity: 1; }
    60% { transform: translate(-3px, 1px); opacity: .65; }
    80% { transform: translate(3px, 0); opacity: .9; }
    100% { transform: translate(0); opacity: 1; }
}

.loader-progress-wrap {
    margin-top: 25px;
}

.loader-progress-info {
    display: flex;
    justify-content: space-between;
    margin-bottom: 9px;
    font-size: 9px;
    letter-spacing: 2px;
    color: #666;
}

.loader-progress {
    width: 100%;
    height: 3px;
    overflow: hidden;
    background: #181818;
}

.loader-progress-bar {
    width: 0%;
    height: 100%;
    background: #fff;
    box-shadow: 0 0 10px rgba(255,255,255,.5);
    transition: width .08s linear;
}

.loader-footer {
    display: flex;
    justify-content: space-between;
    margin-top: 15px;
    font-size: 8px;
    letter-spacing: 1px;
    color: #444;
}

.loader-flash {
    position: absolute;
    inset: 0;
    background: #fff;
    opacity: 0;
    pointer-events: none;
    z-index: 50;
    transition: opacity .04s linear;
}


/* =========================================================
   SCROLL PROGRESS
========================================================= */

.scroll-progress {
    position: fixed;
    top: 0;
    left: 0;
    width: 0%;
    height: 3px;
    background: #fff;
    z-index: 10000;
}


/* =========================================================
   CUSTOM CURSOR
========================================================= */

.cursor {
    position: fixed;
    width: 14px;
    height: 14px;
    border: 1px solid #fff;
    border-radius: 50%;
    pointer-events: none;
    z-index: 10001;
    transform: translate(-50%, -50%);
    mix-blend-mode: difference;
    transition:
        width .25s ease,
        height .25s ease,
        background .25s ease;
}

.cursor.active {
    width: 45px;
    height: 45px;
    background: #fff;
}


/* =========================================================
   NAVBAR
========================================================= */

.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 80px;
    z-index: 999;
    display: flex;
    align-items: center;
    transition: .4s ease;
}

.navbar.scrolled {
    background: rgba(5,5,5,.82);
    backdrop-filter: blur(15px);
    border-bottom: 1px solid #1d1d1d;
}

.nav-container {
    width: min(1400px, 90%);
    margin: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-family: "Space Mono", monospace;
    font-size: 15px;
    letter-spacing: 3px;
    font-weight: 700;
}

.logo span {
    color: #777;
}

.nav-links {
    display: flex;
    gap: 35px;
    list-style: none;
}

.nav-links a {
    position: relative;
    font-family: "Space Mono", monospace;
    font-size: 11px;
    color: #888;
    letter-spacing: 1px;
    transition: .3s ease;
}

.nav-links a:hover {
    color: #fff;
}

.nav-links a::after {
    content: "";
    position: absolute;
    bottom: -7px;
    left: 0;
    width: 0;
    height: 1px;
    background: #fff;
    transition: .3s ease;
}

.nav-links a:hover::after {
    width: 100%;
}


/* =========================================================
   HERO
========================================================= */

.hero {
    min-height: 100vh;
    position: relative;
    display: flex;
    align-items: center;
    overflow: hidden;
    background:
        radial-gradient(
            circle at 75% 35%,
            rgba(255,255,255,.08),
            transparent 25%
        ),
        radial-gradient(
            circle at 20% 80%,
            rgba(255,255,255,.04),
            transparent 25%
        ),
        #050505;
}

.hero::before {
    content: "";
    position: absolute;
    inset: 0;
    opacity: .05;
    background-image:
        linear-gradient(
            rgba(255,255,255,.2) 1px,
            transparent 1px
        ),
        linear-gradient(
            90deg,
            rgba(255,255,255,.2) 1px,
            transparent 1px
        );
    background-size: 70px 70px;
}

.hero-container {
    width: min(1400px, 90%);
    margin: auto;
    display: grid;
    grid-template-columns: 1.1fr .9fr;
    gap: 50px;
    align-items: center;
    position: relative;
    z-index: 2;
}

.hero-label {
    font-family: "Space Mono", monospace;
    font-size: 12px;
    letter-spacing: 5px;
    color: #888;
    margin-bottom: 25px;
}

.hero h1 {
    font-family: "Space Mono", monospace;
    font-size: clamp(60px, 10vw, 135px);
    line-height: .85;
    letter-spacing: -8px;
    font-weight: 700;
    margin-bottom: 35px;
}

.hero-description {
    max-width: 570px;
    color: #999;
    font-size: 17px;
    line-height: 1.9;
    margin-bottom: 40px;
}

.hero-buttons {
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
}

.btn {
    position: relative;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 150px;
    padding: 14px 25px;
    border: 1px solid #444;
    font-family: "Space Mono", monospace;
    font-size: 10px;
    letter-spacing: 2px;
    overflow: hidden;
    transition: .35s ease;
}

.btn::before {
    content: "";
    position: absolute;
    inset: 0;
    background: #fff;
    transform: translateY(101%);
    transition: .35s ease;
    z-index: -1;
}

.btn:hover {
    color: #000;
    border-color: #fff;
}

.btn:hover::before {
    transform: translateY(0);
}

.btn.primary {
    background: #fff;
    color: #000;
    border-color: #fff;
}

.btn.primary::before {
    background: #222;
}

.btn.primary:hover {
    color: #fff;
}


/* =========================================================
   HERO IMAGE
========================================================= */

.hero-image-area {
    position: relative;
    display: flex;
    justify-content: center;
}

.hero-image-wrapper {
    width: min(480px, 100%);
    aspect-ratio: 4 / 5;
    position: relative;
    z-index: 2;
}

.hero-image {
    width: 100%;
    height: 100%;
    overflow: hidden;
    border: 1px solid #333;
    position: relative;
    background: #111;
}

.hero-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: none;
    display: block;
    transition: transform .7s ease;
}

.hero-image:hover img {
    transform: scale(1.03);
}

.image-number {
    position: absolute;
    right: -15px;
    bottom: -20px;
    font-family: "Space Mono", monospace;
    font-size: 90px;
    color: rgba(255,255,255,.06);
    font-weight: 700;
    z-index: -1;
}


/* =========================================================
   GRAPHICS
========================================================= */

.graphic-bg {
    position: absolute;
    inset: 0;
    pointer-events: none;
}

.orb {
    position: absolute;
    border-radius: 50%;
    border: 1px solid rgba(255,255,255,.08);
}

.orb-1 {
    width: 420px;
    height: 420px;
    right: 4%;
    top: 15%;
}

.orb-2 {
    width: 180px;
    height: 180px;
    left: 5%;
    bottom: 10%;
}

.cross {
    position: absolute;
    width: 35px;
    height: 35px;
    opacity: .35;
}

.cross::before,
.cross::after {
    content: "";
    position: absolute;
    background: #fff;
}

.cross::before {
    width: 100%;
    height: 1px;
    top: 50%;
}

.cross::after {
    width: 1px;
    height: 100%;
    left: 50%;
}

.cross-1 {
    top: 20%;
    left: 48%;
}

.cross-2 {
    right: 5%;
    bottom: 15%;
}

.code-stream {
    position: absolute;
    right: 2%;
    top: 25%;
    width: 120px;
    opacity: .13;
    font-family: "Space Mono", monospace;
    font-size: 8px;
    line-height: 2;
    color: #fff;
    white-space: pre-line;
    overflow: hidden;
    height: 300px;
}


/* =========================================================
   GENERAL
========================================================= */

section {
    position: relative;
}

.section-container {
    width: min(1400px, 90%);
    margin: auto;
}

.section-label {
    font-family: "Space Mono", monospace;
    font-size: 10px;
    color: #777;
    letter-spacing: 3px;
    margin-bottom: 20px;
}

.section-title {
    font-family: "Space Mono", monospace;
    font-size: clamp(45px, 8vw, 100px);
    letter-spacing: -5px;
    line-height: .9;
}


/* =========================================================
   ABOUT
========================================================= */

.about {
    padding: 160px 0;
    border-top: 1px solid #181818;
    overflow: hidden;
}

.about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 100px;
    align-items: center;
}

.about-text {
    max-width: 650px;
}

.about-text h2 {
    font-family: "Space Mono", monospace;
    font-size: clamp(45px, 7vw, 90px);
    line-height: .9;
    letter-spacing: -5px;
    margin-bottom: 45px;
}

.about-text p {
    color: #999;
    font-size: 16px;
    line-height: 2;
    margin-bottom: 20px;
}

.about-visual {
    position: relative;
    min-height: 620px;
    border: 1px solid #252525;
    overflow: hidden;
}

.about-visual img {
    width: 100%;
    height: 100%;
    min-height: 620px;
    object-fit: cover;
    display: block;
    filter: none;
    transition: transform 1s ease;
}

.about-visual:hover img {
    transform: scale(1.04);
}

.about-overlay {
    position: absolute;
    inset: 0;
    background:
        linear-gradient(
            to top,
            rgba(0,0,0,.65),
            transparent 55%
        );
}

.about-number {
    position: absolute;
    right: 20px;
    bottom: -15px;
    font-family: "Space Mono", monospace;
    font-size: 150px;
    line-height: 1;
    color: rgba(255,255,255,.1);
    font-weight: 700;
}

.about-caption {
    position: absolute;
    left: 25px;
    bottom: 25px;
    font-family: "Space Mono", monospace;
    font-size: 10px;
    letter-spacing: 2px;
}


/* =========================================================
   EDUCATION
========================================================= */

.education {
    margin-top: 100px;
}

.education-title {
    font-family: "Space Mono", monospace;
    font-size: 13px;
    letter-spacing: 3px;
    margin-bottom: 25px;
}

.education-item {
    border-top: 1px solid #242424;
    padding: 25px 0;
    display: grid;
    grid-template-columns: 70px 1fr auto;
    gap: 20px;
    align-items: center;
}

.edu-number {
    font-family: "Space Mono", monospace;
    color: #666;
    font-size: 11px;
}

.edu-main {
    font-size: 16px;
}

.edu-sub {
    color: #777;
    font-size: 13px;
    margin-top: 5px;
}

.edu-year {
    color: #666;
    font-family: "Space Mono", monospace;
    font-size: 10px;
}


/* =========================================================
   GPA
========================================================= */

.gpa-box {
    margin-top: 30px;
    padding: 25px;
    border: 1px solid #252525;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.gpa-label {
    font-family: "Space Mono", monospace;
    color: #777;
    font-size: 10px;
    letter-spacing: 2px;
}

.gpa-number {
    font-family: "Space Mono", monospace;
    font-size: 42px;
    font-weight: 700;
}


/* =========================================================
   HOBBIES
========================================================= */

.hobbies {
    margin-top: 55px;
}

.hobbies-title {
    font-family: "Space Mono", monospace;
    font-size: 12px;
    letter-spacing: 3px;
    margin-bottom: 20px;
}

.hobbies-list {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.hobby {
    padding: 10px 15px;
    border: 1px solid #292929;
    color: #999;
    font-size: 12px;
    transition: .3s ease;
}

.hobby:hover {
    border-color: #777;
    color: #fff;
}


/* =========================================================
   SKILLS
========================================================= */

.skills {
    padding: 160px 0;
    border-top: 1px solid #181818;
    overflow: hidden;
}

.skills-header {
    margin-bottom: 80px;
}

.skills-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    border-top: 1px solid #252525;
    border-left: 1px solid #252525;
}

.skill-card {
    min-height: 220px;
    padding: 30px;
    border-right: 1px solid #252525;
    border-bottom: 1px solid #252525;
    position: relative;
    overflow: hidden;
    transition: .4s ease;
}

.skill-card::before {
    content: "";
    position: absolute;
    width: 120px;
    height: 120px;
    border-radius: 50%;
    border: 1px solid rgba(255,255,255,.05);
    right: -50px;
    bottom: -50px;
    transition: .5s ease;
}

.skill-card:hover {
    background: #0d0d0d;
}

.skill-card:hover::before {
    transform: scale(1.5);
}

.skill-icon {
    font-size: 35px;
    margin-bottom: 40px;
    display: block;
}

.skill-name {
    font-family: "Space Mono", monospace;
    font-size: 13px;
    letter-spacing: 1px;
}

.skill-level {
    color: #666;
    font-size: 10px;
    margin-top: 8px;
}


/* =========================================================
   PORTFOLIO
========================================================= */

.portfolio {
    padding: 100px 0 160px;
    border-top: 1px solid #181818;
    overflow: hidden;
}

.portfolio-header {
    width: min(1400px, 90%);
    margin: auto;
    display: none;
}

.portfolio-row {
    overflow: hidden;
    width: 100%;
    margin: 30px 0;
}

.portfolio-track {
    display: flex;
    width: max-content;
    gap: 25px;
    will-change: transform;
}

.work {
    width: 420px;
    height: 260px;
    flex-shrink: 0;
    position: relative;
    overflow: hidden;
    background:
        linear-gradient(
            135deg,
            #181818,
            #080808
        );
    border: 1px solid #292929;
    transform: rotate(-5deg);
    transition: .5s ease;
}

.work:hover {
    transform:
        rotate(0deg)
        scale(1.025);
}

.work.has-image {
    background-size: cover;
    background-position: center;
}

.work::after {
    content: "";
    position: absolute;
    inset: 0;
    background:
        linear-gradient(
            to top,
            rgba(0,0,0,.9),
            rgba(0,0,0,.05) 70%
        );
}

.work-content {
    position: absolute;
    z-index: 3;
    left: 25px;
    right: 25px;
    bottom: 22px;
}

.work-category {
    font-family: "Space Mono", monospace;
    font-size: 9px;
    letter-spacing: 2px;
    color: #999;
    margin-bottom: 8px;
}

.work-title {
    font-size: 22px;
    font-weight: 400;
}

.work-arrow {
    position: absolute;
    z-index: 3;
    right: 25px;
    top: 22px;
    width: 35px;
    height: 35px;
    border: 1px solid rgba(255,255,255,.3);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: "Space Mono", monospace;
    transition: .3s ease;
}

.work:hover .work-arrow {
    background: #fff;
    color: #000;
}

.portfolio-center {
    text-align: center;
    margin: 85px 0;
    pointer-events: none;
}

.portfolio-center span {
    font-family: "Space Mono", monospace;
    font-size: clamp(45px, 10vw, 130px);
    letter-spacing: -8px;
    color: #111;
    -webkit-text-stroke: 1px #292929;
}


/* =========================================================
   CONTACT
========================================================= */

.contact {
    padding: 160px 0;
    border-top: 1px solid #181818;
}

.contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 100px;
}

.contact h2 {
    font-family: "Space Mono", monospace;
    font-size: clamp(45px, 7vw, 90px);
    line-height: .9;
    letter-spacing: -5px;
    margin-bottom: 35px;
}

.contact-description {
    color: #888;
    line-height: 1.9;
    max-width: 500px;
}

.contact-links {
    display: flex;
    flex-direction: column;
}

.contact-link {
    padding: 25px 0;
    border-top: 1px solid #252525;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-family: "Space Mono", monospace;
    font-size: 11px;
    letter-spacing: 1px;
    color: #999;
    transition: .3s ease;
}

.contact-link:last-child {
    border-bottom: 1px solid #252525;
}

.contact-link:hover {
    color: #fff;
    padding-left: 10px;
}

.contact-link span:last-child {
    font-size: 18px;
}


/* =========================================================
   FOOTER
========================================================= */

footer {
    border-top: 1px solid #181818;
    padding: 35px 0;
}

.footer-container {
    width: min(1400px, 90%);
    margin: auto;
    display: flex;
    justify-content: space-between;
    gap: 20px;
    font-family: "Space Mono", monospace;
    font-size: 9px;
    letter-spacing: 2px;
    color: #555;
}


/* =========================================================
   REVEAL
========================================================= */

.reveal {
    opacity: 0;
    transform: translateY(50px);
}


/* =========================================================
   RESPONSIVE
========================================================= */

@media (max-width: 1100px) {

    .hero-container {
        grid-template-columns: 1fr .8fr;
    }

    .skills-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .work {
        width: 350px;
        height: 220px;
    }

}

@media (max-width: 800px) {

    .nav-links {
        gap: 15px;
    }

    .nav-links a {
        font-size: 9px;
    }

    .hero {
        padding: 130px 0 80px;
    }

    .hero-container {
        grid-template-columns: 1fr;
        gap: 70px;
    }

    .hero-image-area {
        justify-content: flex-start;
    }

    .hero-image-wrapper {
        width: min(430px, 90%);
    }

    .about-grid {
        grid-template-columns: 1fr;
        gap: 60px;
    }

    .about-visual {
        min-height: 500px;
    }

    .about-visual img {
        min-height: 500px;
    }

    .contact-grid {
        grid-template-columns: 1fr;
        gap: 60px;
    }

    .code-stream {
        display: none;
    }

}

@media (max-width: 600px) {

    .navbar {
        height: 65px;
    }

    .nav-links {
        display: none;
    }

    .logo {
        font-size: 12px;
    }

    .hero h1 {
        letter-spacing: -5px;
    }

    .hero-description {
        font-size: 14px;
    }

    .about,
    .skills,
    .contact {
        padding: 100px 0;
    }

    .about-text h2,
    .contact h2 {
        letter-spacing: -3px;
    }

    .about-visual,
    .about-visual img {
        min-height: 420px;
    }

    .education-item {
        grid-template-columns: 45px 1fr;
    }

    .edu-year {
        grid-column: 2;
    }

    .skills-grid {
        grid-template-columns: 1fr 1fr;
    }

    .skill-card {
        min-height: 180px;
        padding: 20px;
    }

    .skill-icon {
        margin-bottom: 25px;
        font-size: 28px;
    }

    .work {
        width: 280px;
        height: 180px;
    }

    .work-title {
        font-size: 17px;
    }

    .portfolio-center {
        margin: 55px 0;
    }

    .portfolio-center span {
        letter-spacing: -4px;
    }

    .footer-container {
        flex-direction: column;
    }

    .loader-terminal {
        min-height: 220px;
        padding: 18px;
    }

    .loader-line {
        font-size: 10px;
    }

    .loader-title {
        font-size: 42px;
        letter-spacing: -2px;
    }

    .loader-top {
        font-size: 8px;
    }

}

</style>

</head>

<body>

<!-- =========================================================
     HACKER LOADER
========================================================= -->

<div id="loader">

<div class="loader-grid"></div>

<div class="loader-scanline"></div>

<div class="loader-content">

    <div class="loader-top">

        <span>
            NONTAPHAT SYSTEM
        </span>

        <span class="loader-status">
            SECURE CONNECTION
        </span>

    </div>


    <div class="loader-terminal">

        <div class="loader-line" id="terminalLine1">
            initializing portfolio system...
        </div>

        <div class="loader-line" id="terminalLine2">
            loading creative modules...
        </div>

        <div class="loader-line" id="terminalLine3">
            establishing connection...
        </div>

        <div class="loader-line active" id="terminalLine4">
            access granted<span class="loader-cursor"></span>
        </div>


        <div class="loader-title" id="loaderTitle">
            Dek 70
        </div>


        <div class="loader-progress-wrap">

            <div class="loader-progress-info">

                <span>
                    LOADING PORTFOLIO
                </span>

                <span id="loaderPercent">
                    0%
                </span>

            </div>


            <div class="loader-progress">

                <div
                    class="loader-progress-bar"
                    id="loaderBar">
                </div>

            </div>

        </div>

    </div>


    <div class="loader-footer">

        <span>
            BOOT_SEQUENCE / 2026
        </span>

        <span>
            NONTAPHAT.PRASOM
        </span>

    </div>

</div>


<div
    class="loader-flash"
    id="loaderFlash">
</div>

</div>

<!-- =========================================================
     SCROLL PROGRESS
========================================================= -->

<div class="scroll-progress"></div>

<!-- =========================================================
     CUSTOM CURSOR
========================================================= -->

<div class="cursor"></div>

<!-- =========================================================
     NAVBAR
========================================================= -->

<nav class="navbar">

<div class="nav-container">

    <a href="#home" class="logo magnetic">
        NONTAPHAT<span>.</span>
    </a>

    <ul class="nav-links">

        <li>
            <a href="#home">
                HOME
            </a>
        </li>

        <li>
            <a href="#about">
                ABOUT
            </a>
        </li>

        <li>
            <a href="#skills">
                SKILLS
            </a>
        </li>

        <li>
            <a href="#portfolio">
                WORK
            </a>
        </li>

        <li>
            <a href="#contact">
                CONTACT
            </a>
        </li>

    </ul>

</div>

</nav>

<!-- =========================================================
     HERO
========================================================= -->

<section class="hero" id="home">

<div class="graphic-bg">

    <div class="orb orb-1"></div>

    <div class="orb orb-2"></div>

    <div class="cross cross-1"></div>

    <div class="cross cross-2"></div>


    <div class="code-stream">
01 10 01 11
0101 1010
001 011 001
110101
010101 011
1001001
10101010
001101
011010
111000
010011
101101
001011
110101
010100
011101
101001
000111
    </div>

</div>


<div class="hero-container">

    <div class="hero-content">

        <div class="hero-label">
            Dek 70 / PORTFOLIO
        </div>


        <h1 class="hero-title">

            <br>

            PortFolio

        </h1>


        <p class="hero-description">

            สวัสดีครับผมนนทพัทธ์ ประสม
            สนใจด้านการพัฒนาเว็บไซต์
            การเขียนโปรแกรม และการออกแบบ
            พร้อมเรียนรู้และสร้างผลงานใหม่ ๆ

        </p>


        <div class="hero-buttons">

            <a
                href="#portfolio"
                class="btn primary magnetic"
            >
                ดูผลงาน
            </a>

            <a
                href="#contact"
                class="btn magnetic"
            >
                ติดต่อ
            </a>

        </div>

    </div>


    <div class="hero-image-area">

        <div class="hero-image-wrapper tilt">

            <div class="hero-image">

                <img
                    src="https://cdn.phototourl.com/member/2026-10-03-67cfba52-62bd-451a-a134-ceca1eb7987e.jpg"
                    alt="Nontaphat Prasom"
                >

            </div>


            <div class="image-number">
                01
            </div>

        </div>

    </div>

</div>

</section>

<!-- =========================================================
     ABOUT
========================================================= -->

<section class="about" id="about">

<div class="section-container">

    <div class="about-grid">


        <div class="about-text reveal">

            <div class="section-label">
                01 / ABOUT ME
            </div>


            <h2>
                About<br>
                Me.
            </h2>


            <p>
                ผมเป็นคนที่สนใจด้าน การพัฒนาเว็บไซต์
                การเขียนโปรแกรม และการออกแบบ
                โดยชอบเรียนรู้สิ่งใหม่ ๆ
                และนำความรู้มาทดลองสร้างผลงานจริง
            </p>


            <p>
                ผมให้ความสำคัญกับการออกแบบเว็บไซต์
                ให้ใช้งานง่าย มีความทันสมัย
                และสามารถแสดงตัวตนรวมถึงแนวคิด
                ของผู้สร้างได้
            </p>


            <p>
                เป้าหมายของผมคือการพัฒนาทักษะ
                ด้านเทคโนโลยีอย่างต่อเนื่อง
                และสร้างผลงานที่สามารถนำไปต่อยอด
                ในอนาคตได้
            </p>


            <div class="education">

                <div class="education-title">
                    EDUCATION
                </div>


                <div class="education-item">

                    <div class="edu-number">
                        01
                    </div>


                    <div>

                        <div class="edu-main">
                            ระดับประถมศึกษา - มัธยมศึกษาตอนต้น
                        </div>

                        <div class="edu-sub">
                            โรงเรียนสารสิทธิ์ธีรศาสตร์
                        </div>

                    </div>


                    <div class="edu-year">
                        SCHOOL
                    </div>

                </div>


                <div class="education-item">

                    <div class="edu-number">
                        02
                    </div>


                    <div>

                        <div class="edu-main">
                            ระดับมัธยมศึกษาตอนปลาย
                        </div>

                        <div class="edu-sub">
                            โรงเรียนสารสิทธิ์พิทยาลัย
                        </div>

                    </div>


                    <div class="edu-year">
                        SCHOOL
                    </div>

                </div>


                <div class="gpa-box">

                    <div class="gpa-label">
                        GPAX / 4 SEMESTERS
                    </div>

                    <div class="gpa-number">
                        2.34
                    </div>

                </div>

            </div>


            <div class="hobbies">

                <div class="hobbies-title">
                    HOBBIES
                </div>


                <div class="hobbies-list">

                    <div class="hobby">
                        เล่นกีตาร์
                    </div>

                    <div class="hobby">
                        เรียนรู้และฝึกเทคโนโลยีใหม่ ๆ
                    </div>

                    <div class="hobby">
                        ฝึกทักษะภาษาอังกฤษ
                    </div>

                </div>

            </div>

        </div>


        <div class="about-visual reveal tilt">

            <img
                src="https://cdn.phototourl.com/member/2026-10-03-67cfba52-62bd-451a-a134-ceca1eb7987e.jpg"
                alt="About Nontaphat"
            >


            <div class="about-overlay"></div>


            <div class="about-number">
                01
            </div>


            <div class="about-caption">
                WEB / CODE / CREATIVE
            </div>

        </div>

    </div>

</div>

</section>

<!-- =========================================================
     SKILLS
========================================================= -->

<section class="skills" id="skills">

<div class="section-container">


    <div class="skills-header reveal">

        <div class="section-label">
        SKILLS
        </div>


        <h2 class="section-title">

                    tech stack<br>

        </h2>

    </div>


    <div class="skills-grid">


        <div class="skill-card reveal">

            <i class="devicon-html5-plain skill-icon"></i>

            <div class="skill-name">
                HTML
            </div>

            <div class="skill-level">
                STRUCTURE / WEB
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-css3-plain skill-icon"></i>

            <div class="skill-name">
                CSS
            </div>

            <div class="skill-level">
                UI / DESIGN
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-javascript-plain skill-icon"></i>

            <div class="skill-name">
                JAVASCRIPT
            </div>

            <div class="skill-level">
                INTERACTION
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-python-plain skill-icon"></i>

            <div class="skill-name">
                PYTHON
            </div>

            <div class="skill-level">
                PROGRAMMING
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-javascript-plain skill-icon"></i>

            <div class="skill-name">
                GSAP
            </div>

            <div class="skill-level">
                ANIMATION
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-git-plain skill-icon"></i>

            <div class="skill-name">
                GIT
            </div>

            <div class="skill-level">
                VERSION CONTROL
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-github-original skill-icon"></i>

            <div class="skill-name">
                GITHUB
            </div>

            <div class="skill-level">
                COLLABORATION
            </div>

        </div>


        <div class="skill-card reveal">

            <i class="devicon-figma-plain skill-icon"></i>

            <div class="skill-name">
                FIGMA
            </div>

            <div class="skill-level">
                UI / UX
            </div>

        </div>

    </div>

</div>

</section>

<!-- =========================================================
     PORTFOLIO
========================================================= -->

<section class="portfolio" id="portfolio">

<div class="portfolio-header">

    <div class="section-label">
        03 / SELECTED WORK
    </div>


    <h2 class="section-title">
        Portfolio.
    </h2>

</div>


<div class="portfolio-row portfolio-top">

    <div class="portfolio-track">


        <div
            class="work has-image"
            style="background-image:url('https://cdn.phototourl.com/member/2026-10-03-73eaab6d-4afa-4d8e-b889-320abe52a1df.jpg');"
        >

            <div class="work-arrow">
                ↗
            </div>


            <div class="work-content">

                <div class="work-title">
                    Sarasit Open house
                </div>

            </div>

        </div>


        <!-- เพิ่มผลงานใบประกาศ -->
        <div
            class="work has-image"
            style="background-image:url('https://cdn.phototourl.com/member/2026-10-03-7b062ed7-cfe6-4ac4-9487-1061a4b01d2d.png');"
        >

            <div class="work-arrow">
                ↗
            </div>


            <div class="work-content">

                <div class="work-category">
                    CERTIFICATE / TRAINING
                </div>

                <div class="work-title">
                    การอบรมการสร้างหน้าเว็บเบื้องต้นด้วย HTML และ CSS
                </div>

            </div>

        </div>


        <div
            class="work has-image"
            style="background-image:url('https://cdn.phototourl.com/member/2026-10-03-a97a7eb7-7daf-47c7-bac8-988fa9056dd8.jpg');"
        >

            <div class="work-arrow">
                ↗
            </div>


        <div class="work">

            <div class="work-arrow">
                ↗
            </div>


            <div class="work-content">

                <div class="work-category">
                    WEB DESIGN
                </div>

                <div class="work-title">
                    Creative Website
                </div>

            </div>

        </div>


        <div class="work">

            <div class="work-arrow">
                ↗
            </div>


            <div class="work-content">

                <div class="work-category">
                    DEVELOPMENT
                </div>

                <div class="work-title">
                    Interactive Project
                </div>

            </div>

        </div>


    </div>

</div>


<div class="portfolio-center">

    <span>
        MY PORTFOLIO
    </span>

</div>


<div class="portfolio-row portfolio-bottom">

    <div class="portfolio-track">


        <div
            class="work has-image"
            style="background-image:url('https://cdn.phototourl.com/member/2026-10-03-a97a7eb7-7daf-47c7-bac8-988fa9056dd8.jpg');"
        >

            <div class="work-arrow">
                ↗
            </div>


            <div class="work-content">

                <div class="work-category">
                    ACTIVITY / PRESENTATION
                </div>

                <div class="work-title">
                    My Activity
                </div>

            </div>

        </div>


        <div
            class="work has-image"
            style="background-image:url('https://cdn.phototourl.com/member/2026-10-03-73eaab6d-4afa-4d8e-b889-320abe52a1df.jpg');" 
        > 
 
            <div class="work-arrow"> 
                ↗ 
            </div> 
 
 
            <div class="work-content"> 
 
                <div class="work-category"> 
                    ACTIVITY / PRESENTATION 
                </div> 
 
                <div class="work-title"> 
                    Sarasit NextGen 
                </div> 
 
            </div> 
 
        </div> 
 
 
        <div class="work"> 
 
            <div class="work-arrow"> 
                ↗ 
            </div> 
 
 
            <div class="work-content"> 
 
                <div class="work-category"> 
                    DEVELOPMENT 
                </div> 
 
                <div class="work-title"> 
                    Interactive Project 
                </div> 
 
            </div> 
 
        </div> 
 
 
        <div class="work"> 
 
            <div class="work-arrow"> 
                ↗ 
            </div> 
 
 
            <div class="work-content"> 
 
                <div class="work-category"> 
                    WEB DESIGN 
                </div> 
 
                <div class="work-title"> 
                    Creative Website 
                </div> 
 
            </div> 
 
        </div> 
 
 
    </div> 
 
</div> 
 
</section> 
 
<!-- ========================================================= 
     CONTACT 
========================================================= --> 
 
<section class="contact" id="contact"> 
 
<div class="section-container"> 
 
    <div class="contact-grid"> 
 
 
        <div class="reveal"> 
 
            <div class="section-label"> 
                04 / CONTACT 
            </div> 
 
 
            <h2> 
                Let's<br> 
                Talk. 
            </h2> 
 
 
            <p class="contact-description"> 
 
                หากต้องการพูดคุยเกี่ยวกับผลงาน 
                การพัฒนาเว็บไซต์ หรือโปรเจกต์ต่าง ๆ 
                สามารถติดต่อผมได้ผ่านช่องทางด้านล่าง 
 
            </p> 
 
        </div> 
 
 
        <div class="contact-links reveal"> 
 
 
            <a 
                href="mailto:" 
                class="contact-link magnetic" 
            > 
 
                <span> 
                    EMAIL 
                </span> 
 
                <span> 
                    ↗ 
                </span> 
 
            </a> 
 
 
            <a 
                href="#" 
                class="contact-link magnetic" 
            > 
 
                <span> 
                    FACEBOOK 
                </span> 
 
                <span> 
                    ↗ 
                </span> 
 
            </a> 
 
 
            <a 
                href="#" 
                class="contact-link magnetic" 
            > 
 
                <span> 
                    INSTAGRAM 
                </span> 
 
                <span> 
                    ↗ 
                </span> 
 
            </a> 
 
 
        </div> 
 
    </div> 
 
</div> 
 
</section> 
 
<!-- ========================================================= 
     FOOTER 
========================================================= --> 
 
<footer> 
 
<div class="footer-container"> 
 
    <span> 
        © 2026 NONTAPHAT PRASOM 
    </span> 
 
 
    <span> 
        DESIGNED &amp; DEVELOPED BY NONTAPHAT 
    </span> 
 
</div> 
 
</footer> 
 
<!-- ========================================================= 
     JAVASCRIPT 
========================================================= --> 
 
<script> 
 
/* ========================================================= 
   HACKER LOADER 
   ไม่พึ่ง GSAP 
   ป้องกัน Loader ค้าง 
========================================================= */ 
 
(function () { 
 
    const loader = 
        document.getElementById("loader"); 
 
    if (!loader) { 
        return; 
    } 
 
 
    const line1 = 
        document.getElementById("terminalLine1"); 
 
    const line2 = 
        document.getElementById("terminalLine2"); 
 
    const line3 = 
        document.getElementById("terminalLine3"); 
 
    const line4 = 
        document.getElementById("terminalLine4"); 
 
 
    const bar = 
        document.getElementById("loaderBar"); 
 
    const percent = 
        document.getElementById("loaderPercent"); 
 
    const title = 
        document.getElementById("loaderTitle"); 
 
    const flash = 
        document.getElementById("loaderFlash"); 
 
 
    const lines = [ 
        line1, 
        line2, 
        line3, 
        line4 
    ]; 
 
 
    lines.forEach(function (line) { 
 
        if (line) { 
            line.classList.remove("show"); 
        } 
 
    }); 
 
 
    setTimeout(function () { 
 
        if (line1) { 
            line1.classList.add("show"); 
        } 
 
    }, 100); 
 
 
    setTimeout(function () { 
 
        if (line2) { 
            line2.classList.add("show"); 
        } 
 
    }, 450); 
 
 
    setTimeout(function () { 
 
        if (line3) { 
            line3.classList.add("show"); 
        } 
 
    }, 800); 
 
 
    setTimeout(function () { 
 
        if (line4) { 
            line4.classList.add("show"); 
        } 
 
    }, 1150); 
 
 
    let progress = 0; 
 
 
    const progressTimer = 
        setInterval(function () { 
 
 
            progress += 
                Math.floor( 
                    Math.random() * 5 
                ) + 2; 
 
 
            if (progress >= 100) { 
                progress = 100; 
            } 
 
 
            if (bar) { 
                bar.style.width = 
                    progress + "%"; 
            } 
 
 
            if (percent) { 
                percent.textContent = 
                    progress + "%"; 
            } 
 
 
            if ( 
                progress >= 82 && 
                title 
            ) { 
 
                title.classList.add( 
                    "glitch" 
                ); 
 
            } 
 
 
            if (progress >= 100) { 
 
                clearInterval( 
                    progressTimer 
                ); 
 
 
                setTimeout(function () { 
 
 
                    if (flash) { 
                        flash.style.opacity = 
                            "1"; 
                    } 
 
 
                    setTimeout(function () { 
 
                        if (flash) { 
                            flash.style.opacity = 
                                "0"; 
                        } 
 
                    }, 55); 
 
 
                    setTimeout(function () { 
 
                        if (flash) { 
                            flash.style.opacity = 
                                ".85"; 
                        } 
 
                    }, 110); 
 
 
                    setTimeout(function () { 
 
                        if (flash) { 
                            flash.style.opacity = 
                                "0"; 
                        } 
 
                    }, 165); 
 
 
                    setTimeout(function () { 
 
                        if (flash) { 
                            flash.style.opacity = 
                                "1"; 
                        } 
 
                    }, 220); 
 
 
                    setTimeout(function () { 
 
                        if (flash) { 
                            flash.style.opacity = 
                                "0"; 
                        } 
 
 
                        loader.style.transition = 
                            "opacity .18s ease"; 
 
                        loader.style.opacity = 
                            "0"; 
 
 
                    }, 280); 
 
 
                    setTimeout(function () { 
 
                        loader.style.display = 
                            "none"; 
 
                    }, 550); 
 
 
                }, 350); 
 
            } 
 
 
        }, 90); 
 
 
    setTimeout(function () { 
 
        if ( 
            loader && 
            loader.style.display !== "none" 
        ) { 
 
            loader.style.opacity = "0"; 
 
 
            setTimeout(function () { 
 
                loader.style.display = 
                    "none"; 
 
            }, 250); 
 
        } 
 
    }, 7000); 
 
 
})(); 
 
 
/* ========================================================= 
   MAIN WEBSITE 
========================================================= */ 
 
document.addEventListener( 
    "DOMContentLoaded", 
    function () { 
 
 
        if ( 
            typeof gsap === "undefined" 
        ) { 
 
            document 
                .querySelectorAll(".reveal") 
                .forEach(function (el) { 
 
                    el.style.opacity = "1"; 
 
                    el.style.transform = 
                        "none"; 
 
                }); 
 
            return; 
 
        } 
 
 
        if ( 
            typeof ScrollTrigger !== 
            "undefined" 
        ) { 
 
            gsap.registerPlugin( 
                ScrollTrigger 
            ); 
 
        } 
 
 
        if ( 
            typeof ScrollToPlugin !== 
            "undefined" 
        ) { 
 
            gsap.registerPlugin( 
                ScrollToPlugin 
            ); 
 
        } 
 
 
        /* ================================================= 
           HERO 
        ================================================= */ 
 
        gsap.set( 
            [ 
                ".hero-label", 
                ".hero-title", 
                ".hero-description", 
                ".hero-buttons", 
                ".hero-image-wrapper" 
            ], 
            { 
                opacity: 1 
            } 
        ); 
 
 
        const heroTimeline = 
            gsap.timeline({ 
                delay: 1.9 
            }); 
 
 
        heroTimeline 
 
            .to( 
                ".hero-label", 
                { 
                    opacity: 1, 
                    duration: .6, 
                    ease: "power3.out" 
                } 
            ) 
 
 
            .from( 
                ".hero-title", 
                { 
                    y: 80, 
                    opacity: 0, 
                    duration: 1.1, 
                    ease: "power4.out" 
                }, 
                "-=.25" 
            ) 
 
 
            .to( 
                ".hero-description", 
                { 
                    opacity: 1, 
                    duration: .7, 
                    ease: "power3.out" 
                }, 
                "-=.55" 
            ) 
 
 
            .to( 
                ".hero-buttons", 
                { 
                    opacity: 1, 
                    duration: .6, 
                    ease: "power3.out" 
                }, 
                "-=.4" 
            ) 
 
 
            .to( 
                ".hero-image-wrapper", 
                { 
                    opacity: 1, 
                    x: 0, 
                    rotate: 0, 
                    duration: 1.2, 
                    ease: "power4.out" 
                }, 
                "-=.8" 
            ); 
 
 
        /* ================================================= 
           HERO FLOAT 
        ================================================= */ 
 
        gsap.to( 
            ".hero-image-wrapper", 
            { 
                y: -12, 
 
                duration: 2.8, 
 
                repeat: -1, 
 
                yoyo: true, 
 
                ease: "sine.inOut" 
            } 
        ); 
 
 
        /* ================================================= 
           BACKGROUND 
        ================================================= */ 
 
        gsap.to( 
            ".orb-1", 
            { 
                rotation: 360, 
 
                duration: 30, 
 
                repeat: -1, 
 
                ease: "none" 
            } 
        ); 
 
 
        gsap.to( 
            ".orb-2", 
            { 
                rotation: -360, 
 
                duration: 20, 
 
                repeat: -1, 
 
                ease: "none" 
            } 
        ); 
 
 
        gsap.to( 
            ".cross-1", 
            { 
                rotation: 360, 
 
                duration: 8, 
 
                repeat: -1, 
 
                ease: "none" 
            } 
        ); 
 
 
        gsap.to( 
            ".cross-2", 
            { 
                rotation: -360, 
 
                duration: 10, 
 
                repeat: -1, 
 
                ease: "none" 
            } 
        ); 
 
 
        /* ================================================= 
           REVEAL 
        ================================================= */ 
 
        if ( 
            typeof ScrollTrigger !== 
            "undefined" 
        ) { 
 
            gsap.utils 
                .toArray(".reveal") 
                .forEach(function (element) { 
 
                    gsap.to( 
                        element, 
                        { 
                            opacity: 1, 
 
                            y: 0, 
 
                            duration: 1, 
 
                            ease: "power3.out", 
 
                            scrollTrigger: { 
 
                                trigger: 
                                    element, 
 
                                start: 
                                    "top 88%", 
 
                                once: true 
 
                            } 
 
                        } 
                    ); 
 
                }); 
 
        } 
 
 
        /* ================================================= 
           HERO PARALLAX 
        ================================================= */ 
 
        if ( 
            typeof ScrollTrigger !== 
            "undefined" 
        ) { 
 
            gsap.to( 
                ".hero-content", 
                { 
                    y: -80, 
 
                    ease: "none", 
 
                    scrollTrigger: { 
 
                        trigger: ".hero", 
 
                        start: "top top", 
 
                        end: "bottom top", 
 
                        scrub: 1 
 
                    } 
 
                } 
            ); 
 
 
            gsap.to( 
                ".hero-image-area", 
                { 
                    y: 100, 
 
                    ease: "none", 
 
                    scrollTrigger: { 
 
                        trigger: ".hero", 
 
                        start: "top top", 
 
                        end: "bottom top", 
 
                        scrub: 1 
 
                    } 
 
                } 
            ); 
 
 
            gsap.to( 
                ".code-stream", 
                { 
                    y: 180, 
 
                    ease: "none", 
 
                    scrollTrigger: { 
 
                        trigger: ".hero", 
 
                        start: "top top", 
 
                        end: "bottom top", 
 
                        scrub: 1 
 
                    } 
 
                } 
            ); 
 
 
            gsap.to( 
                ".about-number", 
                { 
                    y: -80, 
 
                    ease: "none", 
 
                    scrollTrigger: { 
 
                        trigger: ".about", 
 
                        start: 
                            "top bottom", 
 
                        end: 
                            "bottom top", 
 
                        scrub: 1 
 
                    } 
 
                } 
            ); 
 
 
            gsap.utils 
                .toArray(".skill-card") 
                .forEach( 
                    function (card, index) { 
 
                        gsap.to( 
                            card, 
                            { 
                                y: 
                                    index % 2 === 0 
                                        ? -35 
                                        : 35, 
 
                                ease: "none", 
 
                                scrollTrigger: { 
 
                                    trigger: 
                                        ".skills", 
 
                                    start: 
                                        "top bottom", 
 
                                    end: 
                                        "bottom top", 
 
                                    scrub: 1 
 
                                } 
 
                            } 
                        ); 
 
                    } 
                ); 
 
 
            gsap.to( 
                ".portfolio-center span", 
                { 
                    x: -100, 
 
                    ease: "none", 
 
                    scrollTrigger: { 
 
                        trigger: 
                            ".portfolio-center", 
 
                        start: 
                            "top bottom", 
 
                        end: 
                            "bottom top", 
 
                        scrub: 1 
 
                    } 
 
                } 
            ); 
 
        } 
 
 
        /* ================================================= 
           INFINITE SLIDER 
        ================================================= */ 
 
        function createInfiniteSlider( 
            row, 
            direction, 
            duration 
        ) { 
 
            if (!row) { 
                return; 
            } 
 
 
            const track = 
                row.querySelector( 
                    ".portfolio-track" 
                ); 
 
 
            if (!track) { 
                return; 
            } 
 
 
            const originalItems = 
                Array.from( 
                    track.children 
                ); 
 
 
            originalItems.forEach( 
                function (item) { 
 
                    track.appendChild( 
                        item.cloneNode(true) 
                    ); 
 
                } 
            ); 
 
 
            const distance = 
                track.scrollWidth / 2; 
 
 
            if ( 
                direction === "left" 
            ) { 
 
                gsap.fromTo( 
                    track, 
 
                    { 
                        x: 0 
                    }, 
 
                    { 
                        x: -distance, 
 
                        duration: 
                            duration, 
 
                        ease: "none", 
 
                        repeat: -1 
                    } 
                ); 
 
            } else { 
 
                gsap.fromTo( 
                    track, 
 
                    { 
                        x: -distance 
                    }, 
 
                    { 
                        x: 0, 
 
                        duration: 
                            duration, 
 
                        ease: "none", 
 
                        repeat: -1 
                    } 
                ); 
 
            } 
 
        } 
 
 
        createInfiniteSlider( 
            document.querySelector( 
                ".portfolio-top" 
            ), 
            "left", 
            22 
        ); 
 
 
        createInfiniteSlider( 
            document.querySelector( 
                ".portfolio-bottom" 
            ), 
            "right", 
            25 
        ); 
 
 
        /* ================================================= 
           MAGNETIC BUTTON 
        ================================================= */ 
 
        document 
            .querySelectorAll(".magnetic") 
            .forEach(function (button) { 
 
 
                button.addEventListener( 
                    "mousemove", 
                    function (event) { 
 
                        const rect = 
                            button.getBoundingClientRect(); 
 
 
                        const x = 
                            event.clientX - 
                            rect.left - 
                            rect.width / 2; 
 
 
                        const y = 
                            event.clientY - 
                            rect.top - 
                            rect.height / 2; 
 
 
                        gsap.to( 
                            button, 
                            { 
                                x: 
                                    x * .2, 
 
                                y: 
                                    y * .2, 
 
                                duration: .3, 
 
                                ease: 
                                    "power2.out" 
                            } 
                        ); 
 
                    } 
                ); 
 
 
                button.addEventListener( 
                    "mouseleave", 
                    function () { 
 
                        gsap.to( 
                            button, 
                            { 
                                x: 0, 
 
                                y: 0, 
 
                                duration: .5, 
 
                                ease: 
                                    "elastic.out(1,.4)" 
                            } 
                        ); 
 
                    } 
                ); 
 
            }); 
 
 
        /* ================================================= 
           3D TILT 
        ================================================= */ 
 
        document 
            .querySelectorAll(".tilt") 
            .forEach(function (element) { 
 
 
                element.addEventListener( 
                    "mousemove", 
                    function (event) { 
 
                        const rect = 
                            element.getBoundingClientRect(); 
 
 
                        const x = 
                            event.clientX - 
                            rect.left; 
 
 
                        const y = 
                            event.clientY - 
                            rect.top; 
 
 
                        const centerX = 
                            rect.width / 2; 
 
 
                        const centerY = 
                            rect.height / 2; 
 
 
                        const rotateX = 
                            ( 
                                (y - centerY) / 
                                centerY 
                            ) * -4; 
 
 
                        const rotateY = 
                            ( 
                                (x - centerX) / 
                                centerX 
                            ) * 4; 
 
 
                        gsap.to( 
                            element, 
                            { 
                                rotateX: 
                                    rotateX, 
 
                                rotateY: 
                                    rotateY, 
 
                                transformPerspective: 
                                    1000, 
 
                                duration: .35, 
 
                                ease: 
                                    "power2.out" 
                            } 
                        ); 
 
                    } 
                ); 
 
 
                element.addEventListener( 
                    "mouseleave", 
                    function () { 
 
                        gsap.to( 
                            element, 
                            { 
                                rotateX: 0, 
 
                                rotateY: 0, 
 
                                duration: .7, 
 
                                ease: 
                                    "power3.out" 
                            } 
                        ); 
 
                    } 
                ); 
 
            }); 
 
 
        /* ================================================= 
           CUSTOM CURSOR 
        ================================================= */ 
 
        const cursor = 
            document.querySelector( 
                ".cursor" 
            ); 
 
 
        if (cursor) { 
 
            window.addEventListener( 
                "mousemove", 
                function (event) { 
 
                    gsap.to( 
                        cursor, 
                        { 
                            x: 
                                event.clientX, 
 
                            y: 
                                event.clientY, 
 
                            duration: .12, 
 
                            ease: 
                                "power2.out" 
                        } 
                    ); 
 
                } 
            ); 
 
 
            document 
                .querySelectorAll( 
                    "a, button, .work, .skill-card" 
                ) 
                .forEach(function (el) { 
 
                    el.addEventListener( 
                        "mouseenter", 
                        function () { 
 
                            cursor.classList.add( 
                                "active" 
                            ); 
 
                        } 
                    ); 
 
 
                    el.addEventListener( 
                        "mouseleave", 
                        function () { 
 
                            cursor.classList.remove( 
                                "active" 
                            ); 
 
                        } 
                    ); 
 
                }); 
 
        } 
 
 
        /* ================================================= 
           NAVBAR + SCROLL PROGRESS 
        ================================================= */ 
 
        const navbar = 
            document.querySelector( 
                ".navbar" 
            ); 
 
 
        const progress = 
            document.querySelector( 
                ".scroll-progress" 
            ); 
 
 
        window.addEventListener( 
            "scroll", 
            function () { 
 
 
                if ( 
                    window.scrollY > 50 
                ) { 
 
                    navbar.classList.add( 
                        "scrolled" 
                    ); 
 
                } else { 
 
                    navbar.classList.remove( 
                        "scrolled" 
                    ); 
 
                } 
 
 
                const scrollTop = 
                    window.scrollY; 
 
 
                const documentHeight = 
                    document.documentElement 
                        .scrollHeight - 
                    window.innerHeight; 
 
 
                const percentage = 
                    documentHeight > 0 
                        ? ( 
                            scrollTop / 
                            documentHeight 
                        ) * 100 
                        : 0; 
 
 
                if (progress) { 
 
                    progress.style.width = 
                        percentage + "%"; 
 
                } 
 
            } 
        ); 
 
 
        /* ================================================= 
           SMOOTH NAVIGATION 
        ================================================= */ 
 
        document 
            .querySelectorAll( 
                'a[href^="#"]' 
            ) 
            .forEach(function (link) { 
 
 
                link.addEventListener( 
                    "click", 
                    function (event) { 
 
                        const target = 
                            document.querySelector( 
                                this.getAttribute( 
                                    "href" 
                                ) 
                            ); 
 
 
                        if (!target) { 
                            return; 
                        } 
 
 
                        event.preventDefault(); 
 
 
                        if ( 
                            typeof ScrollToPlugin !== 
                            "undefined" 
                        ) { 
 
                            gsap.to( 
                                window, 
                                { 
                                    duration: 
                                        1.1, 
 
                                    scrollTo: { 
 
                                        y: target, 
 
                                        offsetY: 
                                            70 
 
                                    }, 
 
                                    ease: 
                                        "power3.inOut" 
                                } 
                            ); 
 
                        } else { 
 
                            target.scrollIntoView({ 
                                behavior: 
                                    "smooth" 
                            }); 
 
                        } 
 
                    } 
                ); 
 
            }); 
 
 
        /* ================================================= 
           REFRESH 
        ================================================= */ 
 
        if ( 
            typeof ScrollTrigger !== 
            "undefined" 
        ) { 
 
            setTimeout( 
                function () { 
 
                    ScrollTrigger.refresh(); 
 
                }, 
                800 
            ); 
 
        } 
 
 
    } 
); 
 
</script> 
 
</body> 
</html>io-Nontaphat
