---
title: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 00b543dbe96ca99446f6797a13b66ee62c422b93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398282"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)

`My.Application.Log`Obiekt może zapisywać informacje w kilku detektorach dzienników. Odbiorniki dzienników są konfigurowane przez plik konfiguracji komputera i mogą zostać zastąpione przez plik konfiguracyjny aplikacji. W tym temacie opisano ustawienia domyślne i sposób określania ustawień aplikacji.

Aby uzyskać więcej informacji na temat domyślnych lokalizacji wyjściowych, zobacz [Praca z dziennikami aplikacji](working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Aby określić odbiorniki my. Application. log

1. Zlokalizuj plik konfiguracji zestawu. Jeśli tworzysz zestaw, możesz uzyskać dostęp do pliku App. config w programie Visual Studio z **Eksplorator rozwiązań**. W przeciwnym razie nazwa pliku konfiguracji jest dołączona do zestawu ". config" i znajduje się w tym samym katalogu, w którym znajduje się zestaw.

    > [!NOTE]
    > Nie każdy zestaw ma plik konfiguracji.

    Plik konfiguracji jest plikiem XML.

2. Znajdź `<listeners>` sekcję w sekcji `<source>` z `name` atrybutem "DefaultSource", który znajduje się w `<sources>` sekcji. Sekcja znajduje się `<sources>` w `<system.diagnostics>` sekcji w sekcji najwyższego poziomu `<configuration>` .

    Jeśli te sekcje nie istnieją, plik konfiguracji komputera może skonfigurować `My.Application.Log` odbiorniki dzienników. W poniższych krokach opisano sposób określania konfiguracji komputera:

    1. Zlokalizuj plik Machine. config komputera. Zazwyczaj znajduje się on w katalogu *systemroot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , gdzie `SystemRoot` jest katalogiem systemu operacyjnego i `frameworkVersion` jest wersją .NET Framework.

        Ustawienia w pliku Machine. config mogą zostać zastąpione przez plik konfiguracyjny aplikacji.

        Jeśli opcjonalne elementy wymienione poniżej nie istnieją, można je utworzyć.

    2. Znajdź sekcję w sekcji `<listeners>` `<source>` z `name` atrybutem "DefaultSource" w sekcji, w sekcji `<sources>` `<system.diagnostics>` , w sekcji najwyższego poziomu `<configuration>` .

        Jeśli te sekcje nie istnieją, `My.Application.Log` mają tylko domyślne odbiorniki dzienników.

3. Znajdź <`add>` elementy w `listeners>` sekcji <.

     Te elementy dodają nazwane odbiorniki dzienników do `My.Application.Log` źródła.

4. W sekcji `<add>` `<sharedListeners>` `<system.diagnostics>` najwyższego poziomu Znajdź elementy z nazwami odbiorników dziennika w sekcji `<configuration>` .

5. W przypadku wielu typów udostępnionych odbiorników dane inicjujące odbiornika zawierają opis, gdzie odbiornik kieruje dane:

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>Odbiornik zapisuje dane w dzienniku plików zgodnie z opisem we wprowadzeniu.

    - <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>Odbiornik zapisuje informacje do dziennika zdarzeń komputera określonego przez `initializeData` parametr. Aby wyświetlić dziennik zdarzeń, można użyć **Eksplorator serwera** lub **Podgląd zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>I <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorniki zapisują w pliku określonym w `initializeData` parametrze.

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>Odbiornik zapisuje dane w konsoli wiersza polecenia.

    - Aby uzyskać informacje o tym, gdzie inne typy odbiorników dzienników zapisują informacje, zapoznaj się z dokumentacją tego typu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](how-to-log-exceptions.md)
- [Instrukcje: zapisywanie komunikatów dziennika](how-to-write-log-messages.md)
- [Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-changing-where-my-application-log-writes-information.md)
- [Zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md)
- [Rozwiązywanie problemów: odbiorcy dzienników](troubleshooting-log-listeners.md)
