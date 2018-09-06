---
title: Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2603c29fe9108a32f3c3ba86a5aba9fae5042b17
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742765"
---
# <a name="measuring-startup-improvement-with-net-native"></a>Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] znacznie poprawia czas uruchamiania aplikacji. To ulepszenie jest szczególnie widoczny na urządzeniach przenośnych, niskim poziomie zasilania i złożonych aplikacji. Ten temat ułatwia rozpoczęcie pracy z Instrumentacją podstawowe, potrzebne do mierzenia to ulepszenie uruchamiania.  
  
 .NET Framework i Windows w celu ułatwienia badania wydajności, użyj platforma zdarzeń o nazwie śledzenie zdarzeń dla Windows (ETW), który umożliwia aplikacji powiadomić narzędzia w przypadku wystąpienia zdarzeń. Następnie służy narzędzie narzędzia PerfView łatwo przeglądać i analizować zdarzeń ETW. W tym temacie opisano sposób:  
  
-   Użyj <xref:System.Diagnostics.Tracing.EventSource> klasy, aby emitować zdarzenia.  
  
-   Korzystanie z programu PerfView do zbierania tych zdarzeń.  
  
-   Korzystanie z programu PerfView do wyświetlania tych zdarzeń.  
  
## <a name="using-eventsource-to-emit-events"></a>Przy użyciu źródła zdarzeń, aby emitować zdarzenia  
 <xref:System.Diagnostics.Tracing.EventSource> udostępnia klasę bazową, z którego ma zostać Tworzenie zdarzenia niestandardowego dostawcy. Ogólnie rzecz biorąc, Utwórz podklasę <xref:System.Diagnostics.Tracing.EventSource> i zawijania `Write*` metody przy użyciu metody zdarzeń. Zwykle używane jest wzorzec singleton dla każdego <xref:System.Diagnostics.Tracing.EventSource>.  
  
 Na przykład klasa w poniższym przykładzie może służyć do mierzenia dwóch charakterystyki wydajności:  
  
-   Czas do `App` wywołano konstruktora klasy.  
  
-   Czas do `MainPage` Konstruktor została wywołana.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Istnieje kilka kwestii, które należy zwrócić uwagę, w tym miejscu. Po pierwsze, pojedynczego jest tworzony w `AppEventSource.Log`. To wystąpienie będzie służyć do rejestrowania wszystkich. Po drugie, każda metoda zdarzeń ma <xref:System.Diagnostics.Tracing.EventAttribute>. Dzięki temu narzędzia skojarzyć indeks <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metody za pomocą metody, która została wywołana na `AppEventSource`.  
  
 Należy pamiętać, że te zdarzenia są wyłącznie informacyjny. Większość kodu aplikacji zostanie wykonany po tych zdarzeń. Należy zrozumieć, które zdarzenia w kodzie odpowiadają na interakcję użytkownika, tych miar i ulepszyć te testy porównawcze. Ponadto się w dzienniku tylko jedno wystąpienie na czas. Często warto mieć skojarzone start i Zatrzymaj zdarzenia dla każdej operacji. Zdarzenie rozpoczęcia, badając uruchamiania aplikacji jest ogólnie zdarzeń "Początek/procesu", który emituje systemu operacyjnego.  
  
 Na przykład załóżmy, że tworzysz czytnik danych RSS. Kilka interesujących lokalizacje, aby rejestrować zdarzenia są:  
  
-   Gdy główna strona najpierw jest renderowany.  
  
-   Gdy starej historii RSS są deserializacji z magazynu lokalnego.  
  
-   Aplikacja rozpoczęcia synchronizowania nowe historie.  
  
-   Gdy aplikacji zostało zakończone, synchronizowanie nowe historie.  
  
 Instrumentacja aplikacji jest bardzo proste: wystarczy wywołanie odpowiedniej metody w klasie pochodnej. Za pomocą `AppEventSource` z poprzedniego przykładu, możliwe jest instrumentowanie aplikacji w następujący sposób:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Podczas instrumentacji aplikacji, możesz przystąpić do zbierania zdarzeń.  
  
## <a name="gathering-events-with-perfview"></a>Zbieranie zdarzeń za pomocą narzędzia PerfView  
 Narzędzia PerfView używa zdarzenia ETW, aby poddawać wszelkiego rodzaju badania wydajności aplikacji. Zawiera on również konfiguracji graficznego interfejsu użytkownika, który pozwala włączyć rejestrowanie dla różnych typów zdarzeń lub wyłączyć. Narzędzia PerfView to bezpłatne narzędzie i można je pobrać z [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=28567). Aby uzyskać więcej informacji, obejrzyj [filmom instruktażowym narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
>  Narzędzia PerfView nie może służyć do zbierania zdarzeń w systemach ARM. Służąca do gromadzenia zdarzeń w systemach ARM, należy użyć Rejestratora wydajności Windows (WPR). Aby uzyskać więcej informacji, zobacz [wpis w blogu Morrison zaliczko](https://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Narzędzia PerfView można również wywołać z wiersza polecenia. Aby zalogować się za pośrednictwem swojego usługodawcy tylko zdarzenia, Otwórz okno wiersza polecenia i wpisz polecenie:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 gdzie:  
  
 `-KernelEvents:Process`  
 Wskazuje, że chcesz wiedzieć, kiedy proces uruchamia i zatrzymuje. Należy zdarzeń uruchomienia procesu/aplikacji, dzięki czemu można odejmować w pozostałym czasie zdarzenia.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Wyłącza innych dostawców, które narzędzia PerfView włącza domyślnie i włącza funkcję dostawcy Moja firma MyApp.  (Gwiazdka wskazuje, że jest <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Wskazuje, czy ma być Rozpocznij zbieranie danych i zapisz ją do outputFile.etl.zip.  
  
 Uruchom aplikację po uruchomieniu narzędzia PerfView. Istnieje kilka kwestii, które należy pamiętać podczas uruchamiania aplikacji:  
  
-   Użyj kompilacji wydania nie kompilacji debugowania. Kompilacje debugowania często zawierają Sprawdzanie dodatkowych błędów i kod, który może spowodować, że aplikacja ma działać wolniej niż oczekiwano obsługi błędów.  
  
-   Z tą aplikacją w załączonym debuggerze, ma wpływ na wydajność aplikacji.  
  
-   Windows używa wielu strategii buforowania, aby przyspieszyć czas uruchamiania aplikacji. Jeśli Twoja aplikacja jest aktualnie w pamięci podręcznej w pamięci i nie musi być załadowany z dysku, zostanie uruchomiony szybciej. W celu zapewnienia spójności, uruchom i zamknij aplikację kilka razy przed pomiaru.  
  
 Po uruchomieniu aplikacji tak, aby narzędzia PerfView może zbierać zdarzenia emitowany, wybierz **Zatrzymaj Kolekcjonowanie** przycisku. Ogólnie rzecz biorąc należy zatrzymać zbieranie przed zamknięciem aplikacji, dzięki czemu nie uzyskać nadmiarowe zdarzenia. Jednak notuje zamykania lub zawieszenie wydajności, należy kontynuować kolekcji.  
  
## <a name="displaying-the-events"></a>Wyświetlanie zdarzeń  
 Aby wyświetlić zdarzenia, które zostały już zebrane, użyj narzędzia PerfView, aby otworzyć etl lub. etl.zip utworzonego pliku i wybierz polecenie **zdarzenia**. ETW zostanie zostały zebrane informacje o dużej liczby zdarzeń, w tym zdarzenia z innych procesów. Aby skoncentrować się badania, wykonaj następujące pola tekstowe w widoku zdarzeń:  
  
-   W **filtra procesu** należy określić nazwę aplikacji (bez ".exe").  
  
-   W **filtr typy zdarzeń** określ `Process/Start | MyCompany-MyApp`. To ustawienie filtrowania dla zdarzeń z Moja firma MyApp i zdarzeń Windows uruchomienia jądra/procesu.  
  
 Wybierz wszystkie zdarzenia wymienione w okienku po lewej stronie (Ctrl-A) i wybierz polecenie **Enter** klucza. Teraz można wyświetlić sygnatury czasowe z każdego zdarzenia. Tych sygnatury czasowe są względem początku śledzenia, więc należy odjąć czasu każdego zdarzenia od czasu rozpoczęcia do identyfikowania czas, jaki upłynął od uruchomienia procesu. Jeśli używasz Ctrl + kliknięcie zaznacz dwa sygnatury czasowe, zobaczysz różnią się one być wyświetlane na pasku stanu u dołu strony. Dzięki temu można łatwo sprawdzić czas między dwoma zdarzeń wyświetlania (w tym uruchomienie procesu). Można otworzyć menu skrótów dla widoku i wybierz z szereg użyteczne opcje, takie jak eksportowania do plików CSV lub otwierania Microsoft Excel, aby zapisać lub przetwarzania danych.  
  
 Powtarzając procedurę dla oryginalnej aplikacji i wersji skompilowanych przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha, można porównać różnice w wydajności.   [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacje zazwyczaj początek szybciej niż non -[!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacji. Jeśli interesuje Cię możesz głębiej, narzędzia PerfView można zidentyfikować także fragmenty kodu, które mają najwięcej czasu. Aby uzyskać więcej informacji, obejrzyj [samouczki narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial) lub przeczytaj [wpis w blogu Morrison zaliczko](https://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Tracing.EventSource>
