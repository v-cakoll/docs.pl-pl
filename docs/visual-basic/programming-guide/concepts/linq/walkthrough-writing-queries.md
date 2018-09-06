---
title: Pisanie zapytań w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 2f641d04b53d2e80985defcd6bd9a4882004fd97
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868014"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Wskazówki: Pisanie zapytań w Visual Basic
W tym instruktażu pokazano, jak funkcje języka Visual Basic można użyć do zapisywania [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażeniach zapytań. Przewodnik pokazuje, jak tworzyć zapytania na liście obiektów dla uczniów, jak uruchamiać zapytania i sposobu ich modyfikacji. Kilka funkcji, w tym inicjatorów obiektów, wnioskowanie o typie lokalnym i typy anonimowe dołączyć do nich zapytania.  
  
 Po ukończeniu tego przewodnika, wszystko będzie gotowe przejść do przykłady i dokumentację, aby uzyskać konkretne [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy Cię interesuje. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy obejmują [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Tworzenie projektu  
  
#### <a name="to-create-a-console-application-project"></a>Aby utworzyć projekt aplikacji konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W **zainstalowane szablony** kliknij **języka Visual Basic**.  
  
4.  Na liście typów projektów, kliknij **aplikację Konsolową**. W **nazwa** wpisz nazwę dla projektu, a następnie kliknij przycisk **OK**.  
  
     Projekt jest tworzony. Domyślnie zawiera odwołania do System.Core.dll. Ponadto **zaimportowane przestrzenie nazw** listy na [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) obejmuje <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.  
  
5.  Na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), upewnij się, że **Option infer** ustawiono **na**.  
  
## <a name="add-an-in-memory-data-source"></a>Dodaj źródło danych w pamięci  
 Źródło danych dla zapytania w tym przewodniku znajduje się lista `Student` obiektów. Każdy `Student` obiekt zawiera imię, nazwisko, rok klasy i rangi akademickich w treści dla uczniów.  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
-   Zdefiniuj `Student` klasy i tworzenie listy wystąpień klasy.  
  
    > [!IMPORTANT]
    >  Kod niezbędnej do zdefiniowania `Student` klasy i tworzenie listy używane w instruktażu przykłady znajduje się w [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Można skopiować go w tym miejscu i wklej go do projektu. Nowy kod zastępuje kodu, które wystąpiły podczas tworzenia projektu.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów  
  
-   Postępuj zgodnie ze wzorcem w `getStudents` metodę, aby dodać inne wystąpienie `Student` klasy do listy. Dodawanie student zostaną wprowadzone do inicjatorów obiektów. Aby uzyskać więcej informacji, zobacz [inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Utwórz kwerendę  
 Po wykonaniu zapytania dodane w tej sekcji tworzy listę uczniów, w której akademickich pozycję umieszcza je w dziesięciu najlepszych. Ponieważ zapytanie wybiera pełne `Student` obiekt typu wyniku zapytania za każdym razem jest `IEnumerable(Of Student)`. Jednak zapytania zwykle nie określono typu w definicji zapytania. Zamiast tego kompilator używa wnioskowanie o typie lokalnym można ustalić typu. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Zmienna zakresu zapytania, `currentStudent`, służy jako punkt odniesienia do każdego `Student` wystąpienia w źródle, `students`, zapewniając dostęp do właściwości każdego obiektu w `students`.  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
1.  Znajdź miejsce w `Main` metoda projektu, który jest oznaczony w następujący sposób:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Skopiuj poniższy kod, a następnie wklej je.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Zatrzymaj wskaźnik myszy nad `studentQuery` w kodzie, aby sprawdzić, czy jest przypisany przez kompilator typu `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Uruchom zapytanie  
 Zmienna `studentQuery` zawiera definicję kwerendy nie wynikami przeprowadzonej kwerendy. Typowe mechanizm do uruchamiania kwerendy jest `For Each` pętli. Każdy element w zwracanej sekwencji jest dostępny za pośrednictwem zmiennej iteracji pętli. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [Your pierwszego zapytania LINQ pisania](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Aby uruchomić zapytanie  
  
1.  Dodaj następujący kod `For Each` pętli poniżej zapytania w projekcie.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  Zatrzymaj wskaźnik myszy nad zmienna sterująca pętli `studentRecord` aby zobaczyć jego typu danych. Typ `studentRecord` jest `Student`, ponieważ `studentQuery` zwraca kolekcję `Student` wystąpień.  
  
3.  Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
## <a name="modify-the-query"></a>Zmodyfikuj zapytanie  
 Jest bardziej czytelne wyniki zapytania, jeśli znajdują się w określonej kolejności. Można sortować zwracana sekwencja, w oparciu o wszystkie dostępne pola.  
  
#### <a name="to-order-the-results"></a>Aby uporządkować wyniki  
  
1.  Dodaj następujący kod `Order By` klauzuli między `Where` instrukcji i `Select` instrukcja kwerendy. `Order By` Klauzuli będzie kolejność wyników alfabetycznie od A do Z, zgodnie z ostatnią nazwę każdego ucznia.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Aby zamówić nazwisko i imię, należy dodać do zapytania obu pól:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Można również określić `Descending` kolejności od Z do A.  
  
3.  Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
#### <a name="to-introduce-a-local-identifier"></a>Aby wprowadzić identyfikator lokalny  
  
1.  Dodaj kod, w tej sekcji, aby wprowadzić identyfikator lokalny w wyrażeniu zapytania. Identyfikator lokalny będzie przechowywać wyniki pośrednie. W poniższym przykładzie `name` jest identyfikator, który przechowuje łączenia student imienia i nazwiska. Identyfikator lokalny może służyć do zapewnienia wygody, lub go może poprawić wydajność dzięki przechowywaniu wyniki wyrażenie, które w przeciwnym razie nalicza się wiele razy.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Aby zaprojektować jedno pole w klauzuli Wybierz  
  
1.  Dodaj zapytanie i `For Each` pętli w tej sekcji, aby utworzyć zapytanie, który wytwarza sekwencję, w której elementy różnią się od elementów w źródle. W poniższym przykładzie źródło to zbiór `Student` obiektów, ale tylko jeden element członkowski każdy obiekt jest zwracany: imię studentów, których nazwisko jest Garcia. Ponieważ `currentStudent.First` jest ciągiem, typ danych sekwencji zwróconej przez `studentQuery3` jest `IEnumerable(Of String)`, sekwencją ciągów. Tak samo jak wcześniejszych przykładach przydział danych w polu `studentQuery3` pozostanie do kompilatora, aby określić za pomocą wnioskowanie o typie lokalnym.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Zatrzymaj wskaźnik myszy nad `studentQuery3` w kodzie, aby sprawdzić, czy jest przypisany typ `IEnumerable(Of String)`.  
  
3.  Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Aby utworzyć typ anonimowy w klauzuli Wybierz  
  
1.  Dodaj kod z tej sekcji, aby zobaczyć, jak anonimowych typów są używane w kwerendach. Można ich używać w zapytaniach zwrócić wiele pól ze źródła danych, a nie pełne rekordy (`currentStudent` rekordów w poprzednich przykładach) lub pojedynczego pola (`First` w poprzedniej sekcji). Zamiast Definiowanie nowego typu nazwanego, który zawiera pola, które chcesz uwzględnić w wyniku, możesz określić pola w `Select` klauzuli i kompilator tworzy typ anonimowy z tych pól jako jego właściwości. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Poniższy przykład tworzy zapytanie zwracające nazwą i ranga seniors, w której akademickich pozycję to od 1 do 10, w kolejności akademickich. W tym przykładzie typ `studentQuery4` musi wywnioskować, ponieważ `Select` klauzula Zwraca wystąpienie typu anonimowego, a typ anonimowy nie ma użytecznych nazw.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
## <a name="additional-examples"></a>Dodatkowe przykłady  
 Teraz, gdy już rozumiesz podstawy, Oto lista dodatkowe przykłady ilustrują elastyczność i możliwości [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Każdy przykład jest poprzedzony przez krótki opis jego działania. Zatrzymaj wskaźnik myszy nad zmienną wyników kwerendy dla każdego zapytania zobaczyć wnioskowany typ. Użyj `For Each` pętli do wygenerowania wyników.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Dodatkowe informacje  
 Po przejściu na podstawowych pojęciach dotyczących pracy z zapytaniami, jesteś gotowy do odczytu dokumentację i przykłady dla określonego typu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy, który Cię interesuje:  
  
 [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
