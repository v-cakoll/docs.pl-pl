---
title: Zagadnienia dotyczące wydajności (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: ec7f3571f60dc7f10816cad90911e50d271a9ce1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324048"
---
# <a name="performance-considerations-entity-framework"></a>Zagadnienia dotyczące wydajności (Entity Framework)
W tym temacie opisano charakterystyki wydajności ADO.NET Entity Framework i zapewnia pewne kwestie dotyczące poprawy wydajności aplikacji platformy Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Etapy wykonywania zapytania  
 Aby lepiej zrozumieć wydajność zapytań w programie Entity Framework, jest przydatne informacje o operacjach, które występują, gdy zapytanie wykonuje względem modelu koncepcyjnego i zwraca dane jako obiekty. W poniższej tabeli opisano w tej serii operacji.  
  
|Operacja|Względny koszt|Częstotliwość|Komentarze|  
|---------------|-------------------|---------------|--------------|  
|Ładowanie metadanych|Średni|Jeden raz w każdej domenie aplikacji.|Metadanych modelu i mapowanie, które są używane przez program Entity Framework jest ładowany do <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Te metadane są buforowane globalnie i jest dostępny dla innych wystąpień <xref:System.Data.Objects.ObjectContext> w tej samej domenie aplikacji.|  
|Otwieranie połączenia z bazą danych|Umiarkowany<sup>1</sup>|Zgodnie z potrzebami.|Ponieważ otwartego połączenia z bazą danych zużywa cenne zasobów [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] otwiera i zamyka połączenie z bazą danych, stosownie do potrzeb. Można także jawnie Otwórz połączenie. Aby uzyskać więcej informacji, zobacz [zarządzania połączeniami i transakcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Generowanie widoków|Wysoka|Jeden raz w każdej domenie aplikacji. (Można wstępnie wygenerować.)|Zanim Entity Framework można wykonać zapytanie do modelu koncepcyjnego i zapisać zmiany w źródle danych, go wygenerować zestaw widoków zapytań lokalnego dostępu do bazy danych. Ze względu na wysokich kosztów generowania tych widoków można wstępnie wygenerować widoków i dodać je do projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz [jak: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).|  
|Trwa przygotowywanie zapytania|Umiarkowany<sup>2</sup>|Tylko jeden raz dla każdego zapytania unikatowy.|Obejmuje koszty do redagowania polecenia zapytań, generowania drzewo poleceń, na podstawie modelu i mapowania metadanych i określenia kształtu elementu zwracanych danych. Ponieważ teraz są buforowane w poleceniach zapytań jednostki SQL i zapytań LINQ, nowsze wykonania tego samego zapytania trwa krócej. Nadal umożliwia zapytania LINQ skompilowane obniżyć ten koszt w późniejszym wykonań i zapytania skompilowane może być bardziej efektywne niż zapytań LINQ, które są automatycznie buforowane. Aby uzyskać więcej informacji, zobacz [zapytania skompilowane (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). Aby uzyskać ogólne informacje na temat wykonywania zapytań LINQ, zobacz [składnik LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Uwaga:**  LINQ do zapytań jednostek, które są stosowane `Enumerable.Contains` operator z kolekcjami w pamięci nie są automatycznie buforowane. Również parametryzacja kolekcji w skompilowanych zapytań LINQ w pamięci nie jest dozwolone.|  
|Wykonywanie zapytania|Niska<sup>2</sup>|Tylko jeden raz dla każdego zapytania.|Koszt wykonywania poleceń względem źródła danych przy użyciu dostawcy danych ADO.NET. Ponieważ większości źródeł danych w pamięci podręcznej planów zapytań, nowsze wykonania tego samego zapytania może potrwać nawet mniej czasu.|  
|Ładowanie i sprawdzanie poprawności typów|Niska<sup>3</sup>|Jeden raz dla każdego <xref:System.Data.Objects.ObjectContext> wystąpienia.|Typy jest ładowany i zweryfikować względem typów, które definiuje modelu koncepcyjnego.|  
|Śledzenie|Niska<sup>3</sup>|Tylko jeden raz dla każdego obiektu, która zwraca kwerendy. <sup>4</sup>|Jeśli zapytanie używa <xref:System.Data.Objects.MergeOption.NoTracking> opcja scalania, tym etapie nie ma wpływu na wydajność.<br /><br /> Jeśli zapytanie używa <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>, lub <xref:System.Data.Objects.MergeOption.OverwriteChanges> merge — opcja, zapytanie, wyniki są śledzone w <xref:System.Data.Objects.ObjectStateManager>. <xref:System.Data.EntityKey> Jest generowany dla każdego śledzonego obiektu, zapytanie zwracające i jest używany do tworzenia <xref:System.Data.Objects.ObjectStateEntry> w <xref:System.Data.Objects.ObjectStateManager>. Jeśli istniejące <xref:System.Data.Objects.ObjectStateEntry> można znaleźć <xref:System.Data.EntityKey>, istniejący obiekt jest zwracany. Jeśli <xref:System.Data.Objects.MergeOption.PreserveChanges>, lub <xref:System.Data.Objects.MergeOption.OverwriteChanges> jest używana opcja, obiekt zostanie zaktualizowany przed zwróceniem.<br /><br /> Aby uzyskać więcej informacji, zobacz [rozwiązanie tożsamości, zarządzania stanem i śledzenia zmian](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Materializowanie obiektów|Umiarkowany<sup>3</sup>|Tylko jeden raz dla każdego obiektu, która zwraca kwerendy. <sup>4</sup>|Proces odczytu zwracanego <xref:System.Data.Common.DbDataReader> obiektu i tworzenia obiektów i ustawiania wartości właściwości, które są oparte na wartości w każdym wystąpieniu <xref:System.Data.Common.DbDataRecord> klasy. Jeśli ten obiekt już istnieje w <xref:System.Data.Objects.ObjectContext> i zapytanie używa <xref:System.Data.Objects.MergeOption.AppendOnly> lub <xref:System.Data.Objects.MergeOption.PreserveChanges> opcji scalania, tym etapie nie ma wpływu na wydajność. Aby uzyskać więcej informacji, zobacz [rozwiązanie tożsamości, zarządzania stanem i śledzenia zmian](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> gdy dostawca źródła danych implementuje buforowanie połączeń, koszt otwarcia połączenia są rozproszone w puli. Dostawcy .NET dla programu SQL Server obsługuje buforowanie połączeń.  
  
 <sup>2</sup> koszt zwiększa się wraz z złożoności zapytania zwiększone.  
  
 <sup>3</sup> zwiększa całkowity koszt jest proporcjonalna do liczby obiektów zwróconych przez zapytanie.  
  
 <sup>4</sup> to obciążenie nie jest wymagana dla EntityClient zapytania, ponieważ dostawca EntityClient zapytania zwrócenia <xref:System.Data.EntityClient.EntityDataReader> zamiast obiektów. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Poniżej przedstawiono inne zagadnienia, które mogą wpłynąć na wydajność aplikacji platformy Entity Framework.  
  
### <a name="query-execution"></a>Wykonywanie zapytania  
 Zapytania mogą być dużej ilości zasobów, należy rozważyć, w którym momencie w kodzie, jak i na komputerze, na jakie zapytanie jest wykonywane.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odroczone a natychmiastowe wykonanie  
 Po utworzeniu <xref:System.Data.Objects.ObjectQuery%601> lub zapytanie LINQ, kwerenda nie może zostać wykonana natychmiast. Wykonanie zapytania jest odroczone do czasu wyniki są wymagane, takie jak podczas `foreach` (C#) lub `For Each` wyliczenia (Visual Basic) lub gdy jest przypisany do wypełnienia <xref:System.Collections.Generic.List%601> kolekcji. Wykonywanie zapytania, rozpoczyna się natychmiast, gdy zostanie wywołana <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> metody <xref:System.Data.Objects.ObjectQuery%601> lub po wywołaniu metody LINQ zwraca pojedynczych zapytań, takich jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Any%2A>. Aby uzyskać więcej informacji, zobacz [zapytań dotyczących obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) i [wykonywania zapytania (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Wykonywanie zapytań LINQ po stronie klienta  
 Mimo że wykonywanie zapytań LINQ występuje na komputerze, który jest hostem źródła danych, niektórych części zapytania LINQ, może być oceniana na komputerze klienckim. Aby uzyskać więcej informacji, zobacz sekcję wykonywania Store [wykonywania zapytania (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Zapytania i mapowanie złożoności  
 Złożoność pojedynczych zapytań i mapowania w modelu jednostki mają znaczący wpływ na wydajność zapytań.  
  
#### <a name="mapping-complexity"></a>Mapowanie złożoności  
 Modele, które są bardziej skomplikowane niż prostego mapowanie jeden do jednego między jednostkami w modelu koncepcyjnym i tabele w modelu magazynu Generowanie poleceń bardziej skomplikowane niż modele, które mają mapowanie jeden do jednego.  
  
#### <a name="query-complexity"></a>Złożoności zapytania  
 Zapytania wymagające dużej liczby sprzężeń za pomocą poleceń, które są wykonywane względem źródła danych lub dużej ilości danych zwracanych może mieć wpływ na wydajność, w następujący sposób:  
  
-   Zapytania względem modelu koncepcyjnego, które wydają się proste może spowodować wykonanie bardziej złożone zapytania względem źródła danych. Taka sytuacja może wystąpić, ponieważ zapytanie do modelu koncepcyjnego Entity Framework przekłada się na równoważne zapytania względem źródła danych. Gdy pojedynczej jednostki modelu koncepcyjnego mapuje do więcej niż jednej tabeli w źródle danych, lub gdy relacji między jednostkami jest mapowany na tabelę sprzężenia, polecenie zapytania wykonywane zapytania do źródła danych może wymagać sprzężenia jeden lub więcej.  
  
    > [!NOTE]
    >  Użyj <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody <xref:System.Data.Objects.ObjectQuery%601> lub <xref:System.Data.EntityClient.EntityCommand> klasy, aby wyświetlić polecenia, które są wykonywane względem źródła danych dla danego zapytania. Aby uzyskać więcej informacji, zobacz [jak: Wyświetl polecenia Store](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
-   Zagnieżdżonych zapytań jednostki SQL może tworzyć sprzężenia, na serwerze i może zwrócić dużą liczbę wierszy.  
  
     Oto przykład zagnieżdżonych zapytania w klauzuli projekcji:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ponadto takich zapytań może spowodować potoku zapytania do generowania jednego zapytania zduplikowanie obiektów na zapytań zagnieżdżonej. W związku z tym pojedynczej kolumny mogą być zduplikowane wiele razy. W niektórych baz danych, w tym program SQL Server może to spowodować tabeli bazy danych TempDB, aby bardzo duża, co może zmniejszyć wydajność serwera. Należy zachować ostrożność podczas wykonywania zapytań zagnieżdżonej.  
  
-   Wszelkie zapytania, które zwracają dużej ilości danych może spowodować obniżenie wydajności, jeśli klient wykonuje operacje, które zużywają zasoby, które w sposób, który jest proporcjonalny do rozmiaru zestawu wyników. W takich przypadkach należy rozważyć ograniczenie ilości danych zwróconych przez zapytanie. Aby uzyskać więcej informacji, zobacz [jak: Wyniki strony za pomocą kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
 Dowolne polecenia generowane automatycznie przez program Entity Framework może być bardziej skomplikowane niż podobnych poleceniach napisany jawnie przez dewelopera bazy danych. Jeśli potrzebujesz jawną kontrolę nad tym polecenia wykonywane względem źródła danych, należy wziąć pod uwagę definiujący mapowanie do procedury składowanej lub funkcji zwracającej tabelę.  
  
#### <a name="relationships"></a>Relacje  
 Zoptymalizować wydajność zapytań należy zdefiniować relacje między jednostkami skojarzeń w modelu jednostki oraz w logicznej relacji w źródle danych.  
  
### <a name="query-paths"></a>Ścieżki zapytania  
 Domyślnie, podczas wykonywania <xref:System.Data.Objects.ObjectQuery%601>, powiązane obiekty nie są zwracane (mimo że obiekty reprezentujące same relacje są). Można ładować powiązanych obiektów w jednym z trzech sposobów:  
  
1. Ustaw ścieżkę zapytania przed <xref:System.Data.Objects.ObjectQuery%601> jest wykonywany.  
  
2. Wywołaj `Load` metody, właściwości nawigacji, który udostępnia obiekt.  
  
3. Ustaw <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> opcja <xref:System.Data.Objects.ObjectContext> do `true`. Należy pamiętać, że odbywa się to automatycznie podczas generowania kodu warstwy obiektu za pomocą [projektancie Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Aby uzyskać więcej informacji, zobacz [generowane Przegląd kodu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Po zastanowieniu się nad stosownej opcji, należy pamiętać, że istnieje zależność między liczba żądań w bazie danych i ilość danych zwracanych w ramach pojedynczego zapytania. Aby uzyskać więcej informacji, zobacz [ładowanie powiązanych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Przy użyciu ścieżki zapytania  
 Ścieżki zapytania definiują grafu obiektów zzwracane przez zapytanie. Podczas definiowania ścieżka kwerendy tylko jedno żądanie w odniesieniu do bazy danych musi zwrócić wszystkie obiekty, które zdefiniował ścieżki. Przy użyciu ścieżki zapytania może spowodować złożone polecenia wykonywane względem źródła danych z obiektu pozornie proste zapytań. Dzieje się tak, ponieważ co najmniej jeden sprzężeń są wymagane do zwrócenia powiązanych obiektów w ramach pojedynczego zapytania. Tę złożoność jest większa w zapytaniach względem modelu złożonego jednostki, takie jak jednostki z dziedziczenia lub ścieżki, która zawiera relacje wiele do wielu.  
  
> [!NOTE]
>  Użyj <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metodę, aby zobaczyć polecenia, które będą generowane przez <xref:System.Data.Objects.ObjectQuery%601>. Aby uzyskać więcej informacji, zobacz [jak: Wyświetl polecenia Store](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
 Gdy ścieżka kwerendy zawiera zbyt wiele powiązanych obiektów lub obiekty zawierają zbyt dużej ilości danych wiersza, źródła danych może być nie może wykonać zapytania. Dzieje się tak, jeśli zapytanie wymaga pośredni magazyn tymczasowy, który rozszerza możliwości źródła danych. W takiej sytuacji można zmniejszyć złożoność zapytania do źródła danych przez jawne ładowanie powiązanych obiektów.  
  
#### <a name="explicitly-loading-related-objects"></a>Jawne ładowanie powiązanych obiektów  
 Można jawnie ładować powiązanych obiektów, wywołując `Load` metody dla właściwości nawigacji, która zwraca <xref:System.Data.Objects.DataClasses.EntityCollection%601> lub <xref:System.Data.Objects.DataClasses.EntityReference%601>. Jawne ładowanie obiektów wymaga przesłania danych do bazy danych zawsze `Load` jest wywoływana.  
  
> [!NOTE]
>  Jeśli wywołasz `Load` podczas zapętlenie przez zbiór zwracanych obiektów, na przykład przy użyciu `foreach` instrukcji (`For Each` w języku Visual Basic), dostawca specyficznymi dla źródła danych musi obsługiwać wiele zestawów wyników active na pojedynczym połączenie. Dla bazy danych programu SQL Server, należy określić wartość `MultipleActiveResultSets = true` w parametrach połączenia dostawcy.  
  
 Można również użyć <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> metody, gdy jest nie <xref:System.Data.Objects.DataClasses.EntityCollection%601> lub <xref:System.Data.Objects.DataClasses.EntityReference%601> właściwości jednostki. Jest to przydatne w przypadku korzystania z jednostki POCO.  
  
 Mimo że jawne ładowanie powiązanych obiektów zmniejsza liczbę sprzężeń i zmniejszyć ilość nadmiarowych danych `Load` wymaga dopuszczalnych połączeń z bazą danych, może stać się kosztownych podczas ładowania jawnie dużą liczbę obiektów.  
  
### <a name="saving-changes"></a>Zapisywanie zmian  
 Gdy wywołujesz <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metody <xref:System.Data.Objects.ObjectContext>, oddzielne tworzenia, aktualizacji i usuwania polecenia jest generowany dla każdego obiektu dodano, zaktualizowano lub usunięto w kontekście. Te polecenia są wykonywane w źródle danych w ramach jednej transakcji. Zgodnie z zapytaniami, wydajność tworzenia, aktualizowania i usuwania działań, zależy od złożoności mapowania w modelu koncepcyjnym.  
  
### <a name="distributed-transactions"></a>Transakcje rozproszone  
 Operacje w transakcji jawnej, które wymagają zasoby, które są zarządzane przez Koordynator transakcji rozproszonych (DTC) będzie znacznie bardziej kosztowne niż podobna operacja, która nie wymaga usługi DTC. Podwyższanie poziomu do usługi DTC mają miejsce w następujących sytuacjach:  
  
-   Transakcji jawnej przy użyciu operacji względem bazy danych programu SQL Server 2000 lub innego źródła danych, która zawsze podwyższanie poziomu jawnych transakcji usługi DTC.  
  
-   Transakcji jawnej przy użyciu operacji względem programu SQL Server 2005, gdy połączenie jest zarządzana przy użyciu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Dzieje się tak, ponieważ program SQL Server 2005 podwyższa poziom usługi DTC zawsze wtedy, gdy połączenie jest zamknięte i otwarcia w pojedynczą transakcję, co jest zachowaniem domyślnym [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Ta promocja usługi DTC nie występuje, gdy za pomocą programu SQL Server 2008. Aby uniknąć tej promocji, podczas korzystania z programu SQL Server 2005, należy jawnie otwierać i zamykać połączenia w ramach transakcji. Aby uzyskać więcej informacji, zobacz [zarządzania połączeniami i transakcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Transakcji jawnej jest używany, gdy co najmniej jednej operacji są wykonywane w <xref:System.Transactions> transakcji. Aby uzyskać więcej informacji, zobacz [zarządzania połączeniami i transakcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Strategie zwiększania wydajności  
 Za pomocą następujących strategii, może zwiększyć ogólną wydajność zapytań w programie Entity Framework.  
  
#### <a name="pre-generate-views"></a>Wstępnie wygenerować widoków  
 Generowanie widoków opartych na modelu jednostki jest znaczącą czy aplikacja wykonuje zapytanie po raz pierwszy. Za pomocą narzędzia EdmGen.exe wstępnie wygenerować widoków jako plik kodu języka Visual Basic lub C#, który można dodać do projektu podczas projektowania. Można także użyć narzędzi przekształcania szablonu tekstu do generowania wstępnie skompilowanym widoków. Wstępnie wygenerowanych widoków są weryfikowane w czasie wykonywania, aby upewnić się, że są one zgodne z bieżącą wersją modelu określonej jednostki. Aby uzyskać więcej informacji, zobacz [jak: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).
  
 Podczas pracy z bardzo dużych modeli, mają zastosowanie następujące zagadnienia:  
  
 Format metadanych .NET ogranicza liczbę znaków w ciągu użytkownika w danym pliku binarnego do 16 777 215 (0xFFFFFF). Jeśli są generowanie widoków dla bardzo dużych modeli i Wyświetl plik osiągnie ten limit rozmiaru, zostanie wyświetlony "nie ma logiczny wolnego miejsca do utworzenia więcej ciągów użytkownika." Błąd kompilacji. To ograniczenie rozmiaru ma zastosowanie do wszystkich zarządzanych danych binarnych. Aby uzyskać więcej informacji, zobacz [blogu](https://go.microsoft.com/fwlink/?LinkId=201476) demonstrujące sposób uniknąć tego błędu, gdy praca z modelami dużych i złożonych.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Należy wziąć pod uwagę przy użyciu opcji scalania NoTracking zapytań  
 Nic nie kosztuje wymagane do śledzenia zwracanych obiektów w kontekście obiektu. Wykrywanie zmian do obiektów i zapewnienie, że wiele żądań dla tej samej jednostki logicznej zwracane to samo wystąpienie obiektu wymaga, że obiekty można dołączyć do <xref:System.Data.Objects.ObjectContext> wystąpienia. Jeśli nie planujesz wprowadzić aktualizacji lub usuwania obiektów i nie wymaga zarządzania tożsamościami, należy wziąć pod uwagę przy użyciu <xref:System.Data.Objects.MergeOption.NoTracking> opcje scalania podczas wykonywania zapytania.  
  
#### <a name="return-the-correct-amount-of-data"></a>Zwrócić poprawną ilość danych  
 W niektórych scenariuszach, określając ścieżkę zapytania za pomocą <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metoda jest znacznie szybsze, ponieważ wymaga mniejszej liczby rund do bazy danych. Jednak w innych scenariuszach dodatkowe rund do bazy danych do załadowania powiązanych obiektów może być szybsze prostsze zapytania za pomocą sprzężeń mniej powodować mniej nadmiarowości danych. W związku z tym zaleca się, należy przetestować wydajność różnych sposobów, aby pobrać powiązanych obiektów. Aby uzyskać więcej informacji, zobacz [ładowanie powiązanych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Aby uniknąć zwracanie zbyt dużej ilości danych w ramach jednego zapytania, należy wziąć pod uwagę stronicowanie wyników zapytania w perspektywie grupy. Aby uzyskać więcej informacji, zobacz [jak: Wyniki strony za pomocą kwerendy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Ogranicz zakres obiektu ObjectContext  
 W większości przypadków należy utworzyć <xref:System.Data.Objects.ObjectContext> wystąpienia w ramach `using` — instrukcja (`Using…End Using` w języku Visual Basic). Może to zwiększyć wydajność przez zapewnienie, że zasoby skojarzone z kontekstu obiektów będą usuwane automatycznie, gdy kod opuszcza blok instrukcji. Jednak podczas wiązania kontrolek do obiektów zarządzanych przez kontekst obiektu <xref:System.Data.Objects.ObjectContext> wystąpienia należy utrzymywać tak długo, jak wiązanie jest wymagane i usunięte ręcznie. Aby uzyskać więcej informacji, zobacz [zarządzania połączeniami i transakcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Należy wziąć pod uwagę, ręcznie otwierając połączenia z bazą danych  
 Gdy aplikacja wykonuje szereg zapytań dotyczących obiektów lub często wywołuje <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> można utrwalić tworzenie, aktualizowanie i usuwanie operacji do źródła danych [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] stale należy otworzyć i zamknąć połączenia ze źródłem danych. W takich sytuacjach należy wziąć pod uwagę ręczne otwieranie połączenia na początku tych operacji i zamykania lub usuwanie połączenia po ukończeniu operacji. Aby uzyskać więcej informacji, zobacz [zarządzania połączeniami i transakcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Dane wydajności  
 Niektóre dane dotyczące wydajności programu Entity Framework jest opublikowany w następujące wpisy na [blog zespołu programu ADO.NET](https://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [Eksplorowanie wydajności programu ADO.NET Entity Framework — część 1](https://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [Eksplorowanie wydajność ADO.NET Entity Framework — część 2](https://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [Porównanie wydajności programu ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie i zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
