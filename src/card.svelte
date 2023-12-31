<script lang="ts">
  // all calculations done with metric units
  let imperial: boolean = false; // true = imperial, false = metric

  let cm: number;
  let kg: number;
  let feet: number;
  let inches: number;
  let stone: number;
  let lbs: number;

  $: imperialWeightTotalLbs = Number(stone) * 14 + Number(lbs);
  $: imperialHeightTotalInches = Number(feet) * 12 + Number(inches);

  function convertLbsToKg(lbs) {
    return lbs * 0.453592;
  }
  function convertInchesToCm(inches) {
    return inches * 2.54;
  }

  function convertKgToLbs(kg) {
    return Math.round(kg * 2.204623);
  }

  function calculateBmi(weight, height) {
    let kg = weight;
    let cm = height;
    if (imperial) {
      kg = convertLbsToKg(weight);
      cm = convertInchesToCm(height);
    }
    return (kg / (cm * 0.01) ** 2).toFixed(1);
  }

  function analyzeResults(bmi) {
    if (bmi < 18.5) {
      return "underweight";
    } else if (bmi >= 18.5 && bmi < 25) {
      return "healthy";
    } else if (bmi >= 25 && bmi < 30) {
      return "overweight";
    } else if (bmi >= 30) {
      return "obese";
    }
  }

  function healthyWeight(height) {
    let baseHeight = 152;
    let difference = height - baseHeight;
    let addition = (difference / 2.54) * 2.3;
    let healthyWeight = Math.round(baseHeight + addition);
    return `${Math.round(
      healthyWeight - healthyWeight * 0.02
    )}lbs and ${Math.round(healthyWeight + healthyWeight * 0.02)}lbs`;
  }
</script>

<div class="card">
  <div class="background" />
  <h2>Enter your details below</h2>

  <fieldset name="imperial" id="metric-imperial">
    <label for="metric">
      <input
        type="radio"
        name="imperial"
        id="metric"
        placeholder="0"
        bind:group={imperial}
        value={false}
      />
      Metric
    </label>

    <label for="imperial">
      <input
        type="radio"
        name="imperial"
        id="imperial"
        placeholder="0"
        bind:group={imperial}
        value={true}
      />
      Imperial
    </label>
  </fieldset>

  {#if imperial}
    <div class="input">
      <label for="height">
        Height
        <div class="imperial">
          <div class="input-wrapper">
            <input
              type="text"
              maxlength="3"
              placeholder="0"
              bind:value={feet}
            />
            <span>ft</span>
          </div>
          <div class="input-wrapper">
            <input
              type="text"
              maxlength="3"
              placeholder="0"
              bind:value={inches}
            />
            <span>in</span>
          </div>
        </div>
      </label>

      <label for="weight">
        Weight
        <div class="imperial">
          <div class="input-wrapper">
            <input
              type="text"
              maxlength="3"
              placeholder="0"
              bind:value={stone}
            />
            <span>st</span>
          </div>
          <div class="input-wrapper">
            <input type="text" maxlength="3" placeholder="0" bind:value={lbs} />
            <span>lbs</span>
          </div>
        </div>
      </label>
    </div>
  {:else}
    <div class="input metric-wrapper">
      <label for="height">
        Height
        <div class="input-wrapper">
          <input
            type="text"
            id="height"
            maxlength="3"
            placeholder="0"
            bind:value={cm}
          />
          <span>cm</span>
        </div>
      </label>

      <label for="weight">
        Weight
        <div class="input-wrapper">
          <input
            type="text"
            id="weight"
            maxlength="3"
            placeholder="0"
            bind:value={kg}
          />
          <span>kg</span>
        </div>
      </label>
    </div>
  {/if}

  <div class="result">
    {#if imperial && inches && lbs}
      <div>
        <p>Your BMI is...</p>
        <div id="bmi">
          {calculateBmi(imperialWeightTotalLbs, imperialHeightTotalInches)}
        </div>
      </div>
      <p>
        Your BMI suggests you're <span class="classification"
          >{analyzeResults(
            calculateBmi(imperialWeightTotalLbs, imperialHeightTotalInches)
          )}</span
        >. Your ideal weight is between
        <span class="range"
          >{healthyWeight(convertInchesToCm(imperialHeightTotalInches))}</span
        >.
      </p>
    {:else if !imperial && cm && kg}
      <div>
        <p>Your BMI is...</p>
        <div id="bmi">
          {calculateBmi(kg, cm)}
        </div>
      </div>
      <p>
        Your BMI suggests you're <span class="classification"
          >{analyzeResults(calculateBmi(kg, cm))}</span
        >. Your ideal weight is between
        <span class="range">{healthyWeight(cm)}</span>.
      </p>
    {:else}
      <div class="welcome">
        <p>Welcome!</p>
        <p>Enter your height and weight and you'll see your BMI result here</p>
      </div>
    {/if}
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
    background: var(--gradient-1);
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
    cursor: pointer;
    width: 2rem;
    height: 2rem;
    display: grid;
    place-content: center;
    outline: 1px solid transparent;
    transition: 200ms background ease-in, 300ms outline ease-in-out;
  }
  input[type="radio"]:hover {
    outline: 1px solid var(--color-blue);
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
    display: grid;
    grid-template-columns: 1fr;
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
  .input-wrapper {
    position: relative;
    font-size: var(--font-heading-md);
    font-weight: 600;
  }
  input[type="text"] {
    border: 1px solid var(--color-borders);
    border-radius: var(--radius-sm);
    padding: 1.25rem 1.5rem;
    width: 100%;
    transition: 200ms border ease-in-out;
  }
  input[type="text"]::placeholder {
    color: var(--color-gunmetal-muted);
  }
  input[type="text"]:hover {
    border: 1px solid var(--color-blue);
    cursor: pointer;
  }
  .input label span {
    position: absolute;
    right: 1.5rem;
    top: 50%;
    transform: translatey(-50%);
    color: var(--color-blue);
  }

  .imperial {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .welcome > p:first-child {
    font-size: var(--font-heading-md);
    line-height: 110%;
    letter-spacing: -5%;
  }

  .result {
    background: var(--color-blue);
    color: var(--color-white);
    border-radius: var(--radius-md) var(--radius-md) var(--radius-md)
      var(--radius-md);
    padding: var(--padding-lg);
    display: grid;
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  .result > :first-child {
    font-weight: 600;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  #bmi {
    font-size: var(--font-heading-lg);
    line-height: 110%;
    letter-spacing: -5%;
  }
  .result p:last-child {
    font-size: var(--font-small);
    font-weight: 400;
  }
  .range {
    font-weight: 600;
  }

  @media (min-width: 768px) {
    .card {
      margin-top: 2.5rem;
      padding: 2rem;
      gap: 2rem;
    }
    .metric-wrapper {
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem;
    }
    .background {
      height: 78%;
    }
    .result {
      border-radius: var(--radius-md) var(--radius-full) var(--radius-full)
        var(--radius-md);
      padding: var(--padding-lg);
      grid-template-columns: 1fr 1fr;
    }
    .welcome {
      grid-column: 1 / 3;
    }
  }
  @media (min-width: 1440px) {
    .card {
      margin-top: 10.4375rem;
    }
    .background {
      height: 737px;
      width: 978px;
    }
    h2 {
      font-size: var(--font-heading-md);
    }
  }
</style>
