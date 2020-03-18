---
title: 'Wskazówki: pisanie zapytań w C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73418054"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Wskazówki: pisanie zapytań w C# (LINQ)
W tym instruktażeniu przedstawiono funkcje języka Języka C#, które są używane do pisania wyrażeń zapytań LINQ.  
  
## <a name="create-a-c-project"></a>Utwórz projekt C#  
  
> [!NOTE]
> Poniższe instrukcje są dla programu Visual Studio. Jeśli używasz innego środowiska programistycznego, utwórz projekt konsoli z odwołaniem `using` do pliku <xref:System.Linq?displayProperty=nameWithType> System.Core.dll i dyrektywy dla obszaru nazw.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Aby utworzyć projekt w programie Visual Studio  
  
1. Uruchom program Visual Studio.  
  
2. Na pasku menu wybierz pozycję **Plik**, **Nowy**, **Projekt**.  
  
     Zostanie otwarte okno dialogowe **Nowy projekt.**  
  
3. Rozwiń **pozycję Zainstalowane**, rozwiń **rozwiń pozycję Szablony**, rozwiń węzeł **Visual C#,** a następnie wybierz pozycję **Aplikacja konsoli**.  
  
4. W polu tekstowym **Nazwa** wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz przycisk **OK.**  
  
     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.  
  
5. Należy zauważyć, że projekt ma odwołanie do System.Core.dll i dyrektywy `using` dla obszaru <xref:System.Linq?displayProperty=nameWithType> nazw.  
  
## <a name="create-an-in-memory-data-source"></a>Utwórz źródło danych w pamięci  
 Źródłem danych dla zapytań jest `Student` prosta lista obiektów. Każdy `Student` rekord ma imię, nazwisko i tablicę liczb całkowitych, która reprezentuje ich wyniki testów w klasie. Skopiuj ten kod do projektu. Należy zwrócić uwagę na następujące cechy:  
  
- Klasa `Student` składa się z właściwości implementowanych automatycznie.  
  
- Każdy uczeń na liście jest inicjowany za pomocą inicjatora obiektów.  
  
- Sama lista jest inicjowana za pomocą inicjatora kolekcji.  
  
 Ta cała struktura danych zostanie zainicjowana i uprzedzona bez jawnych wywołań do dowolnego konstruktora lub jawnego dostępu do elementów członkowskich. Aby uzyskać więcej informacji na temat tych nowych funkcji, zobacz [Właściwości autoimplementowane](../../classes-and-structs/auto-implemented-properties.md) oraz [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
- Dodaj `Student` klasę i iizapoczątkowaną `Program` listę uczniów do klasy w projekcie.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów  
  
1. Dodaj nowy `Student` do `Students` listy i użyj nazwy i wyników testów do wyboru. Spróbuj wpisać wszystkie nowe informacje o uczniach, aby lepiej nauczyć się składni inicjatora obiektu.  
  
## <a name="create-the-query"></a>Utwórz zapytanie  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
- W `Main` metodzie aplikacji utwórz prostą kwerendę, która po wykonaniu stworzy listę wszystkich uczniów, których wynik w pierwszym teście był większy niż 90. Należy zauważyć, `Student` że ponieważ cały obiekt jest zaznaczony, typem kwerendy jest `IEnumerable<Student>`. Chociaż kod może również używać niejawnego pisania przy użyciu [var](../../../language-reference/keywords/var.md) słowa kluczowego, jawne wpisywanie jest używany do wyraźnego zilustrowania wyników. (Aby uzyskać `var`więcej informacji na temat , zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Należy również zauważyć, że zmienna zakresu `student`kwerendy, `Student` służy jako odwołanie do każdego w źródle, zapewniając dostęp do elementów członkowskich dla każdego obiektu.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Wykonanie zapytania  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1. Teraz napisz `foreach` pętlę, która spowoduje wykonanie kwerendy. Należy zwrócić uwagę na następujące informacje dotyczące kodu:  
  
    - Każdy element w zwróconej sekwencji jest dostępny za `foreach` pośrednictwem zmiennej iteracji w pętli.  
  
    - Typ tej zmiennej `Student`jest , a typ zmiennej `IEnumerable<Student>`kwerendy jest zgodny.  
  
2. Po dodaniu tego kodu skompiluj i uruchom aplikację, aby wyświetlić wyniki w oknie **Konsoli.**  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Aby dodać inny warunek filtru  
  
1. Można połączyć wiele warunków logicznych w klauzuli `where` w celu dalszego uściślania kwerendy. Poniższy kod dodaje warunek, tak aby kwerenda zwraca tych uczniów, których pierwszy wynik był ponad 90 i których ostatni wynik był mniejszy niż 80. Klauzula `where` powinna przypominać następujący kod.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Zmodyfikuj zapytanie  
  
#### <a name="to-order-the-results"></a>Aby uporządkować wyniki  
  
1. Łatwiej będzie skanować wyniki, jeśli są one w jakiejś kolejności. Zwracaną sekwencję można zamówić za pomocą dowolnego dostępnego pola w elementach źródłowych. Na przykład następująca `orderby` klauzula porządkuje wyniki w kolejności alfabetycznej od A do Z zgodnie z nazwiskiem każdego ucznia. Dodaj następującą `orderby` klauzulę do `where` zapytania, zaraz `select` po instrukcji i przed instrukcją:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Teraz zmień `orderby` klauzulę tak, aby uporządkowała wyniki w odwrotnej kolejności zgodnie z wynikiem w pierwszym teście, od najwyższego wyniku do najniższego wyniku.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Zmień `WriteLine` ciąg formatu, aby zobaczyć wyniki:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Aby pogrupować wyniki  
  
1. Grupowanie jest zaawansowaną możliwością w wyrażeniach kwerend. Kwerenda z klauzulą grupy tworzy sekwencję grup, a `Key` każda grupa sama zawiera sekwencję i sekwencję składającą się ze wszystkich członków tej grupy. Następujące nowe zapytania grupują uczniów przy użyciu pierwszej litery ich nazwiska jako klucza.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Należy zauważyć, że typ kwerendy został zmieniony. Teraz tworzy sekwencję grup, które `char` mają typ jako klucz `Student` i sekwencję obiektów. Ponieważ typ kwerendy uległ zmianie, następujący `foreach` kod zmienia również pętlę wykonywania:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uruchom aplikację i wyświetl wyniki w oknie **Konsoli.**  
  
     Aby uzyskać więcej informacji, zobacz [klauzulę group](../../../language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Aby jawnie wpisać zmienną lokalną  
  
1. Jawne `IEnumerables` kodowanie `IGroupings` może szybko stać się nużące. Możesz napisać to samo `foreach` zapytanie i pętli `var`znacznie wygodniej za pomocą . Słowo `var` kluczowe nie zmienia typów obiektów; po prostu instruuje kompilator, aby wywnioskować typy. Zmień typ `studentQuery` i zmienną `group` iteracji i `var` ponownie uruchom kwerendę. Należy zauważyć, `foreach` że w pętli wewnętrznej zmienna iteracji jest nadal wpisywana jako `Student`, a kwerenda działa tak jak poprzednio. Zmień `s` zmienną iteracji i `var` uruchom kwerendę ponownie. Widzisz, że masz dokładnie takie same wyniki.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Aby uzyskać więcej informacji na temat [var](../../../language-reference/keywords/var.md), zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Aby uporządkować grupy według kluczy wartości  
  
1. Po uruchomieniu poprzedniej kwerendy można zauważyć, że grupy nie są w kolejności alfabetycznej. Aby to zmienić, należy `orderby` podać `group` klauzulę po klauzuli. Ale aby `orderby` użyć klauzuli, najpierw potrzebujesz identyfikatora, który służy jako `group` odwołanie do grup utworzonych przez klauzulę. Identyfikator należy podać przy `into` użyciu słowa kluczowego w następujący sposób:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Po uruchomieniu tej kwerendy zobaczysz, że grupy są teraz sortowane w kolejności alfabetycznej.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Aby wprowadzić identyfikator przy użyciu let  
  
1. Za pomocą `let` słowa kluczowego można wprowadzić identyfikator dla dowolnego wyniku wyrażenia w wyrażeniu zapytania. Ten identyfikator może być wygodą, jak w poniższym przykładzie lub może zwiększyć wydajność, przechowując wyniki wyrażenia, dzięki czemu nie muszą być obliczane wiele razy.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Aby uzyskać więcej informacji, zobacz [klauzulę let](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Aby użyć metody składni w wyrażeniu zapytania  
  
1. Zgodnie z opisem w [składni kwerendy i składni metody w LINQ,](./query-syntax-and-method-syntax-in-linq.md)niektóre operacje kwerendy mogą być wyrażone tylko przy użyciu składni metody. Poniższy kod oblicza całkowity wynik `Student` dla każdego w sekwencji `Average()` źródłowej, a następnie wywołuje metodę na wyniki tej kwerendy, aby obliczyć średni wynik klasy.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Aby przekształcić lub zaprojektować w klauzuli wyboru  
  
1. Jest bardzo często dla kwerendy do tworzenia sekwencji, których elementy różnią się od elementów w sekwencji źródłowych. Usuń lub skomentuj poprzednią pętlę zapytania i wykonywania i zastąp ją następującym kodem. Należy zauważyć, że kwerenda zwraca `Students`sekwencję ciągów (nie `foreach` ), a ten fakt jest odzwierciedlony w pętli.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Kod wcześniej w tym instruktażu wskazał, że średni wynik klasy wynosi około 334. Aby utworzyć `Students` sekwencję, której całkowity wynik jest większy `Student ID`niż średnia klasa, wraz `select` z ich , można użyć typu anonimowego w instrukcji:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Następne kroki  
 Po zapoznaniu się z podstawowymi aspektami pracy z zapytaniami w języku C#, można przystąpić do zapoznania się z dokumentacją i przykładami dla określonego typu dostawcy LINQ, który Cię interesuje:  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ do DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ do XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ do obiektów (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Zobacz też

- [Zapytanie zintegrowane z językiem (LINQ) (C#)](./index.md)
- [Wyrażenia zapytań LINQ](../../../linq/index.md)
