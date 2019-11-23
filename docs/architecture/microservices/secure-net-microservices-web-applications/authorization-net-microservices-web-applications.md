---
title: Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — zapoznaj się z głównymi opcjami autoryzacji w ASP.NET Core aplikacje — oparta na rolach i oparta na zasadach.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296469"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="e7d59-103">Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych</span><span class="sxs-lookup"><span data-stu-id="e7d59-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="e7d59-104">Po uwierzytelnieniu ASP.NET Core internetowe interfejsy API muszą autoryzować dostęp.</span><span class="sxs-lookup"><span data-stu-id="e7d59-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="e7d59-105">Ten proces umożliwia usłudze udostępnianie interfejsów API niektórym uwierzytelnionym użytkownikom, ale nie wszystkim.</span><span class="sxs-lookup"><span data-stu-id="e7d59-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="e7d59-106">[Autoryzację](/aspnet/core/security/authorization/introduction) można wykonać w oparciu o role użytkowników lub na podstawie zasad niestandardowych, które mogą obejmować sprawdzanie oświadczeń lub innych algorytmów heurystycznych.</span><span class="sxs-lookup"><span data-stu-id="e7d59-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="e7d59-107">Ograniczanie dostępu do trasy ASP.NET Core MVC jest tak proste jak stosowanie atrybutu Autoryzuj do metody akcji (lub do klasy kontrolera, jeśli wszystkie akcje kontrolera wymagają autoryzacji), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e7d59-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="e7d59-108">Domyślnie dodanie atrybutu Autoryzuj bez parametrów spowoduje ograniczenie dostępu do uwierzytelnionych użytkowników dla tego kontrolera lub akcji.</span><span class="sxs-lookup"><span data-stu-id="e7d59-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="e7d59-109">Aby dodatkowo ograniczyć interfejs API do dostępności tylko dla określonych użytkowników, atrybut można rozszerzyć, aby określić wymagane role lub zasady, które użytkownicy muszą spełnić.</span><span class="sxs-lookup"><span data-stu-id="e7d59-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="e7d59-110">Implementowanie autoryzacji opartej na rolach</span><span class="sxs-lookup"><span data-stu-id="e7d59-110">Implement role-based authorization</span></span>

<span data-ttu-id="e7d59-111">Tożsamość ASP.NET Core ma wbudowaną koncepcję ról.</span><span class="sxs-lookup"><span data-stu-id="e7d59-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="e7d59-112">Oprócz użytkowników, ASP.NET Core tożsamość przechowuje informacje o różnych rolach używanych przez aplikację i śledzi użytkowników, którym przypisano role.</span><span class="sxs-lookup"><span data-stu-id="e7d59-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="e7d59-113">Te przypisania można programowo zmienić za pomocą typu `RoleManager`, który aktualizuje role w magazynie trwałym, a także typ `UserManager`, który może udzielić lub odwołać role użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e7d59-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="e7d59-114">W przypadku uwierzytelniania za pomocą tokenów okaziciela JWT, oprogramowanie pośredniczące uwierzytelniania okaziciela JWT ASP.NET Core wypełniać role użytkownika na podstawie oświadczeń ról znalezionych w tokenie.</span><span class="sxs-lookup"><span data-stu-id="e7d59-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="e7d59-115">Aby ograniczyć dostęp do akcji lub kontrolera MVC do użytkowników w określonych rolach, można dołączyć parametr Role w adnotacji Autoryzuj (Attribute), jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="e7d59-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="e7d59-116">W tym przykładzie tylko użytkownicy z rolą Administrator lub PowerUser mogą uzyskać dostęp do interfejsów API w kontrolerze ControlPanel (na przykład wykonując akcję SetTime).</span><span class="sxs-lookup"><span data-stu-id="e7d59-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="e7d59-117">Interfejs API zamykania jest dodatkowo ograniczony, aby zezwalać na dostęp tylko użytkownikom w roli administratora.</span><span class="sxs-lookup"><span data-stu-id="e7d59-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="e7d59-118">Aby wymagać, aby użytkownik znajdował się w wielu rolach, należy użyć wielu atrybutów autoryzacji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e7d59-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="e7d59-119">W tym przykładzie do wywołania API1 użytkownik musi:</span><span class="sxs-lookup"><span data-stu-id="e7d59-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="e7d59-120">Należy do roli administrator *lub* PowerUser, *a* także</span><span class="sxs-lookup"><span data-stu-id="e7d59-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="e7d59-121">Należy do roli RemoteEmployee *i*</span><span class="sxs-lookup"><span data-stu-id="e7d59-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="e7d59-122">Zaspokoj niestandardową procedurę obsługi autoryzacji CustomPolicy.</span><span class="sxs-lookup"><span data-stu-id="e7d59-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="e7d59-123">Implementowanie autoryzacji opartej na zasadach</span><span class="sxs-lookup"><span data-stu-id="e7d59-123">Implement policy-based authorization</span></span>

<span data-ttu-id="e7d59-124">Niestandardowe reguły autoryzacji można także napisać przy użyciu [zasad autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="e7d59-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="e7d59-125">Ta sekcja zawiera omówienie.</span><span class="sxs-lookup"><span data-stu-id="e7d59-125">This section provides an overview.</span></span> <span data-ttu-id="e7d59-126">Aby uzyskać więcej informacji, zobacz [warsztat ASP.NET Authorization](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="e7d59-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="e7d59-127">Niestandardowe zasady autoryzacji są rejestrowane w metodzie Startup. ConfigureServices przy użyciu usługi. Metoda addauthorization.</span><span class="sxs-lookup"><span data-stu-id="e7d59-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="e7d59-128">Ta metoda pobiera delegata, który konfiguruje argument AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="e7d59-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="e7d59-129">Jak pokazano w przykładzie, zasady można kojarzyć z różnymi typami wymagań.</span><span class="sxs-lookup"><span data-stu-id="e7d59-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="e7d59-130">Po zarejestrowaniu zasad można je stosować do akcji lub kontrolera przez przekazanie nazwy zasad jako argumentu zasad autoryzacji atrybutu Autoryzuj (na przykład `[Authorize(Policy="EmployeesOnly")]`) zasady mogą mieć wiele wymagań, a nie tylko jeden (jak pokazano w tych przykładach).</span><span class="sxs-lookup"><span data-stu-id="e7d59-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="e7d59-131">W poprzednim przykładzie pierwsze wywołanie addpolicy jest tylko alternatywnym sposobem autoryzacji przez rolę.</span><span class="sxs-lookup"><span data-stu-id="e7d59-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="e7d59-132">Jeśli `[Authorize(Policy="AdministratorsOnly")]` zostanie zastosowana do interfejsu API, tylko użytkownicy z rolą Administrator będą mogli uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="e7d59-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="e7d59-133">Drugie wywołanie <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> ilustruje łatwy sposób, aby wymagać określonego żądania dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e7d59-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="e7d59-134">Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> również opcjonalnie przyjmuje oczekiwane wartości dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="e7d59-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="e7d59-135">Jeśli wartości są określone, wymaganie jest spełnione tylko wtedy, gdy użytkownik ma zarówno żądanie poprawnego typu, jak i jedną z określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="e7d59-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="e7d59-136">Jeśli używasz oprogramowania pośredniczącego uwierzytelniania okaziciela JWT, wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e7d59-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="e7d59-137">Najbardziej interesujące zasady pokazane w tym miejscu znajdują się w trzeciej metodzie `AddPolicy`, ponieważ używa ona niestandardowego wymagania dotyczącego autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="e7d59-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="e7d59-138">Za pomocą niestandardowych wymagań dotyczących autoryzacji możesz mieć doskonałą kontrolę nad sposobem autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="e7d59-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="e7d59-139">Aby to działało, należy zaimplementować następujące typy:</span><span class="sxs-lookup"><span data-stu-id="e7d59-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="e7d59-140">Typ wymagań, który pochodzi od <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> i zawiera pola określające szczegóły wymagania.</span><span class="sxs-lookup"><span data-stu-id="e7d59-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="e7d59-141">W tym przykładzie jest to pole wiek dla przykładowego typu `MinimumAgeRequirement`.</span><span class="sxs-lookup"><span data-stu-id="e7d59-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="e7d59-142">Procedura obsługi implementująca <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, gdzie T jest typem <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement>, który może spełniać program obsługi.</span><span class="sxs-lookup"><span data-stu-id="e7d59-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="e7d59-143">Program obsługi musi zaimplementować metodę <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A>, która sprawdza, czy określony kontekst zawierający informacje o użytkowniku spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="e7d59-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="e7d59-144">Jeśli użytkownik spełnia wymagania, wywołanie do `context.Succeed` będzie wskazywać, że użytkownik jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="e7d59-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="e7d59-145">Jeśli istnieje wiele sposobów, że użytkownik może spełnić wymagania dotyczące autoryzacji, można utworzyć wiele programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="e7d59-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="e7d59-146">Oprócz rejestrowania wymagań zasad niestandardowych przy użyciu wywołań `AddPolicy` należy również zarejestrować niestandardowe programy obsługi wymagań za pomocą iniekcji zależności (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span><span class="sxs-lookup"><span data-stu-id="e7d59-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="e7d59-147">Przykładem niestandardowego wymagania dotyczącego autoryzacji i obsługi sprawdzania wieku użytkownika (na podstawie `DateOfBirth`ego) jest dostępny w [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Coreowej.</span><span class="sxs-lookup"><span data-stu-id="e7d59-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e7d59-148">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e7d59-148">Additional resources</span></span>

- <span data-ttu-id="e7d59-149"> \ **uwierzytelniania ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="e7d59-149">**ASP.NET Core Authentication** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="e7d59-150"> \ **autoryzacji ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="e7d59-150">**ASP.NET Core Authorization** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="e7d59-151"> \ **autoryzacji opartej na rolach**</span><span class="sxs-lookup"><span data-stu-id="e7d59-151">**Role-based Authorization** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="e7d59-152"> \ **autoryzacji opartej na zasadach niestandardowych**</span><span class="sxs-lookup"><span data-stu-id="e7d59-152">**Custom Policy-Based Authorization** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="e7d59-153">[Poprzedni](index.md)
>[Następny](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="e7d59-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
