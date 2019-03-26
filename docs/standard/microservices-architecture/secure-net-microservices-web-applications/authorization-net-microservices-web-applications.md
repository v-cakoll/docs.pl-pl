---
title: Informacje o autoryzacji w aplikacji sieci web i mikrousługi platformy .NET
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web — zapoznaj się z omówieniem opcji głównego autoryzacji w aplikacji platformy ASP.NET Core — opartej na rolach i oparte na zasadach.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466364"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="c0b02-103">Informacje o autoryzacji w aplikacji sieci web i mikrousługi platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c0b02-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="c0b02-104">Po uwierzytelnieniu interfejsów API sieci Web programu ASP.NET Core konieczne Autoryzowanie dostępu.</span><span class="sxs-lookup"><span data-stu-id="c0b02-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="c0b02-105">Ten proces umożliwia usłudze się interfejsów API, niektórzy użytkownicy uwierzytelnieni, ale nie dla wszystkich.</span><span class="sxs-lookup"><span data-stu-id="c0b02-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="c0b02-106">[Autoryzacja](/aspnet/core/security/authorization/introduction) mogą być oparte na rolach użytkowników lub na podstawie zasad niestandardowych, która może obejmować kontrolę opartą na oświadczeniach lub inne algorytmy heurystyczne.</span><span class="sxs-lookup"><span data-stu-id="c0b02-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="c0b02-107">Ograniczanie dostępu do trasy ASP.NET Core MVC jest równie proste jak stosowanie atrybutu autoryzacji do metody akcji (lub klasy kontrolera, jeśli wszystkie kontrolera akcji wymaga autoryzacji), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c0b02-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="c0b02-108">Domyślnie Dodawanie atrybutu autoryzacji bez parametrów zostaną ograniczyć dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji.</span><span class="sxs-lookup"><span data-stu-id="c0b02-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="c0b02-109">Aby bardziej ograniczyć interfejsu API, które będą dostępne dla tylko przez określonych użytkowników, ten atrybut można rozszerzyć, aby określić wymagane role lub zasad, które muszą spełniać użytkownicy.</span><span class="sxs-lookup"><span data-stu-id="c0b02-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="c0b02-110">Implementowanie autoryzacji opartej na rolach</span><span class="sxs-lookup"><span data-stu-id="c0b02-110">Implement role-based authorization</span></span>

<span data-ttu-id="c0b02-111">Tożsamość platformy ASP.NET Core ma wbudowane koncepcji ról.</span><span class="sxs-lookup"><span data-stu-id="c0b02-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="c0b02-112">Oprócz użytkowników ASP.NET Core Identity przechowuje informacje dotyczące różnych ról, używanych przez aplikację i śledzi użytkowników, którzy są przypisane do ról.</span><span class="sxs-lookup"><span data-stu-id="c0b02-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="c0b02-113">Te przypisania można zmienić programowo za pomocą `RoleManager` typ, który aktualizuje ról w trwałego magazynu i `UserManager` typ, który można udzielić lub odwołać role użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c0b02-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="c0b02-114">Jeśli masz uwierzytelnia się za pomocą tokenów elementu nośnego JWT, oprogramowanie pośredniczące uwierzytelniania elementu nośnego tokenu JWT programu ASP.NET Core spowoduje wypełnienie role użytkownika na podstawie oświadczeń roli w tokenie.</span><span class="sxs-lookup"><span data-stu-id="c0b02-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="c0b02-115">Aby ograniczyć dostęp do kontrolera dla użytkowników w określonych ról lub Akcja kontrolera MVC, może zawierać parametru role w adnotacji autoryzacji (atrybut), jak pokazano na następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="c0b02-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="c0b02-116">W tym przykładzie tylko użytkownicy w roli administratora lub Użytkownik_zaawansowany mogą dostęp do interfejsów API w kontrolerze Panelu sterowania (takie jak wykonanie akcji SetTime).</span><span class="sxs-lookup"><span data-stu-id="c0b02-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="c0b02-117">Interfejs API zamykania dalsze jest ograniczony do zezwolenia na dostęp tylko do użytkowników w roli administratora.</span><span class="sxs-lookup"><span data-stu-id="c0b02-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="c0b02-118">Aby wymagać od użytkownika znajdowała się na wiele ról, użyj wiele atrybutów autoryzacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c0b02-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="c0b02-119">W tym przykładzie do wywołania API1, użytkownik musi:</span><span class="sxs-lookup"><span data-stu-id="c0b02-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="c0b02-120">Mieć Administrator *lub* roli Użytkownik_zaawansowany *i*</span><span class="sxs-lookup"><span data-stu-id="c0b02-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="c0b02-121">Należeć do roli RemoteEmployee *i*</span><span class="sxs-lookup"><span data-stu-id="c0b02-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="c0b02-122">Spełnia niestandardowe Obsługa CustomPolicy autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="c0b02-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="c0b02-123">Implementowanie autoryzacji opartej na zasadach</span><span class="sxs-lookup"><span data-stu-id="c0b02-123">Implement policy-based authorization</span></span>

<span data-ttu-id="c0b02-124">Reguły autoryzacji niestandardowej można również będą zapisywane przy użyciu [zasady autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="c0b02-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="c0b02-125">Ta sekcja zawiera omówienie.</span><span class="sxs-lookup"><span data-stu-id="c0b02-125">This section provides an overview.</span></span> <span data-ttu-id="c0b02-126">Aby uzyskać więcej informacji, zobacz [Workshop autoryzacji programu ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="c0b02-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="c0b02-127">Zasady autoryzacji dla niestandardowego są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. Metoda AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="c0b02-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="c0b02-128">Ta metoda przyjmuje obiekt delegowany, który konfiguruje AuthorizationOptions argument.</span><span class="sxs-lookup"><span data-stu-id="c0b02-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="c0b02-129">Jak pokazano w przykładzie, mogą być skojarzone z różnymi typami wymagania.</span><span class="sxs-lookup"><span data-stu-id="c0b02-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="c0b02-130">Po zasady są zarejestrowane, mogą być stosowane do akcji lub kontrolera przez przekazanie nazwy zasad jako argument zasad autoryzacji atrybutu (na przykład `[Authorize(Policy="EmployeesOnly")]`) zasady mogą mieć wiele wymagań, nie tylko jeden (jak pokazano w tych przykłady).</span><span class="sxs-lookup"><span data-stu-id="c0b02-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="c0b02-131">W poprzednim przykładzie pierwsze wywołanie AddPolicy jest po prostu alternatywny sposób autoryzowania przez rolę.</span><span class="sxs-lookup"><span data-stu-id="c0b02-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="c0b02-132">Jeśli `[Authorize(Policy="AdministratorsOnly")]` jest stosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="c0b02-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="c0b02-133">Drugi <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> wywołanie pokazuje prosty sposób wymagają danego oświadczenia powinna istnieć dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0b02-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="c0b02-134"><xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> Metoda przyjmuje również opcjonalnie oczekiwane wartości oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="c0b02-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="c0b02-135">Jeśli nie określono wartości, to wymaganie można spełnić tylko wtedy, gdy użytkownik ma zarówno poprawnego typu oświadczenia i jednej z określonymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="c0b02-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="c0b02-136">Jeśli używasz oprogramowania pośredniczącego uwierzytelniania elementu nośnego JWT wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0b02-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="c0b02-137">Najciekawsze zasad wyświetlana w tym miejscu jest w trzecim `AddPolicy` metody, ponieważ używa ona wymaganie autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="c0b02-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="c0b02-138">Za pomocą niestandardowych określonych wymagań, możesz mieć dużą kontrolę nad jak odbywa się autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="c0b02-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="c0b02-139">Aby to zrobić należy zaimplementować te typy:</span><span class="sxs-lookup"><span data-stu-id="c0b02-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="c0b02-140">Typ wymagania, który pochodzi od klasy <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> i zawiera pola, określając szczegóły zapotrzebowania.</span><span class="sxs-lookup"><span data-stu-id="c0b02-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="c0b02-141">W tym przykładzie jest to pola Wiek przykładowej `MinimumAgeRequirement` typu.</span><span class="sxs-lookup"><span data-stu-id="c0b02-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="c0b02-142">Program obsługi, który implementuje <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, gdzie T jest typem <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> spełniających program obsługi.</span><span class="sxs-lookup"><span data-stu-id="c0b02-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="c0b02-143">Program obsługi musi implementować <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> metody, która sprawdza, czy określony kontekst, który zawiera informacje o użytkowniku spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="c0b02-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="c0b02-144">Jeśli użytkownik spełnia wymagania, wywołanie `context.Succeed` wskaże, że użytkownik jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="c0b02-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="c0b02-145">Jeśli istnieje wiele sposobów, że użytkownik może spełniają wymagania autoryzacji można utworzyć procedury obsługi wielu.</span><span class="sxs-lookup"><span data-stu-id="c0b02-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="c0b02-146">Oprócz rejestrowania wymagania zasad niestandardowych z `AddPolicy` wywołań, należy również zarejestrować niestandardowe wymagania obsługi za pomocą iniekcji zależności (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span><span class="sxs-lookup"><span data-stu-id="c0b02-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="c0b02-147">Przykład wymóg autoryzacji niestandardowego oraz obsługi kontroli wieku użytkownika (na podstawie `DateOfBirth` oświadczenia) jest dostępna w programie ASP.NET Core [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="c0b02-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c0b02-148">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="c0b02-148">Additional resources</span></span>

- <span data-ttu-id="c0b02-149">**Uwierzytelnianie programu ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="c0b02-149">**ASP.NET Core Authentication** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="c0b02-150">**Autoryzacji platformy ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="c0b02-150">**ASP.NET Core Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="c0b02-151">**Autoryzacja oparta na rolach** \\</span><span class="sxs-lookup"><span data-stu-id="c0b02-151">**Role-based Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="c0b02-152">**Autoryzacja niestandardowa oparta na zasadach** \\</span><span class="sxs-lookup"><span data-stu-id="c0b02-152">**Custom Policy-Based Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="c0b02-153">[Poprzednie](index.md)
>[dalej](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="c0b02-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
