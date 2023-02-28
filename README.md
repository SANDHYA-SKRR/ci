import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class AppService {

  constructor(private http: HttpClient) { }
  getEmp(query: string) {
    return this.http.get<any>(`http://localhost:3000/employees/search?q=${query}`);
  }
}


<p-autoComplete [(ngModel)]="selectedEmp"
 [suggestions]="empList" 
 (completeMethod)="search($event)"
 field="title">
</p-autoComplete>


import { Component } from '@angular/core';
import { AppService } from './app.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'autocomplete';
  empList = [];
  selectedEmp: any;
 constructor(private service: AppService) {}
  search($event: any) {
    // console.log($event)
    this.service.getEmp($event.query).subscribe (
      response => this.empList = response.employees
    )
    
  }
}





