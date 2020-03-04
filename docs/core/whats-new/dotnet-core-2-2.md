---
title: Co nowego w programie .NET Core 2.2
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 2,2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156585"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="6a53c-103">Co nowego w programie .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6a53c-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="6a53c-104">Program .NET Core 2,2 zawiera usprawnienia wdrażania aplikacji, obsługi zdarzeń dla usług środowiska uruchomieniowego, uwierzytelniania do baz danych Azure SQL, wydajności kompilatora JIT i iniekcji kodu przed wykonaniem metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="6a53c-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="6a53c-105">Nowy tryb wdrażania</span><span class="sxs-lookup"><span data-stu-id="6a53c-105">New deployment mode</span></span>

<span data-ttu-id="6a53c-106">Począwszy od platformy .NET Core 2,2, można wdrożyć pliki [wykonywalne zależne od platformy](../deploying/index.md#publish-runtime-dependent), które są plikami **exe** zamiast plików **dll** .</span><span class="sxs-lookup"><span data-stu-id="6a53c-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-runtime-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="6a53c-107">Funkcje podobne do wdrożeń zależnych od platformy, zależne od struktury pliki wykonywalne (całego) nadal polegają na obecności udostępnionej wersji systemu .NET Core do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="6a53c-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="6a53c-108">Aplikacja zawiera tylko kod i wszystkie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="6a53c-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="6a53c-109">W przeciwieństwie do wdrożeń zależnych od struktury FDEs są specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="6a53c-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="6a53c-110">Ten nowy tryb wdrożenia ma odrębną zaletę kompilowania pliku wykonywalnego zamiast biblioteki, co oznacza, że można uruchomić aplikację bezpośrednio bez wywoływania `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6a53c-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="6a53c-111">Podstawowe</span><span class="sxs-lookup"><span data-stu-id="6a53c-111">Core</span></span>

<span data-ttu-id="6a53c-112">**Obsługa zdarzeń w usługach środowiska uruchomieniowego**</span><span class="sxs-lookup"><span data-stu-id="6a53c-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="6a53c-113">Często warto monitorować użycie usług środowiska uruchomieniowego w aplikacji, takich jak GC, JIT i wątków, aby zrozumieć, jak wpływają na aplikację.</span><span class="sxs-lookup"><span data-stu-id="6a53c-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="6a53c-114">W systemach Windows jest to zwykle wykonywane przez monitorowanie zdarzeń ETW bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="6a53c-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="6a53c-115">Mimo że ta funkcja nadal działa, nie zawsze jest możliwe korzystanie z funkcji ETW, jeśli jest uruchomiona w środowisku z niskim poziomem uprawnień lub w systemie Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="6a53c-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="6a53c-116">Począwszy od platformy .NET Core 2,2, zdarzenia CoreCLR można teraz wykorzystać przy użyciu klasy <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a53c-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6a53c-117">Te zdarzenia opisują zachowanie takich usług w czasie wykonywania jak GC, JIT, wątków i międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="6a53c-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="6a53c-118">Są to te same zdarzenia, które są ujawniane w ramach dostawcy ETW CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6a53c-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="6a53c-119">Dzięki temu aplikacje mogą zużywać te zdarzenia lub korzystać z mechanizmu transportu w celu wysyłania ich do usługi agregacji telemetrii.</span><span class="sxs-lookup"><span data-stu-id="6a53c-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="6a53c-120">Możesz zobaczyć, jak subskrybować zdarzenia w następującym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="6a53c-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="6a53c-121">Ponadto program .NET Core 2,2 dodaje następujące dwie właściwości do klasy <xref:System.Diagnostics.Tracing.EventWrittenEventArgs>, aby uzyskać dodatkowe informacje na temat zdarzeń ETW:</span><span class="sxs-lookup"><span data-stu-id="6a53c-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="6a53c-122">Dane</span><span class="sxs-lookup"><span data-stu-id="6a53c-122">Data</span></span>

<span data-ttu-id="6a53c-123">**Uwierzytelnianie w usłudze AAD w bazach danych Azure SQL przy użyciu właściwości SQLConnection. AccessToken**</span><span class="sxs-lookup"><span data-stu-id="6a53c-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="6a53c-124">Począwszy od platformy .NET Core 2,2, token dostępu wystawiony przez Azure Active Directory może służyć do uwierzytelniania w usłudze Azure SQL Database.</span><span class="sxs-lookup"><span data-stu-id="6a53c-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="6a53c-125">Aby można było obsługiwać tokeny dostępu, właściwość <xref:System.Data.SqlClient.SqlConnection.AccessToken> została dodana do klasy <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="6a53c-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="6a53c-126">Aby skorzystać z uwierzytelniania w usłudze AAD, Pobierz wersję 4,6 pakietu NuGet system. Data. SqlClient.</span><span class="sxs-lookup"><span data-stu-id="6a53c-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="6a53c-127">Aby skorzystać z tej funkcji, można uzyskać wartość tokenu dostępu przy użyciu [Active Directory Authentication Library dla platformy .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawartej w pakiecie NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) .</span><span class="sxs-lookup"><span data-stu-id="6a53c-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="6a53c-128">Udoskonalenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="6a53c-128">JIT compiler improvements</span></span>

<span data-ttu-id="6a53c-129">**Kompilacja warstwowa pozostaje funkcją wyboru**</span><span class="sxs-lookup"><span data-stu-id="6a53c-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="6a53c-130">W programie .NET Core 2,1 kompilator JIT zaimplementował nową technologię kompilatora, *kompilację warstwową*jako funkcję wyboru.</span><span class="sxs-lookup"><span data-stu-id="6a53c-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="6a53c-131">Celem kompilacji warstwowej jest zwiększona wydajność.</span><span class="sxs-lookup"><span data-stu-id="6a53c-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="6a53c-132">Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="6a53c-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="6a53c-133">Jednak w przypadku niewielkich ścieżek kodu kompilator może poświęcać więcej czasu na optymalizację kodu niż środowisko uruchomieniowe poświęca na wykonywanie niezoptymalizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6a53c-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="6a53c-134">Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="6a53c-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="6a53c-135">**Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6a53c-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="6a53c-136">**Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często.</span><span class="sxs-lookup"><span data-stu-id="6a53c-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="6a53c-137">Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="6a53c-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="6a53c-138">Aby uzyskać informacje na temat poprawy wydajności, która może wynikać z kompilacji warstwowej, zobacz temat [ogłaszanie programu .NET Core 2,2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="6a53c-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="6a53c-139">W programie .NET Core 2,2 w wersji zapoznawczej 2 kompilacja warstwowa została włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6a53c-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="6a53c-140">Jednak firma Microsoft zdecydowała się, że nadal nie możesz domyślnie włączyć kompilacji warstwowej.</span><span class="sxs-lookup"><span data-stu-id="6a53c-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="6a53c-141">Dlatego w przypadku platformy .NET Core 2,2 kompilacja warstwowa nadal jest funkcją wyboru.</span><span class="sxs-lookup"><span data-stu-id="6a53c-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="6a53c-142">Aby uzyskać informacje o tym, jak przeprowadzić kompilację warstwową, zobacz [udoskonalenia kompilatora JIT](dotnet-core-2-1.md#jit-compiler-improvements) w artykule [co nowego w programie .NET Core 2,1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="6a53c-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="6a53c-143">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6a53c-143">Runtime</span></span>

<span data-ttu-id="6a53c-144">**Wprowadzanie kodu przed wykonaniem metody Main**</span><span class="sxs-lookup"><span data-stu-id="6a53c-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="6a53c-145">Począwszy od platformy .NET Core 2,2, można użyć punktu zaczepienia uruchomienia, aby wstrzyknąć kod przed uruchomieniem głównej metody aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a53c-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="6a53c-146">Punkty zaczepienia uruchomienia umożliwiają hostowi dostosowanie zachowania aplikacji po ich wdrożeniu bez konieczności ponownego kompilowania lub zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a53c-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="6a53c-147">Oczekujemy, że dostawcy hostingu definiują niestandardową konfigurację i zasady, w tym ustawienia, które mogą mieć wpływ na zachowanie ładowania głównego punktu wejścia, takie jak <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6a53c-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="6a53c-148">Punkt zaczepienia może służyć do konfigurowania iniekcji lub wstrzykiwania danych telemetrycznych, konfigurowania wywołań zwrotnych do obsługi lub definiowania innych zachowań zależnych od środowiska.</span><span class="sxs-lookup"><span data-stu-id="6a53c-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="6a53c-149">Punkt zaczepienia jest oddzielony od punktu wejścia, dzięki czemu kod użytkownika nie musi być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="6a53c-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="6a53c-150">Aby uzyskać więcej informacji, zobacz punkt [zaczepienia uruchamiania hosta](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) .</span><span class="sxs-lookup"><span data-stu-id="6a53c-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a53c-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a53c-151">See also</span></span>

- [<span data-ttu-id="6a53c-152">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="6a53c-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="6a53c-153">Co nowego w ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="6a53c-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="6a53c-154">Nowe funkcje w EF Core 2,2</span><span class="sxs-lookup"><span data-stu-id="6a53c-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
