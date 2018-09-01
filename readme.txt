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
are instructions in the DOM

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
*ngIf="serverCreated; else noServer"
*ngFor

non-structural directive
----------------------
[(ngModel)]="serverName"
ng-template
ngStyle
ngClass

























