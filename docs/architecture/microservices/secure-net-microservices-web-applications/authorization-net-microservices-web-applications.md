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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="c9f09-103">Informacje o autoryzacji w mikrousługach .NET i aplikacjach internetowych</span><span class="sxs-lookup"><span data-stu-id="c9f09-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="c9f09-104">Po uwierzytelnieniu ASP.NET core interfejsów API sieci Web muszą autoryzować dostęp.</span><span class="sxs-lookup"><span data-stu-id="c9f09-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="c9f09-105">Ten proces umożliwia usłudze udostępnianie interfejsów API niektórym uwierzytelnionym użytkownikom, ale nie wszystkim.</span><span class="sxs-lookup"><span data-stu-id="c9f09-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="c9f09-106">[Autoryzacja](/aspnet/core/security/authorization/introduction) może być wykonywana na podstawie ról użytkowników lub na podstawie zasad niestandardowych, które mogą obejmować inspekcję oświadczeń lub innych heurystyki.</span><span class="sxs-lookup"><span data-stu-id="c9f09-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users' roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="c9f09-107">Ograniczenie dostępu do ASP.NET trasy Core MVC jest tak proste, jak zastosowanie atrybutu Authorize do metody akcji (lub do klasy kontrolera, jeśli wszystkie akcje kontrolera wymagają autoryzacji), jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c9f09-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller's class if all the controller's actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="c9f09-108">Domyślnie dodanie atrybutu Authorize bez parametrów ograniczy dostęp do uwierzytelnionych użytkowników dla tego kontrolera lub akcji.</span><span class="sxs-lookup"><span data-stu-id="c9f09-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="c9f09-109">Aby dodatkowo ograniczyć interfejs API, który ma być dostępny tylko dla określonych użytkowników, atrybut można rozwinąć, aby określić wymagane role lub zasady, które użytkownicy muszą spełnić.</span><span class="sxs-lookup"><span data-stu-id="c9f09-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="c9f09-110">Wdrażanie autoryzacji opartej na rolach</span><span class="sxs-lookup"><span data-stu-id="c9f09-110">Implement role-based authorization</span></span>

<span data-ttu-id="c9f09-111">ASP.NET Podstawowa tożsamość ma wbudowaną koncepcję ról.</span><span class="sxs-lookup"><span data-stu-id="c9f09-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="c9f09-112">Oprócz użytkowników ASP.NET Tożsamość podstawowa przechowuje informacje o różnych rolach używanych przez aplikację i śledzi, którzy użytkownicy są przypisani do ról.</span><span class="sxs-lookup"><span data-stu-id="c9f09-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="c9f09-113">Te przypisania można zmienić programowo z typem, `RoleManager` który aktualizuje role w utrwalone magazynu i `UserManager` typu, który może przyznać lub odwołać role od użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c9f09-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="c9f09-114">Jeśli uwierzytelniasz się za pomocą tokenów nośnych JWT, ASP.NET core JWT oprogramowanie pośredniczące uwierzytelniania na okaziciela wypełni role użytkownika na podstawie oświadczeń roli znalezionych w tokenie.</span><span class="sxs-lookup"><span data-stu-id="c9f09-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user's roles based on role claims found in the token.</span></span> <span data-ttu-id="c9f09-115">Aby ograniczyć dostęp do akcji lub kontrolera MVC do użytkowników w określonych rolach, można dołączyć parametr Roles w adnotacji Autoryzacyjnej (atrybut), jak pokazano w następującym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="c9f09-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="c9f09-116">W tym przykładzie tylko użytkownicy w rolach administratora lub PowerUser mogą uzyskiwać dostęp do interfejsów API w kontrolerze ControlPanel (na przykład wykonywania akcji SetTime).</span><span class="sxs-lookup"><span data-stu-id="c9f09-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="c9f09-117">Interfejs API ShutDown jest dodatkowo ograniczony, aby zezwolić na dostęp tylko do użytkowników w roli administratora.</span><span class="sxs-lookup"><span data-stu-id="c9f09-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="c9f09-118">Aby wymagać, aby użytkownik był w wielu rolach, należy użyć wielu atrybutów Autoryzuj, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c9f09-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="c9f09-119">W tym przykładzie, aby wywołać API1, użytkownik musi:</span><span class="sxs-lookup"><span data-stu-id="c9f09-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="c9f09-120">Być w roli administratora *lub* PowerUser, *i*</span><span class="sxs-lookup"><span data-stu-id="c9f09-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="c9f09-121">Wcielić się w rolę RemoteEmployee *i*</span><span class="sxs-lookup"><span data-stu-id="c9f09-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="c9f09-122">Spełnij niestandardowy program obsługi autoryzacji CustomPolicy.</span><span class="sxs-lookup"><span data-stu-id="c9f09-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="c9f09-123">Wdrażanie autoryzacji opartej na zasadach</span><span class="sxs-lookup"><span data-stu-id="c9f09-123">Implement policy-based authorization</span></span>

<span data-ttu-id="c9f09-124">Reguły autoryzacji niestandardowej można również zapisywać przy użyciu [zasad autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="c9f09-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="c9f09-125">Ta sekcja zawiera omówienie.</span><span class="sxs-lookup"><span data-stu-id="c9f09-125">This section provides an overview.</span></span> <span data-ttu-id="c9f09-126">Aby uzyskać więcej informacji, zobacz [warsztaty autoryzacji ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="c9f09-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="c9f09-127">Zasady autoryzacji niestandardowej są rejestrowane w metodzie Startup.ConfigureServices przy użyciu usługi. AddAuthorization metody.</span><span class="sxs-lookup"><span data-stu-id="c9f09-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="c9f09-128">Ta metoda przyjmuje pełnomocnika, który konfiguruje argument AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="c9f09-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="c9f09-129">Jak pokazano w przykładzie, zasady mogą być skojarzone z różnymi typami wymagań.</span><span class="sxs-lookup"><span data-stu-id="c9f09-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="c9f09-130">Po zarejestrowaniu zasad można je zastosować do akcji lub kontrolera, przekazując nazwę zasad jako argument Zasad atrybutu Authorize (na przykład `[Authorize(Policy="EmployeesOnly")]`) Zasady mogą mieć wiele wymagań, a nie tylko jeden (jak pokazano w tych przykładach).</span><span class="sxs-lookup"><span data-stu-id="c9f09-130">After the policies are registered, they can be applied to an action or controller by passing the policy's name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="c9f09-131">W poprzednim przykładzie pierwsze wywołanie AddPolicy jest tylko alternatywnym sposobem autoryzowania przez rolę.</span><span class="sxs-lookup"><span data-stu-id="c9f09-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="c9f09-132">Jeśli `[Authorize(Policy="AdministratorsOnly")]` jest stosowany do interfejsu API, tylko użytkownicy w roli administratora będą mogli uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="c9f09-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="c9f09-133">Drugie <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> wywołanie pokazuje łatwy sposób wymagać, że określone oświadczenie powinno być obecne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9f09-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="c9f09-134">Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> również opcjonalnie przyjmuje oczekiwane wartości dla oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="c9f09-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="c9f09-135">Jeśli wartości są określone, wymaganie jest spełnione tylko wtedy, gdy użytkownik ma zarówno oświadczenie prawidłowego typu i jedną z określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="c9f09-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="c9f09-136">Jeśli używasz oprogramowania pośredniczącego uwierzytelniania na okaziciela JWT, wszystkie właściwości JWT będą dostępne jako oświadczenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9f09-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="c9f09-137">Najciekawsze zasady pokazane tutaj jest `AddPolicy` w trzeciej metody, ponieważ używa wymagania autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="c9f09-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="c9f09-138">Za pomocą wymagań autoryzacji niestandardowej, można mieć dużą kontrolę nad jak autoryzacja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="c9f09-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="c9f09-139">Aby to zadziałało, należy zaimplementować następujące typy:</span><span class="sxs-lookup"><span data-stu-id="c9f09-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="c9f09-140">Typ wymagania, który pochodzi <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> z i który zawiera pola określające szczegóły wymagania.</span><span class="sxs-lookup"><span data-stu-id="c9f09-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="c9f09-141">W tym przykładzie jest to pole `MinimumAgeRequirement` wiekowe dla typu próbki.</span><span class="sxs-lookup"><span data-stu-id="c9f09-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="c9f09-142">Program obsługi, <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>który implementuje , <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> gdzie T jest typem, który program obsługi może spełnić.</span><span class="sxs-lookup"><span data-stu-id="c9f09-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="c9f09-143">Program obsługi musi <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> implementować metodę, która sprawdza, czy określony kontekst, który zawiera informacje o użytkowniku spełnia wymagania.</span><span class="sxs-lookup"><span data-stu-id="c9f09-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="c9f09-144">Jeśli użytkownik spełnia wymagania, wywołanie `context.Succeed` wskazuje, że użytkownik jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="c9f09-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="c9f09-145">Jeśli istnieje wiele sposobów, że użytkownik może spełnić wymagania autoryzacji, można utworzyć wiele programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="c9f09-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="c9f09-146">Oprócz rejestrowania niestandardowych wymagań `AddPolicy` dotyczących zasad za pomocą wywołań, należy również`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`zarejestrować niestandardowe programy obsługi wymagań za pośrednictwem iniekcji zależności ( ).</span><span class="sxs-lookup"><span data-stu-id="c9f09-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="c9f09-147">Przykład wymagania autoryzacji niestandardowej i programu obsługi do sprawdzania wieku `DateOfBirth` użytkownika (na podstawie oświadczenia) jest dostępny w [dokumentacji autoryzacji](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Core .</span><span class="sxs-lookup"><span data-stu-id="c9f09-147">An example of a custom authorization requirement and handler for checking a user's age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c9f09-148">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="c9f09-148">Additional resources</span></span>

- <span data-ttu-id="c9f09-149">**Uwierzytelnianie ASP.NET rdzeniowe** </span><span class="sxs-lookup"><span data-stu-id="c9f09-149">**ASP.NET Core Authentication** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="c9f09-150">**Autoryzacja ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="c9f09-150">**ASP.NET Core Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="c9f09-151">**Autoryzacja oparta na rolach** </span><span class="sxs-lookup"><span data-stu-id="c9f09-151">**Role-based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="c9f09-152">**Autoryzacja oparta na zasadach niestandardowych** </span><span class="sxs-lookup"><span data-stu-id="c9f09-152">**Custom Policy-Based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="c9f09-153">[Poprzedni](index.md)
>[następny](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="c9f09-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
