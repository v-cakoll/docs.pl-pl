---
title: Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — uzyskaj przegląd głównych opcji autoryzacji w ASP.NET podstawowych aplikacji — opartych na rolach i opartych na zasadach.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f6b69faceac9a9b4819212cc04f89080f3ddad56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501766"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych

Po uwierzytelnieniu ASP.NET podstawowe interfejsy API sieci Web muszą autoryzować dostęp. Ten proces umożliwia usłudze udostępnianie interfejsów API niektórym uwierzytelnionym użytkownikom, ale nie wszystkim. [Autoryzacja](/aspnet/core/security/authorization/introduction) może być wykonana na podstawie ról użytkowników lub na podstawie zasad niestandardowych, które mogą obejmować sprawdzanie oświadczeń lub innych heurystyki.

Ograniczenie dostępu do ASP.NET core MVC jest tak proste, jak zastosowanie authorize atrybut do metody akcji (lub do klasy kontrolera, jeśli wszystkie akcje kontrolera wymagają autoryzacji), jak pokazano w poniższym przykładzie:

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

Domyślnie dodanie atrybutu Authorize bez parametrów ograniczy dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji. Aby jeszcze bardziej ograniczyć interfejs API, który ma być dostępny tylko dla określonych użytkowników, atrybut można rozszerzyć, aby określić wymagane role lub zasady, które użytkownicy muszą spełniać.

## <a name="implement-role-based-authorization"></a>Implementowanie autoryzacji opartej na rolach

ASP.NET Core Identity ma wbudowaną koncepcję ról. Oprócz użytkowników ASP.NET tożsamość podstawowa przechowuje informacje o różnych rolach używanych przez aplikację i śledzi, którzy użytkownicy są przypisani do ról. Te przypisania można zmieniać programowo z typem, `RoleManager` który aktualizuje role w magazynie utrwalonym, oraz `UserManager` typu, który może przyznać lub odwołać role od użytkowników.

Jeśli uwierzytelniasz się przy użyciu tokenów elementu nośnego JWT, ASP.NET core JWT zagłębienia uwierzytelniania na okaziciela wypełni role użytkownika na podstawie oświadczeń ról znalezionych w tokenie. Aby ograniczyć dostęp do akcji MVC lub kontrolera dla użytkowników w określonych rolach, można dołączyć parametr Roles w adnotacji autoryzuj (atrybut), jak pokazano w następującym fragmencie kodu:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

W tym przykładzie tylko użytkownicy w roli Administrator lub PowerUser mogą uzyskiwać dostęp do interfejsów API na kontrolerze ControlPanel (na przykład wykonując akcję SetTime). Interfejs API Zamknięcia jest ponadto ograniczony, aby zezwolić na dostęp tylko użytkownikom w roli administratora.

Aby wymagać od użytkownika pełnienia wielu ról, należy użyć wielu atrybutów Authorize, jak pokazano w poniższym przykładzie:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

W tym przykładzie, aby wywołać interfejs API1, użytkownik musi:

- Być w roli administratora *lub* użytkownika mocy, *i*

- Być w roli RemoteEmployee *i*

- Spełnianie niestandardowego programu obsługi autoryzacji CustomPolicy.

## <a name="implement-policy-based-authorization"></a>Wdrażanie autoryzacji opartej na zasadach

Niestandardowe reguły autoryzacji można również zapisywać przy użyciu [zasad autoryzacji.](https://docs.asp.net/en/latest/security/authorization/policies.html) Ta sekcja zawiera omówienie. Aby uzyskać więcej informacji, zobacz [ASP.NET Warsztaty autoryzacji](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Niestandardowe zasady autoryzacji są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. AddAuthorization metody. Ta metoda przyjmuje pełnomocnika, który konfiguruje AuthorizationOptions argument.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));

    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));

    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

Jak pokazano w przykładzie, zasady mogą być skojarzone z różnymi typami wymagań. Po zarejestrowaniu zasad można je zastosować do akcji lub kontrolera, przekazując nazwę zasady jako argument Zasad `[Authorize(Policy="EmployeesOnly")]`atrybutu Authorize (na przykład) Zasady mogą mieć wiele wymagań, a nie tylko jedno (jak pokazano w tych przykładach).

W poprzednim przykładzie pierwsze wywołanie AddPolicy jest tylko alternatywny sposób autoryzowania przez rolę. Jeśli `[Authorize(Policy="AdministratorsOnly")]` zostanie zastosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.

Drugie <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> wywołanie pokazuje łatwy sposób wymagać, że określone oświadczenie powinno być obecne dla użytkownika. Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> również opcjonalnie przyjmuje oczekiwane wartości oświadczenia. Jeśli wartości są określone, wymaganie jest spełnione tylko wtedy, gdy użytkownik ma zarówno oświadczenie poprawnego typu, jak i jedną z określonych wartości. Jeśli używasz pośredniczowceuwierzytelniające uwierzytelnianie jwt, wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.

Najciekawsze zasady pokazane `AddPolicy` w tym miejscu jest w trzeciej metody, ponieważ używa niestandardowego wymogu autoryzacji. Korzystając z niestandardowych wymagań autoryzacji, można mieć dużą kontrolę nad jak autoryzacja jest wykonywana. Aby to zadziałało, należy zaimplementować te typy:

- A Wymagania typ, <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> który pochodzi od i który zawiera pola określające szczegóły wymagania. W przykładzie jest to pole wieku `MinimumAgeRequirement` dla typu próbki.

- Program obsługi, <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>który implementuje , <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> gdzie T jest typem, który program obsługi może zaspokoić. Program obsługi musi <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> implementować metodę, która sprawdza, czy określony kontekst, który zawiera informacje o użytkowniku spełnia wymagania.

Jeśli użytkownik spełnia wymagania, wywołanie `context.Succeed` wskazuje, że użytkownik jest autoryzowany. Jeśli istnieje wiele sposobów, że użytkownik może spełniać wymagania autoryzacji, można utworzyć wiele programów obsługi.

Oprócz rejestrowania wymagań zasad `AddPolicy` niestandardowych za pomocą wywołań, należy również zarejestrować`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`niestandardowe programy obsługi wymagań za pośrednictwem iniekcji zależności ( ).

Przykład niestandardowego wymagania autoryzacji i obsługi sprawdzania wieku użytkownika `DateOfBirth` (na podstawie oświadczenia) jest dostępny w [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Core.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **ASP.NET uwierzytelnianie podstawowe** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **autoryzacja rdzenia ASP.NET** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Autoryzacja oparta na rolach** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Autoryzacja oparta na zasadach niestandardowych** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](developer-app-secrets-storage.md)
