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
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353607"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)

Obiekt `My.Application.Log` może zapisywać informacje do kilku odbiorników dziennika. Detektory dziennika są konfigurowane przez plik konfiguracyjny komputera i mogą zostać zastąpione przez plik konfiguracyjny aplikacji. W tym temacie opisano ustawienia domyślne i sposób określania ustawień aplikacji.

Aby uzyskać więcej informacji na temat domyślnych lokalizacji danych wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Aby określić detektory dla My.Application.Log

1. Zlokalizuj plik konfiguracyjny złożenia. W przypadku tworzenia zestawu można uzyskać dostęp do app.config w programie Visual Studio z **Eksploratora rozwiązań**. W przeciwnym razie nazwa pliku konfiguracji jest nazwą zestawu dołączona do ".config" i znajduje się w tym samym katalogu co zestaw.

    > [!NOTE]
    > Nie każdy zestaw ma plik konfiguracyjny.

    Plik konfiguracyjny jest plikiem XML.

2. Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource", `<sources>` znajdującym się w sekcji. Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.

    Jeśli te sekcje nie istnieją, plik konfiguracyjny `My.Application.Log` komputera może skonfigurować detektory dziennika. W poniższych krokach opisano sposób określania, co definiuje plik konfiguracji komputera:

    1. Znajdź plik machine.config komputera. Zazwyczaj znajduje się w katalogu *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG,* `SystemRoot` gdzie znajduje się katalog `frameworkVersion` systemu operacyjnego i jest wersją programu .NET Framework.

        Ustawienia w pliku machine.config mogą zostać zastąpione przez plik konfiguracyjny aplikacji.

        Jeśli elementy opcjonalne wymienione poniżej nie istnieją, można je utworzyć.

    2. `<listeners>` Zlokalizuj `<source>` sekcję `name` w sekcji z atrybutem `<sources>` "DefaultSource" w sekcji, w `<system.diagnostics>` sekcji, w sekcji najwyższego poziomu. `<configuration>`

        Jeśli te sekcje nie istnieją, a `My.Application.Log` następnie ma tylko domyślne detektory dziennika.

3. Zlokalizuj `add>` elementy <w `listeners>` sekcji <.

     Te elementy dodać nazwane `My.Application.Log` detektory dziennika do źródła.

4. `<add>` Zlokalizuj elementy z nazwami `<sharedListeners>` odbiorników dziennika `<system.diagnostics>` w sekcji, w `<configuration>` sekcji, w sekcji najwyższego poziomu.

5. Dla wielu typów współużytkowników udostępnione dane inicjowania odbiornika zawiera opis, gdzie odbiornik kieruje dane:

    - Odbiornik <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> zapisuje do dziennika plików, zgodnie z opisem we wstępie.

    - Odbiornik <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> zapisuje informacje do dziennika zdarzeń komputera `initializeData` określonego przez parametr. Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podglądu zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [Zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).

    - I <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorniki zapis do pliku `initializeData` określonego w parametrze.

    - Odbiornik <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> zapisuje na konsoli wiersza polecenia.

    - Aby uzyskać informacje o tym, gdzie inne typy detektorów dziennika zapisują informacje, zapoznaj się z dokumentacją tego typu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Porady: wyjątki rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Porady: zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md)
- [Rozwiązywanie problemów: odbiorniki logu](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
