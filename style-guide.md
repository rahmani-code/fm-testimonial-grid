/_ ===== Google Font ===== _/
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@500;600;700&display=swap");

/_ ===== Color tokens ===== _/
:root {
--purple-500: hsl(263, 55%, 52%);
--white: hsl(0, 0%, 100%);
--grey-100: hsl(214, 17%, 92%);
--grey-500: hsl(217, 19%, 35%);
--dark-blue: hsl(219, 29%, 14%);
--black: hsl(0, 0%, 7%);
}

/_ ===== Base / reset ===== _/
_,
_::before,
\*::after {
box-sizing: border-box;
}

body {
margin: 0;
font-family: "Barlow Semi Condensed", sans-serif;
background: var(--grey-100);
color: var(--black);
}

img {
display: block;
max-width: 100%;
}

/_ ===== Page wrapper — vertically & horizontally centers the grid ===== _/
.testimonials {
min-height: 100vh;
display: grid;
place-items: center;
padding: 70px 24px;
}

.testimonials\_\_container {
width: 100%;
max-width: 1110px;
}

/_ ===== Responsive grid ===== _/
.testimonials\_\_grid {
display: grid;
gap: 24px;
/_ Mobile: single column _/
grid-template-columns: 1fr;
}

/_ ===== Card base ===== _/
.testimonial-card {
border-radius: 8px;
padding: 26px 32px 32px;
box-shadow: 40px 60px 50px -47px rgba(72, 85, 106, 0.25);
background: var(--white);
color: var(--grey-500);
}

/_ ===== Card header ===== _/
.testimonial-card\_\_header {
display: flex;
align-items: center;
gap: 17px;
margin-bottom: 18px;
}

.testimonial-card\_\_avatar img {
width: 28px;
height: 28px;
border-radius: 50%;
border: 2px solid transparent; /_ overridden per theme below _/
}

.testimonial-card\_\_name {
font-weight: 500;
font-size: 13px;
line-height: 1;
color: inherit;
}

.testimonial-card\_\_status {
margin-top: 4px;
font-weight: 500;
font-size: 11px;
opacity: 0.5;
color: inherit;
}

/_ ===== Card body ===== _/
.testimonial-card\_\_title {
font-weight: 600;
font-size: 20px;
line-height: 1.2;
margin: 0 0 16px;
color: inherit;
}

.testimonial-card\_\_quote {
margin: 0;
font-weight: 500;
font-size: 13px;
line-height: 1.7;
opacity: 0.7;
color: inherit;
}

/_ ===== Desktop 4-column layout ===== _/
@media (min-width: 1024px) {
.testimonials\_\_grid {
grid-template-columns: repeat(4, 1fr);
gap: 30px;
align-items: start; /_ cards keep their natural height _/
}

.testimonial-card--daniel {
grid-column: 1 / span 2;
grid-row: 1;
}

.testimonial-card--jonathan {
grid-column: 3;
grid-row: 1;
}

.testimonial-card--kira {
grid-column: 4;
grid-row: 1 / span 2;
}

.testimonial-card--jeanette {
grid-column: 1;
grid-row: 2;
}

.testimonial-card--patrick {
grid-column: 2 / span 2;
grid-row: 2;
}
}

/_ ===== Card themes ===== _/

/_ --- Daniel: purple --- _/
.testimonial-card--daniel {
background: var(--purple-500);
color: var(--white);
position: relative;
overflow: hidden; /_ keeps the giant quote mark inside the card _/
}

.testimonial-card--daniel::before {
content: "";
position: absolute;
top: 0;
right: 80px; /_ matches the design — quote mark is offset from right _/
width: 104px;
height: 102px;
background: url("./images/bg-pattern-quotation.svg") no-repeat center / contain;
pointer-events: none;
z-index: 0;
}

/_ Push card content above the pseudo-element _/
.testimonial-card--daniel .testimonial-card**header,
.testimonial-card--daniel .testimonial-card**content {
position: relative;
z-index: 1;
}

.testimonial-card--daniel .testimonial-card\_\_avatar img {
border-color: hsl(264, 82%, 70%); /_ subtle purple tint ring _/
}

/_ --- Jonathan: slate --- _/
.testimonial-card--jonathan {
background: var(--grey-500);
color: var(--white);
}

.testimonial-card--jonathan .testimonial-card\_\_avatar img {
border-color: hsl(217, 19%, 50%);
}

/_ --- Patrick: dark blue --- _/
.testimonial-card--patrick {
background: var(--dark-blue);
color: var(--white);
}

.testimonial-card--patrick .testimonial-card\_\_avatar img {
border-color: hsl(219, 29%, 30%);
}

/_ --- Jeanette & Kira: white (default) --- _/
.testimonial-card--jeanette .testimonial-card**avatar img,
.testimonial-card--kira .testimonial-card**avatar img {
border-color: hsl(263, 55%, 52%); /_ purple ring on white cards _/
}

/_ Kira: keep name/status in dark tone so it reads on white _/
.testimonial-card--jeanette .testimonial-card**name,
.testimonial-card--kira .testimonial-card**name {
color: var(--dark-blue);
}
