---
title: Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
ms.openlocfilehash: 41a693f18ffea0e5ce0ca742bc251d147e8e3784
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180997"
---
# <a name="measuring-startup-improvement-with-net-native"></a>Dokonywanie pomiaru poprawy szybkości uruchomienia za pomocą architektury .NET Native
Program .NET Native znacznie skraca czas uruchamiania aplikacji. Ta poprawa jest szczególnie zauważalna na przenośnych urządzeniach o niskim poużycie i złożonych aplikacjach. W tym temacie pomaga rozpocząć pracę z podstawowym instrumentacją potrzebnym do pomiaru tego ulepszenia uruchamiania.  
  
 Aby ułatwić badania wydajności, program .NET Framework i system Windows używają struktury zdarzeń o nazwie Śledzenie zdarzeń dla systemu Windows (ETW), która umożliwia aplikacji powiadamianie o narzędziach o wystąpieniu zdarzeń. Następnie można użyć narzędzia o nazwie PerfView, aby łatwo przeglądać i analizować zdarzenia ETW. W tym temacie wyjaśniono, jak:  
  
- <xref:System.Diagnostics.Tracing.EventSource> Klasa służy do emitowania zdarzeń.  
  
- Użyj PerfView do zbierania tych zdarzeń.  
  
- Użyj PerfView do wyświetlania tych zdarzeń.  
  
## <a name="using-eventsource-to-emit-events"></a>Używanie usługi EventSource do emitowania zdarzeń  
 <xref:System.Diagnostics.Tracing.EventSource>udostępnia klasę podstawową, z której można utworzyć niestandardowego dostawcy zdarzeń. Ogólnie rzecz biorąc należy utworzyć <xref:System.Diagnostics.Tracing.EventSource> podklasę i zawinąć `Write*` metody z własnych metod zdarzeń. Wzorzec singleton jest zwykle <xref:System.Diagnostics.Tracing.EventSource>używany dla każdego .  
  
 Na przykład klasa w poniższym przykładzie może służyć do pomiaru dwóch cech wydajności:  
  
- Czas, do `App` konstruktora klasy został wywołany.  
  
- Czas, `MainPage` aż konstruktor został powołany.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Jest tu kilka rzeczy, które należy zauważyć. Po pierwsze, singleton `AppEventSource.Log`jest tworzony w . To wystąpienie będzie używane dla wszystkich rejestrowania. Po drugie, każda <xref:System.Diagnostics.Tracing.EventAttribute>metoda zdarzenia ma . Pomaga to narzędziom skojarzyć indeks <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metody z `AppEventSource`metodą, która została wywołana .  
  
 Należy zauważyć, że te zdarzenia są czysto ilustracyjne. Większość kodu aplikacji zostanie uruchomiony po tych zdarzeniach. Należy zrozumieć, które zdarzenia w kodzie odpowiadają interakcjami użytkownika, zmierzyć je i poprawić te testy porównawcze. Ponadto zdarzenia same rejestrują tylko jedno wystąpienie w czasie. Często warto sparować zdarzenia start i stop dla każdej operacji. Podczas badania uruchamiania aplikacji zdarzenie start jest zazwyczaj zdarzenie "Proces/start", które emituje system operacyjny.  
  
 Załóżmy na przykład, że tworzysz czytnik RSS. Kilka interesujących miejsc do zarejestrowania zdarzenia to:  
  
- Gdy strona główna jest renderowana po raz pierwszy.  
  
- Gdy stare historie RSS są deserializowane z magazynu lokalnego.  
  
- Gdy aplikacja rozpocznie synchronizację nowych wątków.  
  
- Po zakończeniu synchronizacji nowych wątków aplikacja.  
  
 Instrumentowanie aplikacji jest proste: wystarczy wywołać odpowiednią metodę w klasie pochodnej. Korzystając `AppEventSource` z poprzedniego przykładu, można instrumentować aplikację w następujący sposób:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Gdy aplikacja jest instrumentowana, możesz zbierać wydarzenia.  
  
## <a name="gathering-events-with-perfview"></a>Zbieranie wydarzeń za pomocą PerfView  
 PerfView używa zdarzeń ETW, aby ułatwić wykonywanie wszelkiego rodzaju badań wydajności w aplikacji. Zawiera również gui konfiguracji, który pozwala włączyć lub wyłączyć rejestrowanie dla różnych typów zdarzeń. PerfView jest darmowym narzędziem i można go pobrać z [Centrum pobierania Microsoft.](https://www.microsoft.com/download/details.aspx?id=28567) Aby uzyskać więcej informacji, obejrzyj [filmy instruktażowe PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
> PerfView nie może służyć do zbierania zdarzeń w systemach ARM. Aby zbierać zdarzenia w systemach ARM, użyj rejestratora wydajności systemu Windows (WPR). Aby uzyskać więcej informacji, zobacz [vance Morrison blogu](https://docs.microsoft.com/archive/blogs/vancem/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device).  
  
 Można również wywołać PerfView z wiersza polecenia. Aby rejestrować tylko zdarzenia od dostawcy, otwórz okno wiersza polecenia i wprowadź polecenie:  
  
```console
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile
```  
  
 gdzie:  
  
 `-KernelEvents:Process`  
 Wskazuje, że chcesz wiedzieć, kiedy proces się rozpoczyna i zatrzymuje. Musisz process/start zdarzenia dla aplikacji, dzięki czemu można je odjąć od innych czasów zdarzeń.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Wyłącza innych dostawców, których perfView domyślnie włącza, i włącza dostawcę MyCompany-MyApp.  (Gwiazdka wskazuje, że jest <xref:System.Diagnostics.Tracing.EventSource>to .)  
  
 `collect outputFile`  
 Wskazuje, że chcesz rozpocząć zbieranie i zapisać dane w pliku outputFile.etl.zip.  
  
 Uruchom aplikację po uruchomieniu PerfView. Podczas uruchamiania aplikacji należy pamiętać o kilku czynnościach:  
  
- Użyj kompilacji wydania, a nie kompilacji debugowania. Kompilacje debugowania często zawierają dodatkowe sprawdzanie błędów i kod obsługi błędów, który może spowodować, że aplikacja będzie działać wolniej niż oczekiwano.  
  
- Uruchamianie aplikacji z dołączonym debugerem wpływa na wydajność aplikacji.  
  
- System Windows używa wielu strategii buforowania, aby przyspieszyć czas uruchamiania aplikacji. Jeśli aplikacja jest obecnie buforowana w pamięci i nie musi być ładowana z dysku, zostanie uruchomiony szybciej. Aby zapewnić spójność, uruchom i zamknij aplikację kilka razy przed jej pomiarem.  
  
 Po uruchomieniu aplikacji, dzięki czemu PerfView może zbierać emitowane zdarzenia, wybierz przycisk **Zatrzymaj kolekcję.** Ogólnie rzecz biorąc należy zatrzymać kolekcji przed zamknięciem aplikacji, aby nie uzyskać obcych zdarzeń. Jeśli jednak mierzysz wydajność zamykania lub zawieszenia, warto kontynuować zbieranie.  
  
## <a name="displaying-the-events"></a>Wyświetlanie zdarzeń  
 Aby wyświetlić zdarzenia, które zostały już zebrane, użyj programu PerfView, aby otworzyć utworzony plik .etl lub .etl.zip i wybrać **opcję Zdarzenia**. ETW będzie zbierać informacje o dużej liczbie zdarzeń, w tym o wydarzeniach z innych procesów. Aby skupić się na badaniu, wykonaj następujące pola tekstowe w widoku zdarzenia:  
  
- W polu **Filtr procesu** określ nazwę aplikacji (bez ".exe").  
  
- W polu **Filtr typy zdarzeń** określ `Process/Start | MyCompany-MyApp`. Spowoduje to ustawienie filtru zdarzeń z aplikacji MyCompany-MyApp oraz zdarzenia Jądro/Proces/Początek systemu Windows.  
  
 Zaznacz wszystkie zdarzenia wymienione w lewym okienku (Ctrl-A) i wybierz klawisz **Enter.** Teraz powinieneś być w stanie zobaczyć sygnatury czasowe z każdego zdarzenia. Te sygnatury czasowe są względem początku śledzenia, więc należy odjąć czas każdego zdarzenia od czasu rozpoczęcia procesu, aby zidentyfikować czas, jaki upłynął od uruchomienia. Jeśli używasz klawiszy Ctrl+Kliknij, aby wybrać dwie sygnatury czasowe, zobaczysz różnicę między nimi wyświetlaną na pasku stanu u dołu strony. Ułatwia to zobaczenie czasu, który upłynął między dowolnymi dwoma zdarzeniami na wyświetlaczu (w tym rozpoczęciem procesu). Można otworzyć menu skrótów dla widoku i wybrać jedną z wielu przydatnych opcji, takich jak eksportowanie do plików CSV lub otwieranie programu Microsoft Excel w celu zapisania lub przetworzenia danych.  
  
 Powtarzając procedurę zarówno dla oryginalnej aplikacji, jak i wersji utworzonej przy użyciu łańcucha narzędzi natywnych platformy .NET, można porównać różnicę w wydajności.   Aplikacje natywne platformy .NET zazwyczaj uruchamiają się szybciej niż non-.NET aplikacje natywne. Jeśli jesteś zainteresowany kopanie głębiej, PerfView można również zidentyfikować części kodu, które zajmują najwięcej czasu. Aby uzyskać więcej informacji, obejrzyj [samouczki PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) lub przeczytaj [wpis vance Morrison na blogu](https://docs.microsoft.com/archive/blogs/vancem/publication-of-the-perfview-performance-analysis-tool).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Tracing.EventSource>
