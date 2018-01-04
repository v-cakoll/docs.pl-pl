---
title: "Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03324850fbcb0264816b71cf8a8c6ad6a9688058
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="measuring-startup-improvement-with-net-native"></a>Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)]znacznie poprawia czas uruchamiania aplikacji. To ulepszenie jest szczególnie widoczny na urządzeniach przenośnych, zasilany z niskim oraz złożone aplikacje. Ten temat ułatwia szybkie wprowadzenie do podstawowych Instrumentacja pomiarze temu usprawnieniu uruchamiania.  
  
 W celu ułatwienia kontroli wydajności, .NET Framework i systemu Windows używają framework zdarzenia o nazwie zdarzenia śledzenia dla systemu Windows (ETW) umożliwiający aplikację, aby powiadomić narzędzi w przypadku wystąpienia zdarzeń. Narzędzie narzędzia PerfView można następnie użyć do łatwego wyświetlania i analizowania zdarzeń funkcji ETW. W tym temacie opisano sposób:  
  
-   Użyj <xref:System.Diagnostics.Tracing.EventSource> klasy do wysyłania zdarzeń.  
  
-   Przy użyciu narzędzia PerfView zbierania tych zdarzeń.  
  
-   Aby wyświetlić te zdarzenia przy użyciu narzędzia PerfView.  
  
## <a name="using-eventsource-to-emit-events"></a>Emituj zdarzeń przy użyciu źródła zdarzeń  
 <xref:System.Diagnostics.Tracing.EventSource>udostępnia klasę podstawową, z których można utworzyć dostawcy zdarzeń niestandardowych. Ogólnie rzecz biorąc, Utwórz podklasę <xref:System.Diagnostics.Tracing.EventSource> i zastępowania `Write*` metod z metody zdarzeń. Wzorzec singleton zazwyczaj jest używane dla każdego <xref:System.Diagnostics.Tracing.EventSource>.  
  
 Na przykład w poniższym przykładzie klasa może służyć do mierzenia dwóch charakterystyki wydajności:  
  
-   Czas `App` konstruktora klasy została wywołana.  
  
-   Czas `MainPage` konstruktor został wywołany.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Istnieje kilka możliwości do Zwróć uwagę, w tym miejscu. Po pierwsze, pojedynczą jest tworzony w `AppEventSource.Log`. To wystąpienie będzie służyć do rejestrowania wszystkich. Po drugie, każda metoda zdarzeń ma <xref:System.Diagnostics.Tracing.EventAttribute>. Dzięki temu narzędzi skojarzyć indeks <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metody za pomocą metody, która została wywołana w `AppEventSource`.  
  
 Należy zauważyć, że te zdarzenia wyłącznie informacyjny. Większość kodu aplikacji zostanie uruchomiony po tych zdarzeń. Zapoznaj się zdarzenia w kodzie odpowiadają interakcji użytkownika, te miary i zwiększyć tych wzorców. Ponadto zdarzenia się zalogowanie się tylko jedno wystąpienie. Często warto mieć skojarzone uruchomienia i Zatrzymaj zdarzenia dla każdej operacji. Rozpatrując uruchamiania aplikacji, zdarzenie rozpoczęcia jest zazwyczaj zdarzeń "Proces/Start", który emituje systemu operacyjnego.  
  
 Na przykład załóżmy, że tworzysz czytnik danych RSS. Kilka interesujące lokalizacje, aby rejestrować zdarzenia są:  
  
-   Jeśli strona główna najpierw jest renderowany.  
  
-   Gdy starych wątków RSS są rozszeregować z magazynu lokalnego.  
  
-   Aplikacja rozpoczęcia synchronizacji nowych scenariuszy.  
  
-   Gdy aplikacji zostało zakończone, synchronizowania nowych scenariuszy.  
  
 Instrumentacji aplikacji jest prosty: po prostu Wywołaj metodę odpowiednią w klasie pochodnej. Przy użyciu `AppEventSource` z poprzedniego przykładu mogą dodawać app w następujący sposób:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Gdy aplikacja jest instrumentowany, wszystko jest gotowe do zbierania zdarzeń.  
  
## <a name="gathering-events-with-perfview"></a>Zbieranie zdarzeń z narzędzia PerfView  
 Narzędzia PerfView używa zdarzenia ETW pomaga szerokiej gamy badania wydajności aplikacji. Obejmuje on też konfiguracji graficznego interfejsu użytkownika, który pozwala włączyć rejestrowanie dla różnych typów zdarzeń lub wyłączyć. Narzędzia PerfView to bezpłatne narzędzie i może zostać pobrany z [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=28567). Aby uzyskać więcej informacji, obserwuj [filmów instruktażowych narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
>  Nie można użyć narzędzia PerfView służąca do gromadzenia zdarzeń w systemach ARM. Aby zbierać zdarzenia w systemach ARM, użyj rejestrowania wydajności systemu Windows (WPR). Aby uzyskać więcej informacji, zobacz [Morrison zaliczko wpis w blogu](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Można także wywoływać narzędzia PerfView z wiersza polecenia. Aby rejestrować tylko zdarzenia z dostawcą, Otwórz okno wiersza polecenia, a następnie wprowadź polecenie:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 gdzie:  
  
 `-KernelEvents:Process`  
 Wskazuje, że chcesz wiedzieć, kiedy rozpoczyna się proces i zatrzymuje. Należy zdarzeń procesu/Start dla aplikacji, więc można odejmować w pozostałych godzinach zdarzeń.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Wyłącza innych dostawców, które narzędzia PerfView włącza domyślnie i włącza dostawcy moja_aplikacja Moja firma.  (Gwiazdka oznacza, że jest <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Wskazuje, czy chcesz uruchomić kolekcji i zapisać dane do outputFile.etl.zip.  
  
 Uruchamianie aplikacji po uruchomieniu narzędzia PerfView. Istnieje kilka sposobów pamiętać podczas uruchamiania aplikacji:  
  
-   Użyj kompilacji wydania nie kompilację debugowania. Kompilacje debugowania często zawierają sprawdzanie błędów dodatkowe i kod, który może spowodować aplikację, aby działać wolniej niż oczekiwano obsługi błędów.  
  
-   Z tą aplikacją debugerze wpływa na wydajność aplikacji.  
  
-   System Windows używa wielu strategii buforowania aby przyspieszyć czasy uruchamiania aplikacji. Jeśli aplikacja jest obecnie w pamięci podręcznej w pamięci i nie musi być załadowany z dysku, zostanie ona rozpoczęta szybciej. Do zapewnienia spójności, uruchom i zamknij aplikację kilka razy przed jego pomiaru.  
  
 Po uruchomieniu aplikacji tak, aby narzędzia PerfView może zbierać emitowany zdarzenia, wybierz **zatrzymania zbierania** przycisku. Ogólnie rzecz biorąc należy zatrzymać zbieranie przed zamknięciem aplikacji, więc nie możesz uzyskać nadmiarowe zdarzenia. Jednak jeśli notuje wydajności zamykania lub zawieszenie, należy kontynuować kolekcji.  
  
## <a name="displaying-the-events"></a>Wyświetlanie zdarzenia  
 Aby wyświetlić zdarzenia, które zostały już zebrane, przy użyciu narzędzia PerfView Otwórz etl lub. etl.zip pliku utworzonego i wybierz polecenie **zdarzenia**. ETW będzie zostały zebrane informacje o większą liczbę zdarzeń, w tym zdarzenia z innymi procesami. Aby skoncentrować się badania, wykonaj następujące pola tekstowe w widoku zdarzeń:  
  
-   W **filtru procesu** Określ nazwę aplikacji (bez ".exe").  
  
-   W **filtr typy zdarzeń** określ `Process/Start | MyCompany-MyApp`. Filtr zdarzeń to ustawienie z moja_aplikacja Moja firma i zdarzenia systemu Windows początek jądra/procesu.  
  
 Wybierz wszystkie zdarzenia wyświetlane w okienku po lewej stronie (Ctrl-A) i wybierz polecenie **Enter** klucza. Teraz można wyświetlić sygnatury czasowe z każdego zdarzenia. Te sygnatury czasowe są względem początku śledzenia, więc odjąć czasowej każdego zdarzenia od godziny rozpoczęcia procesu, aby określić czas, który upłynął od momentu uruchomienia. Jeśli używasz Ctrl + kliknięcie, aby wybrać dwa znaczniki czasu zobaczysz różnica między nimi wyświetlany w pasku stanu w dolnej części strony. Dzięki temu można łatwo sprawdzić czas, który upłynął od dwóch zdarzeń wyświetlania (w tym procesu start). Można otworzyć menu skrótów dla widoku i wybierz z liczbą przydatne opcje, takie jak eksportowania plików CSV lub otwierania Microsoft Excel, aby zapisać lub przetwarzania danych.  
  
 Powtarzając procedurę dla oryginalnej aplikacji i wersji zostały utworzone przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha, możesz porównać różnica w wydajności.   [!INCLUDE[net_native](../../../includes/net-native-md.md)]aplikacje zazwyczaj start szybciej niż z systemem innym niż[!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikacji. Jeśli interesuje Cię tu przeszukuje głębiej, narzędzia PerfView można zidentyfikować także fragmenty kodu, które są tworzone najwięcej czasu. Aby uzyskać więcej informacji, obserwuj [samouczki narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial) lub odczytać [wpis w blogu Morrison zaliczko](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Tracing.EventSource>
