
<div class="form-group">

  <label for="rows">Number of Rows:</label>

  <select class="form-control" id="rows" [(ngModel)]="selectedRows">

    <option *ngFor="let row of rows" [value]="row">{{row}}</option>

  </select>

</div>

<div class="form-group">

  <label for="columns">Number of Columns:</label>

  <select class="form-control" id="columns" [(ngModel)]="selectedColumns">

    <option *ngFor="let column of columns" [value]="column">{{column}}</option>

  </select>

</div>

<table class="table">

  <thead>

    <tr>

      <th *ngFor="let col of [].constructor(selectedColumns)">Column {{col + 1}}</th>

    </tr>

  </thead>

  <tbody>

    <tr *ngFor="let row of [].constructor(selectedRows)">

      <td *ngFor="let col of [].constructor(selectedColumns)">{{row + 1}}.{{col + 1}}</td>

    </tr>

  </tbody>

</table>

selectedRows = 3;

  selectedColumns = 4;

  rows = [3, 4, 5];

  columns = [4, 5, 6];

