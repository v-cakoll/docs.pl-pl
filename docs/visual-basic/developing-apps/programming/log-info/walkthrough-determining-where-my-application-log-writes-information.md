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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353607"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)

Obiekt `My.Application.Log` może zapisywać informacje do kilku odbiorników dzienników. Odbiorniki dzienników są konfigurowane przez plik konfiguracji komputera i mogą zostać zastąpione przez plik konfiguracyjny aplikacji. W tym temacie opisano ustawienia domyślne i sposób określania ustawień aplikacji.

Aby uzyskać więcej informacji na temat domyślnych lokalizacji wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Aby określić odbiorniki my. Application. log

1. Zlokalizuj plik konfiguracji zestawu. Jeśli tworzysz zestaw, możesz uzyskać dostęp do pliku App. config w programie Visual Studio z **Eksplorator rozwiązań**. W przeciwnym razie nazwa pliku konfiguracji jest dołączona do zestawu ". config" i znajduje się w tym samym katalogu, w którym znajduje się zestaw.

    > [!NOTE]
    > Nie każdy zestaw ma plik konfiguracji.

    Plik konfiguracji jest plikiem XML.

2. Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource" znajdującym się w sekcji `<sources>`. Sekcja `<sources>` znajduje się w sekcji `<system.diagnostics>` w sekcji `<configuration>` najwyższego poziomu.

    Jeśli te sekcje nie istnieją, plik konfiguracji komputera może skonfigurować odbiorniki dziennika `My.Application.Log`. W poniższych krokach opisano sposób określania konfiguracji komputera:

    1. Zlokalizuj plik Machine. config komputera. Zazwyczaj znajduje się on w katalogu *systemroot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , gdzie `SystemRoot` jest katalogiem systemu operacyjnego, a `frameworkVersion` to wersja .NET Framework.

        Ustawienia w pliku Machine. config mogą zostać zastąpione przez plik konfiguracyjny aplikacji.

        Jeśli opcjonalne elementy wymienione poniżej nie istnieją, można je utworzyć.

    2. Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource" w sekcji `<sources>`, w sekcji `<system.diagnostics>`, na liście `<configuration>` najwyższego poziomu.

        Jeśli te sekcje nie istnieją, `My.Application.Log` ma tylko domyślne odbiorniki dzienników.

3. Znajdź <`add>` elementy w sekcji <`listeners>`.

     Te elementy Dodaj nazwane odbiorniki dzienników do `My.Application.Log` źródło.

4. Znajdź `<add>` elementy z nazwami odbiorników dziennika w sekcji `<sharedListeners>`, w sekcji `<system.diagnostics>`, w sekcji `<configuration>` najwyższego poziomu.

5. W przypadku wielu typów udostępnionych odbiorników dane inicjujące odbiornika zawierają opis, gdzie odbiornik kieruje dane:

    - Odbiornik <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> zapisuje dane w dzienniku plików zgodnie z opisem we wprowadzeniu.

    - Odbiornik <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> zapisuje informacje w dzienniku zdarzeń komputera określonym przez parametr `initializeData`. Aby wyświetlić dziennik zdarzeń, można użyć **Eksplorator serwera** lub **Podgląd zdarzeń systemu Windows**. Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).

    - Odbiorniki <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisują do pliku określonego w parametrze `initializeData`.

    - Odbiornik <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> zapisuje dane w konsoli wiersza polecenia.

    - Aby uzyskać informacje o tym, gdzie inne typy odbiorników dzienników zapisują informacje, zapoznaj się z dokumentacją tego typu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md)
- [Rozwiązywanie problemów: odbiorcy dzienników](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
