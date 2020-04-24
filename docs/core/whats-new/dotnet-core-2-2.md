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
# <a name="whats-new-in-net-core-22"></a>Co nowego w programie .NET Core 2.2

.NET Core 2.2 zawiera ulepszenia we wdrażaniu aplikacji, obsługa zdarzeń dla usług środowiska wykonawczego, uwierzytelnianie w bazach `Main` danych SQL platformy Azure, wydajność kompilatora JIT i iniekcję kodu przed wykonaniem metody.

## <a name="new-deployment-mode"></a>Nowy tryb wdrażania

Począwszy od programu .NET Core 2.2, można wdrażać [pliki wykonywalne zależne od struktury](../deploying/index.md#publish-runtime-dependent), które są plikami **exe** zamiast plików **dll.** Funkcjonalnie podobne do wdrożeń zależnych od struktury, pliki wykonywalne zależne od struktury (FDE) nadal opierają się na obecności udostępnionej wersji systemu .NET Core do uruchomienia. Aplikacja zawiera tylko kod i wszelkie zależności innych firm. W przeciwieństwie do wdrożeń zależnych od struktury, FDEs są specyficzne dla platformy.

Ten nowy tryb wdrażania ma wyraźną zaletę tworzenia pliku wykonywalnego zamiast biblioteki, co oznacza, że można uruchomić aplikację bezpośrednio bez wywoływania `dotnet` najpierw.

## <a name="core"></a>Podstawowe

**Obsługa zdarzeń w usługach środowiska uruchomieniowego**

Często można monitorować korzystanie przez aplikację z usług środowiska wykonawczego, takich jak GC, JIT i ThreadPool, aby zrozumieć, jak wpływają one na aplikację.W systemach Windows jest to zwykle wykonywane przez monitorowanie zdarzeń ETW bieżącego procesu.Chociaż nadal działa dobrze, nie zawsze jest możliwe użycie ETW, jeśli pracujesz w środowisku o niskich uprawnieniach lub w systemie Linux lub macOS.

Począwszy od .NET Core 2.2, Zdarzenia CoreCLR <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> można teraz używać przy użyciu klasy. Te zdarzenia opisują zachowanie takich usług środowiska wykonawczego, jak GC, JIT, ThreadPool i interop. Są to te same zdarzenia, które są udostępniane jako część dostawcy CoreCLR ETW.Dzięki temu aplikacje do korzystania z tych zdarzeń lub użyć mechanizmu transportu, aby wysłać je do usługi agregacji telemetrii. Możesz zobaczyć, jak subskrybować zdarzenia w poniższym przykładzie kodu:

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

Ponadto .NET Core 2.2 dodaje następujące dwie <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> właściwości do klasy, aby zapewnić dodatkowe informacje o zdarzeniach ETW:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Dane

**Uwierzytelnianie AAD w bazach danych SQL Azure za pomocą właściwości SqlConnection.AccessToken**

Począwszy od platformy .NET Core 2.2 token dostępu wystawiony przez usługę Azure Active Directory może służyć do uwierzytelniania w bazie danych SQL platformy Azure. Aby obsługiwać tokeny <xref:System.Data.SqlClient.SqlConnection.AccessToken> dostępu, właściwość <xref:System.Data.SqlClient.SqlConnection> została dodana do klasy. Aby skorzystać z uwierzytelniania AAD, pobierz wersję 4.6 pakietu System.Data.SqlClient NuGet. Aby korzystać z tej funkcji, można uzyskać wartość tokenu dostępu przy użyciu [biblioteki uwierzytelniania usługi Active Directory dla platformy .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawartej w pakiecie [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet.

## <a name="jit-compiler-improvements"></a>Ulepszenia kompilatora JIT

**Kompilacja warstwowa pozostaje funkcją opt-in**

W .NET Core 2.1 kompilator JIT zaimplementował nową technologię kompilatora, *kompilację warstwową*, jako funkcję opt-in. Celem kompilacji warstwowej jest zwiększona wydajność. Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu. W przypadku mało używanych ścieżek kodu kompilator może jednak poświęcić więcej czasu na optymalizację kodu niż środowisko wykonawcze spędza wykonywanie nieoptymalizowanego kodu. Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:

- **Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.

- **Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często. Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.

Aby uzyskać informacje na temat poprawy wydajności, która może wynikać z kompilacji warstwowej, zobacz [Ogłaszanie .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

W .NET Core 2.2 Preview 2 kompilacja warstwowa została domyślnie włączona. Jednak zdecydowaliśmy, że nadal nie jesteśmy gotowi, aby włączyć kompilacji warstwowej domyślnie. Tak więc w .NET Core 2.2 kompilacja warstwowa nadal jest funkcją opt-in. Aby uzyskać informacje na temat wyrażenia zgody na kompilację warstwową, zobacz [ulepszenia kompilatora Jit](dotnet-core-2-1.md#jit-compiler-improvements) w [co nowego w programie .NET Core 2.1](dotnet-core-2-1.md).

## <a name="runtime"></a>Środowisko uruchomieniowe

**Wstrzykiwanie kodu przed wykonaniem Main metody**

Począwszy od .NET Core 2.2, można użyć haka startowego, aby wstrzyknąć kod przed uruchomieniem metody głównej aplikacji. Haki startowe umożliwiają hostowi dostosowanie zachowania aplikacji po ich wdrożeniu bez konieczności ponownej kompilacji lub zmiany aplikacji.

Oczekujemy, że dostawcy hostingu zdefiniują niestandardową konfigurację i zasady, w <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> tym ustawienia, które mogą mieć wpływ na zachowanie obciążenia głównego punktu wejścia, takie jak zachowanie. Hak może służyć do konfigurowania śledzenia lub wtrysku telemetrii, skonfigurować wywołania zwrotne do obsługi lub zdefiniować inne zachowanie zależne od środowiska. Hak jest oddzielony od punktu wejścia, dzięki czemu kod użytkownika nie musi być modyfikowany.

Aby uzyskać więcej informacji, zobacz [hak uruchamiania hosta.](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md)

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie .NET Core 3.1](dotnet-core-3-1.md)
- [Co nowego w ASP.NET Core 2.2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Nowe funkcje w EF Core 2.2](/ef/core/what-is-new/ef-core-2.2)
