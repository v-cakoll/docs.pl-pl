---
title: Co nowego w programie .NET Core 2.2
description: Dowiedz się więcej o nowych funkcjach, które można znaleźć w .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156585"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="2fdf1-103">Co nowego w programie .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2fdf1-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="2fdf1-104">.NET Core 2.2 zawiera ulepszenia we wdrażaniu aplikacji, obsłudze zdarzeń dla usług wykonawczych, uwierzytelnianiu baz danych `Main` SQL platformy Azure, wydajności kompilatora JIT i iniekcji kodu przed wykonaniem metody.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="2fdf1-105">Nowy tryb wdrażania</span><span class="sxs-lookup"><span data-stu-id="2fdf1-105">New deployment mode</span></span>

<span data-ttu-id="2fdf1-106">Począwszy od .NET Core 2.2, można wdrożyć [pliki wykonywalne zależne od struktury,](../deploying/index.md#publish-runtime-dependent)które są plikami **exe** zamiast plikami **dll.**</span><span class="sxs-lookup"><span data-stu-id="2fdf1-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-runtime-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="2fdf1-107">Funkcjonalnie podobne do wdrożeń zależnych od struktury, pliki wykonywalne zależne od struktury (FDE) nadal polegają na obecności udostępnionej wersji programu .NET Core do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="2fdf1-108">Aplikacja zawiera tylko kod i wszelkie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="2fdf1-109">W przeciwieństwie do wdrożeń zależnych od struktury fdes są specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="2fdf1-110">Ten nowy tryb wdrażania ma wyraźną zaletę tworzenia pliku wykonywalnego zamiast biblioteki, co oznacza, że można uruchomić aplikację bezpośrednio bez uprzedniego wywoływania. `dotnet`</span><span class="sxs-lookup"><span data-stu-id="2fdf1-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="2fdf1-111">Podstawowe</span><span class="sxs-lookup"><span data-stu-id="2fdf1-111">Core</span></span>

<span data-ttu-id="2fdf1-112">**Obsługa zdarzeń w usługach wykonywania**</span><span class="sxs-lookup"><span data-stu-id="2fdf1-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="2fdf1-113">Często można monitorować korzystanie z usług wykonywania aplikacji, takich jak GC, JIT i ThreadPool, aby zrozumieć, jak wpływają one na aplikację.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="2fdf1-114">W systemach Windows jest to często wykonywane przez monitorowanie zdarzeń ETW bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="2fdf1-115">Chociaż nadal działa to dobrze, nie zawsze jest możliwe użycie ETW, jeśli korzystasz w środowisku o niskich uprawnieniach lub w systemie Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="2fdf1-116">Począwszy od .NET Core 2.2, CoreCLR zdarzenia <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> mogą być teraz używane przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2fdf1-117">Zdarzenia te opisują zachowanie takich usług w czasie wykonywania, takich jak GC, JIT, ThreadPool i interop.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="2fdf1-118">Są to te same zdarzenia, które są udostępniane jako część dostawcy CoreCLR ETW.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="2fdf1-119">Dzięki temu aplikacje do korzystania z tych zdarzeń lub użyć mechanizmu transportu, aby wysłać je do usługi agregacji telemetrii.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="2fdf1-120">Możesz zobaczyć, jak subskrybować zdarzenia w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="2fdf1-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="2fdf1-121">Ponadto .NET Core 2.2 dodaje następujące dwie <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> właściwości do klasy, aby zapewnić dodatkowe informacje o zdarzeniach ETW:</span><span class="sxs-lookup"><span data-stu-id="2fdf1-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="2fdf1-122">Dane</span><span class="sxs-lookup"><span data-stu-id="2fdf1-122">Data</span></span>

<span data-ttu-id="2fdf1-123">**Uwierzytelnianie usługi AAD do baz danych SQL platformy Azure z właściwością SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="2fdf1-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="2fdf1-124">Począwszy od .NET Core 2.2, token dostępu wystawiony przez usługę Azure Active Directory może służyć do uwierzytelniania w bazie danych SQL platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="2fdf1-125">Aby obsługiwać tokeny <xref:System.Data.SqlClient.SqlConnection.AccessToken> dostępu, właściwość została <xref:System.Data.SqlClient.SqlConnection> dodana do klasy.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="2fdf1-126">Aby skorzystać z uwierzytelniania usługi AAD, pobierz wersję 4.6 pakietu System.Data.SqlClient NuGet.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="2fdf1-127">Aby korzystać z tej funkcji, można uzyskać wartość tokenu dostępu przy użyciu [biblioteki uwierzytelniania usługi Active Directory dla .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawartej w pakiecie [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="2fdf1-128">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="2fdf1-128">JIT compiler improvements</span></span>

<span data-ttu-id="2fdf1-129">**Kompilacja warstwowa pozostaje funkcją opt-in**</span><span class="sxs-lookup"><span data-stu-id="2fdf1-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="2fdf1-130">W .NET Core 2.1 kompilator JIT zaimplementował nową technologię kompilatora, *kompilację warstwową*, jako funkcję opt-in.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="2fdf1-131">Celem kompilacji warstwowej jest zwiększona wydajność.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="2fdf1-132">Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonania kodu.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="2fdf1-133">W przypadku mało używanych ścieżek kodu kompilator może poświęcić więcej czasu na optymalizację kodu niż czas wykonywania spędza na wykonywaniu niezoptymalizowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="2fdf1-134">Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="2fdf1-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="2fdf1-135">**Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="2fdf1-136">**Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są często wykonywane.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="2fdf1-137">Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="2fdf1-138">Aby uzyskać informacje na temat poprawy wydajności, która może wynikać z kompilacji warstwowej, zobacz [Ogłaszanie .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="2fdf1-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="2fdf1-139">W .NET Core 2.2 Preview 2 kompilacja warstwowa została domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="2fdf1-140">Jednak zdecydowaliśmy, że nadal nie jesteśmy gotowi, aby domyślnie włączyć kompilację warstwową.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="2fdf1-141">Tak więc w .NET Core 2.2 kompilacja warstwowa nadal jest funkcją opt-in.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="2fdf1-142">Aby uzyskać informacje na temat optowania kompilacji warstwowej, zobacz [Ulepszenia kompilatora Jit](dotnet-core-2-1.md#jit-compiler-improvements) w [What's New w .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="2fdf1-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="2fdf1-143">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2fdf1-143">Runtime</span></span>

<span data-ttu-id="2fdf1-144">**Wstrzykiwanie kodu przed wykonaniem Metody Głównej**</span><span class="sxs-lookup"><span data-stu-id="2fdf1-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="2fdf1-145">Począwszy od .NET Core 2.2, można użyć haka startowego, aby wstrzyknąć kod przed uruchomieniem metody głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="2fdf1-146">Haki uruchamiania umożliwiają hostowi dostosowanie zachowania aplikacji po ich wdrożeniu bez konieczności ponownej kompilacji lub zmiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="2fdf1-147">Oczekujemy, że dostawcy hostingu zdefiniować konfigurację niestandardową i zasady, w <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> tym ustawienia, które potencjalnie wpływają na zachowanie obciążenia głównego punktu wejścia, takie jak zachowanie.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="2fdf1-148">Hak może służyć do konfigurowania śledzenia lub iniekcji telemetrii, do konfigurowania wywołań wywołania wstecznego do obsługi lub do definiowania innych zachowań zależnych od środowiska.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="2fdf1-149">Hak jest oddzielony od punktu wejścia, dzięki czemu kod użytkownika nie musi być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="2fdf1-150">Zobacz [Hak uruchamiania hosta,](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="2fdf1-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fdf1-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fdf1-151">See also</span></span>

- [<span data-ttu-id="2fdf1-152">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="2fdf1-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="2fdf1-153">Co nowego w ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2fdf1-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="2fdf1-154">Nowe funkcje ef core 2.2</span><span class="sxs-lookup"><span data-stu-id="2fdf1-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
