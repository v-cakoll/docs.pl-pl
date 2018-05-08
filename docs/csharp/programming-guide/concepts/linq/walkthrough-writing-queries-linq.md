---
title: 'Wskazówki: pisanie zapytań w C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: 10ffdbd6430c0ad55b0a5d71f217a7cb18163741
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Wskazówki: pisanie zapytań w C# (LINQ)
W tym przewodniku przedstawiono funkcji języka C#, które są używane do zapisu wyrażenia zapytań LINQ.  
  
## <a name="create-a-c-project"></a>Utwórz projekt C#  
  
> [!NOTE]
>  Poniższe instrukcje dotyczą programu Visual Studio. Jeśli używasz Środowisko deweloperskie innego, tworzenie projektu konsoli z odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Aby utworzyć projekt w programie Visual Studio  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  Rozwiń węzeł **zainstalowana**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **aplikacji konsoli**.  
  
4.  W **nazwa** polu tekstowym Wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
5.  Powiadomienie, że projekt zawiera odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="create-an-in-memory-data-source"></a>Utwórz źródło danych w pamięci  
 Źródło danych zapytania jest to prosta lista `Student` obiektów. Każdy `Student` rekord zawiera imię, nazwisko i tablicę liczb całkowitych, która reprezentuje wyniki testu w klasie. Skopiuj ten kod do projektu. Należy uwzględnić następujące cechy:  
  
-   `Student` Klasy składa się z właściwości zaimplementowane automatycznie.  
  
-   Na liście użytkowników jest inicjowana przy użyciu inicjatora obiektu.  
  
-   Samej listy został zainicjowany przy użyciu inicjatora kolekcji.  
  
 Ta struktura danych całego zostanie zainicjowany i wystąpienia bez jawnego wywołania konstruktora lub jawnego członka dostępu. Aby uzyskać więcej informacji na temat nowych funkcji, zobacz [właściwości Auto-Implemented](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
-   Dodaj `Student` klasy i zainicjowane listę studentom / `Program` klasy w projekcie.  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów  
  
1.  Dodaj nową `Student` do `Students` listy i użyj nazwy i wyniki dowolnego testu. Spróbuj wpisać wszystkie nowe informacje dla użytkowników domowych, aby lepiej informacje składni inicjatora obiektu.  
  
## <a name="create-the-query"></a>Utwórz zapytanie  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
-   W aplikacji `Main` metody tworzenia prostego zapytania, który, po jego wykonaniu utworzy listę wszystkich studentów, którego wynik na pierwszego testu była większa niż 90. Należy pamiętać, że ponieważ cały `Student` obiektu jest zaznaczona, jest typu zapytania `IEnumerable<Student>`. Mimo że kod można również użyć niejawnego wpisanie przy użyciu [var](../../../../csharp/language-reference/keywords/var.md) — słowo kluczowe, wpisując jawne jest używana do wyraźnie zilustrowania wyniki. (Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Należy zauważyć, że kwerendy zmiennej zakresu `student`, służy jako punkt odniesienia do każdego `Student` w źródle, zapewniając dostęp do elementu członkowskiego dla każdego obiektu.  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>Wykonanie zapytania  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1.  Teraz zapisać `foreach` pętli, które spowodują wykonanie zapytania w celu wykonania. Należy pamiętać, że o kodzie:  
  
    -   Każdy element zwrócony sekwencji jest dostępny za pośrednictwem zmiennej iteracji w `foreach` pętli.  
  
    -   Ta zmienna jest `Student`, i typu zmienną zapytania jest zgodny, `IEnumerable<Student>`.  
  
2.  Po dodaniu tego kodu, skompiluj i uruchom aplikację, aby zobaczyć wyniki w **konsoli** okna.  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>Aby dodać inny warunek filtru  
  
1.  Można połączyć wiele warunków logicznych w `where` klauzuli celu uściślenia zapytania. Poniższy kod dodaje warunek tak, aby zapytanie zwraca tych studentów których pierwszy wynik został ponad 90 i których ostatni wynik był mniejszy niż 80. `where` Klauzuli powinien przypominać następujący kod.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [gdzie klauzuli](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Zmodyfikuj zapytanie  
  
#### <a name="to-order-the-results"></a>Aby uporządkować wyniki  
  
1.  Będzie bardziej czytelne wyniki, jeśli są one w określonej kolejności. Można zamówić sekwencja zwrócony przez wszystkie dostępne pola w elementy źródłowe. Na przykład następująca `orderby` klauzuli porządkuje wyniki w kolejności alfabetycznej z zakresu od A do Z zgodnie z ostatnią nazwy użytkowników. Dodaj następujące `orderby` klauzuli do zapytania, prawy po `where` instrukcji i przed `select` instrukcji:  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Teraz zmienić `orderby` klauzulę, tak że porządkuje wyniki w kolejności odwrotnej zgodnie z wynik na pierwszego testu z najwyższym wynik do najmniejszej liczby punktów.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Zmień `WriteLine` ciąg formatu, tak aby były widoczne wyniki:  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Aby pogrupować wyniki  
  
1.  Metoda grupowania jest przydatna możliwość w wyrażeniach zapytań. Zapytań z klauzulą grupy tworzy sekwencję grup, a każda grupa sam zawiera `Key` i sekwencji, która składa się z wszystkich członków tej grupy. Następujące nowe zapytanie grupuje studentów przy użyciu pierwszą literę ich nazwiska jako klucza.  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Należy pamiętać, że typ zapytania zostanie zmieniona. Teraz tworzy sekwencję grupy, które mają `char` typu jako klucza i sekwencji `Student` obiektów. Ponieważ typ zapytania został zmieniony, poniższy kod zmiany `foreach` wykonywania pętli również:  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Uruchom aplikację i wyświetlić wyniki w **konsoli** okna.  
  
     Aby uzyskać więcej informacji, zobacz [klauzuli group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Aby jawnie wpisać zmienną lokalną  
  
1.  Jawnie kodowania `IEnumerables` z `IGroupings` może szybko stać się nużące. Można zapisać tego samego zapytania i `foreach` pętli znacznie ułatwia przy użyciu `var`. `var` — Słowo kluczowe nie zmienia typy obiektów; właśnie nakazuje kompilatorowi wnioskowanie typów. Zmień typ `studentQuery` i zmiennej iteracji `group` do `var` i ponownie uruchom zapytanie. Należy pamiętać, że w wewnętrznej `foreach` pętli, zmiennej iteracji jest nadal typu `Student`, a zapytanie działa tak jak poprzednio. Zmień `s` zmiennej iteracji `var` i ponownie uruchom zapytanie. Możesz sprawdzić, czy pobrać dokładnie takie same wyniki.  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Aby uzyskać więcej informacji na temat [var](../../../../csharp/language-reference/keywords/var.md), zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Aby uporządkować grupy według kluczy wartości  
  
1.  Uruchomienie poprzedniego zapytania, można zauważyć, że grupy nie są w kolejności alfabetycznej. Aby zmienić to ustawienie, musisz podać `orderby` klauzula po `group` klauzuli. Do użycia, ale `orderby` klauzuli, należy najpierw identyfikator, który służy jako punkt odniesienia dla grup utworzonych przez `group` klauzuli. Podaj identyfikator przy użyciu `into` — słowo kluczowe, w następujący sposób:  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Po uruchomieniu tego zapytania, pojawi się, że grupy teraz są sortowane w kolejności alfabetycznej.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Aby wprowadzić identyfikator przy użyciu let  
  
1.  Można użyć `let` — słowo kluczowe wprowadzić identyfikator dowolny wynik wyrażenia w wyrażeniu zapytania. Ten identyfikator może być wygody, jak w poniższym przykładzie lub go poprawić wydajność dzięki przechowywaniu wynik wyrażenia, aby nie ma zostać obliczona wiele razy.  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Aby uzyskać więcej informacji, zobacz [klauzula let](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Aby użyć metody składni w wyrażeniu zapytania  
  
1.  Zgodnie z opisem w [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), niektóre operacje zapytań można wyrazić tylko przy użyciu składni metody. Poniższy kod oblicza łączny wynik dla każdego `Student` w sekwencji źródłowej, a następnie wywołania `Average()` metody wyników zapytania do obliczania średniej wyniku klasy. Należy pamiętać, umieszczania nawiasy otaczające wyrażenie zapytania.  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Aby przekształcić lub zaprojektować w klauzuli wyboru  
  
1.  Jest bardzo często zapytanie w celu utworzenia sekwencji, której elementy różnią się od elementów w sekwencji źródłowej. Usuń lub komentarz z poprzednich zapytań i wykonywania pętli i zastąp go następującym kodem. Należy pamiętać, że zapytanie zwraca sekwencję ciągów (nie `Students`), a fakt ten jest odzwierciedlone w `foreach` pętli.  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Kodu we wcześniejszej części tego przewodnika wykazały, że wynik średniej klasy jest około 334. Aby utworzyć sekwencję `Students` których łączny wynik jest większa niż klasa średnią wraz z ich `Student ID`, można użyć typu anonimowego w `select` instrukcji:  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>Następne kroki  
 Po zapoznaniu się z podstawowej aspektów pracy z kwerendy w języku C#, możesz przystąpić do odczytu dokumentacja i przykłady dla określonego typu dostawcy LINQ, które planuje się:  
  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ do XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ do obiektów (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
