---
title: Rejestrowanie i śledzenie — .NET Core
description: Wprowadzenie do rejestrowania i śledzenia .NET Core.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714420"
---
# <a name="net-core-logging-and-tracing"></a>Rejestrowanie i śledzenie programu .NET Core

Rejestrowanie i śledzenie są naprawdę dwie nazwy dla tej samej techniki. Prosta technika jest stosowana od wczesnych dni komputerów. Obejmuje po prostu instrumenting aplikacji do zapisu danych wyjściowych do zużycia później.

## <a name="reasons-to-use-logging-and-tracing"></a>Powody używania rejestrowania i śledzenia

Ta prosta technika jest zaskakująco potężna. Może być używany w sytuacjach, gdy debuger nie powiedzie się:

- Problemy występujące przez długi czas, może być trudne do debugowania z tradycyjnym debugerem. Dzienniki pozwalają na szczegółową kontrolę pośmiertną obejmującą długie okresy czasu. Natomiast debuggery są ograniczone do analizy w czasie rzeczywistym.
- Aplikacje wielowątkowe i aplikacje rozproszone są często trudne do debugowania.  Dołączanie debugera ma tendencję do modyfikowania zachowań. Szczegółowe dzienniki mogą być analizowane w razie potrzeby, aby zrozumieć złożone systemy.
- Problemy w aplikacjach rozproszonych mogą wynikać ze złożonej interakcji między wieloma składnikami i może nie być uzasadnione łączenie debugera z każdą częścią systemu.
- Wiele usług nie powinno być wstrzymanych. Dołączanie debugera często powoduje błędy timeout.
- Problemy nie zawsze są przewidziane. Rejestrowanie i śledzenie są przeznaczone dla niskiego narzutów, dzięki czemu programy zawsze mogą nagrywać w przypadku wystąpienia problemu.

## <a name="net-core-apis"></a>Interfejsy API rdzenia .NET

### <a name="print-style-apis"></a>Interfejsy API stylu drukowania

<xref:System.Console?displayProperty=nameWithType>Interfejsy <xref:System.Diagnostics.Trace?displayProperty=nameWithType>API , i <xref:System.Diagnostics.Debug?displayProperty=nameWithType> klasy zapewniają podobne interfejsy API stylu drukowania wygodne do rejestrowania.

Wybór interfejsu API stylu drukowania zależy od Ciebie. Kluczowe różnice to:

- <xref:System.Console?displayProperty=nameWithType>
  - Zawsze włączony i zawsze zapisuje w konsoli.
  - Przydatne informacje, które klient może być konieczne, aby zobaczyć w wydaniu.
  - Ponieważ jest to najprostsze podejście, jest często używany do tymczasowego debugowania ad hoc. Ten kod debugowania często nigdy nie jest zaewidencjonowany do kontroli źródła.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Włączone tylko `TRACE` wtedy, gdy jest zdefiniowana.
  - Zapisuje do <xref:System.Diagnostics.Trace.Listeners>dołączonego , <xref:System.Diagnostics.DefaultTraceListener>domyślnie .
  - Użyj tego interfejsu API podczas tworzenia dzienników, które będą włączone w większości kompilacji.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Włączone tylko `DEBUG` wtedy, gdy jest zdefiniowana.
  - Zapisuje do dołączonego debugera.
  - Na `*nix` zapisuje do stderr jeśli `COMPlus_DebugWriteToStdErr` jest ustawiona.
  - Użyj tego interfejsu API podczas tworzenia dzienników, które będą włączone tylko w kompilacjach debugowania.

### <a name="logging-events"></a>Rejestrowanie zdarzeń

Następujące interfejsy API są bardziej zorientowane na zdarzenia. Zamiast rejestrowania prostych ciągów rejestrują obiekty zdarzeń.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource jest głównym głównym interfejsem API śledzenia .NET Core.
  - Dostępne we wszystkich wersjach .NET Standard.
  - Umożliwia tylko śledzenie obiektów serializable.
  - Zapisuje do dołączonego [odbiornika zdarzeń](xref:System.Diagnostics.Tracing.EventListener).
  - Program .NET Core udostępnia odbiorniki dla:
    - Usługa EventPipe programu .NET Core na wszystkich platformach
    - [Śledzenie zdarzeń dla systemu Windows (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Struktura śledzenia LTTng dla systemu Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Zawarte w .NET Core i jako [pakiet NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) dla .NET Framework.
  - Umożliwia śledzenie obiektów nieseryjnych w procesie.
  - Zawiera mostek umożliwiający zapisanie wybranych pól zarejestrowanych obiektów w pliku <xref:System.Diagnostics.Tracing.EventSource>.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Zapewnia ostateczny sposób identyfikowania komunikatów dziennika wynikających z określonego działania lub transakcji. Ten obiekt może służyć do skorelowania dzienników w różnych usługach.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Tylko w systemie Windows.
  - Zapisuje wiadomości w dzienniku zdarzeń systemu Windows.
  - Administratorzy systemu oczekują, że w dzienniku zdarzeń systemu Windows pojawią się komunikaty o błędach aplikacji krytycznych.

## <a name="ilogger-and-logging-frameworks"></a>Platformy ILogger i rejestrowania

Interfejsy API niskiego poziomu mogą nie być właściwym wyborem dla potrzeb rejestrowania. Warto rozważyć struktury rejestrowania.

Interfejs <xref:Microsoft.Extensions.Logging.ILogger> został użyty do utworzenia wspólnego interfejsu rejestrowania, w którym rejestratory mogą być wstawiane za pomocą iniekcji zależności.

Na przykład, aby umożliwić dokonanie najlepszego `ASP.NET` wyboru dla aplikacji oferuje obsługę dla wyboru wbudowanych i innych platform:

- [ASP.NET wbudowanych dostawców rejestrowania](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET zewnętrzni dostawcy usług rejestrowania](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Rejestrowanie odwołań pokrewnych

- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Porady: dodawanie instrukcji śledzenia do kodu aplikacji](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET rejestrowanie](/aspnet/core/fundamentals/logging) zawiera przegląd technik rejestrowania, które obsługuje.

- [Interpolacja ciągów C#](../../csharp/language-reference/tokens/interpolated.md) może uprościć pisanie kodu rejestrowania.

- Właściwość <xref:System.Exception.Message?displayProperty=nameWithType> jest przydatna do rejestrowania wyjątków.

- Klasa <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> może być przydatne do podania informacji stosu w dziennikach.

## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności

Formatowanie ciągów może zająć zauważalny czas przetwarzania procesora CPU.

W aplikacjach o krytycznym znaczeniu dla wydajności zaleca się:

- Unikaj dużej ilości rejestrowania, gdy nikt nie słucha. Unikaj konstruowania kosztownych komunikatów rejestrowania, sprawdzając, czy rejestrowanie jest włączone jako pierwsze.
- Rejestruj tylko to, co jest przydatne.
- Odroczyć fantazyjne formatowanie do etapu analizy.
