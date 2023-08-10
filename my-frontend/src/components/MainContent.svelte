<script>
  let sections = [
      { text: 'Section 1' },
      { text: 'Section 2' },
      { text: 'Section 3' },
      { text: 'Section 4' },
  ];
</script>

<style>
  body {
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      height: 100vh;
  }

  .row {
      display: flex;
      flex: 1;
  }

  .column {
      flex: 1;
      border-right: 1px solid #ccc;
      border-bottom: 1px solid #ccc;
      padding: 20px;
      box-sizing: border-box;
  }

  .column:last-child {
      border-right: none;
  }

  .row:last-child .column {
      border-bottom: none;
  }

  /* Additional styling for the first row's first column */
  .row:first-child .column:first-child {
      display: flex;
      flex-direction: column;
  }

  .row:first-child .column:first-child .sub-column {
      flex: 1;
      border-right: 1px solid #ccc;
      padding: 10px;
      box-sizing: border-box;
  }

  .row:first-child .column:first-child .sub-column:last-child {
      border-right: none;
  }

  /* Line styling for the sections */
  .row:first-child .column:first-child .sub-column {
      border-bottom: 1px solid #ccc;
  }
</style>

<div class="row">
  <div class="column">
      {#each sections as section}
          <div class="sub-column">{section.text}</div>
      {/each}
  </div>
  <div class="column">Row 1, Column 2</div>
</div>
<div class="row">
  <div class="column">Row 2, Column 1</div>
  <div class="column">Row 2, Column 2</div>
</div>