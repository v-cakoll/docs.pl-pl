---
title: Wprowadzenie do LINQ w Visual Basic
ms.date: 08/28/2018
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
ms.openlocfilehash: 0b163ac4af4e487ccab4c18b7907eba5a31e5779
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509055"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Wprowadzenie do LINQ w Visual Basic
Language-Integrated Query (LINQ) umożliwia wykonywanie zapytań do Visual Basic i dostarcza proste oraz wydajne narzędzia podczas pracy z danymi wszelkiego rodzaju. Zamiast wysyłania kwerendy do bazy danych w celu przetworzenia lub posługiwanie się różną składnią kwerendy dla każdego typu danych, które przeszukujesz, LINQ wprowadza kwerendy jako część języka Visual Basic. Używa zunifikowaną składnię, bez względu na typ danych.  
  
 LINQ umożliwia zapytania o dane z bazy danych programu SQL Server, XML, tablic w pamięci i kolekcje, zestawami danych ADO.NET lub dowolnego innego źródła danych w lokalnym lub zdalnym, który obsługuje LINQ. Można zrobić to wszystko stosując typowe elementy języka Visual Basic. Ponieważ zapytania są napisane w języku Visual Basic, wyniki zapytania są zwracane jako obiekty jednoznaczne. Obiekty te obsługują IntelliSense, co pozwala na szybsze pisanie kodu i wyłapywanie błędów w zapytaniach w czasie kompilacji, a nie w czasie wykonywania. Zapytania LINQ może służyć jako źródło dodatkowych kwerend w uściślaniu wyników. Mogą być również powiązane z kontrolkami, aby użytkownicy mogli łatwo przeglądać i modyfikować wyniki zapytania.  
  
 Na przykład poniższy kod pokazuje zapytanie LINQ, która zwraca listę klientów z kolekcji i grup, które je na podstawie ich lokalizacji.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady we wstępie i w [struktura zapytania LINQ](#structure-of-a-linq-query) sekcji, Dołącz następujący kod, który zwróci listę klientów i zamówień.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
## <a name="linq-providers"></a>Dostawcy LINQ  
 A *dostawcy LINQ* mapuje zapytań LINQ Visual Basic do źródła danych, którego dotyczy kwerenda. Kiedy piszesz zapytanie LINQ, dostawca zapytanie i przekształca je w poleceń, które źródła danych będą mogli wykonać. Dostawca konwertuje również dane ze źródła do obiektów, które tworzą wyników zapytania. Na koniec Konwertuje obiekty do danych podczas wysyłania aktualizacji do źródła danych.  
  
 Visual Basic obejmuje następujących dostawców LINQ.  
  
|Dostawcy|Opis|  
|---|---|  
|LINQ do obiektów|Dostawca LINQ to Objects umożliwia zapytania w pamięci, kolekcje i tablice. Jeśli obiekt obsługuje <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> interfejsu, dostawca LINQ to Objects umożliwia przeprowadzenie w nim zapytania.<br /><br /> Możesz włączyć LINQ do dostawcy obiektów importując <xref:System.Linq> przestrzeń nazw, która jest importowana domyślnie dla wszystkich projektów w języku Visual Basic.<br /><br /> Aby uzyskać więcej informacji dotyczących dostawcy LINQ to Objects, zobacz [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ do SQL|Dostawca LINQ to SQL umożliwia zapytania i modyfikację danych w bazie danych programu SQL Server. Ułatwia to mapowanie modelu obiektu dla aplikacji do tabel i obiektów w bazie danych.<br /><br /> Visual Basic sprawia, że łatwiej jest pracować z LINQ to SQL, umieszczając Object Relational Designer (O/R Designer). Projektant jest używany do tworzenia modelu obiektów w aplikacji, która mapuje do obiektów w bazie danych. O/R Designer również zapewnia funkcje procedurom składowanym w mapie i funkcje <xref:System.Data.Linq.DataContext> obiektu, który zarządza komunikacją z bazą danych i zapisuje stan kontroli optymistycznej współbieżności.<br /><br /> Aby uzyskać więcej informacji dotyczących dostawcy LINQ to SQL, zobacz [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Aby uzyskać więcej informacji dotyczących Object Relational Designer, zobacz [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ do XML|Dostawca LINQ to XML oferuje zapytania i modyfikację XML. Możesz zmodyfikować XML w pamięci lub załadować XML z, a następnie zapisz XML do pliku.<br /><br /> Ponadto dostawca LINQ to XML umożliwia literały XML i właściwości osi XML, które umożliwiają pisanie XML bezpośrednio w kodzie języka Visual Basic. Aby uzyskać więcej informacji, zobacz [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ do DataSet|Dostawca LINQ to DataSet umożliwia utworzenie zapytania i aktualizację danych w [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawu danych. Możesz dodać moc LINQ do aplikacji, które używają zestawów danych, aby uprościć i rozszerzyć swoje zdolności zapytań, agregowania i aktualizowanie danych w zestawie danych.<br /><br /> Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Struktura zapytania LINQ  
 Kwerenda LINQ, często nazywane *wyrażeniu zapytania*, składa się z kombinacji zdań zapytania, które identyfikują źródła danych i zmiennych iteracji dla zapytania. Wyrażenie zapytania może również obejmować instrukcje dotyczące sortowania, filtrowania, grupowania i łączenie lub obliczeń do zastosowania do źródła danych. Składnia wyrażenia kwerendy przypomina składnię SQL; w związku z tym można znaleźć wiele składni znane.  
  
 Wyrażenie zapytania zaczyna się od `From` klauzuli. Ta klauzula identyfikuje dane źródłowe dla zapytania i zmienne, które służą do odwoływania się do każdego elementu Źródło danych indywidualnie. Te zmienne nazywane są *należeć do zakresu zmiennych* lub *zmienne iteracji*. `From` Klauzula jest wymagana dla zapytania, z wyjątkiem `Aggregate` zapytań, gdzie `From` klauzula jest opcjonalne. Po, zakres i źródła zapytania są identyfikowane w `From` lub `Aggregate` zdań, może zawierać dowolną kombinację zdań zapytania w celu doprecyzowania zapytania. Aby uzyskać szczegółowe informacje dotyczące klauzul kwerendy Zobacz operatory zapytań LINQ w Visual Basic w dalszej części tego tematu. Na przykład poniższe zapytanie identyfikuje kolekcję źródłową danych klienta jako `customers` zmienną i zmienną iteracji o nazwie `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 W tym przykładzie jest poprawnym zapytaniem siebie. jednak zapytanie staje się mocniejsze po dodaniu większej liczby klauzul zapytania, aby udoskonalić wynik. Na przykład można dodać `Where` klauzuli, aby filtrować wynik według co najmniej jedną wartość. Wyrażenia kwerendy są jednowierszowym kodem; klauzule dodatkowe kwerendy można dołączyć tylko na końcu zapytania. Możesz rozbić zapytanie w wielu wierszach tekstu, aby polepszyć czytelność za pomocą znaku podkreślenia (\_) znak kontynuacji wiersza. Poniższy przykład kodu pokazuje przykład zapytania, które obejmuje `Where` klauzuli.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Innym potęrżnym zdaniem zapytania jest `Select` zdanie, które pozwala zwrócić tylko wybrane pola ze źródła danych. Zapytania LINQ zwracają przeliczalne kolekcje obiektów silnie typizowanych. Zapytanie może zwracać kolekcją typów anonimowych lub nazwanych. Możesz użyć `Select` klauzulę, aby zwrócić tylko jedno pole ze źródła danych. Gdy to zrobisz, typ zwracanej kolekcji jest typem tego pojedynczego pola. Można również użyć `Select` klauzulę, aby zwrócić wiele pól ze źródła danych. Gdy to zrobisz, typ zwracanej kolekcji jest nowym typem anonimowym. Można również przeprowadzać Dopasowywanie pola zwróconych przez zapytanie do pól określonego typu nazwanego. Poniższy przykład kodu pokazuje wyrażenie zapytania, które zwraca kolekcję typów anonimowe, mających członków wypełnionych danymi z wybranych pól ze źródła danych.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 Zapytania LINQ można również połączyć wiele źródeł danych i zwrócenia pojedynczego wyniku. Można to zrobić za pomocą co najmniej jeden `From` zdań, lub za pomocą `Join` lub `Group Join` klauzul zapytania. Poniższy przykład kodu pokazuje wyrażenie zapytania, które łączy dane klienta i zamówienia i zwraca kolekcję typów anonimowych, zawierające dane klienta i zamówienia.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Możesz użyć `Group Join` klauzulę, aby utworzyć hierarchiczny wynik zapytania, który zawiera kolekcję obiektów klienta. Każdy obiekt klienta ma właściwość, która zawiera zbiór wszystkich zamówień tego klienta. Poniższy przykład kodu pokazuje wyrażenie zapytania, które łączy dane klienta i zamówienia w postaci wyniku hierarchicznego i zwraca kolekcję typów anonimowych. Zapytanie zwraca typ, który zawiera `CustomerOrders` właściwość, która zawiera kolekcję danych zamówienia dla klienta. Obejmuje również `OrderTotal` właściwość, która zawiera sumę dla wszystkich zamówień tego klienta. (To zapytanie jest równoważne z LEFT OUTER JOIN).  
  
 [!code-vb[VbVbalrIntroToLINQ#6](codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Istnieje kilka dodatkowych operatorów zapytań LINQ, które można użyć do utworzenia mocnych wyrażeń zapytania. Następna sekcji tego tematu omawia różne klauzule zapytań, które można uwzględnić w wyrażeniu zapytania. Aby uzyskać szczegółowe informacje dotyczące klauzul kwerendy w języku Visual Basic, zobacz [zapytania](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Operatory zapytań LINQ Visual Basic  

Klasy w <xref:System.Linq> przestrzeni nazw i inne obszary nazw obsługi zapytań LINQ to metody, które można wywołać, aby utworzyć i dostosować zapytania, w zależności od potrzeb aplikacji. Visual Basic zawiera słowa kluczowe dla następujących wspólnych klauzul kwerendy. Aby uzyskać szczegółowe informacje dotyczące klauzul kwerendy w języku Visual Basic, zobacz [zapytania](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Klauzula From

Albo [ `From` klauzuli](../../../../visual-basic/language-reference/queries/from-clause.md) lub `Aggregate` zdanie jest wymagane do rozpoczęcia zapytania. A `From` klauzula Określa, kolekcji źródłowej i zmienną iteracji dla zapytania. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#7](codesnippet/VisualBasic/introduction-to-linq_8.vb)]

### <a name="select-clause"></a>Select — Klauzula

Opcjonalna. A [ `Select` klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md) deklaruje zestaw zmiennych iteracji dla zapytania. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#8](codesnippet/VisualBasic/introduction-to-linq_9.vb)]

Jeśli `Select` klauzuli nie zostanie określona, zmienne iteracji dla zapytania składają się ze zmiennych iteracji, określony przez `From` lub `Aggregate` klauzuli.

### <a name="where-clause"></a>Klauzula Where

Opcjonalna. A [ `Where` klauzuli](../../../../visual-basic/language-reference/queries/where-clause.md) określa warunek filtrowania dla zapytania. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#9](codesnippet/VisualBasic/introduction-to-linq_10.vb)]

### <a name="order-by-clause"></a>Klauzula Order By]

| Opcjonalnie. [ `Order By` Klauzuli](../../../../visual-basic/language-reference/queries/order-by-clause.md) określa porządek sortowania dla kolumn w zapytaniu. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#10](codesnippet/VisualBasic/introduction-to-linq_11.vb)]

### <a name="join-clause"></a>Join — Klauzula

Opcjonalna. A [ `Join` klauzuli](../../../../visual-basic/language-reference/queries/join-clause.md) łączy dwie kolekcje w jedną kolekcję. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#11](codesnippet/VisualBasic/introduction-to-linq_12.vb)]

### <a name="group-by-clause"></a>Group By — Klauzula

Opcjonalna. A [ `Group By` klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md) grupuje elementy wyników zapytań. Może służyć do zastosowania funkcji agregujących do każdej grupy. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#12](codesnippet/VisualBasic/introduction-to-linq_13.vb)]

### <a name="group-join-clause"></a>Group Join — Klauzula

Opcjonalna. A [ `Group Join` klauzuli](../../../../visual-basic/language-reference/queries/group-join-clause.md) łączy dwie kolekcje w jedną hierarchiczną kolekcję. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#13](codesnippet/VisualBasic/introduction-to-linq_14.vb)]

### <a name="aggregate-clause"></a>Aggregate — Klauzula

Albo [ `Aggregate` klauzuli](../../../../visual-basic/language-reference/queries/aggregate-clause.md) lub `From` zdanie jest wymagane do rozpoczęcia zapytania. `Aggregate` Klauzuli stosuje jedną lub więcej funkcji agregujących do kolekcji. Na przykład, można użyć `Aggregate` klauzuli, aby obliczyć sumę wszystkich elementów zwróconych przez kwerendę, tak jak w poniższym przykładzie.

[!code-vb[VbVbalrIntroToLINQ#14](codesnippet/VisualBasic/introduction-to-linq_15.vb)]

Można również użyć `Aggregate` klauzulę, aby zmodyfikować zapytanie. Na przykład, można użyć `Aggregate` klauzuli w celu wykonywania obliczeń na kolekcji powiązanych zapytań. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#15](codesnippet/VisualBasic/introduction-to-linq_16.vb)]

### <a name="let-clause"></a>Let — Klauzula

Opcjonalna. A [ `Let` klauzuli](../../../../visual-basic/language-reference/queries/let-clause.md) oblicza wartość i przypisuje go do nowej zmiennej w zapytaniu. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#16](codesnippet/VisualBasic/introduction-to-linq_17.vb)]

### <a name="distinct-clause"></a>Distinct — Klauzula

Opcjonalna. A `Distinct` klauzuli ogranicza wartości bieżącej zmiennej iteracji w celu wyeliminowania zduplikowanych wartości w wynikach kwerendy. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#17](codesnippet/VisualBasic/introduction-to-linq_18.vb)]

### <a name="skip-clause"></a>Skip — Klauzula

Opcjonalna. A [ `Skip` klauzuli](../../../../visual-basic/language-reference/queries/skip-clause.md) pomija określoną liczbę elementów w kolekcji, a następnie zwraca pozostałe elementy. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#18](codesnippet/VisualBasic/introduction-to-linq_19.vb)]

### <a name="skip-while-clause"></a>Skip While — Klauzula

Opcjonalna. A [ `Skip While` klauzuli](../../../../visual-basic/language-reference/queries/skip-while-clause.md) omija elementy w kolekcji, tak długo, jak długo określony warunek przyjmuje `true` , a następnie zwraca pozostałe elementy. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#19](codesnippet/VisualBasic/introduction-to-linq_20.vb)]

### <a name="take-clause"></a>Take — Klauzula

Opcjonalna. A [ `Take` klauzuli](../../../../visual-basic/language-reference/queries/take-clause.md) zwraca określoną liczbę elementów sąsiadujących z początku kolekcji. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#20](codesnippet/VisualBasic/introduction-to-linq_21.vb)]

### <a name="take-while-clause"></a>Take While — Klauzula

Opcjonalna. A [ `Take While` klauzuli](../../../../visual-basic/language-reference/queries/take-while-clause.md) zawiera elementy w kolekcji, tak długo, jak długo określony warunek przyjmuje `true` i pomija pozostałe elementy. Na przykład:

[!code-vb[VbVbalrIntroToLINQ#21](codesnippet/VisualBasic/introduction-to-linq_22.vb)]
  
## <a name="use-additional-linq-query-features"></a>Korzystanie z dodatkowych funkcji zapytania LINQ  
  
Można użyć dodatkowych funkcji zapytania LINQ, wywołując elementy wyliczalnych lub odpytywalnych typów dostarczonych przez LINQ. Te dodatkowe możliwości można użyć poprzez wywołanie konkretnego operatora zapytania w wyniku wyrażenia zapytania. Na przykład w poniższym przykładzie użyto <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> metodę, aby połączyć dwa wyniki zapytań w jeden wynik zapytania. Używa ona <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> metodę, aby zwrócić wynik kwerendy w postaci listy ogólnej.
  
 [!code-vb[VbVbalrIntroToLINQ#22](codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Aby uzyskać szczegółowe informacje o dodatkowych możliwościach LINQ, zobacz [standardowe operatory zapytań — Przegląd](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Połączenie z bazą danych za pomocą LINQ to SQL  
 W języku Visual Basic należy zidentyfikować obiekty bazy danych programu SQL Server, takie jak tabele, widoki i procedury składowane, które chcesz uzyskać dostęp za pomocą LINQ do pliku SQL. Plik LINQ to SQL ma rozszerzenie .dbml.  
  
 Jeśli masz prawidłowe połączenie z bazą danych programu SQL Server, możesz dodać **klasy LINQ do SQL** szablonu elementu projektu. Wyświetli to Object Relational Designer (O/R designer). O/R Designer umożliwia przeciąganie elementów, które chcesz uzyskać dostęp w swoim kodzie z **Eksploratora serwera**/**Eksplorator bazy danych** na powierzchnię projektanta. Plik LINQ to SQL dodaje <xref:System.Data.Linq.DataContext> obiektu do projektu. Ten obiekt zawiera właściwości i kolekcje dla tabel i widoków, które mają dostęp do i metody dla procedur przechowywanych, które ma zostać wywołana. Po zapisaniu zmian do programu LINQ to SQL (.dbml) plik, te obiekty są dostępne w kodzie, odwołując się do <xref:System.Data.Linq.DataContext> obiekt, który jest zdefiniowany przez projektanta O/R. <xref:System.Data.Linq.DataContext> Obiektu dla Twojego projektu jest nazwany na podstawie nazwy użytkownika plik LINQ to SQL. Na przykład plik LINQ to SQL o nazwie Northwind.dbml utworzy <xref:System.Data.Linq.DataContext> obiektu o nazwie `NorthwindDataContext`.  
  
 Przykłady z instrukcjami krok po kroku, zobacz [porady: zapytanie dotyczące bazy danych](how-to-query-a-database-by-using-linq.md) i [porady: wywoływanie procedury przechowywane](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Funkcje Visual Basic obsługujące LINQ  
 Visual Basic obejmuje inne zauważalne cechy, które upewnij korzystanie z LINQ jest proste i zmniejszyć ilość kodu, który trzeba napisać, aby wykonać zapytania LINQ. Należą do nich między innymi:  
  
-   **Typy anonimowe**, które umożliwiają tworzenie nowego typu opartego na wynikach zapytania.  
  
-   **Niejawnie wpisane zmienne**, które umożliwiają odroczenie określania typu i umożliwiają kompilator wywnioskować typ bazując na wyniku zapytania.  
  
-   **Metody rozszerzenia**, które pozwalają rozszerzyć istniejący typ własnymi metodami bez modyfikowania samego typu.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Basic funkcji czy obsługa LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Wykonanie odroczonych i natychmiastowych zapytań

 Wykonywanie kwerendy różni się od tworzenia kwerendy. Po utworzeniu zapytania, jego wykonanie zostanie wywołane przez oddzielny mechanizm. Zapytania mogą być wykonywane natychmiast po tym, jak to zdefiniowano (*natychmiastowe wykonanie*), lub definicji mogą być przechowywane i zapytania, które może być wykonane później (*wykonanie odroczone*).  
  
 Domyślnie podczas tworzenia zapytania, samo zapytanie nie jest wykonywane natychmiast. Zamiast tego definicja kwerendy jest przechowywana w zmiennej, która jest używana do odwoływać się do wyniku zapytania. Gdy zmienna wynik zapytania odbywa się w dalszej części kodu, takich jak w `For…Next` pętli, zapytanie jest wykonywane. Ten proces jest nazywany *wykonanie odroczone*.  
  
 Zapytania mogą być również wykonywane gdy są zdefiniowane, co jest określane jako *natychmiastowe wykonanie*. Możesz wyzwolić natychmiastowe wykonanie, stosując metodę która wymaga dostępu do indywidualnych elementów wyniku zapytania. Może to być wynikiem dodania funkcji agregującej, takich jak `Count`, `Sum`, `Average`, `Min`, lub `Max`. Aby uzyskać więcej informacji na temat funkcji agregujących, zobacz [Aggregate — klauzula](../../../language-reference/queries/aggregate-clause.md).  
  
 Za pomocą `ToList` lub `ToArray` metody również wymusi natychmiastowe wykonanie. Może to być przydatne, gdy użytkownik chce przeprowadzić zapytanie natychmiastowo i wyniki w pamięci podręcznej. Aby uzyskać więcej informacji o tych metodach, zobacz [konwertowanie typów danych](../../concepts/linq/converting-data-types.md).  
  
 Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [Your pierwszego zapytania LINQ pisania](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML w Visual Basic  
 Funkcje języka XML w Visual Basic obejmują literały XML i właściwości osi XML, które umożliwiają łatwe tworzenie, dostęp, zapytania i modyfikację XML w kodzie. Literały XML umożliwiają pisanie XML bezpośrednio w kodzie. Kompilator Visual Basic traktuje XML jako obiekt pierwszej klasy.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć XML element, dostęp do jego elementów podrzędnych i atrybutów i zbadać zawartość elementu za pomocą LINQ.  
  
 [!code-vb[VbXmlSamples#8](../../../language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Powiązane zasoby  
  
|Temat|Opis|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Opisuje funkcje języka XML w Visual Basic, które mogą być wyszukiwane i które umożliwiają objęcie XML jako obiekty najwyższej jakości danych kodu języka Visual Basic.|  
|[Zapytania](../../../language-reference/queries/index.md)|Zawiera dodatkowe informacje dotyczące klauzul kwerendy, które są dostępne w języku Visual Basic.|  
|[LINQ (Language-Integrated Query)](../../concepts/linq/index.md)|Zawiera ogólne informacje, wskazówki programowania i przykłady dla programu LINQ.|  
|[LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)|Zawiera ogólne informacje, wskazówki programowania i przykłady dla programu LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Zawiera ogólne informacje, wskazówki programowania i przykłady dla programu LINQ do obiektów.|  
|[LINQ to ADO.NET (strona portalu)](../../concepts/linq/linq-to-adonet-portal-page.md)|Zawiera łącza do ogólne informacje, wskazówki programowania i przykłady dla programu LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Zawiera ogólne informacje, wskazówki programowania i przykłady dla programu LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Jak wskazówki i porady
 [Porady: zapytanie dotyczące bazy danych](how-to-query-a-database-by-using-linq.md)  
  
 [Porady: wywoływanie procedury przechowywanej](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Porady: modyfikowanie danych w bazie danych](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Porady: łączenie danych za pomocą sprzężeń](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Porady: sortowanie wyników zapytania](how-to-sort-query-results-by-using-linq.md)  
  
 [Porady: filtrowanie wyników zapytania](how-to-filter-query-results-by-using-linq.md)  
  
 [Porady: liczba, Suma lub średnia danych](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [17 rozdziałów: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) w [Programming Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Zobacz także

- [LINQ (Language-Integrated Query)](../../concepts/linq/index.md)  
- [Przegląd interfejsu LINQ to XML w Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)  
- [Omówienie LINQ to DataSet](~/docs/framework/data/adonet/linq-to-dataset-overview.md)  
- [LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)  
- [Narzędzia LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
