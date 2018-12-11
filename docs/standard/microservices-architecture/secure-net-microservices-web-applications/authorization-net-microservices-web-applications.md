---
title: Informacje o autoryzacji w aplikacji sieci web i mikrousługi platformy .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Informacje o autoryzacji w aplikacji sieci web i mikrousługi platformy .NET
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 53202d0f890df040480b9f54c54aaefdd025dffa
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149569"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Informacje o autoryzacji w aplikacji sieci web i mikrousługi platformy .NET

Po uwierzytelnieniu interfejsów API sieci Web programu ASP.NET Core konieczne Autoryzowanie dostępu. Ten proces umożliwia usłudze się interfejsów API, niektórzy użytkownicy uwierzytelnieni, ale nie dla wszystkich. [Autoryzacja](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) mogą być oparte na rolach użytkowników lub na podstawie zasad niestandardowych, która może obejmować kontrolę opartą na oświadczeniach lub inne algorytmy heurystyczne.

Ograniczanie dostępu do trasy ASP.NET Core MVC jest równie proste jak stosowanie atrybutu autoryzacji do metody akcji (lub klasy kontrolera, jeśli wszystkie kontrolera akcji wymaga autoryzacji), jak pokazano w poniższym przykładzie:

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

Domyślnie Dodawanie atrybutu autoryzacji bez parametrów zostaną ograniczyć dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji. Aby bardziej ograniczyć interfejsu API, które będą dostępne dla tylko przez określonych użytkowników, ten atrybut można rozszerzyć, aby określić wymagane role lub zasad, które muszą spełniać użytkownicy.

## <a name="implementing-role-based-authorization"></a>Implementowanie autoryzacji opartej na rolach

Tożsamość platformy ASP.NET Core ma wbudowane koncepcji ról. Oprócz użytkowników ASP.NET Core Identity przechowuje informacje dotyczące różnych ról, używanych przez aplikację i śledzi użytkowników, którzy są przypisane do ról. Te przypisania można zmienić programowo za pomocą typu RoleManager, (które aktualizuje ról w trwałego magazynu) i typu interfejs UserManager, (które można przypisać lub cofnąć to przypisanie użytkowników z ról).

Jeśli używasz uwierzytelniania za pomocą tokenów elementu nośnego JWT oprogramowanie pośredniczące uwierzytelniania elementu nośnego tokenu JWT programu ASP.NET Core spowoduje wypełnienie role użytkownika na podstawie oświadczeń roli w tokenie. Aby ograniczyć dostęp do kontrolera dla użytkowników w określonych ról lub Akcja kontrolera MVC, może zawierać parametru role w nagłówku autoryzacji, jak pokazano w poniższym przykładzie:

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

W tym przykładzie tylko użytkownicy w roli administratora lub Użytkownik_zaawansowany mogą dostęp do interfejsów API w kontrolerze Panelu sterowania (takie jak wykonanie akcji SetTime). Interfejs API zamykania dalsze jest ograniczony do zezwolenia na dostęp tylko do użytkowników w roli administratora.

Aby wymagać od użytkownika znajdowała się na wiele ról, użyj wiele atrybutów autoryzacji, jak pokazano w poniższym przykładzie:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

W tym przykładzie do wywołania API1, użytkownik musi:

-   Mieć administrator *lub* roli Użytkownik_zaawansowany *i*

-   Należeć do roli RemoteEmployee *i*

-   Spełnia niestandardowe Obsługa CustomPolicy autoryzacji.

## <a name="implementing-policy-based-authorization"></a>Implementowanie autoryzacji opartej na zasadach

Reguły autoryzacji niestandardowej można również będą zapisywane przy użyciu [zasady autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html). Ta sekcja zawiera omówienie. Więcej szczegółów znajduje się w dokumentacji online [Workshop autoryzacji programu ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Zasady autoryzacji dla niestandardowego są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. Metoda AddAuthorization. Ta metoda przyjmuje obiekt delegowany, który konfiguruje AuthorizationOptions argument.

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

Jak pokazano w przykładzie, mogą być skojarzone z różnymi typami wymagania. Po zasady są zarejestrowane, mogą być stosowane do akcji lub kontrolera przez przekazanie nazwy zasad jako argument zasad autoryzacji atrybutu (na przykład \[Authorize(Policy="EmployeesOnly")\]) może mieć zasady wiele wymagań, nie tylko jeden (jak pokazano w tych przykładach).

W poprzednim przykładzie pierwsze wywołanie AddPolicy jest po prostu alternatywny sposób autoryzowania przez rolę. Jeśli \[Authorize(Policy="AdministratorsOnly")\] jest stosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.

Drugie wywołanie AddPolicy pokazuje prosty sposób wymagają danego oświadczenia powinna istnieć dla użytkownika. Metoda RequireClaim przyjmuje również opcjonalnie oczekiwane wartości oświadczenia. Jeśli nie określono wartości, to wymaganie można spełnić tylko wtedy, gdy użytkownik ma zarówno poprawnego typu oświadczenia i jednej z określonymi wartościami. Jeśli używasz oprogramowania pośredniczącego uwierzytelniania elementu nośnego JWT wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.

Najbardziej interesujących zasady przedstawione w tym miejscu jest w Trzecia metoda AddPolicy, ponieważ używa ona wymagania autoryzacja niestandardowa. Za pomocą niestandardowych określonych wymagań, możesz mieć dużą kontrolę nad jak odbywa się autoryzacji. Aby to zrobić należy zaimplementować te typy:

-   Typ wymagania, która jest pochodną IAuthorizationRequirement, i zawiera pola, określając szczegóły zapotrzebowania. W tym przykładzie to wiek pole jest typu MinimumAgeRequirement próbki.

-   Program obsługi, który implementuje AuthorizationHandler&lt;T&gt;, gdzie T jest typem IAuthorizationRequirement, która może spełnić program obsługi. Program obsługi musi implementować metody HandleRequirementAsync, która sprawdza, czy określony kontekst, który zawiera informacje o użytkowniku spełnia wymagania.

Jeśli użytkownik spełnia wymagania, wywołanie do kontekstu. Powodzenie będzie wskazywać, że użytkownik jest autoryzowany. Jeśli istnieje wiele sposobów, że użytkownik może spełniają wymagania autoryzacji można utworzyć procedury obsługi wielu.

Oprócz rejestrowania wymagania dotyczące niestandardowych zasad z wywołaniami AddPolicy, należy również zarejestrować obsługi niestandardowe wymagania za pośrednictwem wstrzykiwanie zależności (usługi. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Przykład wymóg autoryzacji niestandardowego oraz obsługi kontroli wieku użytkownika (oparte na oświadczenia DateOfBirth) jest dostępna w programie ASP.NET Core [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Uwierzytelnianie programu ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autoryzacji platformy ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autoryzacja oparta na rolach**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Autoryzacja niestandardowa oparta na zasadach**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](developer-app-secrets-storage.md)