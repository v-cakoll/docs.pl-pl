---
title: "Pisanie zapytań w języku Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: "70"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e78d93895a86ad9b2456e5ac7c05db83ebf0379d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Wskazówki: Pisanie zapytań w Visual Basic
W tym przewodniku przedstawiono sposób użycia funkcje języka Visual Basic można zapisać [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia zapytań. Instruktaż pokazuje, jak tworzyć zapytania na liście obiektów dla użytkowników domowych, jak uruchamiać zapytania i sposobu ich modyfikacji. Zapytania zastosować kilka funkcji w tym inicjatory obiektów, wnioskowanie o typie lokalnym i typy anonimowe.  
  
 Po ukończeniu tego przewodnika, wszystko będzie gotowe do przeniesienia przykłady i dokumentację dla konkretnych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w dostawcy. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]obejmują dostawców [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Tworzenie projektu  
  
#### <a name="to-create-a-console-application-project"></a>Aby utworzyć projekt aplikacji konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W **zainstalowane szablony** kliknij **Visual Basic**.  
  
4.  Na liście typów projektów kliknij **aplikacji konsoli**. W **nazwa** , wpisz nazwę projektu, a następnie kliknij przycisk **OK**.  
  
     Projekt jest tworzony. Domyślnie zawiera odwołania do System.Core.dll. Ponadto **importowane przestrzenie nazw** listy na [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) obejmuje <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.  
  
5.  Na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), upewnij się, że **Option infer** ustawiono **na**.  
  
## <a name="add-an-in-memory-data-source"></a>Dodaj źródło danych w pamięci  
 Źródło danych dla zapytania w tym przewodniku przedstawiono listę `Student` obiektów. Każdy `Student` obiekt zawiera imię, nazwisko roku klasy i academic rangę w treści studenta.  
  
#### <a name="to-add-the-data-source"></a>Aby dodać źródło danych  
  
-   Zdefiniuj `Student` klasy, a następnie utwórz listę wystąpień klasy.  
  
    > [!IMPORTANT]
    >  Kod należy zdefiniować `Student` klasy i tworzenia listy używane w tym przewodnikiem przykłady znajduje się w [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Możesz skopiować go stamtąd i wklej go do projektu. Nowy kod zastępuje kod, który pojawił się podczas tworzenia projektu.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów  
  
-   Postępuj zgodnie ze wzorcem w `getStudents` metodę, aby dodać inne wystąpienie `Student` klasy do listy. Dodawanie student przedstawiono inicjatory obiektów. Aby uzyskać więcej informacji, zobacz [inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Utwórz kwerendę  
 Po wykonaniu zapytania dodane w tej sekcji tworzy listę studentów, w której academic pozycję umieszczane w pierwszych dziesięciu. Ponieważ zapytanie wybiera pełną `Student` obiekt jest zawsze typu wyniku kwerendy `IEnumerable(Of Student)`. Jednak typu zapytania zwykle nie określono definicji zapytania. Zamiast tego kompilator używa wnioskowanie o typie lokalnym można określić typu. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Zmienna zakresu kwerendy, `currentStudent`, służy jako punkt odniesienia do każdego `Student` wystąpienia w źródle, `students`, zapewniając dostęp do właściwości każdego obiektu w `students`.  
  
#### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie  
  
1.  Znajdź w miejscu `Main` metody projektu, który jest oznaczony w następujący sposób:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Skopiuj poniższy kod i wklej go w.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Wskaźnik myszy nad `studentQuery` w kodzie, aby sprawdzić, czy jest przypisany przez kompilator typu `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Uruchom zapytanie  
 Zmienna `studentQuery` zawiera definicję zapytania nie wyniki działania zapytania. Typowy mechanizm uruchomienia zapytania jest `For Each` pętli. Każdy element zwrócony sekwencji jest dostępny za pośrednictwem zmiennej iteracji pętli. Aby uzyskać więcej informacji na temat wykonywania zapytania, zobacz [Your pierwszego zapytania LINQ zapisu](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Aby uruchomić zapytanie  
  
1.  Dodaj następujące `For Each` pętli poniżej zapytanie w projekcie.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  Wskaźnik myszy nad zmienna sterująca pętli for `studentRecord` aby zobaczyć jego typu danych. Typ `studentRecord` jest wywnioskowany jako `Student`, ponieważ `studentQuery` zwraca kolekcję `Student` wystąpień.  
  
3.  Tworzenie i uruchamianie aplikacji, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
## <a name="modify-the-query"></a>Zmodyfikuj zapytanie  
 Jest bardziej czytelne wyniki zapytania, jeśli znajdują się w określonej kolejności. Można sortować sekwencja zwróconych na podstawie wszystkie dostępne pola.  
  
#### <a name="to-order-the-results"></a>Aby uporządkować wyniki  
  
1.  Dodaj następujące `Order By` klauzuli między `Where` instrukcji i `Select` instrukcji kwerendy. `Order By` Klauzuli będzie kolejność wyników alfabetycznie z zakresu od A do Z, zgodnie z ostatnią nazwy użytkowników.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Aby uporządkować według nazwisko, a następnie imię, należy dodać do zapytania oba pola:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Można również określić `Descending` zamówienia Z A.  
  
3.  Tworzenie i uruchamianie aplikacji, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
#### <a name="to-introduce-a-local-identifier"></a>Aby wprowadzić identyfikator lokalny  
  
1.  Dodaj kod w tej sekcji wprowadzenie identyfikatora lokalnego w wyrażeniu zapytania. Lokalny identyfikator będą przechowywane pośrednich wyników. W poniższym przykładzie `name` jest identyfikator, który przechowuje łączenia student imienia i nazwiska. Lokalny identyfikator może służyć do zapewnienia wygody, lub go poprawić wydajność dzięki przechowywaniu wyniki wyrażenie, które w przeciwnym razie oblicza wiele razy.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Tworzenie i uruchamianie aplikacji, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Aby zaprojektować jedno pole w klauzuli Wybierz  
  
1.  Dodaj zapytanie i `For Each` pętli z tej sekcji, aby utworzyć kwerendę, która tworzy sekwencję, której elementy różnią się od elementów w źródle. W poniższym przykładzie źródła jest kolekcją `Student` obiektów, ale tylko jeden element członkowski każdy obiekt jest zwracany: imię studentów, których nazwisko jest Kowalski. Ponieważ `currentStudent.First` jest typu string, typ danych sekwencji zwróconej przez `studentQuery3` jest `IEnumerable(Of String)`, sekwencję ciągów. Tak samo jak wcześniej przykładach, typ przypisania danych `studentQuery3` pozostało dla kompilatora określić za pomocą wnioskowanie o typie lokalnym.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Wskaźnik myszy nad `studentQuery3` w kodzie, aby sprawdzić, czy jest przypisany typ `IEnumerable(Of String)`.  
  
3.  Tworzenie i uruchamianie aplikacji, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Aby utworzyć typ anonimowy w klauzuli Wybierz  
  
1.  Należy dodać kodu w tej sekcji, aby wyświetlić typy anonimowe jak są używane w zapytaniach. Można ich używać w zapytaniach należy zwrócić kilka pól ze źródła danych, a nie rejestruje pełnej (`currentStudent` rekordów w poprzednich przykładach) lub pojedynczego pola (`First` w poprzedniej sekcji). Zamiast definiować nowego typu o nazwie, który zawiera pola, które mają zostać uwzględnione w wynikach, możesz określić pola w `Select` klauzul i kompilator tworzy typu anonimowego z tych pól, jako jego właściwości. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Poniższy przykład tworzy zapytanie zwraca nazwę i rangę seniors której academic pozycję to od 1 do 10, w kolejności academic. W tym przykładzie typ `studentQuery4` należy go wywnioskować, ponieważ `Select` klauzula Zwraca wystąpienie klasy typu anonimowego, a typ anonimowy nie ma używać nazwy.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Tworzenie i uruchamianie aplikacji, naciskając klawisze CTRL + F5. Należy pamiętać, wyniki w oknie konsoli.  
  
## <a name="additional-examples"></a>Dodatkowe przykłady  
 Teraz, gdy zrozumieniu podstaw poniżej przedstawiono listę dodatkowe przykłady ilustrujący elastyczność i możliwości [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Każdy przykład jest poprzedzony krótki opis jego działania. Wskaźnik myszy nad zmiennej wynik zapytania dla każdego zapytania zobaczyć wnioskowany typ. Użyj `For Each` pętli w celu uzyskania wyników.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Dodatkowe informacje  
 Po zapoznaniu się z podstawowymi koncepcjami dotyczącymi programu Praca z zapytaniami, można przystąpić do odczytu dokumentacja i przykłady dla określonego typu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy, który chcesz:  
  
 [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)
