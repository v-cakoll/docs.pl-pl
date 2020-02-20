---
title: Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — zapoznaj się z głównymi opcjami autoryzacji w ASP.NET Core aplikacje — oparta na rolach i oparta na zasadach.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f6b69faceac9a9b4819212cc04f89080f3ddad56
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501766"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych

Po uwierzytelnieniu ASP.NET Core internetowe interfejsy API muszą autoryzować dostęp. Ten proces umożliwia usłudze udostępnianie interfejsów API niektórym uwierzytelnionym użytkownikom, ale nie wszystkim. [Autoryzację](/aspnet/core/security/authorization/introduction) można wykonać w oparciu o role użytkowników lub na podstawie zasad niestandardowych, które mogą obejmować sprawdzanie oświadczeń lub innych algorytmów heurystycznych.

Ograniczanie dostępu do trasy ASP.NET Core MVC jest tak proste jak stosowanie atrybutu Autoryzuj do metody akcji (lub do klasy kontrolera, jeśli wszystkie akcje kontrolera wymagają autoryzacji), jak pokazano w poniższym przykładzie:

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

Domyślnie dodanie atrybutu Autoryzuj bez parametrów spowoduje ograniczenie dostępu do uwierzytelnionych użytkowników dla tego kontrolera lub akcji. Aby dodatkowo ograniczyć interfejs API do dostępności tylko dla określonych użytkowników, atrybut można rozszerzyć, aby określić wymagane role lub zasady, które użytkownicy muszą spełnić.

## <a name="implement-role-based-authorization"></a>Implementowanie autoryzacji opartej na rolach

Tożsamość ASP.NET Core ma wbudowaną koncepcję ról. Oprócz użytkowników, ASP.NET Core tożsamość przechowuje informacje o różnych rolach używanych przez aplikację i śledzi użytkowników, którym przypisano role. Te przypisania można programowo zmienić za pomocą typu `RoleManager`, który aktualizuje role w magazynie trwałym, a także typ `UserManager`, który może udzielić lub odwołać role użytkowników.

W przypadku uwierzytelniania za pomocą tokenów okaziciela JWT, oprogramowanie pośredniczące uwierzytelniania okaziciela JWT ASP.NET Core wypełniać role użytkownika na podstawie oświadczeń ról znalezionych w tokenie. Aby ograniczyć dostęp do akcji lub kontrolera MVC do użytkowników w określonych rolach, można dołączyć parametr Role w adnotacji Autoryzuj (Attribute), jak pokazano w poniższym fragmencie kodu:

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

W tym przykładzie tylko użytkownicy z rolą Administrator lub PowerUser mogą uzyskać dostęp do interfejsów API w kontrolerze ControlPanel (na przykład wykonując akcję SetTime). Interfejs API zamykania jest dodatkowo ograniczony, aby zezwalać na dostęp tylko użytkownikom w roli administratora.

Aby wymagać, aby użytkownik znajdował się w wielu rolach, należy użyć wielu atrybutów autoryzacji, jak pokazano w następującym przykładzie:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

W tym przykładzie do wywołania API1 użytkownik musi:

- Należy do roli administrator *lub* PowerUser, *a* także

- Należy do roli RemoteEmployee *i*

- Zaspokoj niestandardową procedurę obsługi autoryzacji CustomPolicy.

## <a name="implement-policy-based-authorization"></a>Implementowanie autoryzacji opartej na zasadach

Niestandardowe reguły autoryzacji można także napisać przy użyciu [zasad autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html). Ta sekcja zawiera omówienie. Aby uzyskać więcej informacji, zobacz [warsztat ASP.NET Authorization](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Niestandardowe zasady autoryzacji są rejestrowane w metodzie Startup. ConfigureServices przy użyciu usługi. Metoda addauthorization. Ta metoda pobiera delegata, który konfiguruje argument AuthorizationOptions.

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

Jak pokazano w przykładzie, zasady można kojarzyć z różnymi typami wymagań. Po zarejestrowaniu zasad można je stosować do akcji lub kontrolera przez przekazanie nazwy zasad jako argumentu zasad autoryzacji atrybutu Autoryzuj (na przykład `[Authorize(Policy="EmployeesOnly")]`) zasady mogą mieć wiele wymagań, a nie tylko jeden (jak pokazano w tych przykładach).

W poprzednim przykładzie pierwsze wywołanie addpolicy jest tylko alternatywnym sposobem autoryzacji przez rolę. Jeśli `[Authorize(Policy="AdministratorsOnly")]` zostanie zastosowana do interfejsu API, tylko użytkownicy z rolą Administrator będą mogli uzyskać do niego dostęp.

Drugie wywołanie <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> ilustruje łatwy sposób, aby wymagać określonego żądania dla użytkownika. Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> również opcjonalnie przyjmuje oczekiwane wartości dla tego żądania. Jeśli wartości są określone, wymaganie jest spełnione tylko wtedy, gdy użytkownik ma zarówno żądanie poprawnego typu, jak i jedną z określonych wartości. Jeśli używasz oprogramowania pośredniczącego uwierzytelniania okaziciela JWT, wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.

Najbardziej interesujące zasady pokazane w tym miejscu znajdują się w trzeciej metodzie `AddPolicy`, ponieważ używa ona niestandardowego wymagania dotyczącego autoryzacji. Za pomocą niestandardowych wymagań dotyczących autoryzacji możesz mieć doskonałą kontrolę nad sposobem autoryzacji. Aby to działało, należy zaimplementować następujące typy:

- Typ wymagań, który pochodzi od <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> i zawiera pola określające szczegóły wymagania. W tym przykładzie jest to pole wiek dla przykładowego typu `MinimumAgeRequirement`.

- Procedura obsługi implementująca <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, gdzie T jest typem <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement>, który może spełniać program obsługi. Program obsługi musi zaimplementować metodę <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A>, która sprawdza, czy określony kontekst zawierający informacje o użytkowniku spełnia wymagania.

Jeśli użytkownik spełnia wymagania, wywołanie do `context.Succeed` będzie wskazywać, że użytkownik jest autoryzowany. Jeśli istnieje wiele sposobów, że użytkownik może spełnić wymagania dotyczące autoryzacji, można utworzyć wiele programów obsługi.

Oprócz rejestrowania wymagań zasad niestandardowych przy użyciu wywołań `AddPolicy` należy również zarejestrować niestandardowe programy obsługi wymagań za pomocą iniekcji zależności (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).

Przykładem niestandardowego wymagania dotyczącego autoryzacji i obsługi sprawdzania wieku użytkownika (na podstawie `DateOfBirth`ego) jest dostępny w [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Coreowej.

## <a name="additional-resources"></a>Dodatkowe zasoby

-  \ **uwierzytelniania ASP.NET Core**
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

-  \ **autoryzacji ASP.NET Core**
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

-  \ **autoryzacji opartej na rolach**
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

-  \ **autoryzacji opartej na zasadach niestandardowych**
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](developer-app-secrets-storage.md)
