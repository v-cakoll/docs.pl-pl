---
title: "Temat autoryzacji w aplikacji sieci web i mikrousług .NET"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Temat autoryzacji w aplikacji sieci web i mikrousług .NET"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6cd7be9bc8216aecf85f99a76e859b411a8735b0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Temat autoryzacji w aplikacji sieci web i mikrousług .NET

Po uwierzytelnieniu interfejsów API platformy ASP.NET Core sieci Web wymagane do autoryzowania dostępu. Ten proces umożliwia usłudze upewnij interfejsów API, niektóre uwierzytelnionych użytkowników, ale nie do wszystkich. [Autoryzacji](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) mogą być wykonywane w oparciu o role użytkowników lub na podstawie niestandardowych zasad, która może obejmować sprawdzania oświadczeń lub inne algorytmy heurystyczne.

Ograniczanie dostępu do platformy ASP.NET Core MVC trasy jest tak proste, jak zastosowanie atrybutu autoryzacji do metody akcji (lub do klasy kontrolera, jeśli wszystkie kontrolera akcji wymaga autoryzacji), jak pokazano w poniższym przykładzie:

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

Domyślnie dodając atrybut autoryzacji bez parametrów zostaną ograniczyć dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji. Aby bardziej ograniczyć interfejsu API, które mają być dostępne tylko dla określonych użytkowników, atrybut można rozszerzyć, aby określić wymagane role lub zasady, które muszą spełniać użytkownicy.

## <a name="implementing-role-based-authorization"></a>Implementowanie autoryzacji opartej na rolach

Tożsamość platformy ASP.NET Core ma wbudowane koncepcji ról. Oprócz użytkowników ASP.NET Core Identity są przechowywane informacje o różnych ról używany przez aplikację i śledzi użytkowników, którzy są przypisane do ról. Te przydziały można zmienić programowo z RoleManager typu (aktualizacje ról w utrwalonego magazynu) i typ interfejs UserManager, (które można przypisać lub Cofnij przypisanie ról użytkowników).

Jeśli uwierzytelnianych tokenów elementu nośnego JWT, oprogramowanie pośredniczące uwierzytelniania elementu nośnego ASP.NET Core JWT są powielane ról użytkownika na podstawie oświadczeń roli znaleziono ją w tokenie. Aby ograniczyć dostęp do MVC akcji lub kontrolera dla użytkowników w określonych ról, może zawierać parametru ról w nagłówku autoryzacji, jak pokazano w poniższym przykładzie:

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

W tym przykładzie tylko użytkownicy o rolach administratora lub Użytkownik_zaawansowany można uzyskać dostępu do interfejsów API w Panelu sterowania kontrolera (np. wykonywanie akcji SetTime). Interfejs API zamykania dalsze jest ograniczona do zezwolić na dostęp tylko do użytkowników w roli administratora.

Wymagać, aby być użytkownik był w wiele ról, należy użyć wiele atrybutów autoryzacji, jak pokazano w poniższym przykładzie:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

W tym przykładzie aby wywołać API1, użytkownik musi:

-   Można w administrator *lub* roli Użytkownik_zaawansowany *i*

-   W roli RemoteEmployee *i*

-   Spełnia niestandardowego programu obsługi dla CustomPolicy autoryzacji.

## <a name="implementing-policy-based-authorization"></a>Wdrażanie na podstawie zasad autoryzacji

Reguły autoryzacji niestandardowej można także napisane przy użyciu [zasady autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html). W tej sekcji, firma Microsoft udostępnia przegląd. Więcej szczegółów znajduje się w dokumentacji online [Workshop autoryzacji programu ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Zasady autoryzacji niestandardowe są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. Metoda AddAuthorization. Ta metoda przyjmuje delegata, który konfiguruje argumentu AuthorizationOptions.

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

Jak pokazano w przykładzie, mogą być skojarzone z różnymi typami wymagania. Gdy zasady są zarejestrowane, mogą być stosowane do akcji lub kontrolera przez przekazanie jako argument zasad autoryzacji atrybutu nazwy zasad (na przykład \[Authorize(Policy="EmployeesOnly")\]) może mieć zasady wiele wymagań, nie tylko jedną (jak pokazano w tym przykładzie).

W poprzednim przykładzie pierwsze wywołanie AddPolicy to po prostu alternatywny sposób autoryzowania przez rolę. Jeśli \[Authorize(Policy="AdministratorsOnly")\] jest stosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.

Drugie wywołanie AddPolicy przedstawiono prosty sposób wymagają określonej oświadczenia powinna występować dla użytkownika. Metoda RequireClaim również opcjonalnie przyjmuje oczekiwanych wartości oświadczenia. Jeśli wartości są określone, to wymaganie można spełnić tylko wtedy, gdy użytkownik ma zarówno poprawnego typu oświadczenia i jednej z określonymi wartościami. Jeśli używasz oprogramowania pośredniczącego uwierzytelniania elementu nośnego JWT wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.

Najbardziej interesujących zasady pokazane są w metodzie AddPolicy trzeci, ponieważ używa wymaganie autoryzacji niestandardowej. Za pomocą wymagania autoryzacji niestandardowej, może mieć wiele kontrolę nad realizację autoryzacji. Aby to zrobić należy zaimplementować te typy:

-   Typ wymagania, która jest pochodną IAuthorizationRequirement i zawiera pola, określając szczegóły zapotrzebowania. W tym przykładzie jest pola wiek dla typu MinimumAgeRequirement próbki.

-   Program obsługi, który implementuje AuthorizationHandler&lt;T&gt;, gdzie T jest typ IAuthorizationRequirement, która spełnia program obsługi. Program obsługi musi implementować metodę HandleRequirementAsync, która sprawdza, czy określony kontekst, który zawiera informacje dotyczące użytkownika spełnia wymagania.

Jeśli użytkownika spełnia wymagania, wywołania do kontekstu. Pomyślnie będzie wskazywać, że użytkownik jest autoryzowany. Jeśli istnieje wiele sposobów, że użytkownik może spełniają wymagania autoryzacji można utworzyć procedury obsługi wielu.

Oprócz rejestrowania wymagania zasad niestandardowych za pomocą wywołania AddPolicy, należy również zarejestrować wymagania niestandardowe programy obsługi, za pomocą iniekcji zależności (usługi. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Przykład wymaganie autoryzacji niestandardowej i obsługi sprawdzania wiek użytkownika (na podstawie DateOfBirth oświadczenia) jest dostępny w ASP.NET Core [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Uwierzytelnianie ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autoryzacji platformy ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autoryzacja oparta na rolach**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Na podstawie zasad autoryzacji niestandardowej**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (developer-app-kluczy tajnych storage.md)
