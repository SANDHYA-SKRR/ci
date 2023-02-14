# ci


First


import { Component, OnInit, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'app-employee-list',
  template: `
    <table>
      <tr *ngFor="let employee of employees">
        <td>
          <input type="checkbox" [(ngModel)]="employee.selected">
        </td>
        <td>{{ employee.name }}</td>
        <td>{{ employee.email }}</td>
      </tr>
    </table>
    <button (click)="submitSelectedEmployees()">Submit</button>
  `
})
export class EmployeeListComponent implements OnInit {
  employees = [
    { name: 'John Doe', email: 'john.doe@example.com', selected: false },
    { name: 'Jane Doe', email: 'jane.doe@example.com', selected: false },
    { name: 'Jim Smith', email: 'jim.smith@example.com', selected: false }
  ];

  @Output() selectedEmployees = new EventEmitter<any[]>();

  constructor() { }

  ngOnInit() {
  }

  submitSelectedEmployees() {
    const selectedEmployees = this.employees.filter(employee => employee.selected);
    this.selectedEmployees.emit(selectedEmployees);
  }
}




Second

import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'app-selected-employee-list',
  template: `
    <table>
      <tr *ngFor="let employee of selectedEmployees">
        <td>{{ employee.name }}</td>
        <td>{{ employee.email }}</td>
      </tr>
    </table>
  `
})
export class SelectedEmployeeListComponent implements OnInit {
  @Input() selectedEmployees: any[];

  constructor() { }

  ngOnInit() {
  }
}



App


import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <app-employee-list (selectedEmployees)="storeSelectedEmployees($event)"></app-employee-list>
    <app-selected-employee-list [selectedEmployees]="storedSelectedEmployees"></app-selected-employee-list>
  `
})
export class AppComponent {
  storedSelectedEmployees: any[] = [];

  storeSelectedEmployees(selectedEmployees) {
    this.storedSelectedEmployees = selectedEmploye
    
    
    
    es;
    
    
    
    
    
    
    
    <nav class="navbar navbar-expand-sm navbar-dark bg-primary">
  <a class="navbar-brand" href="#">Header</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link" href="#">Option 1</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Option 2</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Option 3</a>
      </li>
    </ul>
  </div>
</nav>

  }
  
  
  
  

