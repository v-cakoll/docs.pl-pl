---
title: Kontrolowanie logowania w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: e7d7d6e60b2f582a579f5811225f4027c37c7876
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504099"
---
# <a name="controlling-net-framework-logging"></a>Kontrolowanie logowania w programie .NET Framework

Śledzenia zdarzeń systemu Windows (ETW) można użyć do rejestrowania zdarzeń środowiska uruchomieniowego języka wspólnego (CLR). Można tworzyć i przeglądać ślady za pomocą następujących narzędzi:

- Narzędzia wiersza polecenia [logman](/windows-server/administration/windows-commands/logman) i [tracerpt](/windows-server/administration/windows-commands/tracerpt_1) dołączone do systemu operacyjnego Windows.

- Narzędzia [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) w zestawie narzędzi [wydajności systemu Windows](/windows-hardware/test/wpt/). Aby uzyskać więcej informacji na temat Xperf, zobacz [blog wydajności systemu Windows](https://docs.microsoft.com/archive/blogs/pigscanfly/).

Aby można było przechwytywać informacje o zdarzeniu CLR, dostawca CLR musi być zainstalowany na komputerze. Aby upewnić się, że dostawca jest zainstalowany, wpisz `logman query providers` w wierszu polecenia. Zostanie wyświetlona lista dostawców. Ta lista powinna zawierać następujący wpis dla dostawcy CLR.

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

Jeśli dostawcy CLR nie ma na liście, można go zainstalować w systemie Windows Vista i nowszych systemach operacyjnych przy użyciu narzędzia wiersza polecenia [wevtutil](/windows-server/administration/windows-commands/wevtutil) systemu Windows. Otwórz okno wiersza polecenia jako administrator. Zmień katalog monitów na folder .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4.\<.NET Version > \). Ten folder zawiera plik CLR-ETW.man. W wierszu polecenia wpisz następujące polecenie, aby zainstalować dostawcę CLR:

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a>Przechwytywanie zdarzeń CLR ETW

Możesz użyć narzędzi wiersza polecenia [logman](/windows-server/administration/windows-commands/logman) i [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) do przechwytywania zdarzeń ETW oraz narzędzi [tracerpt](/windows-server/administration/windows-commands/tracerpt_1) i [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) do dekodowania zdarzeń śledzenia.

Aby włączyć rejestrowanie, użytkownik musi określić trzy rzeczy:

- Dostawca do komunikacji.

- 64-bitowa liczba, która reprezentuje zestaw słów kluczowych. Każde słowo kluczowe reprezentuje zestaw zdarzeń, które dostawca może włączyć. Ta liczba przedstawia połączony zestaw słów kluczowych do włączenia.

- Mała liczba reprezentująca poziom (szczegółowości) rejestrowania. Poziom 1 jest najmniej szczegółowy, a poziom 5 jest najbardziej szczegółowy. Poziom 0 jest domyślny, a jego znaczenie jest specyficzne dla dostawcy.

### <a name="to-capture-clr-etw-events-using-logman"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Logman

1. W wierszu polecenia wpisz polecenie:

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     gdzie:

    - `-p` parametr identyfikuje identyfikator GUID dostawcy.

    - `0x1CCBD` określa kategorie zdarzeń, które zostaną zgłoszone.

    - `0x5` ustawia poziom rejestrowania (w tym przypadku, verbose (5)).

    - Parametr `-ets` nakazuje programowi logman Wysyłanie poleceń do sesji śledzenia zdarzeń.

    - `-ct perf` parametr określa, że funkcja `QueryPerformanceCounter` zostanie użyta do rejestrowania sygnatury czasowej dla każdego zdarzenia.

2. Aby zatrzymać rejestrowanie zdarzeń, wpisz polecenie:

     `logman stop clrevents -ets`

     To polecenie tworzy plik binarny śledzenia o nazwie clrevents.etl.

### <a name="to-capture-clr-etw-events-using-xperf"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Xperf

1. W wierszu polecenia wpisz polecenie:

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     gdzie GUID jest identyfikatorem GUID dostawcy ETW CLR, a `0x1CCBD:5` śledzi wszystko na poziomie i poniżej poziomu 5 (pełne).

2. Aby zatrzymać śledzenie, wpisz polecenie:

     `Xperf -stop clr`

     To polecenie tworzy plik śledzenia o nazwie clrevents.etl.

## <a name="viewing-clr-etw-events"></a>Wyświetlanie zdarzeń CLR ETW

Aby wyświetlić zdarzenia CLR ETW, należy użyć poleceń wymienionych poniżej. Opis zdarzeń można znaleźć w temacie [zdarzenia ETW środowiska CLR](clr-etw-events.md).

### <a name="to-view-clr-etw-events-using-tracerpt"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Tracerpt

- W wierszu polecenia wpisz polecenie:

     `tracerpt clrevents.etl`

     To polecenie tworzy dwa pliki: dumpfile.xml i summary.txt. Plik dumpfile.xml zawiera listę wszystkich zdarzeń, a plik summary.txt zawiera podsumowanie wszystkich zdarzeń.

### <a name="to-view-clr-etw-events-using-xperf"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Xperf

- W wierszu polecenia wpisz polecenie:

     `xperf clrevents.etl`

     To polecenie otwiera podgląd plików Xperf ETL. W tej przeglądarce zdarzenia CLR są wyświetlane w widoku **zdarzenia ogólne** . Aby wyświetlić siatkę danych zdarzeń uporządkowanych według typu, wybierz region czasu w tym widoku, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Podsumowanie**.

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Aby przekonwertować plik etl na plik z wartościami rozdzielanymi przecinkami

- W wierszu polecenia wpisz polecenie:

     `xperf -i clrevents.etl -f clrevents.csv`

     To polecenie powoduje zrzucenie przez narzędzie XPerf zdarzeń do pliku z wartościami rozdzielanymi przecinkami (CSV), który można wyświetlać. Różne zdarzenia mają różne pola, więc ten plik CSV zawiera więcej niż jeden wiersz nagłówka przed danymi. Pierwsze pole w każdym wierszu jest typem zdarzenia wskazującym, który nagłówek powinien być używany do określenia pozostałych pól.

## <a name="see-also"></a>Zobacz też

- [Zestaw narzędzi wydajności systemu Windows](/windows-hardware/test/wpt/)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
