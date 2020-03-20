---
title: Zagadnienia dotyczące wydajności (entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 0ff018fe0d8199dcd790bcd3de18751662e0a92b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149742"
---
# <a name="performance-considerations-entity-framework"></a>Zagadnienia dotyczące wydajności (entity Framework)
W tym temacie opisano charakterystyki wydajności ADO.NET entity framework i zawiera pewne zagadnienia, aby poprawić wydajność aplikacji entity framework.  
  
## <a name="stages-of-query-execution"></a>Etapy wykonywania kwerendy  
 Aby lepiej zrozumieć wydajność zapytań w entity framework, jest przydatne do zrozumienia operacji, które występują, gdy kwerenda wykonuje względem modelu koncepcyjnego i zwraca dane jako obiekty. W poniższej tabeli opisano tę serię operacji.  
  
|Operacja|Koszt względny|Częstotliwość|Komentarze|  
|---------------|-------------------|---------------|--------------|  
|Ładowanie metadanych|Średni|Raz w każdej domenie aplikacji.|Metadane modelu i mapowania używane przez <xref:System.Data.Metadata.Edm.MetadataWorkspace>entity framework jest ładowany do . Te metadane są buforowane globalnie i <xref:System.Data.Objects.ObjectContext> są dostępne dla innych wystąpień w tej samej domenie aplikacji.|  
|Otwieranie połączenia z bazą danych|Umiarkowany<sup>1</sup>|W razie potrzeby.|Ponieważ otwarte połączenie z bazą danych zużywa cenny zasób, entity framework otwiera i zamyka połączenie z bazą danych tylko w razie potrzeby. Można również jawnie otworzyć połączenie. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Generowanie widoków|Wysoka|Raz w każdej domenie aplikacji. (Może być wstępnie wygenerowany.)|Zanim entity Framework można wykonać kwerendę względem modelu koncepcyjnego lub zapisać zmiany w źródle danych, musi wygenerować zestaw lokalnych widoków kwerendy, aby uzyskać dostęp do bazy danych. Ze względu na wysokie koszty generowania tych widoków można wstępnie wygenerować widoki i dodać je do projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz [Jak: Wstępnie generować widoki, aby poprawić wydajność kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).|  
|Przygotowywanie kwerendy|Umiarkowany<sup>2</sup>|Raz dla każdego unikatowego zapytania.|Zawiera koszty tworzenia polecenia kwerendy, generowania drzewa poleceń na podstawie metadanych modelu i mapowania oraz definiowania kształtu zwróconych danych. Ponieważ teraz zarówno polecenia kwerendy encji SQL, jak i zapytania LINQ są buforowane, późniejsze wykonania tej samej kwerendy zajmują mniej czasu. Nadal można użyć skompilowanych zapytań LINQ, aby zmniejszyć ten koszt w późniejszych wykonaniach i skompilowanych kwerend może być bardziej wydajne niż zapytania LINQ, które są automatycznie buforowane. Aby uzyskać więcej informacji, zobacz [Skompilowane kwerendy (LINQ do jednostek)](./language-reference/compiled-queries-linq-to-entities.md). Aby uzyskać ogólne informacje na temat wykonywania kwerend LINQ, zobacz [LINQ do jednostek](./language-reference/linq-to-entities.md). **Uwaga:**  LINQ do jednostek kwerendy, które stosują `Enumerable.Contains` operatora do kolekcji w pamięci nie są automatycznie buforowane. Również parametryzowanie kolekcji w pamięci w skompilowanych kwerend LINQ jest niedozwolone.|  
|Wykonywanie kwerendy|Niski<sup>2</sup>|Raz dla każdej kwerendy.|Koszt wykonania polecenia względem źródła danych przy użyciu dostawcy danych ADO.NET. Ponieważ większość źródeł danych buforuje plany kwerend, późniejsze wykonanie tej samej kwerendy może zająć jeszcze mniej czasu.|  
|Ładowanie i sprawdzanie poprawności typów|Niski<sup>3</sup>|Raz dla <xref:System.Data.Objects.ObjectContext> każdego wystąpienia.|Typy są ładowane i sprawdzane względem typów zdefiniowanych przez model koncepcyjny.|  
|Śledzenie|Niski<sup>3</sup>|Raz dla każdego obiektu, który zwraca kwerenda. <sup>4</sup>|Jeśli kwerenda używa <xref:System.Data.Objects.MergeOption.NoTracking> opcji scalania, ten etap nie wpływa na wydajność.<br /><br /> Jeśli kwerenda używa <xref:System.Data.Objects.MergeOption.AppendOnly> <xref:System.Data.Objects.MergeOption.PreserveChanges>opcji <xref:System.Data.Objects.MergeOption.OverwriteChanges> , lub scalania, wyniki <xref:System.Data.Objects.ObjectStateManager>kwerendy są śledzone w pliku . Jest <xref:System.Data.EntityKey> generowany dla każdego śledzonego obiektu, który zwraca <xref:System.Data.Objects.ObjectStateEntry> kwerenda <xref:System.Data.Objects.ObjectStateManager>i jest używany do tworzenia w programie . Jeśli istniejące <xref:System.Data.Objects.ObjectStateEntry> można znaleźć <xref:System.Data.EntityKey>dla , istniejący obiekt jest zwracany. Jeśli <xref:System.Data.Objects.MergeOption.PreserveChanges>używana <xref:System.Data.Objects.MergeOption.OverwriteChanges> jest opcja , lub opcja, obiekt jest aktualizowany przed jego zwrotem.<br /><br /> Aby uzyskać więcej informacji, zobacz [Rozpoznawanie tożsamości, Zarządzanie stanami i Śledzenie zmian](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Materializacja obiektów|Umiarkowany<sup>3</sup>|Raz dla każdego obiektu, który zwraca kwerenda. <sup>4</sup>|Proces odczytywania <xref:System.Data.Common.DbDataReader> zwracanego obiektu i tworzenia obiektów i ustawiania wartości właściwości, <xref:System.Data.Common.DbDataRecord> które są oparte na wartościach w każdym wystąpieniu klasy. Jeśli obiekt już istnieje <xref:System.Data.Objects.ObjectContext> w kwerendzie, <xref:System.Data.Objects.MergeOption.AppendOnly> a <xref:System.Data.Objects.MergeOption.PreserveChanges> kwerenda używa opcji lub scalania, ten etap nie wpływa na wydajność. Aby uzyskać więcej informacji, zobacz [Rozpoznawanie tożsamości, Zarządzanie stanami i Śledzenie zmian](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> Gdy dostawca źródła danych implementuje buforowanie połączeń, koszt otwarcia połączenia jest rozdzielany między pulę. Dostawca platformy .NET dla programu SQL Server obsługuje buforowanie połączeń.  
  
 <sup>2</sup> Koszt wzrasta wraz ze zwiększoną złożonością zapytań.  
  
 <sup>3</sup> Całkowity koszt zwiększa się proporcjonalnie do liczby obiektów zwracanych przez kwerendę.  
  
 <sup>4</sup> To obciążenie nie jest wymagane dla entityclient kwerend, <xref:System.Data.EntityClient.EntityDataReader> ponieważ zapytania EntityClient zwracać zamiast obiektów. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Dodatkowe uwagi  
 Poniżej przedstawiono inne zagadnienia, które mogą mieć wpływ na wydajność aplikacji entity framework.  
  
### <a name="query-execution"></a>Wykonywanie zapytania  
 Ponieważ kwerendy mogą być intensywnie korzystające z zasobów, należy wziąć pod uwagę, w jakim punkcie w kodzie i na jakim komputerze kwerenda jest wykonywana.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odroczone a natychmiastowe wykonanie  
 Podczas tworzenia <xref:System.Data.Objects.ObjectQuery%601> kwerendy lub LINQ kwerenda może nie być wykonywane natychmiast. Wykonanie kwerendy jest odroczone, dopóki wyniki `foreach` są potrzebne, `For Each` takie jak podczas (C#) lub (Visual Basic) wyliczenie lub gdy jest przypisany do wypełnienia <xref:System.Collections.Generic.List%601> kolekcji. Wykonanie kwerendy rozpoczyna się <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> natychmiast <xref:System.Data.Objects.ObjectQuery%601> po wywołaniu metody na lub po wywołaniu metody <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.Any%2A>LINQ, która zwraca kwerendę singleton, taką jak lub . Aby uzyskać więcej informacji, zobacz [Kwerendy obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) i [wykonywanie zapytań (LINQ do jednostek)](./language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Wykonywanie zapytań LINQ po stronie klienta  
 Mimo że wykonanie kwerendy LINQ występuje na komputerze, na którym znajduje się źródło danych, niektóre części zapytania LINQ mogą być oceniane na komputerze klienckim. Aby uzyskać więcej informacji, zobacz sekcję Wykonywanie magazynu [wykonywania kwerend (LINQ do jednostek).](./language-reference/query-execution.md)  
  
### <a name="query-and-mapping-complexity"></a>Złożoność zapytań i mapowania  
 Złożoność poszczególnych zapytań i mapowania w modelu jednostki będzie miała znaczący wpływ na wydajność kwerendy.  
  
#### <a name="mapping-complexity"></a>Złożoność mapowania  
 Modele, które są bardziej złożone niż proste mapowanie jeden do jednego między jednostkami w modelu koncepcyjnym i tabel w modelu magazynu generują bardziej złożone polecenia niż modele, które mają mapowanie jeden do jednego.  
  
#### <a name="query-complexity"></a>Złożoność kwerendy  
 Kwerendy, które wymagają dużej liczby sprzężeń w poleceniach, które są wykonywane względem źródła danych lub które zwracają dużą ilość danych, mogą wpływać na wydajność w następujący sposób:  
  
- Zapytania dotyczące modelu koncepcyjnego, które wydają się proste, mogą spowodować wykonanie bardziej złożonych zapytań względem źródła danych. Może to nastąpić, ponieważ Entity Framework tłumaczy kwerendę względem modelu koncepcyjnego na równoważne zapytanie względem źródła danych. Gdy pojedyncza jednostka ustawiona w modelu koncepcyjnym jest mapowana na więcej niż jedną tabelę w źródle danych lub gdy relacja między jednostkami jest mapowana do tabeli sprzężenia, polecenie kwerendy wykonywane względem kwerendy źródła danych może wymagać co najmniej jednego sprzężenia.  
  
    > [!NOTE]
    > Użyj <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody <xref:System.Data.Objects.ObjectQuery%601> lub <xref:System.Data.EntityClient.EntityCommand> klas, aby wyświetlić polecenia, które są wykonywane względem źródła danych dla danej kwerendy. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie poleceń sklepu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
- Zagnieżdżone encji zapytań SQL może utworzyć sprzężenia na serwerze i może zwrócić dużą liczbę wierszy.  
  
     Poniżej przedstawiono przykład zagnieżdżonej kwerendy w klauzuli rzutowania:  
  
    ```sql  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ponadto takie zapytania powodują potok kwerendy do generowania pojedynczej kwerendy z duplikacji obiektów w kwerendach zagnieżdżonych. Z tego powodu pojedyncza kolumna może być duplikowana wiele razy. W niektórych bazach danych, w tym SQL Server, może to spowodować, że tabela TempDB wzrośnie bardzo duże, co może zmniejszyć wydajność serwera. Należy zwrócić uwagę podczas wykonywania zapytań zagnieżdżonych.  
  
- Wszelkie kwerendy, które zwracają dużą ilość danych może spowodować zmniejszenie wydajności, jeśli klient wykonuje operacje, które zużywają zasoby w sposób, który jest proporcjonalny do rozmiaru zestawu wyników. W takich przypadkach należy rozważyć ograniczenie ilości danych zwracanych przez kwerendę. Aby uzyskać więcej informacji, zobacz [Jak: Wyniki kwerendy na stronie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))—  
  
 Wszystkie polecenia generowane automatycznie przez entity framework może być bardziej skomplikowane niż podobne polecenia napisane jawnie przez dewelopera bazy danych. Jeśli potrzebujesz jawną kontrolę nad poleceniami wykonywanymi dla źródła danych, należy rozważyć zdefiniowanie mapowania do funkcji wycenianej w tabeli lub procedury składowanej.  
  
#### <a name="relationships"></a>Relacje  
 Aby uzyskać optymalną wydajność kwerendy, należy zdefiniować relacje między jednostkami zarówno jako skojarzenia w modelu jednostki, jak i jako relacje logiczne w źródle danych.  
  
### <a name="query-paths"></a>Ścieżki kwerend  
 Domyślnie podczas wykonywania <xref:System.Data.Objects.ObjectQuery%601>, powiązane obiekty nie są zwracane (chociaż obiekty, które reprezentują same relacje są). Powiązane obiekty można załadować na jeden z trzech sposobów:  
  
1. Ustaw ścieżkę kwerendy przed wykonaniem. <xref:System.Data.Objects.ObjectQuery%601>  
  
2. Wywołanie `Load` metody na właściwość nawigacji, który udostępnia obiekt.  
  
3. Ustaw <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> opcję na <xref:System.Data.Objects.ObjectContext> `true`do . Należy zauważyć, że odbywa się to automatycznie podczas generowania kodu warstwy obiektowej za pomocą [projektanta modeli danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Aby uzyskać więcej informacji, zobacz [Omówienie wygenerowanego kodu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Jeśli wziąć pod uwagę, która opcja użyć, należy pamiętać, że istnieje kompromis między liczbą żądań w bazie danych i ilość danych zwracanych w jednej kwerendzie. Aby uzyskać więcej informacji, zobacz [Ładowanie powiązanych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Korzystanie ze ścieżek kwerend  
 Ścieżki kwerend definiują wykres obiektów zwracanych przez kwerendę. Podczas definiowania ścieżki kwerendy, tylko jedno żądanie względem bazy danych jest wymagane do zwrócenia wszystkich obiektów, które ścieżka definiuje. Za pomocą ścieżek kwerend może spowodować złożone polecenia wykonywane względem źródła danych z pozornie prostych zapytań obiektów. Dzieje się tak, ponieważ co najmniej jedno sprzężenia są wymagane do zwrócenia powiązanych obiektów w jednej kwerendzie. Ta złożoność jest większa w kwerendach względem złożonego modelu jednostki, takiego jak jednostka z dziedziczeniem lub ścieżka, która zawiera relacje wiele do wielu.  
  
> [!NOTE]
> Użyj <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody, aby wyświetlić polecenie, <xref:System.Data.Objects.ObjectQuery%601>które zostanie wygenerowane przez plik . Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie poleceń sklepu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
 Jeśli ścieżka kwerendy zawiera zbyt wiele powiązanych obiektów lub obiekty zawierają zbyt dużo danych wiersza, źródło danych może nie być w stanie ukończyć kwerendy. Dzieje się tak, jeśli kwerenda wymaga pośredniego magazynu tymczasowego, który przekracza możliwości źródła danych. W takim przypadku można zmniejszyć złożoność kwerendy źródła danych, jawnie ładując powiązane obiekty.  
  
#### <a name="explicitly-loading-related-objects"></a>Jawne ładowanie powiązanych obiektów  
 Można jawnie załadować powiązanych `Load` obiektów, wywołując metodę <xref:System.Data.Objects.DataClasses.EntityCollection%601> na <xref:System.Data.Objects.DataClasses.EntityReference%601>właściwość nawigacji, która zwraca lub . Jawnie ładowania obiektów wymaga w obie strony `Load` do bazy danych za każdym razem jest wywoływana.  
  
> [!NOTE]
> jeśli wywołasz `Load` podczas zapętlania za pośrednictwem kolekcji `foreach` zwróconych`For Each` obiektów, takich jak podczas korzystania z instrukcji (w języku Visual Basic), dostawca specyficzne dla źródła danych musi obsługiwać wiele aktywnych zestawów wyników na jednym połączeniu. W przypadku bazy danych programu SQL `MultipleActiveResultSets = true` Server należy określić wartość ciągu połączenia dostawcy.  
  
 Można również użyć <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> metody, gdy <xref:System.Data.Objects.DataClasses.EntityCollection%601> <xref:System.Data.Objects.DataClasses.EntityReference%601> nie ma lub właściwości na jednostki. Jest to przydatne, gdy używasz jednostek POCO.  
  
 Chociaż jawne ładowanie powiązanych obiektów zmniejszy liczbę sprzężeń `Load` i zmniejszy ilość nadmiarowych danych, wymaga powtarzających się połączeń z bazą danych, które mogą stać się kosztowne podczas jawnego ładowania dużej liczby obiektów.  
  
### <a name="saving-changes"></a>Zapisywanie zmian  
 Po wywołaniu <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metody <xref:System.Data.Objects.ObjectContext>na , oddzielne tworzenie, aktualizowanie lub usuwanie polecenia jest generowany dla każdego dodanego, zaktualizowanego lub usuniętego obiektu w kontekście. Polecenia te są wykonywane w źródle danych w pojedynczej transakcji. Podobnie jak w przypadku zapytań, wydajność operacji tworzenia, aktualizacji i usuwania zależy od złożoności mapowania w modelu koncepcyjnym.  
  
### <a name="distributed-transactions"></a>Transakcje rozproszone  
 Operacje w jawnej transakcji, które wymagają zasobów, które są zarządzane przez koordynatora transakcji rozproszonych (DTC) będzie znacznie droższe niż podobnej operacji, która nie wymaga usługi DTC. Awans do UOUE nastąpi w następujących sytuacjach:  
  
- Jawna transakcja z operacją względem bazy danych programu SQL Server 2000 lub innego źródła danych, które zawsze promują jawne transakcje do usługi DTC.  
  
- Jawna transakcja z operacją przeciwko programowi SQL Server 2005, gdy połączenie jest zarządzane przez platformę Entity Framework. Dzieje się tak, ponieważ SQL Server 2005 promuje do usługi DTC, gdy połączenie jest zamknięte i ponownie otwarte w ramach jednej transakcji, co jest domyślnym zachowaniem entity framework. Ta promocja usługi DTC nie występuje podczas korzystania z programu SQL Server 2008. Aby uniknąć tej promocji podczas korzystania z programu SQL Server 2005, należy jawnie otworzyć i zamknąć połączenie w ramach transakcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Jawna transakcja jest używana, gdy jedna <xref:System.Transactions> lub więcej operacji są wykonywane wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Strategie poprawy wydajności  
 Można poprawić ogólną wydajność zapytań w entity framework przy użyciu następujących strategii.  
  
#### <a name="pre-generate-views"></a>Wstępne generowanie widoków  
 Generowanie widoków na podstawie modelu jednostki jest kosztem znacznym przy pierwszym wykonaniu kwerendy przez aplikację. Narzędzie EdmGen.exe służy do wstępnego generowania widoków jako pliku kodu języka Visual Basic lub C#, który można dodać do projektu podczas projektowania. Można również użyć zestawu narzędzi do przekształcania szablonów tekstu do generowania wstępnie skompilowanych widoków. Wstępnie wygenerowane widoki są sprawdzane w czasie wykonywania, aby upewnić się, że są one zgodne z bieżącą wersją określonego modelu jednostki. Aby uzyskać więcej informacji, zobacz [Jak: Wstępnie generować widoki, aby poprawić wydajność kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).
  
 Podczas pracy z bardzo dużymi modelami stosuje się następujące kwestie:  
  
 Format metadanych platformy .NET ogranicza liczbę znaków ciągu użytkownika w danym pliku binarnym do 16 777 215 (0xFFFFFFFF). Jeśli generujesz widoki dla bardzo dużego modelu, a plik widoku osiągnie ten limit rozmiaru, otrzymasz "Nie pozostało miejsce logiczne, aby utworzyć więcej ciągów użytkowników". skompilować błąd. To ograniczenie rozmiaru dotyczy wszystkich zarządzanych plików binarnych. Aby uzyskać więcej informacji, zobacz [blog,](https://docs.microsoft.com/archive/blogs/appfabriccat/solving-the-no-logical-space-left-to-create-more-user-strings-error-and-improving-performance-of-pre-generated-views-in-visual-studio-net4-entity-framework) który pokazuje, jak uniknąć błędu podczas pracy z dużymi i złożonymi modelami.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Rozważ użycie opcji scalania NoTracking dla kwerend  
 Istnieje koszt wymagany do śledzenia zwróconych obiektów w kontekście obiektu. Wykrywanie zmian w obiektach i zapewnienie, że wiele żądań dla tej samej <xref:System.Data.Objects.ObjectContext> jednostki logicznej zwraca to samo wystąpienie obiektu, wymaga dołączania obiektów do wystąpienia. Jeśli nie planujesz wprowadzania aktualizacji lub usuwania obiektów i nie <xref:System.Data.Objects.MergeOption.NoTracking> wymagasz zarządzania tożsamościami, należy rozważyć użycie opcji scalania podczas wykonywania kwerend.  
  
#### <a name="return-the-correct-amount-of-data"></a>Zwracanie poprawnej ilości danych  
 W niektórych scenariuszach określanie ścieżki <xref:System.Data.Objects.ObjectQuery%601.Include%2A> kwerendy przy użyciu metody jest znacznie szybsze, ponieważ wymaga mniej rund do bazy danych. Jednak w innych scenariuszach dodatkowe wycieczki w obie strony do bazy danych w celu załadowania powiązanych obiektów może być szybsze, ponieważ prostsze zapytania z mniejszą liczbą sprzężeń spowodować mniejszą nadmiarowość danych. Z tego powodu zaleca się przetestowanie wydajności różnych sposobów pobierania powiązanych obiektów. Aby uzyskać więcej informacji, zobacz [Ładowanie powiązanych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Aby uniknąć zwracania zbyt dużej ilości danych w jednej kwerendzie, należy wziąć pod uwagę stronicowanie wyników kwerendy do grup łatwiej zarządzaniu. Aby uzyskać więcej informacji, zobacz [Jak: Wyniki kwerendy na stronie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))—  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Ograniczanie zakresu obiektuContext  
 W większości przypadków należy <xref:System.Data.Objects.ObjectContext> utworzyć wystąpienie w instrukcji `using` (w`Using…End Using` języku Visual Basic). Może to zwiększyć wydajność, zapewniając, że zasoby skojarzone z kontekstem obiektu są usuwane automatycznie, gdy kod kończy blok instrukcji. Jednak gdy formanty są powiązane z obiektami zarządzanymi przez kontekst obiektu, <xref:System.Data.Objects.ObjectContext> wystąpienie powinno być obsługiwane tak długo, jak powiązanie jest potrzebne i usuwane ręcznie. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Rozważ ręczne otwarcie połączenia z bazą danych  
 Gdy aplikacja wykonuje serię zapytań o obiekt <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> lub często wywołuje do utrwalania operacji tworzenia, aktualizacji i usuwania do źródła danych, Entity Framework musi stale otwierać i zamykać połączenie ze źródłem danych. W takich sytuacjach należy rozważyć ręczne otwarcie połączenia na początku tych operacji i zamknięcie lub usunięcie połączenia po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Dane wydajności  
 Niektóre dane dotyczące wydajności dla entity framework jest publikowany w następujących wpisach na [ADO.NET blogu zespołu:](https://docs.microsoft.com/archive/blogs/adonet/)  
  
- [Badanie wydajności ADO.NET entity framework - część 1](https://docs.microsoft.com/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-1)  
  
- [Badanie wydajności ADO.NET entity framework – część 2](https://docs.microsoft.com/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-2)  
  
- [Porównanie wydajności ADO.NET entity framework](https://docs.microsoft.com/archive/blogs/adonet/ado-net-entity-framework-performance-comparison)  
  
## <a name="see-also"></a>Zobacz też

- [Projektowanie i zagadnienia dotyczące wdrażania](development-and-deployment-considerations.md)
