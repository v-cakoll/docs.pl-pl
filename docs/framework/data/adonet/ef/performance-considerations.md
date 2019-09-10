---
title: Zagadnienia dotyczące wydajności (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: eb46b183ec1e930dfe5c4a1eea237024033c357d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854601"
---
# <a name="performance-considerations-entity-framework"></a>Zagadnienia dotyczące wydajności (Entity Framework)
W tym temacie opisano charakterystyki wydajności ADO.NET Entity Framework i przedstawiono kilka kwestii, które pomogą ulepszyć wydajność aplikacji Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Etapy wykonywania zapytania  
 Aby lepiej zrozumieć wydajność zapytań w Entity Framework, warto zrozumieć operacje wykonywane, gdy zapytanie jest wykonywane względem modelu koncepcyjnego i zwraca dane jako obiekty. W poniższej tabeli opisano tę serię operacji.  
  
|Operacja|Koszt względny|Częstotliwość|Komentarze|  
|---------------|-------------------|---------------|--------------|  
|Ładowanie metadanych|Zawartość|Jeden raz w każdej domenie aplikacji.|Metadane modelu i mapowania używane przez Entity Framework są ładowane do <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Te metadane są buforowane globalnie i są dostępne dla innych wystąpień <xref:System.Data.Objects.ObjectContext> w tej samej domenie aplikacji.|  
|Otwieranie połączenia z bazą danych|Umiarkowane<sup>1</sup>|Zgodnie z wymaganiami.|Ponieważ otwarte połączenie z bazą danych zużywa cenny zasób, Entity Framework otwiera i zamyka połączenie z bazą danych tylko w razie potrzeby. Możesz również jawnie otworzyć połączenie. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Generowanie widoków|Wysoka|Jeden raz w każdej domenie aplikacji. (Można wstępnie wygenerować).|Zanim Entity Framework będzie mogła wykonać zapytanie względem modelu koncepcyjnego lub zapisać zmiany w źródle danych, musi wygenerować zestaw lokalnych widoków zapytań, aby uzyskać dostęp do bazy danych. Ze względu na wysoki koszt generowania tych widoków można wstępnie wygenerować widoki i dodać je do projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz [jak: Wstępnie Generuj widoki, aby zwiększyć wydajność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))zapytań.|  
|Przygotowywanie zapytania|Umiarkowane<sup>2</sup>|Jednokrotnie dla każdego unikatowego zapytania.|Obejmuje koszty tworzenia polecenia zapytania, generowania drzewa poleceń na podstawie modelu i metadanych mapowania oraz definiowania kształtu zwracanych danych. Ponieważ teraz zarówno Entity SQL polecenia zapytania i zapytania LINQ są buforowane, późniejsze wykonywanie tego samego zapytania trwa krócej. Można nadal używać skompilowanych zapytań LINQ, aby ograniczyć ten koszt do późniejszych wykonań, a skompilowane zapytania mogą być bardziej wydajne niż zapytania LINQ, które są automatycznie buforowane. Aby uzyskać więcej informacji, zobacz [skompilowane zapytania (LINQ to Entities)](./language-reference/compiled-queries-linq-to-entities.md). Aby uzyskać ogólne informacje na temat wykonywania zapytań LINQ, zobacz [LINQ to Entities](./language-reference/linq-to-entities.md). **Uwaga:**  LINQ to Entities zapytania, które stosują `Enumerable.Contains` operator do kolekcji w pamięci, nie są automatycznie buforowane. Parametryzacja również kolekcje w pamięci w skompilowanych zapytaniach LINQ są niedozwolone.|  
|Wykonywanie zapytania|Niski<sup>2</sup>|Jeden raz dla każdego zapytania.|Koszt wykonywania polecenia względem źródła danych przy użyciu dostawcy danych ADO.NET. Ze względu na to, że większość źródeł danych buforuje plany zapytań, późniejsze wykonania tego samego zapytania mogą trwać nawet krócej.|  
|Ładowanie i sprawdzanie poprawności typów|Niski<sup>3</sup>|Jeden raz dla <xref:System.Data.Objects.ObjectContext> każdego wystąpienia.|Typy są ładowane i sprawdzane pod kątem typów, które definiuje model koncepcyjny.|  
|Śledzenie|Niski<sup>3</sup>|Jeden raz dla każdego obiektu zwracanego przez zapytanie. <sup>4</sup>|Jeśli zapytanie używa <xref:System.Data.Objects.MergeOption.NoTracking> opcji scalania, ten etap nie ma wpływu na wydajność.<br /><br /> Jeśli <xref:System.Data.Objects.MergeOption.AppendOnly>zapytanie używa <xref:System.Data.Objects.MergeOption.PreserveChanges> opcji,<xref:System.Data.Objects.MergeOption.OverwriteChanges> lub scalania, wyniki zapytania są śledzone w. <xref:System.Data.Objects.ObjectStateManager> Generowany jest dla każdego śledzonego obiektu zwracanego przez zapytanie i służy do tworzenia w <xref:System.Data.Objects.ObjectStateManager>obiekcie <xref:System.Data.Objects.ObjectStateEntry>. <xref:System.Data.EntityKey> Jeśli istniejący <xref:System.Data.Objects.ObjectStateEntry> element można znaleźć <xref:System.Data.EntityKey>dla, zwracany jest istniejący obiekt. Jeśli jest używana opcja <xref:System.Data.Objects.MergeOption.OverwriteChanges> lub, obiekt jest aktualizowany przed zwróceniem. <xref:System.Data.Objects.MergeOption.PreserveChanges><br /><br /> Aby uzyskać więcej informacji, zobacz [rozpoznawanie tożsamości, zarządzanie stanami i Change Tracking](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Materializacji obiekty|Umiarkowane<sup>3</sup>|Jeden raz dla każdego obiektu zwracanego przez zapytanie. <sup>4</sup>|Proces odczytywania zwracanego <xref:System.Data.Common.DbDataReader> obiektu i tworzenia obiektów oraz ustawiania wartości właściwości, które są oparte na wartościach każdego wystąpienia <xref:System.Data.Common.DbDataRecord> klasy. Jeśli obiekt już istnieje w <xref:System.Data.Objects.ObjectContext> , a zapytanie <xref:System.Data.Objects.MergeOption.AppendOnly> używa opcji lub <xref:System.Data.Objects.MergeOption.PreserveChanges> scalania, ten etap nie ma wpływu na wydajność. Aby uzyskać więcej informacji, zobacz [rozpoznawanie tożsamości, zarządzanie stanami i Change Tracking](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> gdy dostawca źródła danych implementuje pulę połączeń, koszt otwarcia połączenia jest dystrybuowany w całej puli. Dostawca platformy .NET dla SQL Server obsługuje pule połączeń.  
  
 <sup>2</sup> koszty zwiększają się z większą złożonością zapytań.  
  
 <sup>3</sup> łączny koszt zwiększa się proporcjonalnie do liczby obiektów zwracanych przez zapytanie.  
  
 <sup>4</sup> ten koszt nie jest wymagany w przypadku zapytań EntityClient, <xref:System.Data.EntityClient.EntityDataReader> ponieważ zapytania EntityClient zwracają obiekty zamiast obiektów. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Poniżej przedstawiono inne zagadnienia, które mogą mieć wpływ na wydajność aplikacji Entity Framework.  
  
### <a name="query-execution"></a>Wykonywanie zapytania  
 Ponieważ zapytania mogą być intensywnie obciążające zasoby, warto zastanowić się, w jakim miejscu kodu i na komputerze, na którym jest wykonywane zapytanie.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odroczone względem natychmiastowego wykonania  
 Po utworzeniu zapytania programu <xref:System.Data.Objects.ObjectQuery%601> lub LINQ zapytanie może nie zostać wykonane od razu. Wykonywanie zapytania jest odroczone do momentu, gdy nie będą one konieczne, na `foreach` przykładC#podczas wyliczania () lub `For Each` (Visual Basic) lub <xref:System.Collections.Generic.List%601> po przypisaniu do wypełnienia kolekcji. Wykonywanie zapytania rozpoczyna się natychmiast po <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> wywołaniu metody <xref:System.Data.Objects.ObjectQuery%601> na lub wywołaniu metody LINQ, która zwraca zapytanie pojedyncze, takie jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Any%2A>. Aby uzyskać więcej informacji, zobacz [zapytania dotyczące obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) i [wykonywanie zapytań (LINQ to Entities)](./language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Wykonywanie zapytań LINQ po stronie klienta  
 Mimo że wykonywanie zapytania LINQ odbywa się na komputerze hostującym źródło danych, niektóre części zapytania LINQ mogą być oceniane na komputerze klienckim. Aby uzyskać więcej informacji, zobacz sekcję wykonywanie w sklepie [wykonywania zapytania (LINQ to Entities)](./language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Złożoność zapytań i mapowania  
 Złożoność poszczególnych zapytań i mapowania w modelu jednostki będą mieć znaczny wpływ na wydajność zapytań.  
  
#### <a name="mapping-complexity"></a>Złożoność mapowania  
 Modele, które są bardziej złożone niż proste mapowanie jeden do jednego między jednostkami w modelu koncepcyjnym i tabelach w modelu magazynu, generują bardziej złożone polecenia niż modele, które mają mapowanie jeden do jednego.  
  
#### <a name="query-complexity"></a>Złożoność zapytania  
 Zapytania, które wymagają dużej liczby sprzężeń w poleceniach, które są wykonywane względem źródła danych lub zwracają znaczną ilość danych, mogą mieć wpływ na wydajność w następujący sposób:  
  
- Zapytania względem modelu koncepcyjnego, który wydaje się proste, mogą spowodować wykonanie bardziej złożonych zapytań względem źródła danych. Taka sytuacja może wystąpić, ponieważ Entity Framework tłumaczy zapytanie względem modelu koncepcyjnego na równoważne zapytanie względem źródła danych. Gdy pojedynczy obiekt ustawiony w modelu koncepcyjnym mapuje się do więcej niż jednej tabeli w źródle danych lub jeśli relacja między jednostkami jest zamapowana na tabelę sprzężeń, polecenie zapytania wykonane względem zapytania źródła danych może wymagać co najmniej jednego sprzężenia.  
  
    > [!NOTE]
    > <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> Użyj metody <xref:System.Data.Objects.ObjectQuery%601> lub ,abywyświetlićpolecenia,któresąwykonywanewzględemźródładanychdladanegozapytania.<xref:System.Data.EntityClient.EntityCommand> Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie poleceń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))magazynu.  
  
- Zagnieżdżone zapytania Entity SQL mogą tworzyć sprzężenia na serwerze i zwracać dużą liczbę wierszy.  
  
     Poniżej znajduje się przykład zagnieżdżonego zapytania w klauzuli projekcji:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ponadto takie zapytania powodują, że potok zapytania generuje pojedyncze zapytanie z duplikowaniem obiektów w zagnieżdżonych zapytaniach. Z tego powodu jedna kolumna może być zduplikowana wiele razy. W przypadku niektórych baz danych, w tym SQL Server, może to spowodować duże powiększenie tabeli TempDB, co może zmniejszyć wydajność serwera. Należy zachować ostrożność podczas wykonywania zagnieżdżonych zapytań.  
  
- Wszystkie zapytania, które zwracają duże ilości danych, mogą spowodować spadek wydajności, jeśli klient wykonuje operacje, które zużywają zasoby w sposób proporcjonalny do rozmiaru zestawu wyników. W takich przypadkach należy rozważyć ograniczenie ilości danych zwracanych przez zapytanie. Aby uzyskać więcej informacji, zobacz [jak: Na stronie za poorednictwem](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))wyników zapytania.  
  
 Wszystkie polecenia generowane automatycznie przez Entity Framework mogą być bardziej skomplikowane niż podobne polecenia, które są jawnie zapisywane przez dewelopera bazy danych. Jeśli potrzebujesz jawnej kontroli nad poleceniami wykonywanymi względem źródła danych, rozważ zdefiniowanie mapowania do funkcji zwracającej tabelę lub procedury składowanej.  
  
#### <a name="relationships"></a>Relacje  
 Aby zapewnić optymalną wydajność zapytań, należy zdefiniować relacje między jednostkami zarówno jako skojarzenia w modelu jednostki, jak i jako relacje logiczne w źródle danych.  
  
### <a name="query-paths"></a>Ścieżki zapytań  
 Domyślnie podczas wykonywania <xref:System.Data.Objects.ObjectQuery%601>obiekty powiązane nie są zwracane (chociaż obiekty reprezentujące same relacje są). Obiekty powiązane można ładować na jeden z trzech sposobów:  
  
1. Ustaw ścieżkę zapytania przed <xref:System.Data.Objects.ObjectQuery%601> wykonaniem.  
  
2. Wywołaj `Load` metodę dla właściwości nawigacji, która uwidacznia obiekt.  
  
3. <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> Ustaw opcję<xref:System.Data.Objects.ObjectContext> na .`true` Należy zauważyć, że jest to wykonywane automatycznie podczas generowania kodu warstwy obiektu za pomocą [projektanta Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Aby uzyskać więcej informacji, zobacz [Omówienie wygenerowanego kodu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Jeśli zdecydujesz się na użycie opcji, pamiętaj, że istnieje kompromis między liczbą żądań względem bazy danych i ilością danych zwracanych w jednym zapytaniu. Aby uzyskać więcej informacji, zobacz [ładowanie powiązanych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Używanie ścieżek zapytania  
 Ścieżki zapytań definiują wykres obiektów zwracanych przez zapytanie. Podczas definiowania ścieżki zapytania tylko jedno żądanie dotyczące bazy danych jest wymagane do zwrócenia wszystkich obiektów, które definiuje ścieżka. Użycie ścieżek zapytania może spowodować, że złożone polecenia są wykonywane względem źródła danych z pozornie prostych zapytań obiektów. Dzieje się tak, ponieważ co najmniej jedno sprzężenie jest wymagane do zwrócenia obiektów pokrewnych w pojedynczym zapytaniu. Ta złożoność jest większa w przypadku zapytań względem złożonego modelu Entity, takiego jak jednostka z dziedziczeniem lub ścieżka, która zawiera relacje wiele-do-wielu.  
  
> [!NOTE]
> Użyj metody, aby zobaczyć polecenie, które zostanie wygenerowane <xref:System.Data.Objects.ObjectQuery%601>przez. <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie poleceń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100))magazynu.  
  
 Gdy ścieżka zapytania zawiera zbyt wiele powiązanych obiektów lub obiekty zawierają zbyt dużo danych wierszy, źródło danych może nie być w stanie zakończyć zapytania. Dzieje się tak, jeśli zapytanie wymaga pośredniego tymczasowego magazynu, który przekracza możliwości źródła danych. W takim przypadku można zmniejszyć złożoność zapytania źródła danych, jawnie ładując powiązane obiekty.  
  
#### <a name="explicitly-loading-related-objects"></a>Jawne ładowanie powiązanych obiektów  
 Można jawnie załadować powiązane obiekty przez wywołanie `Load` metody dla właściwości nawigacji, która <xref:System.Data.Objects.DataClasses.EntityCollection%601> zwraca lub <xref:System.Data.Objects.DataClasses.EntityReference%601>. Jawne ładowanie obiektów wymaga przeprowadzenia rundy do bazy danych za każdym razem `Load` , gdy jest wywoływana.  
  
> [!NOTE]
> w przypadku wywołania `Load` podczas zapętlania za pomocą kolekcji zwróconych obiektów, takich jak `foreach` użycie instrukcji (`For Each` w Visual Basic), dostawca specyficzny dla źródła danych musi obsługiwać wiele aktywnych zestawów wyników na jednym połączenia. `MultipleActiveResultSets = true` W przypadku bazy danych SQL Server należy określić wartość w parametrach połączenia dostawcy.  
  
 Możesz również użyć metody, <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> Jeśli <xref:System.Data.Objects.DataClasses.EntityReference%601> nie ma żadnych <xref:System.Data.Objects.DataClasses.EntityCollection%601> właściwości w jednostkach. Jest to przydatne w przypadku korzystania z jednostek POCO.  
  
 Mimo że jawne ładowanie powiązanych obiektów zmniejsza liczbę sprzężeń i zmniejsza ilość nadmiarowych danych, `Load` wymaga powtarzających się połączeń z bazą danych, co może być kosztowne w przypadku jawnego ładowania dużej liczby obiektów.  
  
### <a name="saving-changes"></a>Zapisywanie zmian  
 Po wywołaniu <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metody <xref:System.Data.Objects.ObjectContext>na, oddzielnym poleceniem Create, Update lub DELETE jest generowane dla każdego dodanego, zaktualizowanego lub usuniętego obiektu w kontekście. Te polecenia są wykonywane na źródle danych w jednej transakcji. Podobnie jak w przypadku zapytań, wydajność operacji tworzenia, aktualizowania i usuwania zależy od złożoności mapowania w modelu koncepcyjnym.  
  
### <a name="distributed-transactions"></a>Transakcje rozproszone  
 Operacje w jawnej transakcji, które wymagają zasobów zarządzanych przez koordynatora transakcji rozproszonych (DTC), będą znacznie droższe niż podobna operacja, która nie wymaga usługi DTC. Podwyższanie poziomu usługi DTC będzie odbywać się w następujących sytuacjach:  
  
- Transakcja jawna z operacją w odniesieniu do bazy danych SQL Server 2000 lub innego źródła danych, które zawsze Podnieś poziom jawnych transakcji do usługi DTC.  
  
- Transakcja jawna z operacją w odniesieniu do SQL Server 2005, gdy połączenie jest zarządzane przez Entity Framework. Dzieje się tak, ponieważ SQL Server 2005 podwyższa do usługi DTC przy każdym zamknięciu i ponownym otwarciu połączenia w ramach jednej transakcji, która jest domyślnym zachowaniem Entity Framework. Ta promocja usługi DTC nie występuje w przypadku korzystania z SQL Server 2008. Aby uniknąć tego podwyższania poziomu w przypadku korzystania z SQL Server 2005, należy jawnie otworzyć i zamknąć połączenie w ramach transakcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Transakcja jawna jest używana, gdy co najmniej jedna operacja jest wykonywana wewnątrz <xref:System.Transactions> transakcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Strategie zwiększania wydajności  
 Można zwiększyć ogólną wydajność zapytań w Entity Framework, korzystając z poniższych strategii.  
  
#### <a name="pre-generate-views"></a>Wstępnie Generuj widoki  
 Generowanie widoków opartych na modelu jednostki jest istotnym kosztem podczas pierwszego wykonywania zapytania przez aplikację. Użyj narzędzia EdmGen. exe, aby wstępnie wygenerować widoki jako plik Visual Basic lub C# kod, który można dodać do projektu podczas projektowania. Można również użyć zestawu narzędzi do przekształcania szablonów tekstowych do generowania wstępnie skompilowanych widoków. Wstępnie wygenerowane widoki są weryfikowane w czasie wykonywania, aby upewnić się, że są one spójne z bieżącą wersją określonego modelu Entity. Aby uzyskać więcej informacji, zobacz [jak: Wstępnie Generuj widoki, aby zwiększyć wydajność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))zapytań.
  
 Podczas pracy z bardzo dużymi modelami stosuje się następujące zagadnienia:  
  
 Format metadanych .NET ogranicza liczbę znaków ciągu użytkownika w danym pliku binarnym do 16 777 215 (0xFFFFFF). Jeśli tworzysz widoki dla bardzo dużego modelu, a plik widoku osiągnie ten limit rozmiaru, otrzymasz wartość "Brak pustego miejsca logicznego, aby utworzyć więcej ciągów użytkownika". błąd kompilacji. To ograniczenie rozmiaru dotyczy wszystkich zarządzanych plików binarnych. Aby uzyskać więcej informacji, zobacz [blog](https://go.microsoft.com/fwlink/?LinkId=201476) pokazujący, jak uniknąć błędu podczas pracy z dużymi i złożonymi modelami.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Rozważ użycie opcji scalania NoTracking dla zapytań  
 Istnieje koszt wymagany do śledzenia zwracanych obiektów w kontekście obiektu. Wykrywanie zmian obiektów i zagwarantowanie, że wiele żądań dla tej samej jednostki logicznej zwróci to samo wystąpienie obiektu, wymagane jest dołączenie obiektów do <xref:System.Data.Objects.ObjectContext> wystąpienia. Jeśli nie planujesz przeprowadzać aktualizacji ani usunięć dla obiektów i nie wymagają zarządzania tożsamościami, rozważ użycie <xref:System.Data.Objects.MergeOption.NoTracking> opcji scalania podczas wykonywania zapytań.  
  
#### <a name="return-the-correct-amount-of-data"></a>Zwróć poprawną ilość danych  
 W niektórych scenariuszach Określanie ścieżki zapytania przy użyciu <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metody jest znacznie szybsze, ponieważ wymaga mniejszej liczby rund do bazy danych. Jednak w innych scenariuszach dodatkowe podróże do bazy danych w celu załadowania powiązanych obiektów mogą być szybsze, ponieważ prostsze zapytania z mniejszą liczbą sprzężeń powodują mniejszą nadmiarowość danych. W związku z tym zalecamy przetestowanie wydajności różnych metod pobierania obiektów pokrewnych. Aby uzyskać więcej informacji, zobacz [ładowanie powiązanych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Aby uniknąć powrotu zbyt dużej ilości danych w jednym zapytaniu, należy rozważyć stronicowanie wyników zapytania w celu łatwiejszego zarządzania grupami. Aby uzyskać więcej informacji, zobacz [jak: Na stronie za poorednictwem](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))wyników zapytania.  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Ogranicz zakres obiektu ObjectContext  
 W większości przypadków należy utworzyć <xref:System.Data.Objects.ObjectContext> wystąpienie `using` wewnątrz instrukcji (`Using…End Using` w Visual Basic). Może to zwiększyć wydajność, upewniając się, że zasoby skojarzone z kontekstem obiektu są usuwane automatycznie, gdy kod opuszcza blok instrukcji. Jeśli jednak formanty są powiązane z obiektami zarządzanymi przez kontekst obiektu, <xref:System.Data.Objects.ObjectContext> wystąpienie powinno być utrzymywane o ile jest to konieczne i usunięte ręcznie. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Rozważ ręczne otworzenie połączenia z bazą danych  
 Gdy aplikacja wykonuje serię zapytań obiektów lub często wywołuje <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> do źródła danych operacje tworzenia, aktualizowania i usuwania, Entity Framework musi ciągle otwierać i zamykać połączenie ze źródłem danych. W takich sytuacjach należy rozważyć ręczne otwarcie połączenia na początku tych operacji oraz zamknięcie lub odłączenie połączenia po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcjami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Dane wydajności  
 Niektóre dane dotyczące wydajności Entity Framework są publikowane w następujących wpisach na [blogu zespołu ADO.NET](https://go.microsoft.com/fwlink/?LinkId=91905):  
  
- [Eksplorowanie wydajności Entity Framework ADO.NET — część 1](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
- [Eksplorowanie wydajności Entity Framework ADO.NET — część 2](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
- [Porównanie wydajności Entity Framework ADO.NET](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie i zagadnienia dotyczące wdrażania](development-and-deployment-considerations.md)
