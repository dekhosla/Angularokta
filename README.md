import { Component } from '@angular/core';
import { OktaAuthStateService, OktaAuthService } from '@okta/okta-angular';

@Component({
  selector: 'app-root',
  template: `
    <h1>Welcome to Angular with Okta</h1>
    <button *ngIf="!(isAuthenticated | async)" (click)="login()">Login</button>
    <button *ngIf="isAuthenticated | async" (click)="logout()">Logout</button>
  `
})
export class AppComponent {
  isAuthenticated = this.oktaAuthStateService.authState$;

  constructor(private oktaAuth: OktaAuthService, private oktaAuthStateService: OktaAuthStateService) {}

  async login() {
    await this.oktaAuth.signInWithRedirect();
  }

  async logout() {
    await this.oktaAuth.signOut();
  }
}
