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
# <a name="whats-new-in-net-core-22"></a>Co nowego w programie .NET Core 2.2

Program .NET Core 2,2 zawiera usprawnienia wdrażania aplikacji, obsługi zdarzeń dla usług środowiska uruchomieniowego, uwierzytelniania do baz danych Azure SQL, wydajności kompilatora JIT i iniekcji kodu przed wykonaniem metody `Main`.

## <a name="new-deployment-mode"></a>Nowy tryb wdrażania

Począwszy od platformy .NET Core 2,2, można wdrożyć pliki [wykonywalne zależne od platformy](../deploying/index.md#publish-runtime-dependent), które są plikami **exe** zamiast plików **dll** . Funkcje podobne do wdrożeń zależnych od platformy, zależne od struktury pliki wykonywalne (całego) nadal polegają na obecności udostępnionej wersji systemu .NET Core do uruchomienia. Aplikacja zawiera tylko kod i wszystkie zależności innych firm. W przeciwieństwie do wdrożeń zależnych od struktury FDEs są specyficzne dla platformy.

Ten nowy tryb wdrożenia ma odrębną zaletę kompilowania pliku wykonywalnego zamiast biblioteki, co oznacza, że można uruchomić aplikację bezpośrednio bez wywoływania `dotnet`.

## <a name="core"></a>Podstawowe

**Obsługa zdarzeń w usługach środowiska uruchomieniowego**

Często warto monitorować użycie usług środowiska uruchomieniowego w aplikacji, takich jak GC, JIT i wątków, aby zrozumieć, jak wpływają na aplikację.W systemach Windows jest to zwykle wykonywane przez monitorowanie zdarzeń ETW bieżącego procesu.Mimo że ta funkcja nadal działa, nie zawsze jest możliwe korzystanie z funkcji ETW, jeśli jest uruchomiona w środowisku z niskim poziomem uprawnień lub w systemie Linux lub macOS.

Począwszy od platformy .NET Core 2,2, zdarzenia CoreCLR można teraz wykorzystać przy użyciu klasy <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType>. Te zdarzenia opisują zachowanie takich usług w czasie wykonywania jak GC, JIT, wątków i międzyoperacyjności. Są to te same zdarzenia, które są ujawniane w ramach dostawcy ETW CoreCLR.Dzięki temu aplikacje mogą zużywać te zdarzenia lub korzystać z mechanizmu transportu w celu wysyłania ich do usługi agregacji telemetrii. Możesz zobaczyć, jak subskrybować zdarzenia w następującym przykładzie kodu:

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

Ponadto program .NET Core 2,2 dodaje następujące dwie właściwości do klasy <xref:System.Diagnostics.Tracing.EventWrittenEventArgs>, aby uzyskać dodatkowe informacje na temat zdarzeń ETW:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Dane

**Uwierzytelnianie w usłudze AAD w bazach danych Azure SQL przy użyciu właściwości SQLConnection. AccessToken**

Począwszy od platformy .NET Core 2,2, token dostępu wystawiony przez Azure Active Directory może służyć do uwierzytelniania w usłudze Azure SQL Database. Aby można było obsługiwać tokeny dostępu, właściwość <xref:System.Data.SqlClient.SqlConnection.AccessToken> została dodana do klasy <xref:System.Data.SqlClient.SqlConnection>. Aby skorzystać z uwierzytelniania w usłudze AAD, Pobierz wersję 4,6 pakietu NuGet system. Data. SqlClient. Aby skorzystać z tej funkcji, można uzyskać wartość tokenu dostępu przy użyciu [Active Directory Authentication Library dla platformy .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawartej w pakiecie NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) .

## <a name="jit-compiler-improvements"></a>Udoskonalenia kompilatora JIT

**Kompilacja warstwowa pozostaje funkcją wyboru**

W programie .NET Core 2,1 kompilator JIT zaimplementował nową technologię kompilatora, *kompilację warstwową*jako funkcję wyboru. Celem kompilacji warstwowej jest zwiększona wydajność. Jednym z ważnych zadań wykonywanych przez kompilator JIT jest optymalizacja wykonywania kodu. Jednak w przypadku niewielkich ścieżek kodu kompilator może poświęcać więcej czasu na optymalizację kodu niż środowisko uruchomieniowe poświęca na wykonywanie niezoptymalizowanego kodu. Kompilacja warstwowa wprowadza dwa etapy kompilacji JIT:

- **Pierwsza warstwa**, która generuje kod tak szybko, jak to możliwe.

- **Druga warstwa**, która generuje zoptymalizowany kod dla tych metod, które są wykonywane często. Druga warstwa kompilacji jest wykonywana równolegle w celu zwiększenia wydajności.

Aby uzyskać informacje na temat poprawy wydajności, która może wynikać z kompilacji warstwowej, zobacz temat [ogłaszanie programu .NET Core 2,2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

W programie .NET Core 2,2 w wersji zapoznawczej 2 kompilacja warstwowa została włączona domyślnie. Jednak firma Microsoft zdecydowała się, że nadal nie możesz domyślnie włączyć kompilacji warstwowej. Dlatego w przypadku platformy .NET Core 2,2 kompilacja warstwowa nadal jest funkcją wyboru. Aby uzyskać informacje o tym, jak przeprowadzić kompilację warstwową, zobacz [udoskonalenia kompilatora JIT](dotnet-core-2-1.md#jit-compiler-improvements) w artykule [co nowego w programie .NET Core 2,1](dotnet-core-2-1.md).

## <a name="runtime"></a>Środowisko uruchomieniowe

**Wprowadzanie kodu przed wykonaniem metody Main**

Począwszy od platformy .NET Core 2,2, można użyć punktu zaczepienia uruchomienia, aby wstrzyknąć kod przed uruchomieniem głównej metody aplikacji. Punkty zaczepienia uruchomienia umożliwiają hostowi dostosowanie zachowania aplikacji po ich wdrożeniu bez konieczności ponownego kompilowania lub zmiany aplikacji.

Oczekujemy, że dostawcy hostingu definiują niestandardową konfigurację i zasady, w tym ustawienia, które mogą mieć wpływ na zachowanie ładowania głównego punktu wejścia, takie jak <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> zachowanie. Punkt zaczepienia może służyć do konfigurowania iniekcji lub wstrzykiwania danych telemetrycznych, konfigurowania wywołań zwrotnych do obsługi lub definiowania innych zachowań zależnych od środowiska. Punkt zaczepienia jest oddzielony od punktu wejścia, dzięki czemu kod użytkownika nie musi być modyfikowany.

Aby uzyskać więcej informacji, zobacz punkt [zaczepienia uruchamiania hosta](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) .

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie .NET Core](index.md)
- [Co nowego w ASP.NET Core 2,2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Nowe funkcje w EF Core 2,2](/ef/core/what-is-new/ef-core-2.2)
