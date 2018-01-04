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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="dd53a-104">Temat autoryzacji w aplikacji sieci web i mikrousług .NET</span><span class="sxs-lookup"><span data-stu-id="dd53a-104">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="dd53a-105">Po uwierzytelnieniu interfejsów API platformy ASP.NET Core sieci Web wymagane do autoryzowania dostępu.</span><span class="sxs-lookup"><span data-stu-id="dd53a-105">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="dd53a-106">Ten proces umożliwia usłudze upewnij interfejsów API, niektóre uwierzytelnionych użytkowników, ale nie do wszystkich.</span><span class="sxs-lookup"><span data-stu-id="dd53a-106">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="dd53a-107">[Autoryzacji](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) mogą być wykonywane w oparciu o role użytkowników lub na podstawie niestandardowych zasad, która może obejmować sprawdzania oświadczeń lub inne algorytmy heurystyczne.</span><span class="sxs-lookup"><span data-stu-id="dd53a-107">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="dd53a-108">Ograniczanie dostępu do platformy ASP.NET Core MVC trasy jest tak proste, jak zastosowanie atrybutu autoryzacji do metody akcji (lub do klasy kontrolera, jeśli wszystkie kontrolera akcji wymaga autoryzacji), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="dd53a-108">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="dd53a-109">Domyślnie dodając atrybut autoryzacji bez parametrów zostaną ograniczyć dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji.</span><span class="sxs-lookup"><span data-stu-id="dd53a-109">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="dd53a-110">Aby bardziej ograniczyć interfejsu API, które mają być dostępne tylko dla określonych użytkowników, atrybut można rozszerzyć, aby określić wymagane role lub zasady, które muszą spełniać użytkownicy.</span><span class="sxs-lookup"><span data-stu-id="dd53a-110">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="dd53a-111">Implementowanie autoryzacji opartej na rolach</span><span class="sxs-lookup"><span data-stu-id="dd53a-111">Implementing role-based authorization</span></span>

<span data-ttu-id="dd53a-112">Tożsamość platformy ASP.NET Core ma wbudowane koncepcji ról.</span><span class="sxs-lookup"><span data-stu-id="dd53a-112">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="dd53a-113">Oprócz użytkowników ASP.NET Core Identity są przechowywane informacje o różnych ról używany przez aplikację i śledzi użytkowników, którzy są przypisane do ról.</span><span class="sxs-lookup"><span data-stu-id="dd53a-113">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="dd53a-114">Te przydziały można zmienić programowo z RoleManager typu (aktualizacje ról w utrwalonego magazynu) i typ interfejs UserManager, (które można przypisać lub Cofnij przypisanie ról użytkowników).</span><span class="sxs-lookup"><span data-stu-id="dd53a-114">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="dd53a-115">Jeśli uwierzytelnianych tokenów elementu nośnego JWT, oprogramowanie pośredniczące uwierzytelniania elementu nośnego ASP.NET Core JWT są powielane ról użytkownika na podstawie oświadczeń roli znaleziono ją w tokenie.</span><span class="sxs-lookup"><span data-stu-id="dd53a-115">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="dd53a-116">Aby ograniczyć dostęp do MVC akcji lub kontrolera dla użytkowników w określonych ról, może zawierać parametru ról w nagłówku autoryzacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="dd53a-116">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="dd53a-117">W tym przykładzie tylko użytkownicy o rolach administratora lub Użytkownik_zaawansowany można uzyskać dostępu do interfejsów API w Panelu sterowania kontrolera (np. wykonywanie akcji SetTime).</span><span class="sxs-lookup"><span data-stu-id="dd53a-117">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="dd53a-118">Interfejs API zamykania dalsze jest ograniczona do zezwolić na dostęp tylko do użytkowników w roli administratora.</span><span class="sxs-lookup"><span data-stu-id="dd53a-118">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="dd53a-119">Wymagać, aby być użytkownik był w wiele ról, należy użyć wiele atrybutów autoryzacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="dd53a-119">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="dd53a-120">W tym przykładzie aby wywołać API1, użytkownik musi:</span><span class="sxs-lookup"><span data-stu-id="dd53a-120">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="dd53a-121">Można w administrator *lub* roli Użytkownik_zaawansowany *i*</span><span class="sxs-lookup"><span data-stu-id="dd53a-121">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="dd53a-122">W roli RemoteEmployee *i*</span><span class="sxs-lookup"><span data-stu-id="dd53a-122">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="dd53a-123">Spełnia niestandardowego programu obsługi dla CustomPolicy autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="dd53a-123">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="dd53a-124">Wdrażanie na podstawie zasad autoryzacji</span><span class="sxs-lookup"><span data-stu-id="dd53a-124">Implementing policy-based authorization</span></span>

<span data-ttu-id="dd53a-125">Reguły autoryzacji niestandardowej można także napisane przy użyciu [zasady autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="dd53a-125">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="dd53a-126">W tej sekcji, firma Microsoft udostępnia przegląd.</span><span class="sxs-lookup"><span data-stu-id="dd53a-126">In this section we provide an overview.</span></span> <span data-ttu-id="dd53a-127">Więcej szczegółów znajduje się w dokumentacji online [Workshop autoryzacji programu ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="dd53a-127">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="dd53a-128">Zasady autoryzacji niestandardowe są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. Metoda AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="dd53a-128">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="dd53a-129">Ta metoda przyjmuje delegata, który konfiguruje argumentu AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="dd53a-129">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="dd53a-130">Jak pokazano w przykładzie, mogą być skojarzone z różnymi typami wymagania.</span><span class="sxs-lookup"><span data-stu-id="dd53a-130">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="dd53a-131">Gdy zasady są zarejestrowane, mogą być stosowane do akcji lub kontrolera przez przekazanie jako argument zasad autoryzacji atrybutu nazwy zasad (na przykład \[Authorize(Policy="EmployeesOnly")\]) może mieć zasady wiele wymagań, nie tylko jedną (jak pokazano w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="dd53a-131">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="dd53a-132">W poprzednim przykładzie pierwsze wywołanie AddPolicy to po prostu alternatywny sposób autoryzowania przez rolę.</span><span class="sxs-lookup"><span data-stu-id="dd53a-132">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="dd53a-133">Jeśli \[Authorize(Policy="AdministratorsOnly")\] jest stosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="dd53a-133">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="dd53a-134">Drugie wywołanie AddPolicy przedstawiono prosty sposób wymagają określonej oświadczenia powinna występować dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dd53a-134">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="dd53a-135">Metoda RequireClaim również opcjonalnie przyjmuje oczekiwanych wartości oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="dd53a-135">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="dd53a-136">Jeśli wartości są określone, to wymaganie można spełnić tylko wtedy, gdy użytkownik ma zarówno poprawnego typu oświadczenia i jednej z określonymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="dd53a-136">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="dd53a-137">Jeśli używasz oprogramowania pośredniczącego uwierzytelniania elementu nośnego JWT wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dd53a-137">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="dd53a-138">Najbardziej interesujących zasady pokazane są w metodzie AddPolicy trzeci, ponieważ używa wymaganie autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="dd53a-138">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="dd53a-139">Za pomocą wymagania autoryzacji niestandardowej, może mieć wiele kontrolę nad realizację autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="dd53a-139">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="dd53a-140">Aby to zrobić należy zaimplementować te typy:</span><span class="sxs-lookup"><span data-stu-id="dd53a-140">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="dd53a-141">Typ wymagania, która jest pochodną IAuthorizationRequirement i zawiera pola, określając szczegóły zapotrzebowania.</span><span class="sxs-lookup"><span data-stu-id="dd53a-141">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="dd53a-142">W tym przykładzie jest pola wiek dla typu MinimumAgeRequirement próbki.</span><span class="sxs-lookup"><span data-stu-id="dd53a-142">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="dd53a-143">Program obsługi, który implementuje AuthorizationHandler&lt;T&gt;, gdzie T jest typ IAuthorizationRequirement, która spełnia program obsługi.</span><span class="sxs-lookup"><span data-stu-id="dd53a-143">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="dd53a-144">Program obsługi musi implementować metodę HandleRequirementAsync, która sprawdza, czy określony kontekst, który zawiera informacje dotyczące użytkownika spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="dd53a-144">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="dd53a-145">Jeśli użytkownika spełnia wymagania, wywołania do kontekstu. Pomyślnie będzie wskazywać, że użytkownik jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="dd53a-145">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="dd53a-146">Jeśli istnieje wiele sposobów, że użytkownik może spełniają wymagania autoryzacji można utworzyć procedury obsługi wielu.</span><span class="sxs-lookup"><span data-stu-id="dd53a-146">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="dd53a-147">Oprócz rejestrowania wymagania zasad niestandardowych za pomocą wywołania AddPolicy, należy również zarejestrować wymagania niestandardowe programy obsługi, za pomocą iniekcji zależności (usługi. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="dd53a-147">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="dd53a-148">Przykład wymaganie autoryzacji niestandardowej i obsługi sprawdzania wiek użytkownika (na podstawie DateOfBirth oświadczenia) jest dostępny w ASP.NET Core [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="dd53a-148">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="dd53a-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="dd53a-149">Additional resources</span></span>

-   <span data-ttu-id="dd53a-150">**Uwierzytelnianie ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="dd53a-150">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="dd53a-151">**Autoryzacji platformy ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="dd53a-151">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="dd53a-152">**Autoryzacja oparta na rolach**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="dd53a-152">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="dd53a-153">**Na podstawie zasad autoryzacji niestandardowej**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="dd53a-153">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="dd53a-154">[Poprzednie] (index.md) [dalej] (developer-app-kluczy tajnych storage.md)</span><span class="sxs-lookup"><span data-stu-id="dd53a-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
