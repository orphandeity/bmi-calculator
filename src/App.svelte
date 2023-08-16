<script lang="ts">
  import logo from "./assets/images/logo.svg";
  import Card from "./card.svelte";
  import image_man_eating from "./assets/images/image-man-eating.webp";
  import icon_eating from "./assets/images/icon-eating.svg";
  import icon_exercise from "./assets/images/icon-exercise.svg";
  import icon_sleep from "./assets/images/icon-sleep.svg";
</script>

<div class="container">
  <main>
    <div class="hero">
      <img src={logo} alt="logo" />
      <h1>Body Mass Index Calculator</h1>
      <p>
        Better understand your weight in relation to your height using our body
        mass index (BM) calculator. While BMI is not the sole determinant of a
        healthy weight, it offers a valuable starting point to evaluate your
        overall health and well-being.
      </p>
    </div>

    <Card />
  </main>

  <section class="information">
    <img src={image_man_eating} alt="man eating sushi roll with chopsticks" />

    <h2>What your BMI result means</h2>

    <p>
      A BMI range of 18.5 to 24.9 is considered a 'healthy weight.' Maintaining
      a healthy weight may lower your chances of experiencing health issues
      later on, such as obesity and type 2 diabetes. Aim for a nutritious diet
      with reduced fat and sugar content, incorporating ample fruits and
      vegetables. Additionally, strive for regular physical activity, ideally
      about 30 minutes daily for five days a week.
    </p>

    <ul>
      <li>
        <div class="eating">
          <img src={icon_eating} alt="" />
        </div>
        <h3>Healthy eating</h3>
        <p>
          Healthy eating promotes weight control, disease prevention, better
          digestion, immunity, mental clarity, and mood.
        </p>
      </li>

      <li>
        <div class="exercise">
          <img src={icon_exercise} alt="" />
        </div>
        <h3>Regular exercise</h3>
        <p>
          Exercise improves fitness, aids weight control, elevates mood, and
          reduces disease risk, fostering wellness and longevity.
        </p>
      </li>

      <li>
        <div class="sleep">
          <img src={icon_sleep} alt="" />
        </div>
        <h3>Adequate sleep</h3>
        <p>
          Sleep enhances mental clarity, emotional stability, and physical
          wellness, promoting overall restoration and rejuvenation.
        </p>
      </li>
    </ul>
  </section>

  <section>
    <div>
      <h2>Limitations of BMI</h2>
      <p>
        Although BMI is often a practical indicator of healthy weight, it is not
        suited for every person. Specific groups should carefully consider their
        BMI outcomes, and in certain cases, the measurement may not be
        beneficial to use.
      </p>
    </div>

    <div>
      <h3>Gender</h3>
      <p>
        The development and body fat composition of girls and boys vary with
        age. Consequently, a child's age and gender are considered when
        evaluating their BMI.
      </p>
    </div>

    <div>
      <h3>Age</h3>
      <p>
        In aging individuals, increased body fat and muscle loss may cause BMI
        to underestimate body fat content.
      </p>
    </div>

    <div>
      <h3>Muscle</h3>
      <p>
        BMI may misclassify muscular individuals as overweight or obese, as it
        doesn't differentiate muscle from fat.
      </p>
    </div>

    <div>
      <h3>Pregnancy</h3>
      <p>
        Expectant mothers experience weight gain due to their growing baby.
        Maintaining a healthy pre-pregnancy BMI is advisable to minimise health
        risks for both mother and child.
      </p>
    </div>

    <div>
      <h3>Race</h3>
      <p>
        Certain health concerns may affect individuals of some Black and Asian
        origins at lower BMIs than others. To learn more, it is advised to
        discuss this with your GP or practice nurse.
      </p>
    </div>
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
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    align-items: center;
    text-align: center;
  }
  .hero img {
    width: 2.5rem;
    height: 2.5rem;
  }

  .information h2 {
    margin: 3rem 1.5rem 0;
  }
  .information p {
    color: var(--color-dark-electric-blue);
  }
  .information > p {
    margin: 2rem 1.5rem 4rem;
  }
  .information ul {
    background: var(--gradient-1);
    padding: 3.5rem 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 2.5rem;
  }
  .information li > :first-child {
    width: 4rem;
    height: 4rem;
    border-radius: var(--radius-full);
    display: grid;
    place-items: center;
  }
  .eating {
    background: var(--color-red);
  }
  .exercise {
    background: var(--color-yellow);
  }
  .sleep {
    background: var(--color-green);
  }
  .information h3 {
    margin: 2rem 0 1.5rem;
  }
</style>
