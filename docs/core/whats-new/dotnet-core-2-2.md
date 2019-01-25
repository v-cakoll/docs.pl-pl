---
title: What's new in .NET Core 2.2
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 2.2.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 058e7ee1dc834ff23a9a4aa191f7eaeb1016375c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679780"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="0faba-103">What's new in .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0faba-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="0faba-104">.NET core 2.2 zawiera ulepszenia wdrożenia aplikacji, obsługę zdarzeń dla usługi czasu wykonywania, uwierzytelnianie bazy danych Azure SQL, wydajności kompilatora JIT i iniekcji kodu przed wykonaniem `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="0faba-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="0faba-105">Nowy tryb wdrożenia</span><span class="sxs-lookup"><span data-stu-id="0faba-105">New deployment mode</span></span>

<span data-ttu-id="0faba-106">Począwszy od platformy .NET Core 2.2, można wdrożyć [zależny od struktury plików wykonywalnych](../deploying/index.md#framework-dependent-executables-fde), które są **.exe** plików zamiast **.dll** plików.</span><span class="sxs-lookup"><span data-stu-id="0faba-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="0faba-107">Podobne do wdrożeń zależny od struktury, zależny od struktury plików wykonywalnych (FDE) nadal zależy od obecności udostępniona wersja systemowe programu .NET Core do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="0faba-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="0faba-108">Aplikacja zawiera tylko Twój kod i wszelkie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="0faba-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="0faba-109">W przeciwieństwie do wdrożeń zależny od struktury FDEs są specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="0faba-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="0faba-110">Ten nowy tryb wdrożenia ma różne zalet kompilowania pliku wykonywalnego, zamiast biblioteki, która oznacza, że aplikację można uruchomić bezpośrednio bez wywoływania `dotnet` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="0faba-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="0faba-111">Core</span><span class="sxs-lookup"><span data-stu-id="0faba-111">Core</span></span>

<span data-ttu-id="0faba-112">**Obsługa zdarzeń w usługach środowiska uruchomieniowego**</span><span class="sxs-lookup"><span data-stu-id="0faba-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="0faba-113">Często może chcieć monitorować użycie aplikacji usług środowiska uruchomieniowego, takich jak GC, JIT i puli wątków, aby zrozumieć ich wpływ na aplikację.</span><span class="sxs-lookup"><span data-stu-id="0faba-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="0faba-114"> W systemach Windows zwykle odbywa się przez monitorowanie zdarzeń ETW bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="0faba-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="0faba-115"> Gdy ta w dalszym ciągu działać prawidłowo, nie zawsze jest możliwe użycie funkcji ETW, jeśli pracujesz w środowisku o niskim poziomie uprawnień lub w systemie Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="0faba-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>  

<span data-ttu-id="0faba-116">Począwszy od platformy .NET Core 2.2 zdarzenia CoreCLR teraz mogą być używane przy użyciu <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> klasy.</span><span class="sxs-lookup"><span data-stu-id="0faba-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> class.</span></span> <span data-ttu-id="0faba-117">Zdarzenia te opisują zachowanie środowiska uruchomieniowego usług GC, JIT, puli wątków i współdziałania.</span><span class="sxs-lookup"><span data-stu-id="0faba-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="0faba-118">Są to te same zdarzenia, które części dostawcy funkcji ETW w środowisku CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0faba-118">These are the same events that parts of the CoreCLR ETW provider.</span></span><span data-ttu-id="0faba-119">  Dzięki temu aplikacje mogą pobierać te zdarzenia lub wysyłać je do usługi telemetrii na agregacji za pomocą mechanizmu transportu.</span><span class="sxs-lookup"><span data-stu-id="0faba-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="0faba-120">Można wyświetlić sposób subskrybowania zdarzeń w następującym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="0faba-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="0faba-121">Ponadto platformy .NET Core 2.2 dodaje dwie poniższe właściwości do <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> klasy, aby zapewnić dodatkowe informacje na temat zdarzenia ETW:</span><span class="sxs-lookup"><span data-stu-id="0faba-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="0faba-122">Dane</span><span class="sxs-lookup"><span data-stu-id="0faba-122">Data</span></span>

<span data-ttu-id="0faba-123">**Uwierzytelnianie usługi AAD do baz danych Azure SQL z właściwością SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="0faba-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="0faba-124">Począwszy od platformy .NET Core 2.2 token dostępu wystawiony przez usługę Azure Active Directory może służyć do uwierzytelniania usługi Azure SQL database.</span><span class="sxs-lookup"><span data-stu-id="0faba-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="0faba-125">Do obsługi tokenów dostępu <xref:System.Data.SqlClient.SqlConnection.AccessToken> właściwość została dodana do <xref:System.Data.SqlClient.SqlConnection> klasy.</span><span class="sxs-lookup"><span data-stu-id="0faba-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="0faba-126">Aby móc korzystać z uwierzytelniania usługi AAD, Pobierz pakiet System.Data.SqlClient NuGet w wersji 4.6.</span><span class="sxs-lookup"><span data-stu-id="0faba-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="0faba-127">Aby można było korzystać z funkcji, można uzyskać przy użyciu wartości tokenu dostępu [Active Directory Authentication Library dla platformy .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawarte w [ `Microsoft.IdentityModel.Clients.ActiveDirectory` ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="0faba-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="0faba-128">Ulepszenia kompilatora JIT</span><span class="sxs-lookup"><span data-stu-id="0faba-128">JIT compiler improvements</span></span>

<span data-ttu-id="0faba-129">**Kompilacja warstwowego pozostaje funkcji opcjonalnych**</span><span class="sxs-lookup"><span data-stu-id="0faba-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="0faba-130">W programie .NET Core 2.1 kompilator JIT zaimplementowane nową technologię kompilatora *warstwowego kompilacji*, jako funkcja opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0faba-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="0faba-131">Celem warstwowego kompilacji jest lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="0faba-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="0faba-132">Jedną z ważnych zadania wykonywane przez kompilator JIT jest zoptymalizowanie wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="0faba-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="0faba-133">Jednak dla ścieżek kodu rzadko używanych kompilator może poświęcić więcej czasu na optymalizację kodu niż środowisko uruchomieniowe zużywa do wykonania kodu w sposób niezoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="0faba-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="0faba-134">Kompilacja warstwowego wprowadzono dwa etapów w ramach kompilacji JIT:</span><span class="sxs-lookup"><span data-stu-id="0faba-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="0faba-135">A **najpierw warstwy**, która generuje kod tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="0faba-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="0faba-136">A **Druga warstwa**, która generuje zoptymalizowanego kodu dla tych metod, które są często wykonywane.</span><span class="sxs-lookup"><span data-stu-id="0faba-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="0faba-137">Druga warstwa kompilacji odbywa się w sposób równoległy, aby uzyskać lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="0faba-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="0faba-138">Aby uzyskać informacje na zwiększenie wydajności, który może wynikać z warstwową kompilacji, zobacz [Announcing .NET Core 2.2 w wersji zapoznawczej 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="0faba-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> 

<span data-ttu-id="0faba-139">W .NET Core 2.2 w wersji zapoznawczej 2 warstwowego kompilacji została włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0faba-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="0faba-140">Jednak firma Microsoft decydujesz, czy możemy przystąpić nadal nie umożliwia warstwowego kompilacji domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0faba-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="0faba-141">Dlatego w .NET Core 2.2, warstwowy kompilacji jest nadal funkcji opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="0faba-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="0faba-142">Aby uzyskać informacji na temat zgody na korzystanie z warstwową kompilacji, zobacz [ulepszenia kompilatora Jit](dotnet-core-2-1.md#jit-compiler-improvements) w [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="0faba-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="0faba-143">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0faba-143">Runtime</span></span>

<span data-ttu-id="0faba-144">**Wprowadzanie kodu przed wykonaniem metody Main**</span><span class="sxs-lookup"><span data-stu-id="0faba-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="0faba-145">Począwszy od platformy .NET Core 2.2 umożliwia hook uruchamiania wstrzyknięcie kodu przed uruchomieniem metody Main aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0faba-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="0faba-146">Punkty zaczepienia uruchamiania umożliwiają hosta dostosować zachowanie aplikacji po ich wdrożeniu bez konieczności ponownego kompilowania lub zmienić aplikację.</span><span class="sxs-lookup"><span data-stu-id="0faba-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="0faba-147">Oczekujemy, że dostawcy hostingu, aby zdefiniować niestandardowe konfiguracje i zasady, w tym ustawień, które potencjalnie mieć wpływ na zachowanie obciążenia główny punkt wejścia, takich jak <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="0faba-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="0faba-148">Punkt zaczepienia można skonfigurować iniekcji śledzenia lub dane telemetryczne, skonfiguruj wywołań zwrotnych do obsługi lub zdefiniowanie innych zachowań zależnych od środowiska.</span><span class="sxs-lookup"><span data-stu-id="0faba-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="0faba-149">Punkt zaczepienia jest niezależna od punktu wejścia, dzięki czemu nie trzeba modyfikować kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0faba-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="0faba-150">Zobacz [hook uruchamiania hosta](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0faba-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="0faba-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0faba-151">See also</span></span>

- [<span data-ttu-id="0faba-152">Co nowego w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="0faba-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="0faba-153">What's new in ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0faba-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="0faba-154">Nowe funkcje programu EF Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0faba-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
