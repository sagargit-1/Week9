Angular App Flow and Creating Components :
===========================================

How the files are called and in which sequence of files the app gets executed when
developing the app.

1. angular.json File

	-	angular.json is the file which has various properties and configuration 
	    of Angular project.

	-	It has a reference to the main.ts file which tells the builder to start the app 
	    from there.
		
2. main.ts

	-	This file acts as the entry point of the application. 
	
	-	main.ts helps in creating the browser environment for the application to run.
	
	-	This is done by - import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
	
	-	After this, main.ts file calls the function bootstrapModule(AppModule) which
		tells the builder to bootstrap the app.
			platformBrowserDynamic().bootstrapModule(AppModule)s
			
3. app.module.ts

	-	From the main.ts file, it is very clear that we are bootstrapping the app with 
	   AppModule.
	   
	-	This AppModule is defined in  app.module.ts file which is found in

		<project_directory>/src/app/app.module.ts
		
	-	This is the module, created with the @NgModule decorator, which has 
	    declarations of all the components that are creating within the app module
		so that angular is aware of them.
		
4. app.component.ts
	
	-	From the app.module.ts file above, we can clearly see that the module asks to 
	    bootstrap the app component. 
		
	-	This app component is in app.component.ts file. This is the file which interacts 
	    with the html of the webpage and serves it with the data.
	
	-	By this time, compiler has all the details about the components of the app and 
	    now they are ready to be used.
		
5. index.html

	-	Now, since angular is well aware of the modules, components, styles, scripts 
	   etc., which are required to display the page, it’s show time!

	-	Here, the index.html file is called.
	
	-	It is found in the src folder of the app. 
	
	-	Compiler dynamically adds all the javascript files at the end of this file. 
	
	-	Since all the components are now known, the html file calls the root 
	    component that is 'app-root'. 
		
	-	The root component is defined in app.components.ts which targets 
	    app.component.html.
	
	-	When this angular app is served and opened in the browser, the scripts injection 
	    is done by the compiler.
		
6. app.component.html

	-	This is the file which contains all the html elements and their binding which 
		are to be displayed when the app loads. 
		
	-	Contents of this file are the first things to be displayed.
	
===================================================================	
	
	
	
	
	----------------------------- Adding Component  ----------------------------------
	
	Creating an Angular Component requires us to follow these steps
	
	
	
	1. Create the Component file.
	
		Select the src/app folder, right-click, and click on the new file. 
		Enter the name of the file as hello-world.component.ts
	
	2. Import the required external Classes/Functions.
	
		import { Component } from '@angular/core';
		
	3. Create the Component class and export it.
	
		export class HelloWorldComponent {
			message = 'Hello World';
		}
 
	4. Add @Component decorator
	
		@Component({
		})
		export class HelloWorldComponent {
			message = 'Hello World';
		}
	5. Add metadata to @Component decorator
	
		@Component({
			selector: 'app-hello-world',
			templateUrl: './hello-world.component.html',
			styleUrls: ['./hello-world.component.css']
		})
	6. Create the Template
	
		Select the src/app folder, right-click, and click on the new file. 
		Enter the name of the file as hello-world.component.html.
		Add following code
		<h1>
			{{message}}!
	</h1>
 
	7. Create the CSS Styles
		
		Select the src/app folder, right-click, and click on the new file. 
		Enter the name of the file as hello-world.component.css.
		
		Add the following styles :
		
		h1{
			font-family: Arial, Helvetica, sans-serif;
		}
		
		
	
	8. Register the Component in Angular Module
	
		import { HelloWorldComponent } from './hello-world.component';
		
	9.  Add it to the declaration array.
	
		 declarations: [
			AppComponent, HelloWorldComponent
		],
		
	10. Final app.module.ts is as follows :
	
	
			import { NgModule } from '@angular/core';
			import { BrowserModule } from '@angular/platform-browser';
			 
			import { AppRoutingModule } from './app-routing.module';
			import { AppComponent } from './app.component';
			import { HelloWorldComponent } from './hello-world.component';
			 
			@NgModule({
			  declarations: [
				AppComponent, HelloWorldComponent
			  ],
			  imports: [
				BrowserModule,
				AppRoutingModule
			  ],
			  providers: [],
			  bootstrap: [AppComponent]
			})
			export class AppModule { }

		Open the app.module.ts and locate the following code.

		bootstrap: [AppComponent]
 
		Update it with the following code.
		
		bootstrap: [HelloWorldComponent]


	11.  Now open the src/app/index.html and locate the following line.

		Replace the <app-root> with  <app-hello-world>
		
		Before replacing : 
		
		<body>
		<app-root></app-root>
		</body>
		
		After replacing :
 
		<body>
		 <app-hello-world></app-hello-world> 
		</body>

	12. Run the application
