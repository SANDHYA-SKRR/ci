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
    this.storedSelectedEmployees = selectedEmployees;
  }
}
