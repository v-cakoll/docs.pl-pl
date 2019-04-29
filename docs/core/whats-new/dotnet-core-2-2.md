---
title: What's new in .NET Core 2.2
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 2.2.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 49a65dd44159e9800f7cf50a1edaa3d9e9b82e47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646790"
---
# <a name="whats-new-in-net-core-22"></a>What's new in .NET Core 2.2

.NET core 2.2 zawiera ulepszenia wdrożenia aplikacji, obsługę zdarzeń dla usługi czasu wykonywania, uwierzytelnianie bazy danych Azure SQL, wydajności kompilatora JIT i iniekcji kodu przed wykonaniem `Main` metody.

## <a name="new-deployment-mode"></a>Nowy tryb wdrożenia

Począwszy od platformy .NET Core 2.2, można wdrożyć [zależny od struktury plików wykonywalnych](../deploying/index.md#framework-dependent-executables-fde), które są **.exe** plików zamiast **.dll** plików. Podobne do wdrożeń zależny od struktury, zależny od struktury plików wykonywalnych (FDE) nadal zależy od obecności udostępniona wersja systemowe programu .NET Core do uruchomienia. Aplikacja zawiera tylko Twój kod i wszelkie zależności innych firm. W przeciwieństwie do wdrożeń zależny od struktury FDEs są specyficzne dla platformy.

Ten nowy tryb wdrożenia ma różne zalet kompilowania pliku wykonywalnego, zamiast biblioteki, która oznacza, że aplikację można uruchomić bezpośrednio bez wywoływania `dotnet` pierwszy.

## <a name="core"></a>Core

**Obsługa zdarzeń w usługach środowiska uruchomieniowego**

Często może chcieć monitorować użycie aplikacji usług środowiska uruchomieniowego, takich jak GC, JIT i puli wątków, aby zrozumieć ich wpływ na aplikację. W systemach Windows zwykle odbywa się przez monitorowanie zdarzeń ETW bieżącego procesu. Gdy ta w dalszym ciągu działać prawidłowo, nie zawsze jest możliwe użycie funkcji ETW, jeśli pracujesz w środowisku o niskim poziomie uprawnień lub w systemie Linux lub macOS. 

Począwszy od platformy .NET Core 2.2 zdarzenia CoreCLR teraz mogą być używane przy użyciu <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> klasy. Zdarzenia te opisują zachowanie środowiska uruchomieniowego usług GC, JIT, puli wątków i współdziałania. Są to te same zdarzenia, które są dostępne w ramach dostawcy funkcji ETW w środowisku CoreCLR.  Dzięki temu aplikacje mogą pobierać te zdarzenia lub wysyłać je do usługi telemetrii na agregacji za pomocą mechanizmu transportu. Można wyświetlić sposób subskrybowania zdarzeń w następującym przykładzie kodu:

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

Ponadto platformy .NET Core 2.2 dodaje dwie poniższe właściwości do <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> klasy, aby zapewnić dodatkowe informacje na temat zdarzenia ETW:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Dane

**Uwierzytelnianie usługi AAD do baz danych Azure SQL z właściwością SqlConnection.AccessToken**

Począwszy od platformy .NET Core 2.2 token dostępu wystawiony przez usługę Azure Active Directory może służyć do uwierzytelniania usługi Azure SQL database. Do obsługi tokenów dostępu <xref:System.Data.SqlClient.SqlConnection.AccessToken> właściwość została dodana do <xref:System.Data.SqlClient.SqlConnection> klasy. Aby móc korzystać z uwierzytelniania usługi AAD, Pobierz pakiet System.Data.SqlClient NuGet w wersji 4.6. Aby można było korzystać z funkcji, można uzyskać przy użyciu wartości tokenu dostępu [Active Directory Authentication Library dla platformy .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) zawarte w [ `Microsoft.IdentityModel.Clients.ActiveDirectory` ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) pakietu NuGet.

## <a name="jit-compiler-improvements"></a>Ulepszenia kompilatora JIT

**Kompilacja warstwowego pozostaje funkcji opcjonalnych**

W programie .NET Core 2.1 kompilator JIT zaimplementowane nową technologię kompilatora *warstwowego kompilacji*, jako funkcja opcjonalna. Celem warstwowego kompilacji jest lepszą wydajność. Jedną z ważnych zadania wykonywane przez kompilator JIT jest zoptymalizowanie wykonywania kodu. Jednak dla ścieżek kodu rzadko używanych kompilator może poświęcić więcej czasu na optymalizację kodu niż środowisko uruchomieniowe zużywa do wykonania kodu w sposób niezoptymalizowany. Kompilacja warstwowego wprowadzono dwa etapów w ramach kompilacji JIT:

- A **najpierw warstwy**, która generuje kod tak szybko, jak to możliwe.

- A **Druga warstwa**, która generuje zoptymalizowanego kodu dla tych metod, które są często wykonywane. Druga warstwa kompilacji odbywa się w sposób równoległy, aby uzyskać lepszą wydajność.

Aby uzyskać informacje na zwiększenie wydajności, który może wynikać z warstwową kompilacji, zobacz [Announcing .NET Core 2.2 w wersji zapoznawczej 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

W .NET Core 2.2 w wersji zapoznawczej 2 warstwowego kompilacji została włączona domyślnie. Jednak firma Microsoft decydujesz, czy możemy przystąpić nadal nie umożliwia warstwowego kompilacji domyślnie. Dlatego w .NET Core 2.2, warstwowy kompilacji jest nadal funkcji opcjonalnych. Aby uzyskać informacji na temat zgody na korzystanie z warstwową kompilacji, zobacz [ulepszenia kompilatora Jit](dotnet-core-2-1.md#jit-compiler-improvements) w [What's new in .NET Core 2.1](dotnet-core-2-1.md).

## <a name="runtime"></a>Środowisko uruchomieniowe

**Wprowadzanie kodu przed wykonaniem metody Main**

Począwszy od platformy .NET Core 2.2 umożliwia hook uruchamiania wstrzyknięcie kodu przed uruchomieniem metody Main aplikacji. Punkty zaczepienia uruchamiania umożliwiają hosta dostosować zachowanie aplikacji po ich wdrożeniu bez konieczności ponownego kompilowania lub zmienić aplikację.

Oczekujemy, że dostawcy hostingu, aby zdefiniować niestandardowe konfiguracje i zasady, w tym ustawień, które potencjalnie mieć wpływ na zachowanie obciążenia główny punkt wejścia, takich jak <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> zachowanie. Punkt zaczepienia można skonfigurować iniekcji śledzenia lub dane telemetryczne, skonfiguruj wywołań zwrotnych do obsługi lub zdefiniowanie innych zachowań zależnych od środowiska. Punkt zaczepienia jest niezależna od punktu wejścia, dzięki czemu nie trzeba modyfikować kodu użytkownika.

Zobacz [hook uruchamiania hosta](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- [Co nowego w programie .NET Core](index.md)
- [What's new in ASP.NET Core 2.2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Nowe funkcje programu EF Core 2.2](/ef/core/what-is-new/ef-core-2.2)
