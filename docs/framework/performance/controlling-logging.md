---
title: Kontrolowanie logowania w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58a9c0d02f4a24acc0df4d4a36d65e02f8bb7603
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-net-framework-logging"></a>Kontrolowanie logowania w programie .NET Framework
Śledzenia zdarzeń systemu Windows (ETW) można użyć do rejestrowania zdarzeń środowiska uruchomieniowego języka wspólnego (CLR). Można tworzyć i przeglądać ślady za pomocą następujących narzędzi:  
  
-   [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) i [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) narzędzi wiersza polecenia, które są dołączone do systemu operacyjnego Windows.  
  
-   [Narzędzia Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) narzędzi w [zestawu narzędzi wydajności systemu Windows](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx). Aby uzyskać więcej informacji na temat narzędzia Xperf, zobacz [blogu wydajność systemu Windows](http://go.microsoft.com/fwlink/?LinkId=179509).  
  
 Aby można było przechwytywać informacje o zdarzeniu CLR, dostawca CLR musi być zainstalowany na komputerze. Aby upewnić się, że dostawca jest zainstalowany, wpisz `logman query providers` w wierszu polecenia. Zostanie wyświetlona lista dostawców. Ta lista powinna zawierać następujący wpis dla dostawcy CLR.  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 Jeśli nie ma dostawcy CLR, można zainstalować go w systemie Windows Vista i nowszych systemów operacyjnych przy użyciu systemu Windows [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) narzędzia wiersza polecenia. Otwórz okno wiersza polecenia jako administrator. Zmień katalog monitu [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] folderu (% WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET wersji>\ ). Ten folder zawiera plik CLR-ETW.man. W wierszu polecenia wpisz następujące polecenie, aby zainstalować dostawcę CLR:  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a>Przechwytywanie zdarzeń CLR ETW  
 Można użyć [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) i [narzędzia Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) narzędzia wiersza polecenia do przechwytywania zdarzeń ETW i [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) i [narzędzia Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) narzędzia w celu zdekodowania zdarzenia śledzenia.  
  
 Aby włączyć rejestrowanie, użytkownik musi określić trzy rzeczy:  
  
-   Dostawca do komunikacji.  
  
-   64-bitowa liczba, która reprezentuje zestaw słów kluczowych. Każde słowo kluczowe reprezentuje zestaw zdarzeń, które dostawca może włączyć. Ta liczba przedstawia połączony zestaw słów kluczowych do włączenia.  
  
-   Mała liczba reprezentująca poziom (szczegółowości) rejestrowania. Poziom 1 jest najmniej szczegółowy, a poziom 5 jest najbardziej szczegółowy. Poziom 0 jest domyślny, a jego znaczenie jest specyficzne dla dostawcy.  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Logman  
  
1.  W wierszu polecenia wpisz polecenie:  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     gdzie:  
  
    -   `-p` Parametr identyfikuje dostawcę identyfikator GUID.  
  
    -   `0x1CCBD` Określa rodzajów zdarzeń, które zostanie wygenerowany.  
  
    -   `0x5` Ustawia poziom rejestrowania (w tym przypadku pełne [5]).  
  
    -   `-ets` Parametr nakazuje Logman należy wysyłać polecenia do sesji śledzenia zdarzeń.  
  
    -   `-ct perf` Parametr określa, że `QueryPerformanceCounter` funkcja będzie służyć do logowania sygnaturę czasową dla każdego zdarzenia.  
  
2.  Aby zatrzymać rejestrowanie zdarzeń, wpisz polecenie:  
  
     `logman stop clrevents -ets`  
  
     To polecenie tworzy plik binarny śledzenia o nazwie clrevents.etl.  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a>Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Xperf  
  
1.  W wierszu polecenia wpisz polecenie:  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     w przypadku identyfikatora GUID dostawców CLR ETW identyfikator GUID, a `0x1CCBD:5` śledzi wszystko w poziomie i poniżej poziomu 5 (pełne).  
  
2.  Aby zatrzymać śledzenie, wpisz polecenie:  
  
     `Xperf -stop clr`  
  
     To polecenie tworzy plik śledzenia o nazwie clrevents.etl.  
  
## <a name="viewing-clr-etw-events"></a>Wyświetlanie zdarzeń CLR ETW  
 Aby wyświetlić zdarzenia CLR ETW, należy użyć poleceń wymienionych poniżej. Opis zdarzenia, zobacz [zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md).  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Tracerpt  
  
-   W wierszu polecenia wpisz polecenie:  
  
     `tracerpt clrevents.etl`  
  
     To polecenie tworzy dwa pliki: dumpfile.xml i summary.txt. Plik dumpfile.xml zawiera listę wszystkich zdarzeń, a plik summary.txt zawiera podsumowanie wszystkich zdarzeń.  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a>Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Xperf  
  
-   W wierszu polecenia wpisz polecenie:  
  
     `xperf clrevents.etl`  
  
     To polecenie otwiera podgląd plików Xperf ETL. W tym podglądzie zdarzeń CLR widoczne w **ogólnego zdarzenia** widoku. Aby wyświetlić siatkę danych zdarzeń według typu, wybierz region czasu, w tym widoku, a następnie kliknij prawym przyciskiem myszy i wybierz **Podsumowanie**.  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a>Aby przekonwertować plik etl na plik z wartościami rozdzielanymi przecinkami  
  
-   W wierszu polecenia wpisz polecenie:  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     To polecenie powoduje zrzucenie przez narzędzie XPerf zdarzeń do pliku z wartościami rozdzielanymi przecinkami (CSV), który można wyświetlać. Różne zdarzenia mają różne pola, więc ten plik CSV zawiera więcej niż jeden wiersz nagłówka przed danymi. Pierwsze pole w każdym wierszu jest typem zdarzenia wskazującym, który nagłówek powinien być używany do określenia pozostałych pól.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw narzędzi wydajności systemu Windows](http://go.microsoft.com/fwlink/?LinkID=161141)  
 [Zdarzenia ETW w środowisku CLR](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
