install CLI
---------------
npm install -g @angular/cli@latest

create new project
------------------------
ng new angular6_app1
cd angular6_app1

start server
---------------
ng serve

use visual studio code for dev
-----------------------------------

Typescript is compiled to JS

Install Bootstrap
-----------------------
npm install --save bootstrap@3
 
Add Bootstrap entry in styles array in angular.json
------------------------------------------------------
C:\osmand\tech\angular\ws\angular6_app2\angular.json

creating a component using cli
---------------------------------------
ng generate component <component-name>

single page is at
----------------------
C:\osmand\tech\angular\ws\angular6_app2\src\index.html

what else cli does?
--------------------
it injects imports in index.html. 
check the source of application page

how does it start
-----------------------

C:\osmand\tech\angular\ws\angular6_app2\src\index.html
C:\osmand\tech\angular\ws\angular6_app2\src\main.ts
C:\osmand\tech\angular\ws\angular6_app2\src\app\app.module.ts
C:\osmand\tech\angular\ws\angular6_app2\src\app\app.component.ts

pay attention to bootstrap: [AppComponent] in app.module.ts

root component
---------------------
C:\osmand\tech\angular\ws\angular6_app2\src\app\app.component.ts

how to use a new component
----------------------------
we declare it in C:\osmand\tech\angular\ws\angular6_app2\src\app\app.module.ts
app.module.ts bundles the functionality of our app
we register new components in declarations[] in app.module.ts

styling
-----------
external
inline

selectors
-----------------
can be defined as element like-  selector: 'app-servers',
can be defined as attrubute like- selector: '[app-server]'. in this case selector can be defined in <div app-server> tag.
can be defined as class like- selector: '.app-server'. in this case selector can be defined in <div class="app-server"> tag.

output data
-----------------
string interpolation {{ name }}
property binding [name] = "Osmand"
event binding (event) = "expression" 
two way data binding [(ngModel)] = "data"

event binding (reserved variable name)
------------------------------------------
$event

other reserved keyword
-------------------------
index

directive
-------------
are instructions in the DOM; attribute and structural directive

@Directive({
	selector: '[appTurnGreen]'
})

export class TurnGreenDirective {
	// ...
}


components
----------------
components are also directives, they are directives with a template


common directives
--------------------

structural directive (with a star) changing the DOM 
-------------------------------------------------------
*ngIf="serverCreated; else noServer" -> this is used to add or remove element in DOM
*ngFor
We can't have more than one structural directive on one element

attribute directive (affect the element they are added to)
--------------------------------------------------------------
[(ngModel)]="serverName"
ng-template
ngStyle
ngClass
ng-content

Angular tools
------------------
Augury chrome plugin
Sources tab on developers tool

custom property binding input and output events
-----------------------------------------------------
// without an alias
@Input() element: { type: string, name: string, content: string};
@Input('srvElement') element: { type: string, name: string, content: string};

css behavior
------------------
angular restricts css to the component in which it is defined. this is opposite to default behavior of css

view encaplusation in angular
----------------------------------
to disable view encapsulation add ViewEncapsulation.None in @Component 
By disabling ViewEncapsulation in a Component, styles declared in that component's css are applied to other components
We typically don't use this functionality

two-way binding vs local reference
---------------------------------------
instead of using two-way binding [(ngModel)] = "propName" we can use local reference #propName when two-way binding is not required
local reference refers to the entire element in which it is defined and is accessible in the whole template.


two-way binding vs local reference defined as ElementRef
----------------------------------------------------------
@ViewChild('serverLocationInput') serverLocationInput: ElementRef;
serverLocation: this.serverLocationInput.nativeElement.value

Lifecycle hooks
-----------------------
ngOnChanges -> 
may be called multiple times
is invoked at start when a new component is created
is invoked when any bound input property changes i.e. properties decorated with  @Input e.g. @Input('srvElement')

ngOnInit ->
is invoked when component is initialized
will run after the constructor

ngDoCheck ->
is invoked when change detection runs
change detection is a mechanism which detects when something changes in the component of a template
Or whenever something changes inside of the component
triggering events invoke ngDoCheck
doesn't cost performance

ngAfterContentInit 
ngAfterContentChecked
ngAfterViewInit
ngAfterViewChecked
ngOnDestroy


More about Directives
-----------------------
it's better to use renderer than to modify DOM directly
we can't add view related lifecycle hook functions to a directive because it doesn't have a view

@HostListener

creating a directive
=====================

ng generate directive <my-directive>
ng g d <my-directive>

How to manage events like mouse enter or exit
==============================================

use decorator @HostListener or @HostBinding

creating our own structural directives
=======================================


switch
-------

[ngSwitch] and *ngSwitchCase, *ngSwitchDefault


Services
-----------

We shouldn't create service instances manually
don't do this: 
    const service = new LoggingService();
    service.logStatusChange(accountStatus);
    
we should use providers (in @Component decorators) and constructor injectors

Angular dependency injector is a hierarchical injector
If we inject a service at the topmost level i.e. at AppModule then the same service instance is available to all the child components. If we inject a service in AppComponent instead, then the same service instance is available to all its child components, but the AppModule (the parent component) will not get the same service instance. 

When we need to inject a service to another service then we should provide the service in AppModule 

Services can be injected to other services by using @Injectable

how do we make a copy of an array in Angular?
----------------------------------------------
arrayname.slice()

routing
-------
How and where do we declare routes? In app.module.ts; it's of type Routes
We need to make an entry under NgModule imports
RouteModule.forRoot(appRoutes) // here appRoutes is an array of Routes we declared above

special router selector
-----------------------
<router-outlet></router-outlet>

while working with routers, we shouldn't use href in anchor tag as it reloads the page. instead we should use a special angular directive routerLink

we can declare routerLink by following three ways:
---------------------------------------------------

routerLink="/mypath"
[routerLink]="'/mypath'"
[routerLink]="['/mypath', '/myadditionalpath']"

how to show an active tab
---------------------------
in simple css we use class="active"

in angular routing there is a special directive routerLinkActive
also check routerLinkActiveOptions this is mainly used for home tab





    
































