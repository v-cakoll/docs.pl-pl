---
title: 'Przewodnik: Pisanie zapytań w języku C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: 345acd17a6357f71f5c047475a4494a1fa793a58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595793"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Przewodnik: Pisanie zapytań w języku C# (LINQ)
W tym instruktażu przedstawiono funkcji języka C#, które służy do zapisywania wyrażenia zapytań LINQ.  
  
## <a name="create-a-c-project"></a>Utwórz projekt C#  
  
> [!NOTE]
>  Poniższe instrukcje dotyczą programu Visual Studio. Jeśli używasz środowiska deweloperskiego różnych, Utwórz projekt konsoli za pomocą odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Aby utworzyć projekt w programie Visual Studio  
  
1. Uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3. Rozwiń **zainstalowane**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz **aplikacji konsoli**.  
  
4. W **nazwa** polu tekstowym Wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
5. Zwróć uwagę, że projekt zawiera odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="create-an-in-memory-data-source"></a>Utwórz źródło danych w pamięci  
 Źródło danych dla zapytania jest prostą listę `Student` obiektów. Każdy `Student` rekord zawiera imię, nazwisko i tablicy liczb całkowitych, reprezentujący ich wyniki testów w klasie. Skopiuj ten kod do projektu. Należy zwrócić uwagę następujących właściwości:  
  
- `Student` Klasy składa się z właściwości zaimplementowane automatycznie.  
  
- Każdy uczeń, na liście jest inicjowany za pomocą inicjatora obiektów.  
  
- Samej listy jest inicjowany za pomocą inicjatora kolekcji.  
  
 Tej struktury danych całego zostanie zainicjowana i tworzone bez jawnego wywołania konstruktora lub jawny element członkowski dostępu. Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz [implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
- Dodaj `Student` klasy i zainicjowany listę uczniów `Program` klasy w projekcie.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów  
  
1. Dodaj nową `Student` do `Students` listy i użyj nazwy i wyniki dowolnego testu. Spróbuj wpisać wszystkie nowe informacje dla uczniów, aby lepiej Poznaj składnię dla inicjatora obiektu.  
  
## <a name="create-the-query"></a>Utwórz zapytanie  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
- Przy stosowaniu `Main` metody tworzenia prostego zapytania, które, gdy jest wykonywany, generuje listę wszystkich uczniów, którego wynik pierwszego testu była większa niż 90. Należy pamiętać, że ponieważ cały `Student` obiekt jest wybrany, jest typ zapytania `IEnumerable<Student>`. Mimo że kod można również użyć niejawnego wpisywania, za pomocą [var](../../../../csharp/language-reference/keywords/var.md) — słowo kluczowe, jawnych typowań służy do wyraźnie przedstawiają wyniki. (Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Należy zauważyć, że zapytania zmienna zakresu `student`, służy jako punkt odniesienia do każdego `Student` w źródle, zapewniając dostęp do elementu członkowskiego dla każdego obiektu.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Wykonanie zapytania  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1. Teraz zapisać `foreach` pętli, która spowoduje, że kwerenda do wykonania. Należy pamiętać o następujących o kodzie:  
  
    - Każdy element w zwracanej sekwencji jest dostępny za pośrednictwem zmiennej iteracji w `foreach` pętli.  
  
    - Typ tej zmiennej jest `Student`, a typ zmiennej zapytania jest zgodny, `IEnumerable<Student>`.  
  
2. Po dodaniu tego kodu, skompilować i uruchomić aplikację, aby zobaczyć wyniki w parametrze **konsoli** okna.  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Aby dodać inny warunek filtru  
  
1. Można połączyć wiele warunków logicznych w `where` klauzulę, aby dalej zawęzić zapytanie. Poniższy kod dodaje warunek, dlatego, że zapytanie zwraca tych studentów, którego wynik pierwszego był ponad 90 i którego ostatni wynik był mniejszy niż 80. `where` Klauzuli powinien przypominać następujący kod.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Zmodyfikuj zapytanie  
  
#### <a name="to-order-the-results"></a>Aby uporządkować wyniki  
  
1. Będzie można ją łatwiej wyników skanowania, jeśli są one w określonej kolejności. Może zamówić łączność obejmującą zwracanej sekwencji według dowolnego pola dostępne w elementy źródłowe. Na przykład następująca `orderby` klauzuli zamówienia wyniki w kolejności alfabetycznej od A do Z, zgodnie z ostatnio nazwę każdego ucznia. Dodaj następujący kod `orderby` klauzuli do kwerendy, zaraz po `where` instrukcji i przed `select` instrukcji:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Teraz Zmień `orderby` klauzuli, tak że porządkuje wyniki w odwrotnej kolejności według oceny pierwszego testu z najwyższym wynikiem do najmniejszej liczby punktów.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Zmiana `WriteLine` ciąg formatu, dzięki czemu można zobaczyć wyniki:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [klauzuli orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Aby pogrupować wyniki  
  
1. Grupowanie jest zaawansowaną możliwością w wyrażeniach zapytań. Zapytanie z klauzulą grupy tworzy sekwencję grup, a każda grupa sam zawiera `Key` i sekwencji, który składa się z wszystkich członków tej grupy. Następujące zapytanie nowe grupy uczniów przy użyciu pierwszej litery swoje nazwisko jako klucz.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Należy pamiętać, że typ zapytania zostanie zmieniona. Teraz wytwarza sekwencję grupy, które mają `char` typ jako klucz i sekwencję `Student` obiektów. Ponieważ typ zapytania została zmieniona, poniższy kod zmiany `foreach` wykonywania pętli również:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uruchom aplikację i wyświetlić wyniki w **konsoli** okna.  
  
     Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Aby jawnie wpisać zmienną lokalną  
  
1. Jawne kodowania `IEnumerables` z `IGroupings` może szybko stać się uciążliwe. Można napisać tego samego zapytania i `foreach` pętli za pomocą znacznie więcej wygodnie `var`. `var` — Słowo kluczowe nie zmienia typów obiektów; po prostu nakazuje kompilatorowi wywnioskowania typów. Zmiana rodzaju `studentQuery` , a zmienna iteracji `group` do `var` i ponownie uruchom zapytanie. Należy pamiętać, że w wewnętrzny `foreach` pętli, Zmienna iteracji nadal jest wpisana jako `Student`, a zapytanie działa tak jak wcześniej. Zmiana `s` zmiennej iteracji w celu `var` i ponownie uruchom zapytanie. Zobaczysz, że uzyskać te same wyniki.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Aby uzyskać więcej informacji na temat [var](../../../../csharp/language-reference/keywords/var.md), zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Aby uporządkować grupy według kluczy wartości  
  
1. Po uruchomieniu poprzednie zapytanie, można zauważyć, że grupy nie są w kolejności alfabetycznej. Aby zmienić to ustawienie, należy podać `orderby` klauzula po `group` klauzuli. Do użycia, ale `orderby` klauzuli, musisz najpierw identyfikator, który służy jako punkt odniesienia do grup utworzonych przez `group` klauzuli. Podaj identyfikator przy użyciu `into` — słowo kluczowe w następujący sposób:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Po uruchomieniu tego zapytania, widoczne będą grupy teraz są sortowane w kolejności alfabetycznej.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Aby wprowadzić identyfikator przy użyciu let  
  
1. Możesz użyć `let` — słowo kluczowe, aby wprowadzić identyfikator dla dowolnego wyniku wyrażenia w wyrażeniu zapytania. Ten identyfikator może być udogodnienie, jak w poniższym przykładzie, lub można go zwiększyć wydajność dzięki przechowywaniu wyniki wyrażenia, tak aby nie ma zostać obliczona wiele razy.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Aby uzyskać więcej informacji, zobacz [let, klauzula](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Aby użyć metody składni w wyrażeniu zapytania  
  
1. Zgodnie z opisem w [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), niektórych operacji zapytań może być wyrażone tylko przy użyciu składni metody. Poniższy kod oblicza łączny wynik dla każdego `Student` w sekwencji źródłowej, a następnie wywołania `Average()` metody wyników tej kwerendy, aby obliczyć średnią ocenę klasy.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Aby przekształcić lub zaprojektować w klauzuli wyboru  
  
1. Jest bardzo często zapytanie w celu utworzenia sekwencji, w której elementy różnią się od elementów w sekwencji źródłowej. Usuń komentarz z poprzedniej kwerendy i wykonywanie pętlę metodyki lub zastąp go następującym kodem. Należy pamiętać, że zapytanie zwraca sekwencję ciągów (nie `Students`), a ten fakt znajduje odzwierciedlenie w `foreach` pętli.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Kodu we wcześniejszej części tego przewodnika wskazane, to około 334 wynik klasy średniej. Aby utworzyć sekwencję `Students` których łączny wynik jest większa niż średnia klasy wraz z ich `Student ID`, można użyć typu anonimowego w `select` instrukcji:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Następne kroki  
 Po przejściu na podstawowych aspektów pracy z zapytaniami w języku C#, jesteś gotowy do odczytu, dokumentację i przykłady dla określonego typu dostawcy LINQ, który Cię interesuje:  
  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
