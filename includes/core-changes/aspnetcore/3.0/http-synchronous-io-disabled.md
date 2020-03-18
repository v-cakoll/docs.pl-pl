---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901584"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="5d935-101">HTTP: Synchroniczne we/wy wyłączone na wszystkich serwerach</span><span class="sxs-lookup"><span data-stu-id="5d935-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="5d935-102">Począwszy od ASP.NET Core 3.0, synchroniczne operacje serwera są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5d935-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5d935-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="5d935-103">Change description</span></span>

<span data-ttu-id="5d935-104">`AllowSynchronousIO`jest opcją na każdym serwerze, która włącza lub `HttpRequest.Body.Read`wyłącza `HttpResponse.Body.Write`synchroniczne interfejsy API We/Wy, takie jak , i `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="5d935-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="5d935-105">Te interfejsy API od dawna źródłem głodu wątku i aplikacji zawiesza.</span><span class="sxs-lookup"><span data-stu-id="5d935-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="5d935-106">Począwszy od ASP.NET Core 3.0 Preview 3, te operacje synchroniczne są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5d935-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="5d935-107">Serwery, których dotyczy problem:</span><span class="sxs-lookup"><span data-stu-id="5d935-107">Affected servers:</span></span>

- <span data-ttu-id="5d935-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="5d935-108">Kestrel</span></span>
- <span data-ttu-id="5d935-109">HttpSys (HttpSys)</span><span class="sxs-lookup"><span data-stu-id="5d935-109">HttpSys</span></span>
- <span data-ttu-id="5d935-110">Przetwarzanie iIS</span><span class="sxs-lookup"><span data-stu-id="5d935-110">IIS in-process</span></span>
- <span data-ttu-id="5d935-111">Testserver</span><span class="sxs-lookup"><span data-stu-id="5d935-111">TestServer</span></span>

<span data-ttu-id="5d935-112">Spodziewaj się błędów podobnych do:</span><span class="sxs-lookup"><span data-stu-id="5d935-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="5d935-113">Każdy serwer `AllowSynchronousIO` ma opcję, która kontroluje to zachowanie i `false`domyślnie dla wszystkich z nich jest teraz .</span><span class="sxs-lookup"><span data-stu-id="5d935-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="5d935-114">Zachowanie można również zastąpić na podstawie na żądanie jako tymczasowe środki zaradcze.</span><span class="sxs-lookup"><span data-stu-id="5d935-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="5d935-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="5d935-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="5d935-116">Jeśli masz problemy `TextWriter` z lub innego strumienia wywołując `Dispose`synchroniczne `DisposeAsync` interfejsu API w , wywołać nowy interfejs API zamiast.</span><span class="sxs-lookup"><span data-stu-id="5d935-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="5d935-117">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="5d935-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5d935-118">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="5d935-118">Version introduced</span></span>

<span data-ttu-id="5d935-119">3.0</span><span class="sxs-lookup"><span data-stu-id="5d935-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5d935-120">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="5d935-120">Old behavior</span></span>

<span data-ttu-id="5d935-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`i `Stream.Flush` były domyślnie dozwolone.</span><span class="sxs-lookup"><span data-stu-id="5d935-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5d935-122">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="5d935-122">New behavior</span></span>

<span data-ttu-id="5d935-123">Te synchroniczne interfejsy API są domyślnie niedozwolone:</span><span class="sxs-lookup"><span data-stu-id="5d935-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="5d935-124">Spodziewaj się błędów podobnych do:</span><span class="sxs-lookup"><span data-stu-id="5d935-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="5d935-125">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="5d935-125">Reason for change</span></span>

<span data-ttu-id="5d935-126">Te synchroniczne interfejsy API od dawna źródłem głodu wątków i aplikacji zawiesza.</span><span class="sxs-lookup"><span data-stu-id="5d935-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="5d935-127">Począwszy od ASP.NET Core 3.0 Preview 3, operacje synchroniczne są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5d935-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5d935-128">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="5d935-128">Recommended action</span></span>

<span data-ttu-id="5d935-129">Użyj asynchronicznych wersji metod.</span><span class="sxs-lookup"><span data-stu-id="5d935-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="5d935-130">Zachowanie można również zastąpić na podstawie na żądanie jako tymczasowe środki zaradcze.</span><span class="sxs-lookup"><span data-stu-id="5d935-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="5d935-131">Kategoria</span><span class="sxs-lookup"><span data-stu-id="5d935-131">Category</span></span>

<span data-ttu-id="5d935-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5d935-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5d935-133">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5d935-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
