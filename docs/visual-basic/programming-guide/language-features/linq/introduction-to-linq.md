---
title: Wprowadzenie do LINQ
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
ms.openlocfilehash: 3f58edf326ab9415d78d7065d74d8c1954fbbf37
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76315866"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Wprowadzenie do LINQ w Visual Basic
Funkcja Query-Integrated Language (LINQ) dodaje możliwości zapytań do Visual Basic i oferuje proste i zaawansowane możliwości podczas pracy z danymi wszelkiego rodzaju. Zamiast wysyłać zapytanie do bazy danych, które mają być przetwarzane, lub pracując z inną składnią zapytania dla każdego typu danych, które są przeszukiwane, LINQ wprowadza zapytania w ramach języka Visual Basic. Używa ujednoliconej składni niezależnie od typu danych.  
  
 LINQ umożliwia wykonywanie zapytań dotyczących danych z bazy danych SQL Server, XML, tablic znajdujących się w pamięci i kolekcji, zestawów danych ADO.NET lub dowolnego innego zdalnego lub lokalnego źródła danych, które obsługuje LINQ. Wszystko to można zrobić za pomocą typowych elementów języka Visual Basic. Ponieważ zapytania są napisane w języku Visual Basic, wyniki zapytania są zwracane jako obiekty silnie wpisane. Te obiekty obsługują funkcję IntelliSense, która umożliwia szybsze pisanie kodu i przechwytywanie błędów w zapytaniach w czasie kompilacji, a nie w czasie wykonywania. Zapytania LINQ mogą służyć jako źródło dodatkowych zapytań, aby uściślić wyniki. Mogą być również powiązane z kontrolkami, aby użytkownicy mogli łatwo wyświetlać i modyfikować wyniki zapytania.  
  
 Na przykład poniższy kod przedstawia zapytanie LINQ, które zwraca listę klientów z kolekcji i grupuje je na podstawie ich lokalizacji.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady we wprowadzeniu i w [strukturze sekcji zapytania LINQ](#structure-of-a-linq-query) , należy uwzględnić Poniższy kod, który zwraca listę klientów i zamówień.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>Dostawcy LINQ  
 *Dostawca LINQ* mapuje zapytania Visual Basic LINQ do źródła danych, którego dotyczy kwerenda. Podczas pisania zapytania LINQ dostawca wykonuje zapytanie i tłumaczy je na polecenia, które mogą zostać wykonane przez źródło danych. Dostawca konwertuje również dane ze źródła do obiektów, które tworzą wynik zapytania. Na koniec Konwertuje obiekty na dane po wysłaniu aktualizacji do źródła danych.  
  
 Visual Basic obejmuje następujących dostawców LINQ.  
  
|Provider|Opis|  
|---|---|  
|LINQ do obiektów|Dostawca LINQ to Objects umożliwia wykonywanie zapytań dotyczących kolekcji i tablic w pamięci. Jeśli obiekt obsługuje interfejs <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>, dostawca LINQ to Objects umożliwia wykonywanie zapytań.<br /><br /> Dostawcę LINQ to Objects można włączyć przez zaimportowanie <xref:System.Linq> przestrzeni nazw, która jest importowana domyślnie dla wszystkich projektów Visual Basic.<br /><br /> Aby uzyskać więcej informacji na temat dostawcy LINQ to Objects, zobacz [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ do SQL|Dostawca LINQ to SQL umożliwia wykonywanie zapytań i modyfikowanie danych w SQL Server bazie danych. Dzięki temu można łatwo zmapować model obiektów dla aplikacji do tabel i obiektów w bazie danych.<br /><br /> Visual Basic ułatwia pracę z LINQ to SQL przez uwzględnienie Object Relational Designer (Projektant O/R). Ten Projektant służy do tworzenia modelu obiektów w aplikacji mapowanej do obiektów w bazie danych. Projektant O/R udostępnia również funkcje do mapowania procedur przechowywanych i funkcji do obiektu <xref:System.Data.Linq.DataContext>, który zarządza komunikacją z bazą danych i przechowuje stan dla optymistycznych kontroli współbieżności.<br /><br /> Aby uzyskać więcej informacji na temat dostawcy LINQ to SQL, zobacz [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Aby uzyskać więcej informacji na temat Object Relational Designer, zobacz [narzędzia LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ do XML|Dostawca LINQ to XML umożliwia wykonywanie zapytań i modyfikowanie kodu XML. Możesz zmodyfikować plik XML w pamięci lub załadować XML z i zapisać XML do pliku.<br /><br /> Dodatkowo dostawca LINQ to XML włącza literały XML i właściwości osi XML, które umożliwiają pisanie kodu XML bezpośrednio w kodzie Visual Basic. Aby uzyskać więcej informacji, zobacz [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|Dostawca LINQ to DataSet umożliwia wykonywanie zapytań i aktualizowanie danych w zestawie danych ADO.NET. Możesz dodać moc LINQ do aplikacji, które używają zestawów danych, aby uprościć i zwiększyć możliwości wykonywania zapytań, agregowania i aktualizowania danych w zestawie danych.<br /><br /> Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Struktura zapytania LINQ  
 Zapytanie LINQ, często nazywane *wyrażeniem zapytania*, składa się z kombinacji klauzul zapytania, które identyfikują źródła danych i zmienne iteracji dla zapytania. Wyrażenie zapytania może również zawierać instrukcje dotyczące sortowania, filtrowania, grupowania i łączenia lub obliczeń, które mają zastosowanie do danych źródłowych. Składnia wyrażenia zapytania jest podobna do składni języka SQL; w związku z tym można znaleźć wiele znanych składni.  
  
 Wyrażenie zapytania rozpoczyna się od klauzuli `From`. Ta klauzula identyfikuje dane źródłowe zapytania i zmienne, które są używane do odwoływania się do każdego elementu danych źródłowych pojedynczo. Te zmienne są nazwanymi *zmiennymi zakresów* lub *zmiennymi iteracji*. Klauzula `From` jest wymagana dla zapytania, z wyjątkiem zapytań `Aggregate`, gdzie klauzula `From` jest opcjonalna. Po zidentyfikowaniu zakresu i źródła zapytania w klauzulach `From` lub `Aggregate` można dołączyć dowolną kombinację klauzul zapytania, aby uściślić zapytanie. Aby uzyskać szczegółowe informacje na temat klauzul zapytania, zobacz Visual Basic operatory zapytań LINQ w dalszej części tego tematu. Na przykład następujące zapytanie identyfikuje źródłową kolekcję danych klienta jako zmienną `customers` i zmienną iteracji o nazwie `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 Ten przykład jest poprawnym zapytaniem. jednak zapytanie jest znacznie bardziej wydajne, gdy dodasz więcej klauzul zapytania, aby uściślić wynik. Na przykład można dodać klauzulę `Where`, aby odfiltrować wynik przez jedną lub więcej wartości. Wyrażenia zapytania są pojedynczym wierszem kodu; można po prostu dołączyć dodatkowe klauzule zapytania do końca zapytania. Możesz przerwać zapytanie w wielu wierszach tekstu, aby zwiększyć czytelność przy użyciu znaku podkreślenia (\_). Poniższy przykład kodu pokazuje przykład kwerendy zawierającej klauzulę `Where`.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 Kolejną zaawansowaną klauzulą zapytania jest klauzula `Select`, która umożliwia zwracanie tylko wybranych pól ze źródła danych. Zapytania LINQ zwracają wyliczalne kolekcje obiektów o jednoznacznie określonym typie. Zapytanie może zwracać kolekcję typów anonimowych lub nazwanych typów. Można użyć klauzuli `Select` do zwrócenia tylko jednego pola ze źródła danych. Gdy to zrobisz, typ zwracanej kolekcji jest typem tego pojedynczego pola. Można również użyć klauzuli `Select`, aby zwrócić wiele pól ze źródła danych. Gdy to zrobisz, typ zwracanej kolekcji jest nowym typem anonimowym. Można również dopasować pola zwracane przez zapytanie do pól o określonym nazwanym typie. Poniższy przykład kodu pokazuje wyrażenie zapytania, które zwraca kolekcję typów anonimowych, które mają elementy członkowskie wypełniane danymi z wybranych pól ze źródła danych.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 Zapytań LINQ można również używać do łączenia wielu źródeł danych i zwracać pojedynczego wyniku. Można to zrobić z co najmniej jedną klauzulą `From` lub za pomocą klauzul zapytania `Join` lub `Group Join`. Poniższy przykład kodu przedstawia wyrażenie zapytania, które łączy dane klienta i zamówienia i zwraca kolekcję typów anonimowych zawierających dane klienta i zamówienia.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 Za pomocą klauzuli `Group Join` można utworzyć hierarchiczny wynik zapytania, który zawiera kolekcję obiektów klienta. Każdy obiekt klienta ma właściwość, która zawiera kolekcję wszystkich zamówień dla tego klienta. Poniższy przykład kodu pokazuje wyrażenie zapytania, które łączy dane klienta i zamówienia jako wynik hierarchiczny i zwraca kolekcję typów anonimowych. Zapytanie zwraca typ, który zawiera właściwość `CustomerOrders`, która zawiera kolekcję danych zamówienia dla klienta. Zawiera również właściwość `OrderTotal`, która zawiera sumę sum dla wszystkich zamówień dla tego klienta. (To zapytanie jest równoważne z lewym SPRZĘŻENIem ZEWNĘTRZNYm).  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 Istnieje kilka dodatkowych operatorów zapytań LINQ, których można użyć do tworzenia zaawansowanych wyrażeń zapytań. W następnej sekcji tego tematu omówiono różne klauzule zapytań, które można uwzględnić w wyrażeniu zapytania. Aby uzyskać szczegółowe informacje na temat klauzul zapytania Visual Basic, zobacz [zapytania](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic operatory zapytań LINQ  

Klasy w przestrzeni nazw <xref:System.Linq> i inne przestrzenie nazw obsługujące zapytania LINQ obejmują metody, które można wywołać, aby tworzyć i udoskonalać zapytania w zależności od potrzeb aplikacji. Visual Basic zawiera słowa kluczowe dla następujących typowych klauzul zapytania. Aby uzyskać szczegółowe informacje na temat klauzul zapytania Visual Basic, zobacz [zapytania](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Klauzula From

Do rozpoczęcia zapytania jest wymagane wyrażenie [`From`](../../../../visual-basic/language-reference/queries/from-clause.md) lub klauzula `Aggregate`. Klauzula `From` Określa kolekcję źródłową i zmienną iteracji dla zapytania. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select — Klauzula

Opcjonalny. [Klauzula`Select`](../../../../visual-basic/language-reference/queries/select-clause.md) deklaruje zestaw zmiennych iteracji dla zapytania. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

Jeśli klauzula `Select` nie zostanie określona, zmienne iteracji dla zapytania składają się ze zmiennych iteracji określonych przez klauzulę `From` lub `Aggregate`.

### <a name="where-clause"></a>Klauzula Where

Opcjonalny. [Klauzula`Where`](../../../../visual-basic/language-reference/queries/where-clause.md) określa warunek filtrowania dla zapytania. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Order By — Klauzula

Opcjonalny. [Klauzula`Order By`](../../../../visual-basic/language-reference/queries/order-by-clause.md) określa kolejność sortowania kolumn w zapytaniu. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join — Klauzula

Opcjonalny. [Klauzula`Join`](../../../../visual-basic/language-reference/queries/join-clause.md) łączy dwie kolekcje w jedną kolekcję. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By — Klauzula

Opcjonalny. [Klauzula`Group By`](../../../../visual-basic/language-reference/queries/group-by-clause.md) Grupuje elementy wyniku zapytania. Może służyć do stosowania funkcji agregujących do każdej grupy. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join — Klauzula

Opcjonalny. [Klauzula`Group Join`](../../../../visual-basic/language-reference/queries/group-join-clause.md) łączy dwie kolekcje w jedną hierarchiczną kolekcję. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate — Klauzula

Do rozpoczęcia zapytania jest wymagane wyrażenie [`Aggregate`](../../../../visual-basic/language-reference/queries/aggregate-clause.md) lub klauzula `From`. Klauzula `Aggregate` stosuje co najmniej jedną funkcję agregującą do kolekcji. Na przykład można użyć klauzuli `Aggregate`, aby obliczyć sumę dla wszystkich elementów zwróconych przez zapytanie, jak w poniższym przykładzie.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

Można również użyć klauzuli `Aggregate`, aby zmodyfikować zapytanie. Na przykład można użyć klauzuli `Aggregate` do wykonania obliczeń w powiązanej kolekcji zapytań. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let — Klauzula

Opcjonalny. [Klauzula`Let`](../../../../visual-basic/language-reference/queries/let-clause.md) oblicza wartość i przypisuje ją do nowej zmiennej w zapytaniu. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct — Klauzula

Opcjonalny. Klauzula `Distinct` ogranicza wartości bieżącej zmiennej iteracji w celu wyeliminowania zduplikowanych wartości w wynikach zapytania. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip — Klauzula

Opcjonalny. [Klauzula`Skip`](../../../../visual-basic/language-reference/queries/skip-clause.md) pomija określoną liczbę elementów w kolekcji, a następnie zwraca pozostałe elementy. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>Skip While — Klauzula

Opcjonalny. [Klauzula`Skip While`](../../../../visual-basic/language-reference/queries/skip-while-clause.md) pomija elementy w kolekcji, tak długo, jak określony warunek jest `true`, a następnie zwraca pozostałe elementy. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take — Klauzula

Opcjonalny. [Klauzula`Take`](../../../../visual-basic/language-reference/queries/take-clause.md) Zwraca określoną liczbę ciągłych elementów z początku kolekcji. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While — Klauzula

Opcjonalny. [Klauzula`Take While`](../../../../visual-basic/language-reference/queries/take-while-clause.md) zawiera elementy w kolekcji, tak długo, jak określony warunek jest `true` i pomija pozostałe elementy. Na przykład:

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Korzystanie z dodatkowych funkcji zapytania LINQ  
  
Możesz użyć dodatkowych funkcji zapytania LINQ, wywołując elementy wyliczalnych i Queryable typów dostarczonych przez LINQ. Możesz użyć tych dodatkowych funkcji przez wywołanie określonego operatora zapytania w wyniku wyrażenia zapytania. Na przykład poniższy przykład używa metody <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType>, aby połączyć wyniki dwóch zapytań w jeden wynik zapytania. Używa metody <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, aby zwrócić wynik zapytania jako listę ogólną.
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 Aby uzyskać szczegółowe informacje o dodatkowych możliwościach LINQ, zobacz [standardowe operatory zapytań — Omówienie](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Łączenie z bazą danych przy użyciu LINQ to SQL  
 W Visual Basic identyfikujesz obiekty bazy danych SQL Server, takie jak tabele, widoki i procedury składowane, do których chcesz uzyskać dostęp przy użyciu pliku LINQ to SQL. Plik LINQ to SQL ma rozszerzenie. dbml.  
  
 Jeśli masz prawidłowe połączenie z bazą danych SQL Server, możesz dodać szablon elementu **LINQ to SQL klas** do projektu. Spowoduje to wyświetlenie Object Relational Designer (Projektant O/R). Projektant O/R umożliwia przeciąganie elementów, do których chcesz uzyskać dostęp w kodzie z **Eksplorator serwera**/**Eksplorator bazy danych** na powierzchnię projektanta. Plik LINQ to SQL dodaje obiekt <xref:System.Data.Linq.DataContext> do projektu. Ten obiekt zawiera właściwości i kolekcje dla tabel i widoków, do których chcesz uzyskać dostęp, oraz metod składowanych, które mają być wywoływane. Po zapisaniu zmian w pliku LINQ to SQL (. dbml) można uzyskać dostęp do tych obiektów w kodzie, odwołując się do obiektu <xref:System.Data.Linq.DataContext>, który jest zdefiniowany przez projektanta O/R. Obiekt <xref:System.Data.Linq.DataContext> dla projektu jest nazwany na podstawie nazwy pliku LINQ to SQL. Na przykład plik LINQ to SQL o nazwie Northwind. dbml utworzy obiekt <xref:System.Data.Linq.DataContext> o nazwie `NorthwindDataContext`.  
  
 Aby uzyskać przykłady instrukcji krok po kroku, zobacz How to [: Query a Database](how-to-query-a-database-by-using-linq.md) and How to: [calld procedur składowanych](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic funkcje, które obsługują LINQ  
 Visual Basic obejmuje inne istotne funkcje, które ułatwiają korzystanie z LINQ Simple i zmniejszają ilość kodu, który należy napisać, aby wykonywać zapytania LINQ. Należą do nich między innymi:  
  
- **Typy anonimowe**, które umożliwiają tworzenie nowego typu na podstawie wyniku zapytania.  
  
- **Niejawnie wpisane zmienne**, które umożliwiają odroczenie określania typu i pozwalają kompilatorowi na wnioskowanie o typie na podstawie wyniku zapytania.  
  
- **Metody rozszerzające**, które umożliwiają rozszerzanie istniejącego typu przy użyciu własnych metod bez modyfikowania samego typu.  
  
 Aby uzyskać szczegółowe informacje, zobacz [Visual Basic funkcje, które obsługują LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Opóźnione i natychmiastowe wykonywanie zapytań

 Wykonywanie zapytania jest niezależne od tworzenia zapytania. Po utworzeniu zapytania jego wykonanie jest wyzwalane przez oddzielny mechanizm. Zapytanie może być wykonywane zaraz po jego zdefiniowaniu (*natychmiastowe wykonanie*) lub definicji może być przechowywane, a zapytanie można wykonać później (*odroczone wykonanie*).  
  
 Domyślnie podczas tworzenia zapytania, samo zapytanie nie jest wykonywane natychmiast. Zamiast tego definicja zapytania jest przechowywana w zmiennej, która jest używana do odwoływania się do wyniku zapytania. Gdy zmienna wyniku zapytania jest dostępna później w kodzie, na przykład w pętli `For…Next`, zapytanie jest wykonywane. Ten proces jest nazywany *wykonaniem odroczonym*.  
  
 Zapytania można również wykonywać, gdy są zdefiniowane, które są określane jako *natychmiastowe wykonanie*. Możesz wyzwolić natychmiastowe wykonywanie, stosując metodę, która wymaga dostępu do poszczególnych elementów wyniku zapytania. Może to być wynikiem dołączenia funkcji agregującej, takiej jak `Count`, `Sum`, `Average`, `Min`lub `Max`. Aby uzyskać więcej informacji na temat funkcji agregujących, zobacz [klauzula Aggregate](../../../language-reference/queries/aggregate-clause.md).  
  
 Użycie metod `ToList` lub `ToArray` spowoduje również wymuszenie natychmiastowego wykonania. Może to być przydatne, gdy chcesz natychmiast wykonać zapytanie i przechować wyniki. Aby uzyskać więcej informacji na temat tych metod, zobacz [konwertowanie typów danych](../../concepts/linq/converting-data-types.md).  
  
 Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML w Visual Basic  
 Funkcje XML w Visual Basic obejmują literały XML i właściwości osi XML, które umożliwiają łatwe tworzenie, uzyskiwanie dostępu do kodu XML i modyfikowanie go w kodzie. Literały XML umożliwiają pisanie XML bezpośrednio w kodzie. Kompilator Visual Basic traktuje kod XML jako obiekt danych pierwszej klasy.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć element XML, uzyskać dostęp do jego elementów podrzędnych i atrybutów, a następnie zbadać zawartość elementu przy użyciu LINQ.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Aby uzyskać więcej informacji, zobacz [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Zasoby pokrewne  
  
|Temat|Opis|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Opisuje funkcje XML w Visual Basic, które mogą być zapytania i które umożliwiają dołączanie XML jako obiektów danych pierwszej klasy w kodzie Visual Basic.|  
|[Zapytania](../../../language-reference/queries/index.md)|Zawiera informacje referencyjne na temat klauzul zapytania, które są dostępne w Visual Basic.|  
|[LINQ (zapytanie zintegrowane z językiem)](../../concepts/linq/index.md)|Zawiera ogólne informacje, wskazówki dotyczące programowania i przykłady dla LINQ.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|Zawiera ogólne informacje, wskazówki dotyczące programowania i przykłady dla LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Zawiera ogólne informacje, wskazówki dotyczące programowania i przykłady dla LINQ to Objects.|  
|[LINQ to ADO.NET (strona portalu)](../../concepts/linq/linq-to-adonet-portal-page.md)|Zawiera linki do ogólnych informacji, wskazówek dotyczących programowania i przykładów dla LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Zawiera ogólne informacje, wskazówki dotyczące programowania i przykłady dla LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Tematy dotyczące i Instruktaż
 [Instrukcje: zapytanie do bazy danych](how-to-query-a-database-by-using-linq.md)  
  
 [Instrukcje: wywoływanie procedury składowanej](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Instrukcje: modyfikowanie danych w bazie danych](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Instrukcje: łączenie danych z sprzężeniami](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Instrukcje: sortowanie wyników zapytania](how-to-sort-query-results-by-using-linq.md)  
  
 [Instrukcje: filtrowanie wyników zapytania](how-to-filter-query-results-by-using-linq.md)  
  
 [Instrukcje: zliczanie, sumowanie lub średnie dane](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Instrukcje: Znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Rozdział 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) w [programowaniu Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Zobacz także

- [LINQ (zapytanie zintegrowane z językiem)](../../concepts/linq/index.md)
- [Omówienie LINQ to XML w Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [Omówienie LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Narzędzia LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
