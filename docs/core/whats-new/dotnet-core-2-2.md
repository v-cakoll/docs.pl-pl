---
title: Co nowego w programie .NET Core 2.2
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 64cb561acd72ff5d4a11fcae7ce59eaad750f74e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644373"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="3d4ee-103">Co nowego w programie .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="3d4ee-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="3d4ee-104">.NET Core 2.2 zawiera ulepszenia we wdrażaniu aplikacji, obsługa zdarzeń dla usług środowiska wykonawczego, uwierzytelnianie w bazach `Main` danych SQL platformy Azure, wydajność kompilatora JIT i iniekcję kodu przed wykonaniem metody.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="3d4ee-105">Nowy tryb wdrażania</span><span class="sxs-lookup"><span data-stu-id="3d4ee-105">New deployment mode</span></span>

<span data-ttu-id="3d4ee-106">Począwszy od programu .NET Core 2.2, można wdrażać [pliki wykonywalne zależne od struktury](../deploying/index.md#publish-runtime-dependent), które są plikami **exe** zamiast plików **dll.**</span><span class="sxs-lookup"><span data-stu-id="3d4ee-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-runtime-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="3d4ee-107">Funkcjonalnie podobne do wdrożeń zależnych od struktury, pliki wykonywalne zależne od struktury (FDE) nadal opierają się na obecności udostępnionej wersji systemu .NET Core do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="3d4ee-108">Aplikacja zawiera tylko kod i wszelkie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="3d4ee-109">W przeciwieństwie do wdrożeń zależnych od struktury, FDEs są specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="3d4ee-110">Ten nowy tryb wdrażania ma wyraźną zaletę tworzenia pliku wykonywalnego zamiast biblioteki, co oznacza, że można uruchomić aplikację bezpośrednio bez wywoływania `dotnet` najpierw.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="3d4ee-111">Podstawowe</span><span class="sxs-lookup"><span data-stu-id="3d4ee-111">Core</span></span>

<span data-ttu-id="3d4ee-112">**Obsługa zdarzeń w usługach środowiska uruchomieniowego**</span><span class="sxs-lookup"><span data-stu-id="3d4ee-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="3d4ee-113">Często można monitorować korzystanie przez aplikację z usług środowiska wykonawczego, takich jak GC, JIT i ThreadPool, aby zrozumieć, jak wpływają one na aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="3d4ee-114">W systemach Windows jest to zwykle wykonywane przez monitorowanie zdarzeń ETW bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="3d4ee-115">Chociaż nadal działa dobrze, nie zawsze jest możliwe użycie ETW, jeśli pracujesz w środowisku o niskich uprawnieniach lub w systemie Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="3d4ee-116">Począwszy od .NET Core 2.2, Zdarzenia CoreCLR <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> można teraz używać przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3d4ee-117">Te zdarzenia opisują zachowanie takich usług środowiska wykonawczego, jak GC, JIT, ThreadPool i interop.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="3d4ee-118">Są to te same zdarzenia, które są udostępniane jako część dostawcy CoreCLR ETW.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="3d4ee-119">Dzięki temu aplikacje do korzystania z tych zdarzeń lub użyć mechanizmu transportu, aby wysłać je do usługi agregacji telemetrii.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="3d4ee-120">Możesz zobaczyć, jak subskrybować zdarzenia w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="3d4ee-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="3d4ee-121">Ponadto .NET Core 2.2 dodaje następujące dwie <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> właściwości do klasy, aby zapewnić dodatkowe informacje o zdarzeniach ETW:</span><span class="sxs-lookup"><span data-stu-id="3d4ee-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="3d4ee-122">Dane</span><span class="sxs-lookup"><span data-stu-id="3d4ee-122">Data</span></span>

<span data-ttu-id="3d4ee-123">**Uwierzytelnianie AAD w bazach danych SQL Azure za pomocą właściwości SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="3d4ee-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="3d4ee-124">Począwszy od platformy .NET Core 2.2 token dostępu wystawiony przez usługę Azure Active Directory może służyć do uwierzytelniania w bazie danych SQL platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="3d4ee-125">Aby obsługiwać tokeny <xref:System.Data.SqlClient.SqlConnection.AccessToken> dostępu, właściwość <xref:System.Data.SqlClient.SqlConnection> została dodana do klasy.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="3d4ee-126">Aby skorzystać z uwierzytelniania AAD, pobierz wersję 4.6 pakietu System.Data.SqlClient NuGet.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="3d4ee-127">Aby korzystać z tej funkcji, można uzyskać wartość tokenu dostępu przy użyciu [biblioteki uwierzytelniania usługi Active Directory dla platformy .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawartej w pakiecie [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="3d4ee-128">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="3d4ee-128">JIT compiler improvements</span></span>

<span data-ttu-id="3d4ee-129">**Kompilacja warstwowa pozostaje funkcją opt-in**</span><span class="sxs-lookup"><span data-stu-id="3d4ee-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="3d4ee-130">W .NET Core 2.1 kompilator JIT zaimplementował nową technologię kompilatora, *kompilację warstwową*, jako funkcję opt-in.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="3d4ee-131">Celem kompilacji warstwowej jest zwiększona wydajność.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="3d4ee-132">Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="3d4ee-133">W przypadku mało używanych ścieżek kodu kompilator może jednak poświęcić więcej czasu na optymalizację kodu niż środowisko wykonawcze spędza wykonywanie nieoptymalizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="3d4ee-134">Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="3d4ee-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="3d4ee-135">**Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="3d4ee-136">**Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="3d4ee-137">Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="3d4ee-138">Aby uzyskać informacje na temat poprawy wydajności, która może wynikać z kompilacji warstwowej, zobacz [Ogłaszanie .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="3d4ee-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="3d4ee-139">W .NET Core 2.2 Preview 2 kompilacja warstwowa została domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="3d4ee-140">Jednak zdecydowaliśmy, że nadal nie jesteśmy gotowi, aby włączyć kompilacji warstwowej domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="3d4ee-141">Tak więc w .NET Core 2.2 kompilacja warstwowa nadal jest funkcją opt-in.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="3d4ee-142">Aby uzyskać informacje na temat wyrażenia zgody na kompilację warstwową, zobacz [ulepszenia kompilatora Jit](dotnet-core-2-1.md#jit-compiler-improvements) w [co nowego w programie .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="3d4ee-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="3d4ee-143">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3d4ee-143">Runtime</span></span>

<span data-ttu-id="3d4ee-144">**Wstrzykiwanie kodu przed wykonaniem Main metody**</span><span class="sxs-lookup"><span data-stu-id="3d4ee-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="3d4ee-145">Począwszy od .NET Core 2.2, można użyć haka startowego, aby wstrzyknąć kod przed uruchomieniem metody głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="3d4ee-146">Haki startowe umożliwiają hostowi dostosowanie zachowania aplikacji po ich wdrożeniu bez konieczności ponownej kompilacji lub zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="3d4ee-147">Oczekujemy, że dostawcy hostingu zdefiniują niestandardową konfigurację i zasady, w <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> tym ustawienia, które mogą mieć wpływ na zachowanie obciążenia głównego punktu wejścia, takie jak zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="3d4ee-148">Hak może służyć do konfigurowania śledzenia lub wtrysku telemetrii, skonfigurować wywołania zwrotne do obsługi lub zdefiniować inne zachowanie zależne od środowiska.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="3d4ee-149">Hak jest oddzielony od punktu wejścia, dzięki czemu kod użytkownika nie musi być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="3d4ee-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="3d4ee-150">Aby uzyskać więcej informacji, zobacz [hak uruchamiania hosta.](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md)</span><span class="sxs-lookup"><span data-stu-id="3d4ee-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d4ee-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d4ee-151">See also</span></span>

- [<span data-ttu-id="3d4ee-152">Co nowego w programie .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3d4ee-152">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="3d4ee-153">Co nowego w ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="3d4ee-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="3d4ee-154">Nowe funkcje w EF Core 2.2</span><span class="sxs-lookup"><span data-stu-id="3d4ee-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
