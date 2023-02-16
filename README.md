
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

import { Injectable } from '@angular/core';

import { Subject } from 'rxjs';

@Injectable({

  providedIn: 'root'

})

export class NotificationService {

  private notificationSubject = new Subject<any>();

  getNotification() {

    return this.notificationSubject.asObservable();

  }

  sendNotification(message: any) {

    this.notificationSubject.next(message);

  }

}

import { Component } from '@angular/core';

import { NotificationService } from 'path/to/notification.service';

@Component({

  selector: 'app-add-data',

  template: `

    <button (click)="addData()">Add Data</button>

  `

})

export class AddDataComponent {

  constructor(private notificationService: NotificationService) { }

  addData() {

    // add data logic here

    this.notificationService.sendNotification('Data added successfully!');

  }

}

import { Component } from '@angular/core';

import { NotificationService } from 'path/to/notification.service';

@Component({

  selector: 'app-receive-notification',

  template: `

    <div *ngIf="notification">{{ notification }}</div>

  `

})

export class ReceiveNotificationComponent {

  notification: any;

  constructor(private notificationService: NotificationService) {

    this.notificationService.getNotification().subscribe((message) => {

      this.notification = message;

    });

  }

}
