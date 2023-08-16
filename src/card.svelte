<script lang="ts">
  // all calculations done with metric units
  let imperial: boolean = false; // true = imperial, false = metric

  let cm: number;
  let kg: number;
  let feet: number;
  let inches: number;
  let stone: number;
  let lbs: number;

  $: metricWeightTotalLbs = Number(stone) * 14 + Number(lbs);
  $: metricHeightTotalInches = Number(feet) * 12 + Number(inches);

  function convertLbsToKg(lbs) {
    return lbs * 0.4535924;
  }
  function convertInchesToCm(inches) {
    return inches * 2.54;
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
        <div class="metric">
          <div class="input-wrapper">
            <input
              type="text"
              id="height"
              maxlength="3"
              placeholder="0"
              bind:value={feet}
            />
            <span>ft</span>
          </div>
          <div class="input-wrapper">
            <input
              type="text"
              id="height"
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
        <div class="metric">
          <div class="input-wrapper">
            <input
              type="text"
              id="weight"
              maxlength="3"
              placeholder="0"
              bind:value={stone}
            />
            <span>st</span>
          </div>
          <div class="input-wrapper">
            <input
              type="text"
              id="weight"
              maxlength="3"
              placeholder="0"
              bind:value={lbs}
            />
            <span>lbs</span>
          </div>
        </div>
      </label>
    </div>
  {:else}
    <div class="input">
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
          {calculateBmi(metricWeightTotalLbs, metricHeightTotalInches)}
        </div>
      </div>
      <p>
        Your BMI suggests you're <span class="classification"
          ><!-- add classification --></span
        >. Your ideal weight is between
        <span class="range"><!-- add range --></span>.
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
          ><!-- add classification --></span
        >. Your ideal weight is between
        <span class="range"><!-- add range --></span>.
      </p>
    {:else}
      <div>
        <p class="welcome">Welcome!</p>
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
  }
  input[type="text"]::placeholder {
    color: var(--color-gunmetal-muted);
  }
  .input label span {
    position: absolute;
    right: var(--padding-base);
    top: 50%;
    transform: translatey(-50%);
    color: var(--color-blue);
  }

  .metric {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .welcome {
    font-size: var(--font-heading-md);
    line-height: 110%;
    letter-spacing: -5%;
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
</style>
