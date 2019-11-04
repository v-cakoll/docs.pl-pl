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
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418054"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Wskazówki: pisanie zapytań w C# (LINQ)
W C# tym instruktażu przedstawiono funkcje języka, które są używane do pisania wyrażeń zapytań LINQ.  
  
## <a name="create-a-c-project"></a>Utwórz projekt C#  
  
> [!NOTE]
> Poniższe instrukcje dotyczą programu Visual Studio. Jeśli używasz innego środowiska programistycznego, Utwórz projekt konsoli z odwołaniem do elementu System. Core. dll i `using` dyrektywie dla przestrzeni nazw <xref:System.Linq?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Aby utworzyć projekt w programie Visual Studio  
  
1. Uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.  
  
     Zostanie otwarte okno dialogowe **Nowy projekt** .  
  
3. Rozwiń węzeł **zainstalowane**, rozwiń węzeł **Szablony**, rozwiń węzeł **wizualizacji C#** , a następnie wybierz pozycję **Aplikacja konsolowa**.  
  
4. W polu tekstowym **Nazwa** wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz przycisk **OK** .  
  
     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.  
  
5. Zwróć uwagę, że projekt zawiera odwołanie do elementu System. Core. dll i dyrektywy `using` dla przestrzeni nazw <xref:System.Linq?displayProperty=nameWithType>.  
  
## <a name="create-an-in-memory-data-source"></a>Utwórz źródło danych w pamięci  
 Źródło danych dla zapytań jest prostą listą obiektów `Student`. Każdy rekord `Student` ma imię, nazwisko i tablicę liczb całkowitych, która reprezentuje wyniki testu w klasie. Skopiuj ten kod do projektu. Należy pamiętać o następujących cechach:  
  
- Klasa `Student` składa się z właściwości, które są implementowane.  
  
- Każdy student na liście jest inicjowany przy użyciu inicjatora obiektów.  
  
- Sama lista została zainicjowana przy użyciu inicjatora kolekcji.  
  
 Ta cała struktura danych zostanie zainicjowana i utworzona bez jawnych wywołań do jakiegokolwiek konstruktora lub jawnego dostępu do elementu członkowskiego. Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz [Autozaimplementowane właściwości](../../classes-and-structs/auto-implemented-properties.md) i [obiekty i Inicjatory kolekcji](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
- Dodaj klasę `Student` i zainicjowaną listę uczniów do klasy `Program` w projekcie.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów  
  
1. Dodaj nowe `Student` do listy `Students` i użyj wybranych ocen. Spróbuj wpisać wszystkie nowe informacje ucznia, aby lepiej poznać składnię inicjatora obiektów.  
  
## <a name="create-the-query"></a>Utwórz zapytanie  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
- W metodzie `Main` aplikacji Utwórz proste zapytanie, które po jego wykonaniu spowoduje utworzenie listy wszystkich uczniów, których wynikiem pierwszego testu była większa niż 90. Należy zauważyć, że ponieważ zaznaczony jest cały `Student` obiekt, typ zapytania jest `IEnumerable<Student>`. Chociaż kod może również używać niejawnego wpisywania przy użyciu słowa kluczowego [var](../../../language-reference/keywords/var.md) , jawne wpisywanie jest używane do jasnego ilustrowania wyników. (Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md)).  
  
     Należy zauważyć, że zmienna zakresu zapytania, `student`, służy jako odwołanie do poszczególnych `Student` w źródle, zapewniając dostęp do elementów członkowskich dla każdego obiektu.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Wykonanie zapytania  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1. Teraz napisz pętlę `foreach`, która spowoduje wykonanie zapytania. Zwróć uwagę na następujące informacje dotyczące kodu:  
  
    - Każdy element w zwróconej sekwencji jest dostępny za pomocą zmiennej iteracji w pętli `foreach`.  
  
    - Typ tej zmiennej jest `Student`, a typ zmiennej zapytania jest zgodny, `IEnumerable<Student>`.  
  
2. Po dodaniu tego kodu, skompiluj i uruchom aplikację, aby wyświetlić wyniki w oknie **konsoli** .  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Aby dodać inny warunek filtru  
  
1. Można połączyć wiele warunków logicznych w klauzuli `where`, aby dodatkowo uściślić zapytanie. Poniższy kod dodaje warunek, aby zapytanie zwracało uczniów, których pierwszy wynik był ponad 90 i którego ostatni wynik był mniejszy niż 80. Klauzula `where` powinna wyglądać podobnie do poniższego kodu.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Zmodyfikuj zapytanie  
  
#### <a name="to-order-the-results"></a>Aby uporządkować wyniki  
  
1. Wyszukiwanie wyników będzie łatwiejsze, jeśli są one w pewnym rodzaju kolejności. Zwracaną sekwencję można zamówić według dowolnego dostępnego pola w elementach źródłowych. Na przykład następująca `orderby` klauzula porządkuje wyniki w kolejności alfabetycznej od A do Z w zależności od nazwiska każdego ucznia. Dodaj następującą klauzulę `orderby` do zapytania, bezpośrednio po instrukcji `where` i przed instrukcją `select`:  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Teraz zmień klauzulę `orderby` tak, aby była uporządkowana w kolejności odwrotnej zgodnie z wynikami pierwszego testu, od najwyższego do najniższego wyniku.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Zmień ciąg formatu `WriteLine` tak, aby można było zobaczyć wyniki:  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Aby pogrupować wyniki  
  
1. Grupowanie jest zaawansowaną możliwością w wyrażeniach zapytań. Zapytanie z klauzulą grupy tworzy sekwencję grup, a każda sama grupa zawiera `Key` i sekwencję, która składa się ze wszystkich członków tej grupy. Poniższe nowe zapytanie grupuje uczniów przy użyciu pierwszej litery nazwiska jako klucza.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Należy zauważyć, że typ zapytania został zmieniony. Teraz tworzy sekwencję grup, które mają typ `char` jako klucz i sekwencję obiektów `Student`. Ponieważ typ zapytania został zmieniony, poniższy kod zmienia również pętlę wykonywania `foreach`:  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Uruchom aplikację i Wyświetl wyniki w oknie **konsoli** .  
  
     Aby uzyskać więcej informacji, zobacz [klauzula](../../../language-reference/keywords/group-clause.md)Group.  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Aby jawnie wpisać zmienną lokalną  
  
1. Jawne kodowanie `IEnumerables` `IGroupings` może szybko stać się żmudnym. Można napisać to samo zapytanie i `foreach` pętlę znacznie bardziej wygodnie przy użyciu `var`. Słowo kluczowe `var` nie zmienia typów obiektów; po prostu nakazuje kompilatorowi wywnioskowanie typów. Zmień typ `studentQuery` i zmiennej iteracji `group` do `var` i ponownie uruchom zapytanie. Należy zauważyć, że w wewnętrznej pętli `foreach` Zmienna iteracji jest nadal wpisana jako `Student`, a zapytanie działa tak jak wcześniej. Zmień `s` zmienną iteracji na `var` i ponownie uruchom zapytanie. Zobaczysz, że uzyskujesz dokładnie te same wyniki.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Aby uzyskać więcej informacji na temat funkcji [var](../../../language-reference/keywords/var.md), zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Aby uporządkować grupy według kluczy wartości  
  
1. Po uruchomieniu poprzedniej kwerendy należy zauważyć, że grupy nie są w kolejności alfabetycznej. Aby to zmienić, należy podać klauzulę `orderby` po klauzuli `group`. Ale aby użyć klauzuli `orderby`, najpierw potrzebny jest identyfikator, który służy jako odwołanie do grup utworzonych przez klauzulę `group`. Identyfikator można podać za pomocą słowa kluczowego `into` w następujący sposób:  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Po uruchomieniu tego zapytania zobaczysz, że grupy są teraz sortowane w kolejności alfabetycznej.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Aby wprowadzić identyfikator przy użyciu let  
  
1. Możesz użyć słowa kluczowego `let`, aby wprowadzić identyfikator dowolnego wyniku wyrażenia w wyrażeniu zapytania. Ten identyfikator może być wygodą, tak jak w poniższym przykładzie, lub może zwiększyć wydajność, przechowując wyniki wyrażenia, aby nie trzeba było obliczyć ich wiele razy.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Aby uzyskać więcej informacji, zobacz [klauzula Let](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Aby użyć metody składni w wyrażeniu zapytania  
  
1. Zgodnie z opisem w składni [zapytania i składni metody w LINQ](./query-syntax-and-method-syntax-in-linq.md), niektóre operacje zapytań można wyrazić tylko przy użyciu składni metody. Poniższy kod oblicza łączny wynik dla każdego `Student` w sekwencji źródłowej, a następnie wywołuje metodę `Average()` dla wyników tego zapytania, aby obliczyć średnią ocenę klasy.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Aby przekształcić lub zaprojektować w klauzuli wyboru  
  
1. Jest bardzo często źródłem zapytania, aby utworzyć sekwencję, której elementy różnią się od elementów w sekwencjach źródłowych. Usuń lub Skomentuj poprzednią pętlę zapytania i wykonywania, a następnie zastąp ją poniższym kodem. Należy zauważyć, że zapytanie zwraca sekwencję ciągów (nie `Students`), a ten fakt jest odzwierciedlony w pętli `foreach`.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Kod we wcześniejszej części tego instruktażu wskazywał, że średni wynik klasy wynosi około 334. Aby utworzyć sekwencję `Students`, której łączny wynik jest większy niż średnia klasy, wraz z ich `Student ID`, można użyć typu anonimowego w instrukcji `select`:  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Następne kroki  
 Po zapoznaniu się z podstawowymi aspektami pracy z zapytaniami w programie C#możesz zapoznać się z dokumentacją i przykładami dotyczącymi określonego typu dostawcy LINQ:  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ to Objects (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie zintegrowane z językiem (LINQ)C#()](./index.md)
- [Wyrażenia zapytania LINQ](../../../linq/index.md)
