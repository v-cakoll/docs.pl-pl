---
title: Zagadnienia dotyczące wydajności (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 581f3bc81c689909164ed3fec246371cf83245ff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="performance-considerations-entity-framework"></a>Zagadnienia dotyczące wydajności (Entity Framework)
W tym temacie opisano charakterystyki wydajności programu ADO.NET Entity Framework oraz przedstawiono pewne kwestie dotyczące pomagają zwiększyć wydajność aplikacji programu Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Etapy wykonywania zapytania  
 Aby lepiej zrozumieć wydajności zapytań w programie Entity Framework, warto informacje o operacjach, które wystąpić, gdy zapytanie wykonuje względem modelu koncepcyjnego i zwraca dane jako obiekty. W poniższej tabeli opisano następujące operacje.  
  
|Operacja|Względny koszt|Częstotliwość|Komentarze|  
|---------------|-------------------|---------------|--------------|  
|Ładowanie metadanych|Umiarkowany|Raz w każdej domenie aplikacji.|Metadane modelu i mapowania używane przez program Entity Framework jest ładowany do <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Te metadane są buforowane globalnie i jest dostępny dla innych wystąpień <xref:System.Data.Objects.ObjectContext> w tej samej domenie aplikacji.|  
|Otwieranie połączenia z bazą danych|Umiarkowany<sup>1</sup>|w razie potrzeby.|Ponieważ Otwieranie połączenia z bazą danych zużywa cenne zasobu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] otwiera i zamyka połączenie z bazą danych tylko w razie potrzeby. Można również jawnie otworzyć połączenia. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcje](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).|  
|Generowanie widoków|Wysoka|Raz w każdej domenie aplikacji. (Można wstępnie wygenerować.)|Zanim programu Entity Framework można wykonać zapytania względem modelu koncepcyjnego lub zapisać zmian w źródle danych, go wygenerować zestaw widoków zapytań lokalnego dostępu do bazy danych. Z powodu wysokiego kosztu generowania tych widoków można wstępnego wygenerowania widoków i dodaj je do projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz [porady: Pre-Generate widoków, aby poprawić wydajność kwerend](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579).|  
|Trwa przygotowywanie zapytania|Umiarkowany<sup>2</sup>|Tylko jeden raz dla każdego zapytania unikatowy.|Obejmuje koszty tworzą polecenia query Generowanie poziomu drzewa poleceń na podstawie modelu i mapowania metadanych i zdefiniuj kształt danych zwracanych. Ponieważ teraz są buforowane zarówno w poleceniach zapytań SQL jednostki i zapytań LINQ, nowsze wykonania tego samego zapytania zająć mniej czasu. Skompilowane zapytania LINQ nadal służy do tego kosztów w późniejszym wykonaniami i skompilowane zapytania może być skuteczniejsza niż zapytań LINQ, które są automatycznie buforowane. Aby uzyskać więcej informacji, zobacz [skompilowane zapytania (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). Aby uzyskać ogólne informacje na temat wykonywania zapytań LINQ, zobacz [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Uwaga:** LINQ do jednostek zapytań, które są stosowane `Enumerable.Contains` operator do kolekcji w pamięci nie są automatycznie buforowane. Parametryzacja również kolekcji w pamięci w skompilowanych zapytań LINQ jest niedozwolone.|  
|Wykonywanie zapytania|Niski<sup>2</sup>|Tylko jeden raz dla każdego zapytania.|Koszt wykonywania polecenia względem źródła danych przy użyciu dostawcy danych ADO.NET. Ponieważ większość źródeł danych pamięci podręcznej planów kwerend, nowsze wykonania tego samego zapytania może potrwać nawet mniej czasu.|  
|Ładowanie i sprawdzanie poprawności typów|Niski<sup>3</sup>|Tylko jeden raz dla każdego <xref:System.Data.Objects.ObjectContext> wystąpienia.|Typów są ładowane ani weryfikowana pod kątem typy, które definiuje modelu koncepcyjnego.|  
|Śledzenie|Niski<sup>3</sup>|Tylko jeden raz dla każdego obiektu, który zwraca zapytanie. <sup>4</sup>|Jeśli zapytanie używa <xref:System.Data.Objects.MergeOption.NoTracking> opcji scalania, tym etapie nie wpływa na wydajność.<br /><br /> Jeśli zapytanie używa <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges>, lub <xref:System.Data.Objects.MergeOption.OverwriteChanges> merge — opcja, zapytania wyniki są śledzone w <xref:System.Data.Objects.ObjectStateManager>. <xref:System.Data.EntityKey> Jest generowany dla każdego śledzonego obiektu zapytanie zwracające i jest używany do tworzenia <xref:System.Data.Objects.ObjectStateEntry> w <xref:System.Data.Objects.ObjectStateManager>. Jeśli istniejące <xref:System.Data.Objects.ObjectStateEntry> można znaleźć <xref:System.Data.EntityKey>, istniejący obiekt jest zwracany. Jeśli <xref:System.Data.Objects.MergeOption.PreserveChanges>, lub <xref:System.Data.Objects.MergeOption.OverwriteChanges> jest używana opcja, przed jego zwróceniem aktualizacji obiektu.<br /><br /> Aby uzyskać więcej informacji, zobacz [rozpoznawania tożsamości, zarządzanie stanem i śledzenia zmian](http://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
|Materializowania obiektów|Umiarkowany<sup>3</sup>|Tylko jeden raz dla każdego obiektu, który zwraca zapytanie. <sup>4</sup>|Proces odczytu zwróconego <xref:System.Data.Common.DbDataReader> obiektu i tworzenia obiektów i ustawiania wartości właściwości, które są oparte na wartościach każde wystąpienie <xref:System.Data.Common.DbDataRecord> klasy. Jeśli ten obiekt już istnieje w <xref:System.Data.Objects.ObjectContext> i zapytanie używa <xref:System.Data.Objects.MergeOption.AppendOnly> lub <xref:System.Data.Objects.MergeOption.PreserveChanges> opcji scalania, tym etapie nie wpływa na wydajność. Aby uzyskać więcej informacji, zobacz [rozpoznawania tożsamości, zarządzanie stanem i śledzenia zmian](http://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
  
 <sup>1</sup> gdy dostawca źródła danych implementuje buforowanie połączeń, kosztów otwarcia połączenia jest dystrybuowana do puli. Dostawcy .NET dla programu SQL Server obsługuje puli połączeń.  
  
 <sup>2</sup> koszt zwiększa się wraz z zapytania zwiększenia złożoności.  
  
 <sup>3</sup> całkowity koszt zwiększa proporcjonalna do liczby obiektów zwróconych przez kwerendę.  
  
 <sup>4</sup> ten narzut nie jest wymagane dla EntityClient zapytania, ponieważ return wysyła zapytanie do dostawcy EntityClient <xref:System.Data.EntityClient.EntityDataReader> zamiast obiektów. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Dodatkowe uwagi  
 Poniżej przedstawiono innych kwestii, które mogą wpływać na wydajność aplikacji programu Entity Framework.  
  
### <a name="query-execution"></a>Wykonywanie zapytania  
 Zapytania mogą być ilości zasobów, należy wziąć pod uwagę w momencie, jakie w kodzie i na komputerze, jakie zapytanie jest wykonywane.  
  
#### <a name="deferred-versus-immediate-execution"></a>Odroczone i natychmiastowego wykonania  
 Po utworzeniu <xref:System.Data.Objects.ObjectQuery%601> lub zapytań LINQ zapytania nie może być wykonane natychmiast. Wykonywanie zapytania została odroczona dopóki wyniki są potrzebne, takich jak podczas `foreach` (C#) lub `For Each` wyliczenia (Visual Basic) lub gdy jest przypisany do wypełnienia <xref:System.Collections.Generic.List%601> kolekcji. Wykonywanie zapytania rozpocznie się natychmiast po wywołaniu <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> metoda <xref:System.Data.Objects.ObjectQuery%601> lub po wywołaniu metody LINQ zwraca pojedynczych zapytań, takich jak <xref:System.Linq.Enumerable.First%2A> lub <xref:System.Linq.Enumerable.Any%2A>. Aby uzyskać więcej informacji, zobacz [zapytań obiektu](http://msdn.microsoft.com/library/0768033c-876f-471d-85d5-264884349276) i [wykonywanie zapytania (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Po stronie klienta wykonywania zapytań LINQ  
 Mimo że wykonywanie zapytań LINQ występuje na komputerze, który obsługuje źródła danych, niektórych części zapytania LINQ może być oceniana na komputerze klienckim. Aby uzyskać więcej informacji, zobacz sekcję wykonywania magazynu [wykonywanie zapytania (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Zapytania i mapowanie złożoności  
 Złożoność poszczególnych kwerend i mapowanie w modelu jednostki będzie mieć znaczący wpływ na wydajność kwerend.  
  
#### <a name="mapping-complexity"></a>Mapowanie złożoności  
 Modele, które są bardziej skomplikowane niż proste mapowanie jeden do jednego między jednostek w modelu koncepcyjnym i tabele w modelu magazynu wygenerować polecenia bardziej złożone niż modeli mapowanie jeden do jednego.  
  
#### <a name="query-complexity"></a>Złożoność zapytania  
 Zapytania wymagające dużą liczbę sprzężeń w poleceń, które są wykonywane w źródle danych lub dużej ilości danych, które zwracają mogą wpływać na wydajność w następujący sposób:  
  
-   Zapytań dotyczących modelu koncepcyjnego, które wydają się proste może spowodować wykonanie bardziej złożonych zapytań względem źródła danych. Może to wystąpić, ponieważ zapytanie model koncepcyjny programu Entity Framework przekłada się na równoważne zapytania względem źródła danych. Po ustawieniu pojedynczej jednostki modelu koncepcyjnym mapy do więcej niż jednej tabeli w źródle danych, lub gdy relacji między obiektami jest mapowany na tabelę sprzężenia, polecenie zapytanie wykonane na kwerendy źródła danych mogą wymagać sprzężenia jeden lub więcej.  
  
    > [!NOTE]
    >  Użyj <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody <xref:System.Data.Objects.ObjectQuery%601> lub <xref:System.Data.EntityClient.EntityCommand> klasy mogą wyświetlać polecenia, które są wykonywane względem źródła danych dla określonego zapytania. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie poleceń magazynu](http://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
-   Zapytania SQL jednostki zagnieżdżone może tworzyć sprzężenia na serwerze i może zwrócić dużą liczbę wierszy.  
  
     Poniżej przedstawiono przykładowe zapytanie zagnieżdżone w klauzuli projekcji:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Ponadto takie kwerendy powoduje potoku zapytania można wygenerować pojedynczego zapytania zduplikowanie obiektów między zapytania zagnieżdżone. W związku z tym pojedynczej kolumny mogą być zduplikowane wiele razy. W niektórych baz danych, w tym program SQL Server może to spowodować tabeli bazy danych TempDB rośnie bardzo duży, która może obniżyć wydajność serwera. Należy zachować ostrożność podczas wykonywania zapytania zagnieżdżone.  
  
-   Wszelkie zapytań, które zwracają dużej ilości danych może spowodować obniżenie wydajności, jeśli klient wykonuje operacje, których użycie zasobów w taki sposób, który jest proporcjonalny do rozmiaru zestawu wyników. W takim przypadku należy rozważyć ograniczenie ilości danych zwróconych przez kwerendę. Aby uzyskać więcej informacji, zobacz [porady: strona za pośrednictwem wyników zapytania](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
 Wszystkie polecenia generowane automatycznie przez program Entity Framework mogą być bardziej skomplikowane niż podobnych poleceń jawnie zapisanych przez dewelopera bazy danych. Jawne kontrolę nad polecenia wykonywane względem źródła danych, należy wziąć pod uwagę Definiowanie mapowania do procedury składowanej lub funkcji zwracającej tabelę.  
  
#### <a name="relationships"></a>Relacje  
 Dla zapytania optymalną wydajność należy zdefiniować relacje między obiektami skojarzenia w modelu jednostki oraz w relacje logiczne w źródle danych.  
  
### <a name="query-paths"></a>Ścieżki zapytania  
 Domyślnie podczas wykonywania <xref:System.Data.Objects.ObjectQuery%601>, powiązane obiekty nie są zwracane (mimo że obiekty, które reprezentują same relacje są). Można ładować powiązanych obiektów w jednym z trzech sposobów:  
  
1.  Ustaw ścieżkę zapytania przed <xref:System.Data.Objects.ObjectQuery%601> jest wykonywana.  
  
2.  Wywołanie `Load` metody dla obiekt ujawniający właściwość nawigacji.  
  
3.  Ustaw <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> opcja <xref:System.Data.Objects.ObjectContext> do `true`. Należy pamiętać, że odbywa się to automatycznie podczas generowania kodu warstwy obiektu z [Projektant modelu danych jednostki](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf). Aby uzyskać więcej informacji, zobacz [wygenerowany Przegląd kodu](http://msdn.microsoft.com/library/6a88ea38-6a90-4107-bc33-531b79ce5b6a).  
  
 Gdy należy wziąć pod uwagę opcji, należy pamiętać, Brak zależności od liczby żądań w bazie danych i ilość danych zwróconych w jednym zapytaniu. Aby uzyskać więcej informacji, zobacz [ładowanie powiązanych obiektów](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
#### <a name="using-query-paths"></a>Używając ścieżek zapytania  
 Ścieżki zapytania zdefiniuj Graf obiektów zwracanych przez zapytanie. Podczas definiowania ścieżki zapytania tylko jedno żądanie w bazie danych jest wymagany do zwrócenia wszystkich obiektów, które określa ścieżkę. Używając ścieżek zapytania może spowodować złożonych polecenia wykonywane względem źródła danych z zapytania pozornie prostego obiektu. Dzieje się tak, ponieważ co najmniej jeden sprzężenia są wymagane do zwrócenia powiązanych obiektów w jednym zapytaniu. Taki poziom złożoności jest większa w kwerendach do modelu jednostki złożonych, takich jak jednostki z dziedziczenia lub ścieżki, która zawiera relacje wiele do wielu.  
  
> [!NOTE]
>  Użyj <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> metody, aby wyświetlić polecenie, które będą generowane przez <xref:System.Data.Objects.ObjectQuery%601>. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie poleceń magazynu](http://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
 Ścieżka zapytania zawiera zbyt wiele powiązanych obiektów lub obiekty zawierają zbyt dużej ilości danych wiersza, źródła danych może być nie może wykonać zapytania. Dzieje się tak, jeśli zapytanie wymaga pośredni magazyn tymczasowy, które przekraczają możliwości źródła danych. W takim przypadku można zmniejszyć złożoność kwerendy źródła danych przez jawnego ładowania powiązanych obiektów.  
  
#### <a name="explicitly-loading-related-objects"></a>Jawnie ładowanie powiązanych obiektów  
 Można jawnie ładować powiązanych obiektów przez wywołanie metody `Load` metody dla właściwości nawigacji, która zwraca <xref:System.Data.Objects.DataClasses.EntityCollection%601> lub <xref:System.Data.Objects.DataClasses.EntityReference%601>. Jawnie ładowanie obiektów wymaga przesłania danych do bazy danych zawsze `Load` jest wywoływana.  
  
> [!NOTE]
>  wywołanie `Load` podczas zapętlenie przez kolekcję zwracanych obiektów, na przykład przy użyciu `foreach` instrukcji (`For Each` w języku Visual Basic), dostawca specyficzne dla źródła danych musi obsługiwać wiele zestawów wyników active w ramach jednej połączenie. Dla bazy danych programu SQL Server, należy określić wartość `MultipleActiveResultSets = true` w parametrach połączenia dostawcy.  
  
 Można również użyć <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> przypadku nie <xref:System.Data.Objects.DataClasses.EntityCollection%601> lub <xref:System.Data.Objects.DataClasses.EntityReference%601> właściwości jednostki. Jest to przydatne w przypadku korzystania z jednostki POCO.  
  
 Mimo że jawnego ładowania powiązane obiekty zmniejsza liczbę sprzężeń i zmniejszyć ilość nadmiarowych danych `Load` wymaga powtarzane połączeń z bazą danych, może być kosztowne podczas jawnego ładowania dużą liczbę obiektów.  
  
### <a name="saving-changes"></a>Trwa zapisywanie zmian  
 Podczas wywoływania <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda <xref:System.Data.Objects.ObjectContext>, Utwórz oddzielne, aktualizacji lub polecenia delete zostanie wygenerowany dla każdy obiekt dodany, zaktualizowanych lub usuniętych, w tym kontekście. Te polecenia są wykonywane w źródle danych w ramach jednej transakcji. Zgodnie z zapytaniami, wydajność tworzenia, aktualizowania i usuwania działań zależy od stopnia złożoności mapowania w modelu koncepcyjnym.  
  
### <a name="distributed-transactions"></a>Transakcje rozproszone  
 Operacje w jawnych transakcji, które wymagają zasobów, które są zarządzane przez koordynatora transakcji rozproszonych (DTC) będzie znacznie droższe niż podobna operacja, która nie wymaga usługi DTC. Podwyższanie poziomu do usługi DTC nastąpi w następujących sytuacjach:  
  
-   Transakcja jawne operacji względem bazy danych programu SQL Server 2000 lub innego źródła danych, która zawsze wspierania jawnych transakcji usługi DTC.  
  
-   Jawne transakcji z operacji programu SQL Server 2005, gdy połączenie jest zarządzana przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Dzieje się tak, ponieważ program SQL Server 2005 wspiera do DTC zawsze, gdy połączenie jest zamknięte i otworzyć ponownie w ramach jednej transakcji, która jest domyślne zachowanie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Podwyższanie poziomu tej usługi DTC nie występuje, gdy za pomocą programu SQL Server 2008. Aby uniknąć tego podwyższania poziomu, używając programu SQL Server 2005, musisz jawnie otwierać i zamykać połączenia w obrębie transakcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcje](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
 Transakcji jawnej jest używany, gdy co najmniej jeden operacje są wykonywane w <xref:System.Transactions> transakcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcje](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="strategies-for-improving-performance"></a>Strategie zwiększania wydajności  
 Można zwiększyć ogólną wydajność zapytań w programie Entity Framework za pomocą następujących strategii.  
  
#### <a name="pre-generate-views"></a>Wstępnego wygenerowania widoków  
 Generowanie widoki oparte na modelu jednostki jest znaczącą czy aplikacja wykonuje zapytanie po raz pierwszy. Użyj narzędzia EdmGen.exe do wstępnego wygenerowania widoków jako plik kodu Visual Basic lub C#, który może być dodany do projektu podczas projektowania. Toolkit transformacji szablonu tekstowego można użyć również do generowania wstępnie skompilowanym widoków. Wstępnie wygenerowanych widoków są weryfikowane w czasie wykonywania, aby upewnić się, że są one zgodne z bieżącą wersją modelu określonej jednostki. Aby uzyskać więcej informacji, zobacz [porady: Pre-Generate widoków, aby poprawić wydajność kwerend](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579) i [izolowanie wydajności przy użyciu Prekompilowanego/wstępnie przygotowany-generated widoki programu Entity Framework 4](http://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409).  
  
 Podczas pracy z bardzo dużych modeli, stosowane są następujące brany pod uwagę:  
  
 Format metadanych .NET ogranicza liczbę znaków ciągu użytkownika danego pliku binarnego do 16 777 215 (0xFFFFFF). Jeśli jest generowany widoków dla bardzo dużych modelu i Wyświetl plik osiągnie ten limit, zostanie wyświetlona "nie pozostawiono logicznego miejsca do utworzenia większej liczby ciągów użytkownika." Błąd kompilacji. Ten rozmiar ograniczenie ma zastosowanie do wszystkich zarządzanych plików binarnych. Aby uzyskać więcej informacji, zobacz [blogu](http://go.microsoft.com/fwlink/?LinkId=201476) który demonstruje sposób uniknąć tego błędu, gdy praca z modelami dużych i złożonych.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Należy wziąć pod uwagę przy użyciu opcji scalania NoTracking zapytań  
 Brak koszt wymaganych do śledzenia zwracanych obiektów w kontekście obiektu. Wykrywanie zmian do obiektów oraz zapewnienie, że wiele żądań dla tej samej jednostki logicznej zwracać tego samego wystąpienia obiektu wymaga, aby obiekty można dołączyć do <xref:System.Data.Objects.ObjectContext> wystąpienia. Jeśli nie zamierzasz wprowadzić aktualizacji lub usuwania obiektów i nie wymagają zarządzania tożsamościami, rozważ użycie <xref:System.Data.Objects.MergeOption.NoTracking> opcje scalania podczas wykonywania zapytania.  
  
#### <a name="return-the-correct-amount-of-data"></a>Zwraca poprawnej ilości danych  
 W niektórych scenariuszach, określając ścieżkę zapytania za pomocą <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metoda jest znacznie szybsza, ponieważ wymaga mniejszej liczby rund do bazy danych. Jednak w innych scenariuszach dodatkowe rund do bazy danych można załadować powiązanych obiektów może być szybsze prostsze zapytania za pomocą sprzężeń mniej powodować mniej nadmiarowości danych. W związku z tym zaleca się, należy przetestować wydajność różnych sposobów, aby pobrać powiązanych obiektów. Aby uzyskać więcej informacji, zobacz [ładowanie powiązanych obiektów](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
 Aby uniknąć zwróceniem zbyt dużej ilości danych w jednym zapytaniu, należy wziąć pod uwagę stronicowania wyników kwerendy w grupy łatwiejsze w zarządzaniu. Aby uzyskać więcej informacji, zobacz [porady: strona za pośrednictwem wyników zapytania](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Ograniczenie zakresu tego obiektu ObjectContext  
 W większości przypadków należy utworzyć <xref:System.Data.Objects.ObjectContext> wystąpienie w ramach `using` instrukcji (`Using…End Using` w języku Visual Basic). Umożliwia to zwiększenie wydajności przez zapewnienie, że zasoby skojarzone z kontekstu obiektu są usuwane automatycznie, gdy kod opuszcza blok instrukcji. Jednak jeśli formanty są powiązane z obiekty zarządzane przez kontekst obiektu <xref:System.Data.Objects.ObjectContext> wystąpienia należy utrzymywać tak długo, jak wiązanie jest potrzebne i usunąć ręcznie. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcje](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Należy wziąć pod uwagę ręcznie Otwieranie połączenia z bazą danych  
 Gdy aplikacja wykonuje szereg zapytania obiektu lub często wywołuje <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> utrwalanie do tworzenia, aktualizacji i usuwania działań ze źródłem danych [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] stale należy otworzyć i zamknąć połączenia ze źródłem danych. W takich sytuacjach należy wziąć pod uwagę ręcznie otwierania połączenia na początku tych operacji i zamknięcie lub usuwanie połączenie po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie połączeniami i transakcje](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="performance-data"></a>Dane wydajności  
 Niektóre dane dotyczące wydajności Entity Framework jest opublikowany w następujących wpisach w [blogu zespołu programu ADO.NET](http://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [Eksploracja wydajności programu ADO.NET Entity Framework — część 1](http://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [Eksploracja wydajności programu ADO.NET Entity Framework — część 2](http://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [Porównanie wydajności programu ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie i zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
