# Angularokta
okta
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { OktaAuthModule, OktaAuthGuard, OKTA_CONFIG } from '@okta/okta-angular';
import { OktaAuth } from '@okta/okta-auth-js';

const oktaConfig = {
  issuer: 'https://your-okta-domain/oauth2/default',
  clientId: 'your-client-id',
  redirectUri: window.location.origin + '/login/callback'
};

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    OktaAuthModule
  ],
  providers: [
    { provide: OKTA_CONFIG, useValue: new OktaAuth(oktaConfig) }
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
