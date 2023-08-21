<script lang="ts">
  import logo from "./assets/images/logo.svg";
  import Card from "./card.svelte";
  import image_man_eating from "./assets/images/image-man-eating.webp";
  import icon_eating from "./assets/images/icon-eating.svg";
  import icon_exercise from "./assets/images/icon-exercise.svg";
  import icon_sleep from "./assets/images/icon-sleep.svg";
  import icon_gender from "./assets/images/icon-gender.svg";
  import icon_age from "./assets/images/icon-age.svg";
  import icon_muscle from "./assets/images/icon-muscle.svg";
  import icon_pregnancy from "./assets/images/icon-pregnancy.svg";
  import icon_race from "./assets/images/icon-race.svg";
</script>

<div class="container">
  <main>
    <div>
      <img src={logo} alt="logo" class="logo" />
      <div class="hero">
        <h1>Body Mass Index Calculator</h1>
        <p>
          Better understand your weight in relation to your height using our
          body mass index (BM) calculator. While BMI is not the sole determinant
          of a healthy weight, it offers a valuable starting point to evaluate
          your overall health and well-being.
        </p>
      </div>
    </div>

    <div>
      <Card />
    </div>
  </main>

  <section class="information">
    <div>
      <img src={image_man_eating} alt="man eating sushi roll with chopsticks" />

      <div>
        <div class="curved-line-left" />
        <h2>What your BMI result means</h2>

        <p>
          A BMI range of 18.5 to 24.9 is considered a 'healthy weight.'
          Maintaining a healthy weight may lower your chances of experiencing
          health issues later on, such as obesity and type 2 diabetes. Aim for a
          nutritious diet with reduced fat and sugar content, incorporating
          ample fruits and vegetables. Additionally, strive for regular physical
          activity, ideally about 30 minutes daily for five days a week.
        </p>
      </div>
    </div>

    <ul>
      <li>
        <img src={icon_eating} alt="" />
        <div>
          <h3>Healthy eating</h3>
          <p>
            Healthy eating promotes weight control, disease prevention, better
            digestion, immunity, mental clarity, and mood.
          </p>
        </div>
      </li>

      <li>
        <img src={icon_exercise} alt="" />
        <div>
          <h3>Regular exercise</h3>
          <p>
            Exercise improves fitness, aids weight control, elevates mood, and
            reduces disease risk, fostering wellness and longevity.
          </p>
        </div>
      </li>

      <li>
        <img src={icon_sleep} alt="" />
        <div>
          <h3>Adequate sleep</h3>
          <p>
            Sleep enhances mental clarity, emotional stability, and physical
            wellness, promoting overall restoration and rejuvenation.
          </p>
        </div>
      </li>
    </ul>
  </section>

  <section class="limitations">
    <div>
      <h2>Limitations of BMI</h2>
      <p>
        Although BMI is often a practical indicator of healthy weight, it is not
        suited for every person. Specific groups should carefully consider their
        BMI outcomes, and in certain cases, the measurement may not be
        beneficial to use.
      </p>
    </div>

    <ul>
      <li>
        <div>
          <img src={icon_gender} alt="" />
          <h3>Gender</h3>
        </div>
        <p>
          The development and body fat composition of girls and boys vary with
          age. Consequently, a child's age and gender are considered when
          evaluating their BMI.
        </p>
      </li>

      <li>
        <div>
          <img src={icon_age} alt="" />
          <h3>Age</h3>
        </div>
        <p>
          In aging individuals, increased body fat and muscle loss may cause BMI
          to underestimate body fat content.
        </p>
      </li>

      <li>
        <div>
          <img src={icon_muscle} alt="" />
          <h3>Muscle</h3>
        </div>
        <p>
          BMI may misclassify muscular individuals as overweight or obese, as it
          doesn't differentiate muscle from fat.
        </p>
      </li>

      <li>
        <div>
          <img src={icon_pregnancy} alt="" />
          <h3>Pregnancy</h3>
        </div>
        <p>
          Expectant mothers experience weight gain due to their growing baby.
          Maintaining a healthy pre-pregnancy BMI is advisable to minimise
          health risks for both mother and child.
        </p>
      </li>

      <li>
        <div>
          <img src={icon_race} alt="" />
          <h3>Race</h3>
        </div>
        <p>
          Certain health concerns may affect individuals of some Black and Asian
          origins at lower BMIs than others. To learn more, it is advised to
          discuss this with your GP or practice nurse.
        </p>
      </li>
    </ul>
  </section>
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    gap: 4.5rem;
  }
  main {
    position: relative;
    width: 100%;
    padding-inline: var(--padding-base);
    padding-top: 2rem;
  }

  .hero {
    margin-top: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    align-items: center;
    text-align: center;
  }
  .hero p {
    color: var(--color-dark-electric-blue);
  }
  .logo {
    margin-inline: auto;
    width: 2.5rem;
    height: 2.5rem;
  }

  @media (min-width: 768px) {
    .container {
      gap: 6rem;
    }
    main {
      position: relative;
      width: 100%;
      padding-inline: var(--padding-base);
      padding-top: 2rem;
    }

    .hero {
      margin-top: 2.5rem;
    }
    .logo {
      width: 2.5rem;
      height: 2.5rem;
    }
  }
  @media (min-width: 1440px) {
    .container {
      gap: 07.5rem;
    }
    main {
      padding-top: 4.6875rem;
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 2rem;
    }
    main > :first-child {
      grid-column: 1 / 6;
      column-span: 6;
    }
    main > :nth-child(2) {
      grid-column: 7 / 13;
      column-span: 5;
    }

    .hero {
      margin-top: 7.9375rem;
      gap: 2.1875rem;
      text-align: left;
    }
    .logo {
      width: 4rem;
      height: 4rem;
      margin: 0;
    }
  }

  .information p {
    color: var(--color-dark-electric-blue);
  }
  .information > :first-child > :last-child {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    margin-inline: var(--padding-base);
    margin-top: 3rem;
    margin-bottom: 4rem;
  }

  .information ul {
    background: var(--gradient-1);
    padding: 3.5rem var(--padding-base);
    display: flex;
    flex-direction: column;
    gap: 2.5rem;
  }
  .information li {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }
  .information li > img {
    width: 4rem;
    height: 4rem;
  }
  .information li > :last-child {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .information h3 {
    font-size: var(--font-heading-md);
  }
  .curved-line-left {
    display: none;
  }
  @media (min-width: 768px) {
    .information > :first-child {
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
    }
    .information > :first-child > :first-child {
      transform: translateX(-75px);
    }
    .information > :first-child > :last-child {
      margin: 0 var(--padding-base) 0 0;
      gap: 2rem;
    }
    .information ul {
      margin-top: 6rem;
      padding: 3.75rem var(--padding-base);
    }
    .information li {
      flex-direction: row;
      align-items: center;
      gap: 2.5rem;
    }
  }
  @media (min-width: 1440px) {
    .information > :first-child {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 2rem;
      margin-inline: var(--padding-base);
    }
    .information > :first-child > :first-child {
      transform: translateX(0);
      grid-column: 1 / 7;
      column-span: 6;
    }
    .information > :first-child > :last-child {
      margin: 0;
      gap: calc(2rem + 3px);
      grid-column: 8 / 13;
      column-span: 5;
      height: 100%;
      justify-content: flex-end;
      padding-bottom: 2.5rem;
      position: relative;
    }
    .information ul {
      border-radius: calc(var(--radius-lg) + 3px);
      padding: 4.5rem 7.25rem 6rem;
      margin-inline: 1.5rem;
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 2rem;
    }
    .information li {
      column-span: 4;
      flex-direction: column;
      align-items: start;
      gap: calc(2.5rem + 5px);
    }
    .information li:first-child {
      grid-column: 1 / 5;
    }
    .information li:nth-child(2) {
      grid-column: 5 / 9;
    }
    .information li:nth-child(3) {
      grid-column: 9 / 13;
    }
    .curved-line-left {
      display: block;
      height: 200px;
      width: 100%;
      position: absolute;
      top: -2.5rem;
      right: -75%;
      background-repeat: no-repeat;
      background-image: url("./pattern-curved-line-left.svg");
    }
  }

  .limitations {
    margin: 0 var(--padding-base) 6rem;
  }
  .limitations > :first-child {
    text-align: center;
  }
  .limitations h2 {
    margin-bottom: 1.5rem;
  }
  .limitations p {
    color: var(--color-dark-electric-blue);
  }
  .limitations ul {
    margin-top: 3.5rem;
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  .limitations li {
    background: var(--color-white);
    padding: 1.5rem;
    border-radius: var(--radius-md);
    box-shadow: var(--shadow-card);
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .limitations li > :first-child {
    display: flex;
    align-items: center;
    gap: 1rem;
  }
  .limitations li > :first-child img {
    width: 2rem;
    height: 2rem;
  }
  .limitations h3 {
    font-size: var(--font-heading-sm);
  }

  @media (min-width: 768px) {
    .limitations h2 {
      margin-bottom: 2rem;
    }
    .limitations ul {
      grid-template-columns: repeat(12, 1fr);
      grid-template-rows: repeat(3, 1fr);
      gap: 1.5rem 1rem;
    }
    .limitations li {
      padding: 2rem;
    }
    .limitations ul > :nth-child(1) {
      grid-column: 1 / 7;
      grid-row: 1 / 2;
    }
    .limitations ul > :nth-child(2) {
      grid-column: 7 / 13;
      grid-row: 1 / 2;
    }
    .limitations ul > :nth-child(3) {
      grid-column: 1 / 7;
      grid-row: 2 / 3;
    }
    .limitations ul > :nth-child(4) {
      grid-column: 7 / 13;
      grid-row: 2 / 3;
    }
    .limitations ul > :nth-child(5) {
      grid-column: 4 / 10;
      grid-row: 3 / 4;
    }
  }
  @media (min-width: 1440px) {
    .limitations {
      position: relative;
    }
    .limitations > :first-child {
      text-align: left;
      max-width: 654px;
      position: relative;
    }
    .limitations > :first-child::before {
      content: "";
      display: block;
      height: 122px;
      width: 100%;
      position: absolute;
      bottom: -130%;
      left: 25%;
      background-repeat: no-repeat;
      background-image: url("./assets/images/pattern-curved-line-right.svg");
    }
    .limitations h2 {
      margin-bottom: calc(2rem + 3px);
    }
    .limitations ul {
      margin-top: 0;
      padding-bottom: 7.4rem;
      grid-template-rows: auto;
      gap: 2rem;
      position: absolute;
      top: 0;
    }
    .limitations ul > :nth-child(1) {
      grid-column: 8 / 12;
      grid-row: 1 / 2;
    }
    .limitations ul > :nth-child(2) {
      grid-column: 5 / 9;
      grid-row: 2 / 3;
    }
    .limitations ul > :nth-child(3) {
      grid-column: 9 / 13;
      grid-row: 2 / 3;
    }
    .limitations ul > :nth-child(4) {
      grid-column: 3 / 7;
      grid-row: 3 / 4;
    }
    .limitations ul > :nth-child(5) {
      grid-column: 7 / 11;
      grid-row: 3 / 4;
    }
  }
</style>
