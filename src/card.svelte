<div class="card">
  <div class="background" />
  <h2>Enter your details below</h2>

  <fieldset name="imperial" id="metric-imperial">
    <label for="metric">
      <input type="radio" name="imperial" id="metric" value="metric" checked />
      Metric
    </label>

    <label for="imperial">
      <input type="radio" name="imperial" id="imperial" value="imperial" />
      Imperial
    </label>
  </fieldset>

  <div class="input">
    <label for="height">
      Height
      <div>
        <input type="text" id="height" maxlength="7" />
        <span>cm</span>
      </div>
    </label>

    <label for="weight">
      Weight
      <div>
        <input type="text" id="weight" maxlength="7" />
        <span>kg</span>
      </div>
    </label>
  </div>

  <div class="result">
    <div>
      <p>Your BMI is...</p>
      <div>
        <!-- add score -->
        23.4
      </div>
    </div>

    <p>
      Your BMI suggests you're <span class="classification"
        ><!-- add classification --></span
      >. Your ideal weight is between
      <span class="range"><!-- add range --></span>.
    </p>
  </div>
</div>

<style>
  .card {
    margin-top: 3rem;
    padding: var(--padding-base);
    background: var(--color-white);
    border-radius: var(--radius-md);
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    box-shadow: var(--shadow-card);
  }
  .background {
    position: absolute;
    inset: 0;
    height: 60%;
    z-index: -1;
    background: linear-gradient(
      to top left,
      var(--color-gradient-1),
      var(--color-gradient-2)
    );
    border-bottom-left-radius: var(--radius-lg);
    border-bottom-right-radius: var(--radius-lg);
  }
  h2 {
    color: var(--color-gunmetal);
  }
  #metric-imperial {
    border: none;
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
  #metric-imperial > * {
    font-weight: 600;
    line-height: 110%;
    display: grid;
    grid-template-columns: 2rem auto;
    gap: 1.125rem;
    align-items: center;
  }
  input[type="radio"] {
    width: 2rem;
    height: 2rem;
    display: grid;
    place-content: center;
    transition: 120ms background ease-in;
  }
  input[type="radio"]:checked {
    background: var(--color-blue-bg);
  }
  input[type="radio"]::before {
    content: "";
    width: 0.875rem;
    height: 0.875rem;
    border-radius: var(--radius-full);
    transform: scale(0);
    transition: 200ms transform ease-out;
    background: var(--color-blue);
  }
  input[type="radio"]:checked::before {
    transform: scale(1);
  }

  #metric,
  #imperial {
    appearance: none;
    border: 1px solid var(--color-borders);
    border-radius: var(--radius-full);
    width: 1.5rem;
    height: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .input {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .input label {
    font-size: var(--font-small);
    color: var(--color-gunmetal);
    line-height: 150%;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }
  .input label > div {
    position: relative;
    font-size: var(--font-heading-md);
    font-weight: 600;
  }
  input[type="text"] {
    border: 1px solid var(--color-borders);
    border-radius: var(--radius-sm);
    padding: 1.25rem 1.5rem;
    width: 100%;
  }
  .input label > div > span {
    position: absolute;
    right: var(--padding-base);
    top: 50%;
    transform: translatey(-50%);
    color: var(--color-blue);
  }

  .result {
    background: var(--color-blue);
    color: var(--color-white);
    border-radius: var(--radius-md);
    padding: var(--padding-lg);
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  .result > :first-child {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }
  .result > :first-child > :first-child {
    font-weight: 600;
  }
  .result > :first-child > :last-child {
    font-size: var(--font-heading-lg);
    font-weight: 600;
    line-height: 110%;
    letter-spacing: -5%;
  }
  .result > :last-child {
    font-size: var(--font-small);
  }
  .range {
    font-weight: 600;
  }
</style>
