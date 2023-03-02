app.component.html

<div class="row form-group g-3">
    <div class="col-md-3">
<p-dropdown [options]="courseOptions" [(ngModel)]="selectedUgCourse" (onChange)="onCourseChange('ug_course')"></p-dropdown>
<div *ngIf="showUgInput" class="other-course-input">
  <label for="ug_course_input">Other Course:</label>
  <input type="text" id="ug_course_input" name="ug_course_input" [(ngModel)]="newUgCourse">
  <input type="checkbox" pTooltip="Enter your username" tooltipPosition="right">
    

</div>
</div>
<div class="col-md-3">

<p-dropdown [options]="courseOptions" [(ngModel)]="selectedPgCourse" (onChange)="onCourseChange('pg_course')"></p-dropdown>
<div *ngIf="showPgInput" class="other-course-input">
  <label for="pg_course_input">Other Course:</label>
  <input type="text" id="pg_course_input" name="pg_course_input" [(ngModel)]="newPgCourse">
  <input type="checkbox" pTooltip="Enter your username" tooltipPosition="right">

</div>
</div>
<div class="col-md-3">

<p-dropdown [options]="courseOptions" [(ngModel)]="selectedDiplomoCourse" (onChange)="onCourseChange('diplomo_course')"></p-dropdown>
<div *ngIf="showDiplomoInput" class="other-course-input">
  <label for="diplomo_course_input">Other Course:</label>
  <input type="text" id="diplomo_course_input" name="diplomo_course_input" [(ngModel)]="newDiplomoCourse">
  <input type="checkbox" pTooltip="Enter your username" tooltipPosition="right">

</div>
</div>
</div>


app.component.ts

courseOptions = [
  { label: 'Bsc', value: 'Bsc' },
  { label: 'Msc', value: 'Msc' },
  { label: 'BE', value: 'BE' },
  { label: 'Others', value: 'Others' }
];

selectedUgCourse: string='';
selectedPgCourse: string='';
selectedDiplomoCourse: string='';
showUgInput = false;
showPgInput = false;
showDiplomoInput = false;
newUgCourse: string='';
newPgCourse: string='';
newDiplomoCourse: string='';

onCourseChange(courseType: string) {
  const selectedCourse = this.getSelectedCourse(courseType);
  switch (courseType) {
    case 'ug_course':
      if (selectedCourse === 'Others') {
        this.showUgInput = true;
      } else {
        this.showUgInput = false;
      }
      break;
    case 'pg_course':
      if (selectedCourse === 'Others') {
        this.showPgInput = true;
      } else {
        this.showPgInput = false;
      }
      break;
      case 'diplomo_course':
        if (selectedCourse === 'Others') {
          this.showDiplomoInput = true;
        } else {
          this.showDiplomoInput = false;
        }
        break;
      default:
        break;
    }
  }
  private getSelectedCourse(courseType: string) {
    switch (courseType) {
      case 'ug_course':
        return this.selectedUgCourse;
      case 'pg_course':
        return this.selectedPgCourse;
      case 'diplomo_course':
        return this.selectedDiplomoCourse;
      default:
        return '';
    }
  }

}
