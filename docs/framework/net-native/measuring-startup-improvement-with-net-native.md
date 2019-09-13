---
title: Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74011a4c70cc8f7da3973698a43b1e97cffb9f9b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927069"
---
# <a name="measuring-startup-improvement-with-net-native"></a>Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
.NET Native znacznie poprawia czas uruchamiania aplikacji. To ulepszenie jest szczególnie zauważalne w przypadku urządzeń przenośnych i z niską obsługą aplikacji. Ten temat ułatwia rozpoczęcie pracy z podstawową Instrumentacją wymaganą do mierzenia tego usprawnienia uruchamiania.  
  
 Aby ułatwić badania wydajności, .NET Framework i system Windows używają platformy zdarzeń o nazwie śledzenie zdarzeń systemu Windows (ETW), która umożliwia aplikacji powiadamianie narzędzi o zdarzeniach. Następnie można użyć narzędzia o nazwie narzędzia PerfView, aby łatwo wyświetlać i analizować zdarzenia ETW. W tym temacie wyjaśniono, jak:  
  
- Użyj klasy <xref:System.Diagnostics.Tracing.EventSource> , aby emitować zdarzenia.  
  
- Użyj narzędzia PerfView, aby zebrać te zdarzenia.  
  
- Użyj narzędzia PerfView, aby wyświetlić te zdarzenia.  
  
## <a name="using-eventsource-to-emit-events"></a>Używanie funkcji EventSource do emisji zdarzeń  
 <xref:System.Diagnostics.Tracing.EventSource>dostarcza klasę bazową, z której należy utworzyć niestandardowego dostawcę zdarzeń. Ogólnie rzecz biorąc tworzysz podklasę <xref:System.Diagnostics.Tracing.EventSource> i `Write*` otaczaj metody własnymi metodami zdarzeń. Pojedynczy wzorzec jest zwykle używany dla każdego z <xref:System.Diagnostics.Tracing.EventSource>nich.  
  
 Na przykład Klasa w poniższym przykładzie może służyć do mierzenia dwóch cech wydajności:  
  
- Czas do momentu `App` wywołania konstruktora klasy.  
  
- Godzina, do której `MainPage` Konstruktor został wywołany.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Istnieje kilka kwestii, na które należy zwrócić uwagę. Najpierw jest tworzony `AppEventSource.Log`pojedynczy element. To wystąpienie będzie używane dla wszystkich dzienników. Druga metoda zdarzenia ma <xref:System.Diagnostics.Tracing.EventAttribute>. Dzięki temu narzędzia mogą skojarzyć indeks <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metody z metodą, która została `AppEventSource`wywołana.  
  
 Należy zauważyć, że te zdarzenia są czysto ilustracyjny. Większość kodu aplikacji będzie uruchamiana po tych zdarzeniach. Należy zrozumieć, które zdarzenia w kodzie odpowiadają interakcjom użytkowników, mierzyć te i ulepszać te testy. Ponadto zdarzenia same rejestruje tylko pojedyncze wystąpienie w czasie. Często warto mieć sparowane zdarzenia uruchamiania i zatrzymywania dla każdej operacji. Podczas badania uruchamiania aplikacji zdarzenie uruchomieniowe jest zazwyczaj zdarzeniem "proces/Start", które jest emitowane przez system operacyjny.  
  
 Załóżmy na przykład, że tworzysz czytelnika RSS. Oto kilka interesujących lokalizacji rejestrowania zdarzeń:  
  
- Gdy Strona główna jest renderowana po raz pierwszy.  
  
- W przypadku deserializacji starych wątków RSS z magazynu lokalnego.  
  
- Gdy aplikacja rozpocznie synchronizowanie nowych wątków.  
  
- Gdy aplikacja zakończyła Synchronizowanie nowych wątków.  
  
 Instrumentacja aplikacji jest prosta: Po prostu wywołaj odpowiednią metodę w klasie pochodnej. Korzystając `AppEventSource` z poprzedniego przykładu, można instrumentować aplikację w następujący sposób:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Gdy aplikacja jest Instrumentacją, można rozpocząć zbieranie zdarzeń.  
  
## <a name="gathering-events-with-perfview"></a>Zbieranie zdarzeń za pomocą narzędzia PerfView  
 Narzędzia PerfView używa zdarzeń ETW, aby pomóc w wykonywaniu wszystkich różnych badań wydajności aplikacji. Zawiera również graficzny interfejs użytkownika konfiguracji, który umożliwia włączenie lub wyłączenie rejestrowania dla różnych typów zdarzeń. Narzędzia PerfView to bezpłatne narzędzie, które można pobrać z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=28567). Aby uzyskać więcej informacji, Obejrzyj [klipy wideo samouczka narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
> Narzędzia PerfView nie można używać do zbierania zdarzeń w systemach ARM. Aby zbierać zdarzenia w systemach ARM, użyj programu Windows Performance Recorder (WP). Aby uzyskać więcej informacji, zobacz [wpis w blogu Vance Morrison](https://blogs.msdn.microsoft.com/vancem/2012/12/19/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device/).  
  
 Możesz również wywołać narzędzia PerfView z wiersza polecenia. Aby rejestrować tylko zdarzenia od dostawcy, Otwórz okno wiersza polecenia i wprowadź polecenie:  
  
```console
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 gdzie:  
  
 `-KernelEvents:Process`  
 Wskazuje, że chcesz wiedzieć, kiedy proces zostanie uruchomiony i zatrzymany. Potrzebujesz zdarzenia procesu/uruchomienia dla aplikacji, aby można było je odjęciu od innych czasów zdarzeń.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Wyłącza innych dostawców, które domyślnie narzędzia PerfView włącza i włącza dostawcę.  (Gwiazdka wskazuje, że jest <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Wskazuje, że chcesz rozpocząć zbieranie danych i zapisać dane w pliku Plik_wyjściowy. etl. zip.  
  
 Uruchom aplikację po rozpoczęciu narzędzia PerfView. Podczas uruchamiania aplikacji można pamiętać o kilku kwestiach:  
  
- Użyj kompilacji wydania, a nie kompilacji debugowania. Kompilacje debugowania często zawierają dodatkowe sprawdzanie błędów i kod obsługi błędu, który może spowodować, że aplikacja będzie działać wolniej niż oczekiwano.  
  
- Uruchomienie aplikacji z dołączonym debugerem ma wpływ na wydajność aplikacji.  
  
- System Windows używa wielu strategii buforowania w celu przyspieszenia czasu uruchamiania aplikacji. Jeśli aplikacja jest obecnie buforowana w pamięci i nie musi być ładowana z dysku, rozpocznie się szybsza. Aby zapewnić spójność, Uruchom i Zamknij aplikację kilka razy przed pomiarem.  
  
 Po uruchomieniu aplikacji, tak aby narzędzia PerfView mógł zbierać emitowane zdarzenia, wybierz przycisk **Zatrzymaj zbieranie** . Ogólnie rzecz biorąc, należy zatrzymać zbieranie danych przed zamknięciem aplikacji, aby nie otrzymywać nadmiarowe zdarzenia. Jednakże w przypadku mierzenia wydajności zamykania lub zawieszania warto kontynuować zbieranie danych.  
  
## <a name="displaying-the-events"></a>Wyświetlanie zdarzeń  
 Aby wyświetlić zdarzenia, które zostały już zebrane, użyj narzędzia PerfView, aby otworzyć utworzony plik ETL lub ETL, a następnie wybierz pozycję **zdarzenia**. ETW będzie zbierać informacje o dużej liczbie zdarzeń, w tym zdarzenia z innych procesów. Aby skoncentrować się na badaniu, uzupełnij następujące pola tekstowe w widoku zdarzenia:  
  
- W polu **Filtr procesu** Określ nazwę aplikacji (bez pliku. exe).  
  
- W polu **Filtr typów zdarzeń** Określ `Process/Start | MyCompany-MyApp`. Powoduje to ustawienie filtru zdarzeń od firmy-MojaApl oraz zdarzenia jądra/procesu/uruchamiania systemu Windows.  
  
 Zaznacz wszystkie zdarzenia wymienione w okienku po lewej stronie (Ctrl-A) i wybierz klawisz **Enter** . Teraz powinno być możliwe wyświetlenie sygnatur czasowych z każdego zdarzenia. Sygnatury czasowe odnoszą się do początku śledzenia, więc należy odjąć czas każdego zdarzenia od momentu rozpoczęcia procesu, aby zidentyfikować czas, który upłynął od uruchomienia. Jeśli używasz kombinacji Ctrl + kliknięcie, aby wybrać dwa sygnatury czasowe, zobaczysz różnicę między nimi na pasku stanu w dolnej części strony. Dzięki temu można łatwo zobaczyć czas upływający między dwoma zdarzeniami wyświetlanymi na ekranie (w tym uruchomieniem procesu). Można otworzyć menu skrótów dla widoku i wybrać spośród wielu przydatnych opcji, takich jak Eksportowanie do plików CSV lub Otwieranie programu Microsoft Excel w celu zapisania lub przetworzenia danych.  
  
 Powtarzając procedurę zarówno dla oryginalnej aplikacji, jak i wersji skompilowanej za pomocą łańcucha narzędzi .NET Native, można porównać różnicę wydajności.   Aplikacje .NET Native są zwykle uruchamiane szybciej niż aplikacje natywne non-.NET. Jeśli interesuje Cię przeszukiwanie stosów, narzędzia PerfView może również zidentyfikować części kodu, które zajmują najwięcej czasu. Aby uzyskać więcej informacji, Obejrzyj [samouczki narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) lub przeczytaj [wpis w blogu Vance Morrison](https://blogs.msdn.microsoft.com/vancem/2011/12/28/publication-of-the-perfview-performance-analysis-tool/).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Tracing.EventSource>
