---
title: Kontrolowanie logowania w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1bee42db7b9a92723b0640d0b3747a7921b8617c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418988"
---
# <a name="controlling-net-framework-logging"></a>Kontrolowanie logowania w programie .NET Framework
Śledzenia zdarzeń systemu Windows (ETW) można użyć do rejestrowania zdarzeń środowiska uruchomieniowego języka wspólnego (CLR). Można tworzyć i przeglądać ślady za pomocą następujących narzędzi:  
  
-   [Logman](https://go.microsoft.com/fwlink/?LinkId=150916) i [Tracerpt](https://go.microsoft.com/fwlink/?LinkId=150919) narzędzi wiersza polecenia, które są zawarte w systemie operacyjnym Windows.  
  
-   [Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) narzędzi w [narzędzi wydajności Windows](https://msdn.microsoft.com/library/windows/hardware/hh162945.aspx). Aby uzyskać więcej informacji dotyczących narzędzia Xperf, zobacz [blog poświęcony wydajności Windows](https://go.microsoft.com/fwlink/?LinkId=179509).  
  
 Aby można było przechwytywać informacje o zdarzeniu CLR, dostawca CLR musi być zainstalowany na komputerze. Aby upewnić się, że dostawca jest zainstalowany, wpisz `logman query providers` w wierszu polecenia. Zostanie wyświetlona lista dostawców. Ta lista powinna zawierać następujący wpis dla dostawcy CLR.  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 Jeśli dostawcy CLR nie ma na liście, możesz zainstalować go w systemach Windows Vista i nowszych systemów operacyjnych przy użyciu Windows [Wevtutil](https://go.microsoft.com/fwlink/?LinkID=150915) narzędzie wiersza polecenia. Otwórz okno wiersza polecenia jako administrator. Zmień katalog monitu [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] folderu (% WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET wersji>\ ). Ten folder zawiera plik CLR-ETW.man. W wierszu polecenia wpisz następujące polecenie, aby zainstalować dostawcę CLR:  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a>Przechwytywanie zdarzeń CLR ETW  
 Możesz użyć [Logman](https://go.microsoft.com/fwlink/?LinkId=150916) i [Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) narzędzia wiersza polecenia, aby przechwytywać zdarzenia ETW i [Tracerpt](https://go.microsoft.com/fwlink/?LinkId=150919) i [Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) narzędzia do zdekodowania zdarzenia śledzenia.  
  
 Aby włączyć rejestrowanie, użytkownik musi określić trzy rzeczy:  
  
-   Dostawca do komunikacji.  
  
-   64-bitowa liczba, która reprezentuje zestaw słów kluczowych. Każde słowo kluczowe reprezentuje zestaw zdarzeń, które dostawca może włączyć. Ta liczba przedstawia połączony zestaw słów kluczowych do włączenia.  
  
-   Mała liczba reprezentująca poziom (szczegółowości) rejestrowania. Poziom 1 jest najmniej szczegółowy, a poziom 5 jest najbardziej szczegółowy. Poziom 0 jest domyślny, a jego znaczenie jest specyficzne dla dostawcy.  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Logman  
  
1.  W wierszu polecenia wpisz polecenie:  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     gdzie:  
  
    -   `-p` Parametr identyfikuje identyfikator GUID dostawcy.  
  
    -   `0x1CCBD` Określa kategorie zdarzeń, które będą zgłaszane.  
  
    -   `0x5` Ustawia poziom rejestrowania (w tym przypadku pełne [5]).  
  
    -   `-ets` Parametr nakazuje narzędziu Logman wysyłanie poleceń do sesji śledzenia zdarzeń.  
  
    -   `-ct perf` Parametr określa, że `QueryPerformanceCounter` funkcja będzie służyć do rejestrowania znacznika czasu dla każdego zdarzenia.  
  
2.  Aby zatrzymać rejestrowanie zdarzeń, wpisz polecenie:  
  
     `logman stop clrevents -ets`  
  
     To polecenie tworzy plik binarny śledzenia o nazwie clrevents.etl.  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Xperf  
  
1.  W wierszu polecenia wpisz polecenie:  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     w przypadku identyfikatora GUID dostawcy CLR ETW identyfikatora GUID, a `0x1CCBD:5` śledzenie wszystkiego na poziomie 5 i niższych (informacja pełna).  
  
2.  Aby zatrzymać śledzenie, wpisz polecenie:  
  
     `Xperf -stop clr`  
  
     To polecenie tworzy plik śledzenia o nazwie clrevents.etl.  
  
## <a name="viewing-clr-etw-events"></a>Wyświetlanie zdarzeń CLR ETW  
 Aby wyświetlić zdarzenia CLR ETW, należy użyć poleceń wymienionych poniżej. Aby uzyskać opis zdarzenia, zobacz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Tracerpt  
  
-   W wierszu polecenia wpisz polecenie:  
  
     `tracerpt clrevents.etl`  
  
     To polecenie tworzy dwa pliki: dumpfile.xml i summary.txt. Plik dumpfile.xml zawiera listę wszystkich zdarzeń, a plik summary.txt zawiera podsumowanie wszystkich zdarzeń.  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Xperf  
  
-   W wierszu polecenia wpisz polecenie:  
  
     `xperf clrevents.etl`  
  
     To polecenie otwiera podgląd plików Xperf ETL. W tym podglądzie zdarzenia CLR wyświetlane w **zdarzenia ogólne** widoku. Aby wyświetlić siatkę danych zdarzeń według typu, zaznacz region czasu w tym widoku, a następnie kliknij prawym przyciskiem myszy i wybierz **Podsumowanie**.  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Aby przekonwertować plik etl na plik z wartościami rozdzielanymi przecinkami  
  
-   W wierszu polecenia wpisz polecenie:  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     To polecenie powoduje zrzucenie przez narzędzie XPerf zdarzeń do pliku z wartościami rozdzielanymi przecinkami (CSV), który można wyświetlać. Różne zdarzenia mają różne pola, więc ten plik CSV zawiera więcej niż jeden wiersz nagłówka przed danymi. Pierwsze pole w każdym wierszu jest typem zdarzenia wskazującym, który nagłówek powinien być używany do określenia pozostałych pól.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw narzędzi wydajności Windows](https://go.microsoft.com/fwlink/?LinkID=161141)  
 [Zdarzenia ETW w środowisku CLR](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
