#### ppa2ddive
#####It's all about components
######Building to events
4:30,pseudo event
```
(keyup)="execute(term,$event)"
```
######creating your own component
7:20
```
import {ViewEncapsulation} from '@angular/core';
@Component({
  encapsulation:ViewEncapsulation.Emulated,Native,None
```

######IO
@Input: pass data from p to c
@Output emit events from c to p
```
(child  component)
export class Component{
  @Outut() execute = new EventEmitter();
  executeSearch(term:string,event:MouseEvent){
    if(event.shiftKey){
    }else{
      this.execute.emit(term);
    }
  }
}
```
parent html
```
<input (execute)="runSearch($event)"
```
parent component
```
export class AppComponent{
runSearch(term:string){
  this.tracks=API.results
}
}
```

syntax sugar:
```
[(term)]="typed" //same as
[term]="typed" (termChange)="typed=$event"
```
######Content projection
5:00
```
ElementRef, nativeElement
```
```
au:any
constructor(private el:ElementRef){}
ngAfterViewInit(){
  this.au = this.el.nativeElement.querySelector('audio');
}
```
#####We Live in an async
######Keep your promises
```
track => this._track  //same as
track => { this._track = track; return track;}
