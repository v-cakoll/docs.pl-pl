---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394251"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="7ab3a-101">Uwierzytelnianie: Google+ przestarzałe i zastąpione</span><span class="sxs-lookup"><span data-stu-id="7ab3a-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="7ab3a-102">Google zaczyna [wyłączać](https://developers.google.com/+/api-shutdown) google+ Logowanie do aplikacji już 28 stycznia 2019.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7ab3a-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="7ab3a-103">Change description</span></span>

<span data-ttu-id="7ab3a-104">ASP.NET 4.x i ASP.NET Core używają interfejsów API logowania Google+ do uwierzytelniania użytkowników kont Google w aplikacjach internetowych.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="7ab3a-105">Pakiety NuGet, których dotyczy problem, to [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) dla ASP.NET `Microsoft.Owin` Core i [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) z ASP.NET formularzami internetowymi i MVC.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="7ab3a-106">Zastępcze interfejsy API Google używają innego źródła i formatu danych.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="7ab3a-107">Środki zaradcze i rozwiązania przedstawione poniżej uwzględniają zmiany strukturalne.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="7ab3a-108">Aplikacje powinny sprawdzać, czy same dane nadal spełniają ich wymagania.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="7ab3a-109">Na przykład nazwy, adresy e-mail, linki do profilu i zdjęcia profilowe mogą zawierać subtelnie inne wartości niż wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7ab3a-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7ab3a-110">Version introduced</span></span>

<span data-ttu-id="7ab3a-111">Wszystkie wersje.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-111">All versions.</span></span> <span data-ttu-id="7ab3a-112">Ta zmiana jest zewnętrzna dla ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7ab3a-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7ab3a-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="7ab3a-114">Owin z ASP.NET formularzami internetowymi i MVC</span><span class="sxs-lookup"><span data-stu-id="7ab3a-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="7ab3a-115">W `Microsoft.Owin` przypadku 3.1.0 i nowszych w [tym miejscu](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)przedstawiono tymczasowe środki zaradcze .</span><span class="sxs-lookup"><span data-stu-id="7ab3a-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="7ab3a-116">Aplikacje powinny zakończyć testowanie z łagodzenia, aby sprawdzić zmiany w formacie danych.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="7ab3a-117">Istnieją plany wydania `Microsoft.Owin` 4.0.1 z poprawką.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="7ab3a-118">Aplikacje korzystające z dowolnej wcześniejszej wersji powinny zostać zaktualizowane do wersji 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="7ab3a-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7ab3a-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="7ab3a-120">Środki zaradcze w [Owin z ASP.NET web forms i MVC](#owin-with-aspnet-web-forms-and-mvc) mogą być dostosowane do ASP.NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="7ab3a-121">Poprawki pakietu NuGet nie są planowane, ponieważ 1.x osiągnął stan [końca życia.](https://dotnet.microsoft.com/platform/support-policy)</span><span class="sxs-lookup"><span data-stu-id="7ab3a-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="7ab3a-122">ASP.NET Rdzeń 2.x</span><span class="sxs-lookup"><span data-stu-id="7ab3a-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="7ab3a-123">W `Microsoft.AspNetCore.Authentication.Google` przypadku wersji 2.x zastąp istniejące wywołanie `AddGoogle` `Startup.ConfigureServices` w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="7ab3a-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="7ab3a-124">Poprawki 2.1 i 2.2 z lutego zawierały poprzednią rekonfigurację jako nową wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="7ab3a-125">Nie ma poprawki dla ASP.NET Core 2.0, ponieważ osiągnął [koniec życia](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="7ab3a-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="7ab3a-126">ASP.NET Rdzeń 3.0</span><span class="sxs-lookup"><span data-stu-id="7ab3a-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="7ab3a-127">Środki zaradcze podane dla ASP.NET Core 2.x mogą być również używane do ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="7ab3a-128">W przyszłych wersjach zapoznawczych 3.0 `Microsoft.AspNetCore.Authentication.Google` pakiet może zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="7ab3a-129">Użytkownicy będą kierowane `Microsoft.AspNetCore.Authentication.OpenIdConnect` do zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="7ab3a-130">Poniższy kod pokazuje, `AddGoogle` jak `AddOpenIdConnect` `Startup.ConfigureServices`zastąpić w .</span><span class="sxs-lookup"><span data-stu-id="7ab3a-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="7ab3a-131">Ta wymiana może być używana z ASP.NET Core 2.0 i nowszym i może być dostosowana do ASP.NET Core 1.x w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="7ab3a-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="7ab3a-132">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7ab3a-132">Category</span></span>

<span data-ttu-id="7ab3a-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7ab3a-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7ab3a-134">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7ab3a-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
