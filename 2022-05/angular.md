## angular监听元素外点击事件

```javascript
constructor(private elementRef: ElementRef) { }
  @HostListener('click')
  clickInside() {
  }

  @HostListener('document:click', ['$event.target'])
  clickOut(targetElement: ElementRef) {
    const clickedInside = this.elementRef.nativeElement.contains(targetElement)
    console.log('clickedInside :>>', clickedInside);
  }
```