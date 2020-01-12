---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901584"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="91e73-101">HTTP: synchroniczna operacja we/wy wyłączona na wszystkich serwerach</span><span class="sxs-lookup"><span data-stu-id="91e73-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="91e73-102">Począwszy od ASP.NET Core 3,0, operacje serwera synchronicznego są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="91e73-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="91e73-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="91e73-103">Change description</span></span>

<span data-ttu-id="91e73-104">`AllowSynchronousIO` to opcja na każdym serwerze, która włącza lub wyłącza synchroniczne interfejsy API we/wy, takie jak `HttpRequest.Body.Read`, `HttpResponse.Body.Write`i `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="91e73-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="91e73-105">Te interfejsy API były źródłem zawieszania wątków i zawieszenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91e73-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="91e73-106">Począwszy od ASP.NET Core 3,0 wersji zapoznawczej 3, te operacje synchroniczne są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="91e73-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="91e73-107">Narażone serwery:</span><span class="sxs-lookup"><span data-stu-id="91e73-107">Affected servers:</span></span>

- <span data-ttu-id="91e73-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="91e73-108">Kestrel</span></span>
- <span data-ttu-id="91e73-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="91e73-109">HttpSys</span></span>
- <span data-ttu-id="91e73-110">Usługi IIS w procesie</span><span class="sxs-lookup"><span data-stu-id="91e73-110">IIS in-process</span></span>
- <span data-ttu-id="91e73-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="91e73-111">TestServer</span></span>

<span data-ttu-id="91e73-112">Oczekiwane błędy są podobne do:</span><span class="sxs-lookup"><span data-stu-id="91e73-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="91e73-113">Każdy serwer ma `AllowSynchronousIO` opcji, która steruje tym zachowaniem, a jego wartość domyślna to teraz `false`.</span><span class="sxs-lookup"><span data-stu-id="91e73-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="91e73-114">Zachowanie może być również zastąpione dla każdego żądania jako tymczasowe środki zaradcze.</span><span class="sxs-lookup"><span data-stu-id="91e73-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="91e73-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="91e73-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="91e73-116">Jeśli masz problemy z `TextWriter` lub innym strumieniem wywołującym synchroniczny interfejs API w `Dispose`, wywołaj zamiast niego nowy interfejs API `DisposeAsync`.</span><span class="sxs-lookup"><span data-stu-id="91e73-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="91e73-117">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="91e73-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="91e73-118">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="91e73-118">Version introduced</span></span>

<span data-ttu-id="91e73-119">3.0</span><span class="sxs-lookup"><span data-stu-id="91e73-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="91e73-120">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="91e73-120">Old behavior</span></span>

<span data-ttu-id="91e73-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`i `Stream.Flush` były domyślnie dozwolone.</span><span class="sxs-lookup"><span data-stu-id="91e73-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="91e73-122">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="91e73-122">New behavior</span></span>

<span data-ttu-id="91e73-123">Te synchroniczne interfejsy API są domyślnie niedozwolone:</span><span class="sxs-lookup"><span data-stu-id="91e73-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="91e73-124">Oczekiwane błędy są podobne do:</span><span class="sxs-lookup"><span data-stu-id="91e73-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="91e73-125">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="91e73-125">Reason for change</span></span>

<span data-ttu-id="91e73-126">Te synchroniczne interfejsy API były źródłem przetrzymania wątku i zawieszenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91e73-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="91e73-127">Począwszy od ASP.NET Core 3,0 wersja zapoznawcza 3 operacje synchroniczne są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="91e73-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="91e73-128">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="91e73-128">Recommended action</span></span>

<span data-ttu-id="91e73-129">Używaj asynchronicznych wersji metod.</span><span class="sxs-lookup"><span data-stu-id="91e73-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="91e73-130">Zachowanie może być również zastąpione dla każdego żądania jako tymczasowe środki zaradcze.</span><span class="sxs-lookup"><span data-stu-id="91e73-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="91e73-131">Kategoria</span><span class="sxs-lookup"><span data-stu-id="91e73-131">Category</span></span>

<span data-ttu-id="91e73-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="91e73-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="91e73-133">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="91e73-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
