
import { Injectable } from '@angular/core';

import { MatSnackBar } from '@angular/material/snack-bar';

@Injectable({

  providedIn: 'root'

})

export class SnackbarService {

  constructor(private snackBar: MatSnackBar) {}

  openSnackBar(message: string, action: string) {

    this.snackBar.open(message, action, {

      duration: 2000,

    });

  }

}

import { Component } from '@angular/core';

import { SnackbarService } from 'path/to/snackbar.service';

@Component({

  selector: 'app-component-a',

  template: `

    <button (click)="showSnackbar()">Show Snackbar</button>

  `

})

export class ComponentA {

  constructor(private snackbarService: SnackbarService) {}

  showSnackbar() {

    this.snackbarService.openSnackBar('Snackbar message', 'Close');

  }

}

import { NgModule } from '@angular/core';

import { MatSnackBarModule } from '@angular/material/snack-bar';

@NgModule({

  imports: [MatSnackBarModule],

  declarations: [ComponentB],

})

export class ComponentBModule {}

import { Component } from '@angular/core';

import { SnackbarService } from 'path/to/snackbar.service';

@Component({

  selector: 'app-component-b',

  template: ``

})

export class ComponentB {

  constructor(private snackbarService: SnackbarService) {}

}

