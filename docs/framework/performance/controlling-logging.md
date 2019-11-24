---
title: Kontrolowanie logowania w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 924d209cd1177ffc1702ebe958c58bfc29c22c38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447677"
---
# <a name="controlling-net-framework-logging"></a>Kontrolowanie logowania w programie .NET Framework

Śledzenia zdarzeń systemu Windows (ETW) można użyć do rejestrowania zdarzeń środowiska uruchomieniowego języka wspólnego (CLR). Można tworzyć i przeglądać ślady za pomocą następujących narzędzi:

- The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.

- The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/). For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).

Aby można było przechwytywać informacje o zdarzeniu CLR, dostawca CLR musi być zainstalowany na komputerze. To confirm that the provider is installed, type `logman query providers` at the command prompt. Zostanie wyświetlona lista dostawców. Ta lista powinna zawierać następujący wpis dla dostawcy CLR.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool. Otwórz okno wiersza polecenia jako administrator. Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ). Ten folder zawiera plik CLR-ETW.man. W wierszu polecenia wpisz następujące polecenie, aby zainstalować dostawcę CLR:

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>Przechwytywanie zdarzeń CLR ETW

You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.

Aby włączyć rejestrowanie, użytkownik musi określić trzy rzeczy:

- Dostawca do komunikacji.

- 64-bitowa liczba, która reprezentuje zestaw słów kluczowych. Każde słowo kluczowe reprezentuje zestaw zdarzeń, które dostawca może włączyć. Ta liczba przedstawia połączony zestaw słów kluczowych do włączenia.

- Mała liczba reprezentująca poziom (szczegółowości) rejestrowania. Poziom 1 jest najmniej szczegółowy, a poziom 5 jest najbardziej szczegółowy. Poziom 0 jest domyślny, a jego znaczenie jest specyficzne dla dostawcy.

### <a name="to-capture-clr-etw-events-using-logman"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Logman

1. W wierszu polecenia wpisz polecenie:

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     gdzie:

    - The `-p` parameter identifies the provider GUID.

    - `0x1CCBD` specifies the categories of events that will be raised.

    - `0x5` sets the level of logging (in this case, verbose (5)).

    - The `-ets` parameter instructs Logman to send commands to event tracing sessions.

    - The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.

2. Aby zatrzymać rejestrowanie zdarzeń, wpisz polecenie:

     `logman stop clrevents -ets`

     To polecenie tworzy plik binarny śledzenia o nazwie clrevents.etl.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Xperf

1. W wierszu polecenia wpisz polecenie:

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).

2. Aby zatrzymać śledzenie, wpisz polecenie:

     `Xperf -stop clr`

     To polecenie tworzy plik śledzenia o nazwie clrevents.etl.

## <a name="viewing-clr-etw-events"></a>Wyświetlanie zdarzeń CLR ETW

Aby wyświetlić zdarzenia CLR ETW, należy użyć poleceń wymienionych poniżej. For a description of the events, see [CLR ETW Events](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Tracerpt

- W wierszu polecenia wpisz polecenie:

     `tracerpt clrevents.etl`

     To polecenie tworzy dwa pliki: dumpfile.xml i summary.txt. Plik dumpfile.xml zawiera listę wszystkich zdarzeń, a plik summary.txt zawiera podsumowanie wszystkich zdarzeń.

### <a name="to-view-clr-etw-events-using-xperf"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Xperf

- W wierszu polecenia wpisz polecenie:

     `xperf clrevents.etl`

     To polecenie otwiera podgląd plików Xperf ETL. In this viewer, the CLR events show up in the **Generic Events** view. To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Aby przekonwertować plik etl na plik z wartościami rozdzielanymi przecinkami

- W wierszu polecenia wpisz polecenie:

     `xperf -i clrevents.etl -f clrevents.csv`

     To polecenie powoduje zrzucenie przez narzędzie XPerf zdarzeń do pliku z wartościami rozdzielanymi przecinkami (CSV), który można wyświetlać. Różne zdarzenia mają różne pola, więc ten plik CSV zawiera więcej niż jeden wiersz nagłówka przed danymi. Pierwsze pole w każdym wierszu jest typem zdarzenia wskazującym, który nagłówek powinien być używany do określenia pozostałych pól.

## <a name="see-also"></a>Zobacz także

- [Windows Performance Toolkit](/windows-hardware/test/wpt/)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
