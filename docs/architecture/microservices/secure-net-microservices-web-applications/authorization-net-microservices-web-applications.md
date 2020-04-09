---
title: Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych
description: Zabezpieczenia w mikrousługach platformy .NET i aplikacjach sieci Web — zapoznaj się z omówieniem głównych opcji autoryzacji w aplikacjach ASP.NET Core — opartych na rolach i opartych na zasadach.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 27936a33ea2bb46cedb9d10ee47a2117e1843e14
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988209"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych

Po uwierzytelnieniu ASP.NET core interfejsów API sieci Web muszą autoryzować dostęp. Ten proces umożliwia usłudze udostępnianie interfejsów API niektórym uwierzytelnionym użytkownikom, ale nie wszystkim. [Autoryzacja](/aspnet/core/security/authorization/introduction) może być wykonywana na podstawie ról użytkowników lub na podstawie zasad niestandardowych, które mogą obejmować inspekcję oświadczeń lub innych heurystyki.

Ograniczenie dostępu do ASP.NET trasy Core MVC jest tak proste, jak zastosowanie atrybutu Authorize do metody akcji (lub do klasy kontrolera, jeśli wszystkie akcje kontrolera wymagają autoryzacji), jak pokazano na poniższym przykładzie:

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

Domyślnie dodanie atrybutu Authorize bez parametrów ograniczy dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji. Aby dodatkowo ograniczyć interfejs API, który ma być dostępny tylko dla określonych użytkowników, atrybut można rozwinąć, aby określić wymagane role lub zasady, które użytkownicy muszą spełnić.

## <a name="implement-role-based-authorization"></a>Wdrażanie autoryzacji opartej na rolach

ASP.NET Podstawowa tożsamość ma wbudowaną koncepcję ról. Oprócz użytkowników ASP.NET Tożsamość podstawowa przechowuje informacje o różnych rolach używanych przez aplikację i śledzi, którzy użytkownicy są przypisani do ról. Te przypisania można zmienić programowo z typem, `RoleManager` który aktualizuje role w utrwalone magazynu i `UserManager` typu, który może przyznać lub odwołać role od użytkowników.

Jeśli uwierzytelniasz się za pomocą tokenów nośnych JWT, ASP.NET core JWT oprogramowanie pośredniczące uwierzytelniania na okaziciela wypełni role użytkownika na podstawie oświadczeń roli znalezionych w tokenie. Aby ograniczyć dostęp do akcji lub kontrolera MVC do użytkowników w określonych rolach, można dołączyć parametr Roles w adnotacji Autoryzacyjnej (atrybut), jak pokazano w następującym fragmencie kodu:

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

W tym przykładzie tylko użytkownicy w rolach administratora lub PowerUser mogą uzyskiwać dostęp do interfejsów API w kontrolerze ControlPanel (na przykład wykonywania akcji SetTime). Interfejs API ShutDown jest dodatkowo ograniczony, aby zezwolić na dostęp tylko do użytkowników w roli administratora.

Aby wymagać, aby użytkownik był w wielu rolach, należy użyć wielu atrybutów Autoryzuj, jak pokazano w poniższym przykładzie:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

W tym przykładzie, aby wywołać API1, użytkownik musi:

- Być w roli administratora *lub* PowerUser, *i*

- Wcielić się w rolę RemoteEmployee *i*

- Spełnij niestandardowy program obsługi autoryzacji CustomPolicy.

## <a name="implement-policy-based-authorization"></a>Wdrażanie autoryzacji opartej na zasadach

Reguły autoryzacji niestandardowej można również zapisywać przy użyciu [zasad autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html). Ta sekcja zawiera omówienie. Aby uzyskać więcej informacji, zobacz [warsztaty autoryzacji ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Zasady autoryzacji niestandardowej są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. AddAuthorization metody. Ta metoda przyjmuje pełnomocnika, który konfiguruje argument AuthorizationOptions.

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

Jak pokazano w przykładzie, zasady mogą być skojarzone z różnymi typami wymagań. Po zarejestrowaniu zasad można je zastosować do akcji lub kontrolera, przekazując nazwę zasad jako argument Zasad atrybutu Authorize (na przykład `[Authorize(Policy="EmployeesOnly")]`) Zasady mogą mieć wiele wymagań, a nie tylko jeden (jak pokazano w tych przykładach).

W poprzednim przykładzie pierwsze wywołanie AddPolicy jest tylko alternatywnym sposobem autoryzowania przez rolę. Jeśli `[Authorize(Policy="AdministratorsOnly")]` jest stosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.

Drugie <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> wywołanie pokazuje łatwy sposób wymagać, że określone oświadczenie powinno być obecne dla użytkownika. Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> również opcjonalnie przyjmuje oczekiwane wartości dla oświadczenia. Jeśli wartości są określone, wymaganie jest spełnione tylko wtedy, gdy użytkownik ma zarówno oświadczenie prawidłowego typu i jedną z określonych wartości. Jeśli używasz oprogramowania pośredniczącego uwierzytelniania na okaziciela JWT, wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.

Najciekawsze zasady pokazane tutaj jest `AddPolicy` w trzeciej metody, ponieważ używa wymagania autoryzacji niestandardowej. Za pomocą wymagań autoryzacji niestandardowej, można mieć dużą kontrolę nad jak autoryzacja jest wykonywana. Aby to zadziałało, należy zaimplementować następujące typy:

- Typ wymagania, który pochodzi <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> z i który zawiera pola określające szczegóły wymagania. W tym przykładzie jest to pole `MinimumAgeRequirement` wiekowe dla typu próbki.

- Program obsługi, <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>który implementuje , <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> gdzie T jest typem, który program obsługi może spełnić. Program obsługi musi <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> implementować metodę, która sprawdza, czy określony kontekst, który zawiera informacje o użytkowniku spełnia wymagania.

Jeśli użytkownik spełnia wymagania, wywołanie `context.Succeed` wskazuje, że użytkownik jest autoryzowany. Jeśli istnieje wiele sposobów, że użytkownik może spełnić wymagania autoryzacji, można utworzyć wiele programów obsługi.

Oprócz rejestrowania niestandardowych wymagań `AddPolicy` dotyczących zasad za pomocą wywołań, należy również`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`zarejestrować niestandardowe programy obsługi wymagań za pośrednictwem iniekcji zależności ( ).

Przykład wymagania autoryzacji niestandardowej i programu obsługi do sprawdzania wieku `DateOfBirth` użytkownika (na podstawie oświadczenia) jest dostępny w [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Core .

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Uwierzytelnianie ASP.NET rdzeniowe** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Autoryzacja ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Autoryzacja oparta na rolach** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Autoryzacja oparta na zasadach niestandardowych** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](developer-app-secrets-storage.md)
