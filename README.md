
<form #myForm="ngForm" (ngSubmit)="onSubmit(myForm)">

  <div>

    <label for="imageUpload">Upload Image</label>

    <input type="file" id="imageUpload" name="imageUpload" accept="image/*" (change)="onImageSelected($event)">

  </div>

  <div>

    <label>Cropped Image Preview</label>

    <img [src]="croppedImage" [ngClass]="{'hidden': !croppedImage}" alt="Cropped Image Preview">

  </div>

  <button type="submit">Submit</button>

</form>

import { Component, OnInit } from '@angular/core';

import { ImageCroppedEvent, CropperSettings } from 'ngx-image-cropper';

@Component({

  selector: 'app-root',

  templateUrl: './app.component.html',

  styleUrls: ['./app.component.css']

})

export class AppComponent implements OnInit {

  title = 'image-cropper-app';

  imageChangedEvent: any = '';

  croppedImage: any = '';

  cropperSettings: CropperSettings;

  ngOnInit(): void {

    this.cropperSettings = new CropperSettings();

    this.cropperSettings.width = 200;

    this.cropperSettings.height = 200;

    this.cropperSettings.croppedWidth = 200;

    this.cropperSettings.croppedHeight = 200;

    this.cropperSettings.canvasWidth = 400;

    this.cropperSettings.canvasHeight = 400;

    this.cropperSettings.minWidth = 100;

    this.cropperSettings.minHeight = 100;

    this.cropperSettings.rounded = false;

    this.cropperSettings.keepAspect = true;

    this.cropperSettings.cropperDrawSettings.strokeColor = 'rgba(255,255,255,1)';

    this.cropperSettings.cropperDrawSettings.strokeWidth = 2;

    this.c

  }

  onImageSelected(event: any): void {

    this.imageChangedEvent = event;

  }

  onSubmit(form: any): void {

    // Extract the cropped image from the image cropper

    const imageBlob = this.dataURItoBlob(this.croppedImage);

    // Attach the image blob to the form data

    const formData = new FormData();

    formData.append('avatar', imageBlob, 'avatar.png');

    // Append other form fields to the form data

    formData.append('name', form.value.name);

    formData.append('email', form.value.email);

    // Submit the form data to the server using a HTTP POST request

    // ...

  }

  // Utility function to convert data URL to Blob object

  private dataURItoBlob(dataURI: string): Blob {

    const byteString = atob(dataURI.split(',')[1]);

    const mimeString = dataURI.split(',')[0].split(':')[1].split(';')[0];

    const ab = new ArrayBuffer(byteString.length);

    const ia = new Uint8Array(ab);

    for (let i = 0; i < byteString.length; i++) {

      ia[i] = byteString.charCodeAt(i);

    }

    return new Blob([ab], { type: mimeString });

  }

  // Event listener for image cropper ready event

  imageCropped(event: ImageCroppedEvent): void {

    this.croppedImage = event.base64;

  }

}


Yesterday was a day that holds a special place in my heart. As a woman, it reminds me of all the amazing women who are mothers, sisters, friends, mentors, and everything in between. It feels very special and I wanted to take a moment to thank you for the wonderful self-defense class you conducted on Women's Day. The session was extremely informative and empowering, and I feel much more confident in my ability to protect myself in dangerous situations.

Overall, I feel that the Women's Day celebration was a great success and a fitting tribute to the incredible women in our community. I feel that the self-defense class was a great investment of my time. Thank you again for organizing the wonderful event and helping us to feel safer and more empowered."

- Sandhya Kothandaramaraja

