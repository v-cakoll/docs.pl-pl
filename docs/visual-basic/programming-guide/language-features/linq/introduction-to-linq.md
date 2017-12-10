---
title: Wprowadzenie do LINQ w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7882614b9663d1c38f137f7a69054d5bbd50b19
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="introduction-to-linq-in-visual-basic"></a>Wprowadzenie do LINQ w Visual Basic
Zapytanie języku zintegrowanym (LINQ) dodaje możliwość wykonywania kwerend do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] i zapewnia prosta i skuteczna możliwości podczas pracy z wszystkich typów danych. Zamiast Wysyłanie zapytania do bazy danych w celu przetworzenia lub Praca z inną składnię dla każdego typu danych, które w przypadku wyszukiwania, LINQ wprowadza zapytania jako część [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] języka. Używa ujednoliconego składni niezależnie od typu danych.  
  
 LINQ można wykonać zapytania o dane z bazy danych programu SQL Server, XML, tablic w pamięci i kolekcje, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawami danych lub innych danych lokalnych lub zdalnych źródła obsługiwane przez LINQ. Można to zrobić wszystkich o wspólnym [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] elementy języka. Ponieważ zapytania są zapisywane [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] języka, wyniki zapytania są zwracane jako silnie typizowanych obiektów. Te obiekty obsługują technologię IntelliSense, co pozwala na szybsze pisanie kodu i catch błędy zapytania w czasie kompilacji zamiast w czasie wykonywania. Można zapytań LINQ jako źródło dodatkowych zapytań do ograniczania wyników. One może również być powiązana do formantów tak, aby użytkownicy łatwo można wyświetlać i modyfikować wyniki zapytania.  
  
 Na przykład poniższy przykładowy kod przedstawia zapytanie LINQ, które zwraca listę klientów z kolekcji i grup, które je na podstawie ich lokalizacji.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 W tym temacie można znaleźć informacje o następujących obszarów:  
  
-   [Uruchamianie przykładów](#RunningtheExamples)  
  
-   [Dostawcy LINQ](#LINQProviders)  
  
-   [Struktura zapytań LINQ](#StructureOfALINQQuery)  
  
-   [Operatory zapytań LINQ w Visual Basic](#VisualBasicLINQQueryOperators)  
  
-   [Połączenia z bazą danych za pomocą LINQ do SQL](#ConnectingToADatabase)  
  
-   [Funkcje Visual Basic obsługujące LINQ](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [Wykonanie odroczone i bezpośrednie kwerendy](#QueryExecution)  
  
-   [Kod XML w Visual Basic](#XMLInVisualBasic)  
  
-   [Zasoby pokrewne](#RelatedResources)  
  
-   [Porady i wskazówki — tematy](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a>Uruchamianie przykładów  
 Aby uruchomić w przykładach w wprowadzenia i w sekcji "Struktura z zapytania LINQ", obejmują następujący kod, który zwraca listę klientów i zamówienia.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a>Dostawcy LINQ  
 A *dostawcy LINQ* mapy z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zapytań LINQ do źródła danych, której dotyczy zapytanie. Podczas pisania zapytań LINQ przyjmuje zapytania i przekłada się on na polecenia, które źródło danych będzie możliwe wykonywanie dostawcy. Dostawca również konwertuje dane ze źródła do obiektów, które tworzą wyników zapytania. Na koniec konwertuje obiektów danych podczas wysyłania aktualizacji do źródła danych.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]zawierają następujących dostawców LINQ.  
  
|Dostawcy|Opis|  
|---|---|  
|LINQ do obiektów|LINQ do obiektów dostawcy umożliwia zapytania w pamięci kolekcji i tablic. Jeśli obiekt obsługuje albo <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> interfejsu LINQ do obiektów dostawcy umożliwia on zapytania.<br /><br /> LINQ do obiektów dostawcy można włączyć, importując <xref:System.Linq> przestrzeni nazw, który jest importowany domyślnie dla wszystkich [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektów.<br /><br /> Aby uzyskać więcej informacji na temat LINQ do obiektów dostawcy, zobacz [LINQ do obiektów](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).|  
|LINQ do SQL|LINQ do SQL dostawcy umożliwia zapytania i modyfikować danych w bazie danych programu SQL Server. Ułatwia to mapowania modelu obiektu do tabel i obiektów w bazie danych aplikacji.<br /><br /> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ułatwia posługiwanie się LINQ do SQL umieszczając Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych). Ten Projektant służy do tworzenia modeli obiektów w aplikacji, która mapuje do obiektów w bazie danych. Projektant obiektów relacyjnych również zapewnia funkcje do mapowania procedury składowane i funkcje, które mają <xref:System.Data.Linq.DataContext> obiektu, który zarządza komunikacji z bazą danych i zapisuje stan kontroli optymistycznej współbieżności.<br /><br /> Aby uzyskać więcej informacji na temat LINQ do SQL dostawcy, zobacz [LINQ do SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md). Aby uzyskać więcej informacji na temat Projektant obiektów relacyjnych, zobacz [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ do XML|LINQ do XML dostawcy umożliwia zapytania i modyfikować XML. Można zmodyfikować XML w pamięci, albo można ładowanie XML z, a następnie zapisz XML w pliku.<br /><br /> Ponadto LINQ do XML dostawcy umożliwia literały XML i właściwości osi XML, które pozwalają na zapis XML bezpośrednio w Twojej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu. Aby uzyskać więcej informacji, zobacz [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ do DataSet|LINQ do DataSet dostawcy umożliwia utworzenie zapytania i aktualizacji danych w [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawu danych. Możesz dodać możliwości LINQ do aplikacji, które używają zestawów danych w celu uproszczenia i rozszerzyć możliwości zapytań, agregację i aktualizowanie danych w zestawie danych.<br /><br /> Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
##  <a name="StructureOfALINQQuery"></a>Struktura zapytań LINQ  
 Zapytania LINQ, często nazywane *zapytania wyrażenie*, składa się z kombinacji klauzule zapytań, które identyfikują źródła danych i zmienne iteracji w zapytaniu. Wyrażenia zapytania można także instrukcje dotyczące sortowanie, filtrowanie, grupowanie i dołączenie lub obliczenia dotyczące źródła danych. Składnia wyrażeń jest podobny składni SQL; w związku z tym może być znacznie składni znane.  
  
 Rozpoczyna się od wyrażenia zapytania `From` klauzuli. Klauzulę identyfikuje źródło danych pod kątem zapytania i zmienne, które są używane do odwoływania się do każdego elementu danych źródłowych pojedynczo. Te zmienne są nazywane *zmienne zakresu* lub *zmienne iteracji*. `From` Jest wymagana klauzula dla zapytania, z wyjątkiem `Aggregate` kwerendy, gdzie `From` klauzula jest opcjonalne. Po zakresu i źródłem zapytania są identyfikowane w `From` lub `Aggregate` klauzule, może zawierać dowolną kombinację klauzule zapytań, aby zawęzić kryteria zapytania. Aby uzyskać więcej informacji o klauzule zapytań, zobacz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] operatorów zapytań LINQ w dalszej części tego tematu. Na przykład poniższe zapytanie określa zbiór źródła danych klienta jako `customers` zmienną i zmiennej iteracji o nazwie `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 W tym przykładzie jest prawidłowa kwerenda siebie. jednak zapytanie staje się znacznie bardziej wydajne, po dodaniu więcej klauzule zapytań, aby doprecyzować wynik. Na przykład można dodać `Where` klauzuli do filtrowania według wartości co najmniej jeden wynik. Wyrażenia zapytania są pojedynczy wiersz kodu; klauzule dodatkowe zapytania można dodać tylko na końcu zapytania. Zapytania można podzielić na wiele wierszy tekstu w celu zwiększenia czytelności za pomocą znaku podkreślenia (\_) znak kontynuacji wiersza. Poniższy przykładowy kod przedstawia przykład kwerendę, która obejmuje `Where` klauzuli.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Inną klauzulę zaawansowane zapytania jest `Select` klauzuli, która umożliwia zwracanie tylko wybrane pola z źródła danych. Zapytania LINQ zwracają wyliczalny kolekcje silnie typizowanych obiektów. Zapytanie może zwrócić zbiór typy anonimowe lub typy nazwane. Można użyć `Select` klauzuli, aby zwrócić tylko jedno pole w źródle danych. Po wykonaniu tej typem kolekcji, zwracany jest typ tego jednego pola. Można również użyć `Select` klauzuli zwrócić wielu pól ze źródła danych. Po wykonaniu tej czynności typem kolekcji, zwracana jest nowego typu anonimowego. Można także dopasować pola zwróconych przez zapytanie do pól określonego typu nazwanego. Poniższy przykładowy kod przedstawia zapytanie zwracające kolekcję typów anonimowych, które mają elementy członkowskie wypełniane przy użyciu danych z wybranego pola ze źródła danych.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 Zapytania LINQ można również łączyć wiele źródeł danych i zwracać jeden wynik. Można to zrobić z co najmniej jednym `From` klauzule, lub za pomocą `Join` lub `Group Join` klauzule zapytań. Poniższy przykład kodu pokazuje łączy danych klienta i kolejność, która zwraca kolekcję typów anonimowych zawierające klienta i dane kolejności wyrażenia zapytania.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Można użyć `Group Join` klauzuli można utworzyć wyniku zapytania hierarchiczne, który zawiera kolekcję obiektów klienta. Każdy obiekt klienta ma właściwość, która zawiera kolekcję wszystkich zleceń dla tego klienta. Poniższy przykład kodu pokazuje wyrażenia zapytania, która łączy danych klienta i kolejność jako wyników hierarchicznych i zwraca kolekcję typów anonimowych. Zapytanie zwraca typ, który zawiera `CustomerOrders` właściwość, która zawiera kolekcję danych kolejności dla klienta. Zawiera także `OrderTotal` właściwość, która zawiera sumę sumy dla wszystkich zleceń dla tego klienta. (To zapytanie jest odpowiednikiem LEFT OUTER JOIN).  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Istnieje kilka dodatkowych LINQ operatorów zapytań, które służy do tworzenia wyrażenia zaawansowanych zapytań. W następnej sekcji tego tematu opisano różne klauzule zapytań, które można uwzględnić w wyrażeniu zapytania. Aby uzyskać więcej informacji o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] klauzule zapytań, zobacz [zapytania](../../../../visual-basic/language-reference/queries/queries.md).  
  
##  <a name="VisualBasicLINQQueryOperators"></a>Operatory zapytań LINQ w Visual Basic  
 Klasy w <xref:System.Linq> przestrzeni nazw i innych przestrzeniach nazw obsługujące zapytań LINQ zawiera metody, które można wywołać w celu utworzenia i Dostosuj zapytań, w zależności od potrzeb aplikacji. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]zawiera słowa kluczowe dla najbardziej typowych klauzule zapytań, zgodnie z opisem w poniższej tabeli.  
  
|Termin|Definicja|  
|---|---|  
|[Klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md)|Albo `From` klauzuli lub `Aggregate` klauzuli jest wymagane do rozpoczęcia zapytania. A `From` klauzuli określa kolekcji źródłowej i zmiennej iteracji dla zapytania. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[SELECT — klauzula](../../../../visual-basic/language-reference/queries/select-clause.md)|Opcjonalny. Deklaruje zestaw zmiennych iteracji dla zapytania. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> Jeśli `Select` klauzuli nie zostanie określony, zmienne iteracji w zapytaniu składają się z zmienne iteracji, określony przez `From` lub `Aggregate` klauzuli.|  
|[Gdy klauzula](../../../../visual-basic/language-reference/queries/where-clause.md)|Opcjonalny. Określa warunek filtrowania dla zapytania. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Order By — klauzula](../../../../visual-basic/language-reference/queries/order-by-clause.md)|Opcjonalny. Określa porządek sortowania dla kolumn w zapytaniu. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[JOIN — klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)|Opcjonalny. Łączy dwie kolekcje do jednej kolekcji. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Group By — klauzula](../../../../visual-basic/language-reference/queries/group-by-clause.md)|Opcjonalny. Grupuje elementy w wyniku zapytania. Może służyć do zastosowania funkcji agregujących do każdej grupy. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Group Join — klauzula](../../../../visual-basic/language-reference/queries/group-join-clause.md)|Opcjonalny. Łączy dwie kolekcje do jednej kolekcji hierarchicznej. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[AGGREGATE — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|Albo `From` klauzuli lub `Aggregate` klauzuli jest wymagane do rozpoczęcia zapytania. `Aggregate` Klauzuli dotyczy kolekcji jednego lub więcej funkcji agregujących. Na przykład można użyć `Aggregate` klauzuli do obliczania sum dla wszystkich elementów zwróconych przez kwerendę.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> Można również użyć `Aggregate` klauzuli zmodyfikować zapytanie. Na przykład można użyć `Aggregate` klauzuli do przeprowadzenia obliczeń na kolekcję powiązane zapytania.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Let — klauzula](../../../../visual-basic/language-reference/queries/let-clause.md)|Opcjonalny. Oblicza wartość i przypisuje go do nowej zmiennej w zapytaniu. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[DISTINCT — klauzula](../../../../visual-basic/language-reference/queries/distinct-clause.md)|Opcjonalny. Ogranicza wartości bieżąca zmienna iteracji w celu wyeliminowania zduplikowanych wartości w wynikach zapytania. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[SKIP — klauzula](../../../../visual-basic/language-reference/queries/skip-clause.md)|Opcjonalny. Pomija określoną liczbę elementów w kolekcji, a następnie zwraca wszystkie pozostałe elementy. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[SKIP While — klauzula](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|Opcjonalny. Pomija elementy w kolekcji, tak długo, jak jest określony warunek `true` , a następnie zwraca wszystkie pozostałe elementy. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Take — klauzula](../../../../visual-basic/language-reference/queries/take-clause.md)|Opcjonalny. Zwraca określoną liczbę elementów ciągłe na początku kolekcji. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Take While — klauzula](../../../../visual-basic/language-reference/queries/take-while-clause.md)|Opcjonalny. Zawiera elementy w kolekcji, tak długo, jak jest określony warunek `true` i pomija pozostałe elementy. Na przykład:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 Aby uzyskać więcej informacji o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] klauzule zapytań, zobacz [zapytania](../../../../visual-basic/language-reference/queries/queries.md).  
  
 Można użyć dodatkowych funkcji zapytania LINQ członkom wywoływania udostępnione przez składnik LINQ typy wyliczalny oraz umożliwia zadawanie zapytań. Te dodatkowe możliwości można użyć poprzez wywołanie operator zapytania określonego w wyniku wyrażenia zapytania. Na przykład poniższy przykład kodu wykorzystuje <xref:System.Linq.Enumerable.Union%2A> metodę, aby połączyć wyniki dwa zapytania w wyniku jednego zapytania. Używa <xref:System.Linq.Enumerable.ToList%2A> metodę, aby zwrócić wynik kwerendy w postaci listy ogólnej.  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Aby uzyskać więcej informacji o dodatkowe funkcje LINQ, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
##  <a name="ConnectingToADatabase"></a>Połączenia z bazą danych za pomocą LINQ do SQL  
 W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], identyfikację obiektów bazy danych programu SQL Server, takich jak tabele, widoki i procedury składowane, że chcesz uzyskać dostęp za pomocą LINQ do SQL pliku. LINQ do SQL pliku ma rozszerzenie .dbml.  
  
 Jeśli masz prawidłowe połączenie z bazą danych programu SQL Server można dodać **klasy LINQ do SQL** szablon elementu do projektu. Spowoduje to wyświetlenie Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych). Projektant obiektów relacyjnych umożliwia przeciągnij elementy, które chcesz uzyskać dostęp w kodzie z **Eksploratora serwera**/**Eksploratora bazy danych** na powierzchnię projektanta. LINQ do SQL pliku dodaje <xref:System.Data.Linq.DataContext> obiektu do projektu. Ten obiekt zawiera właściwości i kolekcje dla tabele i widoki, które mają dostęp do i metody dla procedur składowanych, które ma zostać wywołana. Po zapisaniu zmian do składnika LINQ to SQL (.dbml) plików, są dostępne te obiekty w kodzie za pomocą odwołań do <xref:System.Data.Linq.DataContext> obiekt, który jest definiowana za pomocą Projektanta obiektów relacyjnych. <xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy użytkownika składnika LINQ to SQL pliku. Na przykład utworzy składnika LINQ to SQL pliku o nazwie Northwind.dbml <xref:System.Data.Linq.DataContext> obiektu o nazwie `NorthwindDataContext`.  
  
 Przykłady z instrukcjami krok po kroku, zobacz [porady: zapytanie dotyczące bazy danych](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md) i [porady: wywołaj procedurę składowaną](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md).  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a>Funkcje Visual Basic obsługujące LINQ  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]zawiera inne ważne funkcje wykorzystać LINQ proste i zmniejszyć ilość kodu, który musi być zapisana do wykonywania zapytań LINQ. Należą do nich między innymi:  
  
-   **Typy anonimowe**, które umożliwiają tworzenie nowego typu na podstawie wyniku zapytania.  
  
-   **Niejawnie wpisane zmienne**, umożliwiają odroczenie Określanie typu i umożliwiają kompilator wnioskować o typie, na podstawie wyniku zapytania.  
  
-   **Metody rozszerzenia**, umożliwiają rozszerzanie istniejącego typu z własnych metody bez modyfikowania samego typu.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Basic funkcji czy obsługa LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md).  
  
##  <a name="QueryExecution"></a>Wykonanie odroczone i bezpośrednie kwerendy  
 Wykonywanie zapytania jest oddzielony od tworzenia zapytania. Po utworzeniu zapytania, jego wykonanie jest wyzwalane przez mechanizm, oddzielne. Można było wykonać zapytanie, jak jest zdefiniowany (*natychmiastowego wykonania*), lub definicji mogą być przechowywane i można było wykonać zapytanie później (*odroczonego wykonania*).  
  
 Domyślnie podczas tworzenia zapytania, zapytanie sam nie wykonuje natychmiast. Zamiast tego definicja zapytania jest przechowywana w zmiennej, która jest używana do utworzenia odwołania wyniku zapytania. Gdy zmiennej wynik zapytania jest dostępny w dalszej części kodu, takie jak w `For…Next` pętli, zapytanie jest wykonywane. Ten proces jest nazywany *odroczonego wykonania*.  
  
 Zapytania mogą być również wykonywane, gdy są zdefiniowane, które jest określone jako *natychmiastowego wykonania*. Możesz wyzwolić natychmiastowego wykonania, stosując metodę, która wymaga dostępu do poszczególnych elementów w wyniku zapytania. Może to być wynik, w tym funkcji agregującej, takich jak `Count`, `Sum`, `Average`, `Min`, lub `Max`. Aby uzyskać więcej informacji na temat funkcji agregujących, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Przy użyciu `ToList` lub `ToArray` metody zostanie też wymusić natychmiastowe wykonanie. Może to być przydatne, jeśli chcesz natychmiast wykonać zapytania i wyników buforowania. Aby uzyskać więcej informacji na temat tych metod, zobacz [konwertowanie typów danych](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Aby uzyskać więcej informacji na temat wykonywania zapytania, zobacz [Your pierwszego zapytania LINQ zapisu](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
##  <a name="XMLInVisualBasic"></a>Kod XML w Visual Basic  
 Plik XML funkcji w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obejmują literały XML i właściwości osi XML, które umożliwiają łatwe tworzenie, dostęp do zapytania i modyfikować w kodzie XML. Literały XML pozwalają na zapis bezpośrednio w kodzie XML. Kompilator Visual Basic traktuje XML jako obiekt danych biletu.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć XML element, dostęp do jego elementów podrzędnych i atrybuty i zapytanie o zawartość elementu za pomocą LINQ.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).  
  
##  <a name="RelatedResources"></a>Zasoby pokrewne  
  
|Temat|Opis|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|Zawiera opis funkcji XML w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] może być badana i które umożliwiają włączenia XML jako obiekty najwyższej jakości danych w sieci [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.|  
|[Zapytania](../../../../visual-basic/language-reference/queries/queries.md)|Udostępnia informacje na temat klauzule zapytań, które są dostępne w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].|  
|[LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|Zawiera informacje ogólne, programowania wskazówki i przykłady dla LINQ.|  
|[LINQ do SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)|Zawiera informacje ogólne, programowania wskazówki i przykłady dla składnika LINQ to SQL.|  
|[LINQ do obiektów](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|Zawiera informacje ogólne, programowania wskazówki i przykłady dla LINQ do obiektów.|  
|[LINQ do ADO.NET (Portal strony)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|Zawiera linki do informacji ogólnych, programowania wskazówki i przykłady dla składnika LINQ to [!INCLUDE[vstecado](~/includes/vstecado-md.md)].|  
|[LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|Zawiera informacje ogólne, programowania wskazówki i przykłady dla LINQ do XML.|  
  
##  <a name="HowToAndWalkthroughTopics"></a>Porady i wskazówki — tematy  
 [Porady: zapytanie dotyczące bazy danych](how-to-query-a-database-by-using-linq.md)  
  
 [Porady: wywoływanie procedury przechowywanej](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Porady: modyfikowanie danych w bazie danych](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Porady: łączenie danych za pomocą sprzężeń](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Porady: sortowanie wyników zapytania](how-to-sort-query-results-by-using-linq.md)  
  
 [Porady: filtrowanie wyników zapytania](how-to-filter-query-results-by-using-linq.md)  
  
 [Porady: liczba, Sum lub uśrednianie danych](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Rozdział 17: LINQ](http://go.microsoft.com/fwlink/?LinkId=195277) w [programowania w języku Visual Basic 2008](http://go.microsoft.com/fwlink/?LinkId=195383)  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Przegląd LINQ do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [LINQ do DataSet — omówienie](../../../../framework/data/adonet/linq-to-dataset-overview.md)  
 [LINQ do SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ do SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [Metody DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
