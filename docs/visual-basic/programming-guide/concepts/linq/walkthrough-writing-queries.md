---
title: pisanie zapytań
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 25905d7ac3ca4bb66a22ad1df421b400eaa6b08f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413274"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Wskazówki: Pisanie zapytań w Visual Basic

W tym instruktażu pokazano, w jaki sposób można użyć funkcji języka Visual Basic, aby napisać wyrażenia zapytania dotyczące języka LINQ. W tym przewodniku pokazano, jak tworzyć zapytania na liście obiektów uczniów, jak uruchamiać zapytania i jak je modyfikować. Zapytania obejmują kilka funkcji, w tym Inicjatory obiektów, wnioskowanie typu lokalnego i typy anonimowe.

Po zakończeniu tego instruktażu będziesz mieć możliwość przejścia do przykładów i dokumentacji dla określonego dostawcy LINQ. Dostawcy LINQ obejmują [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , LINQ to DataSet i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .

## <a name="create-a-project"></a>Tworzenie projektu

### <a name="to-create-a-console-application-project"></a>Aby utworzyć projekt aplikacji konsoli

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. Na liście **zainstalowane szablony** kliknij pozycję **Visual Basic**.

4. Na liście typów projektów kliknij pozycję **Aplikacja konsolowa**. W polu **Nazwa** wpisz nazwę projektu, a następnie kliknij przycisk **OK**.

    Projekt zostanie utworzony. Domyślnie zawiera odwołanie do System. Core. dll. Ponadto lista **zaimportowanych obszarów nazw** na [stronie odwołania, projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) zawiera <xref:System.Linq?displayProperty=nameWithType> przestrzeń nazw.

5. Na [stronie kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)upewnij się, że **opcja wnioskowanie** jest ustawiona na wartość **włączone**.

## <a name="add-an-in-memory-data-source"></a>Dodaj źródło danych w pamięci

Źródło danych dla zapytań w tym instruktażu jest listą `Student` obiektów. Każdy `Student` obiekt zawiera imię, nazwisko, rok klasy i ocenę rangi w treści ucznia.

### <a name="to-add-the-data-source"></a>Aby dodać źródło danych

- Zdefiniuj `Student` klasę i Utwórz listę wystąpień klasy.

  > [!IMPORTANT]
  > Kod wymagany do zdefiniowania `Student` klasy i utworzenia listy używanej w przykładach instruktażu znajduje się w temacie [How to: Create a list items](how-to-create-a-list-of-items.md). Możesz skopiować go z tego miejsca i wkleić do projektu. Nowy kod zastępuje kod, który pojawił się podczas tworzenia projektu.

### <a name="to-add-a-new-student-to-the-students-list"></a>Aby dodać nowego studenta do listy studentów

- Postępuj zgodnie ze wzorcem w `getStudents` metodzie, aby dodać kolejne wystąpienie `Student` klasy do listy. Dodanie ucznia spowoduje wprowadzenie do inicjatorów obiektów. Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów: typy nazwane i anonimowe](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).

## <a name="create-a-query"></a>Tworzenie zapytania

Po wykonaniu zapytanie dodane w tej sekcji tworzy listę studentów, których ranga akademickia umieszcza je w górnej części. Ponieważ zapytanie wybiera kompletny obiekt za `Student` każdym razem, typ wyniku zapytania to `IEnumerable(Of Student)` . Jednak typ zapytania zazwyczaj nie jest określony w definicjach zapytań. Zamiast tego kompilator używa wnioskowania typu lokalnego, aby określić typ. Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../../language-features/variables/local-type-inference.md). Zmienna zakresu zapytania, `currentStudent` służy jako odwołanie do każdego `Student` wystąpienia w źródle, `students` zapewniając dostęp do właściwości każdego obiektu w `students` .

### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie

1. Znajdź miejsce w `Main` metodzie projektu, które jest oznaczone w następujący sposób:

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    Skopiuj poniższy kod i wklej go w.

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. Umieść wskaźnik myszy nad `studentQuery` kodem, aby upewnić się, że typ przypisany do kompilatora to `IEnumerable(Of Student)` .

## <a name="run-the-query"></a>Uruchom zapytanie

Zmienna `studentQuery` zawiera definicję zapytania, a nie wyniki wykonywania zapytania. Typowym mechanizmem uruchamiania zapytania jest `For Each` pętla. Każdy element w zwróconej sekwencji jest dostępny za pomocą zmiennej iteracji pętli. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](writing-your-first-linq-query.md).

### <a name="to-run-the-query"></a>Aby uruchomić zapytanie

1. Dodaj następującą `For Each` pętlę poniżej zapytania w projekcie.

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. Umieść wskaźnik myszy nad zmienną sterującą pętli, `studentRecord` Aby zobaczyć jej typ danych. Typ `studentRecord` jest wnioskowany `Student` , ponieważ `studentQuery` zwraca kolekcję `Student` wystąpień.

3. Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Zwróć uwagę na wyniki w oknie konsoli.

## <a name="modify-the-query"></a>Zmodyfikuj zapytanie

Można łatwiej skanować wyniki zapytania, jeśli znajdują się one w określonej kolejności. Zwracaną sekwencję można posortować na podstawie dowolnego dostępnego pola.

### <a name="to-order-the-results"></a>Aby uporządkować wyniki

1. Dodaj następującą `Order By` klauzulę między `Where` instrukcją a `Select` instrukcją zapytania. `Order By`Klauzula porządkuje wyniki w porządku alfabetycznym od A do z, zgodnie z nazwiskiem każdego ucznia.

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. Aby zamówić według imienia i nazwiska, Dodaj oba pola do zapytania:

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    Można również określić `Descending` kolejność od z do A.

3. Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Zwróć uwagę na wyniki w oknie konsoli.

### <a name="to-introduce-a-local-identifier"></a>Aby wprowadzić identyfikator lokalny

1. Dodaj kod w tej sekcji, aby wprowadzić identyfikator lokalny w wyrażeniu zapytania. Identyfikator lokalny będzie przechowywać wynik pośredni. W poniższym przykładzie `name` jest identyfikator, który posiada połączenie imion i nazwisk studenta. Identyfikatora lokalnego można użyć dla wygody lub zwiększyć wydajność, przechowując wyniki wyrażenia, które w przeciwnym razie można obliczyć wiele razy.

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Zwróć uwagę na wyniki w oknie konsoli.

### <a name="to-project-one-field-in-the-select-clause"></a>Aby zaprojektować jedno pole w klauzuli Wybierz

1. Dodaj zapytanie i `For Each` pętlę z tej sekcji, aby utworzyć zapytanie, które tworzy sekwencję, której elementy różnią się od elementów w źródle. W poniższym przykładzie źródłem jest kolekcja `Student` obiektów, ale tylko jeden element członkowski każdego obiektu jest zwracany: imię i nazwisko uczniów, których nazwisko to Garcia. Ponieważ `currentStudent.First` jest ciągiem, typem danych sekwencji zwracanych przez `studentQuery3` is jest `IEnumerable(Of String)` , sekwencja ciągów. Jak w poprzednich przykładach przypisanie typu danych dla programu `studentQuery3` jest pozostawione dla kompilatora do określenia przy użyciu wnioskowania o typie lokalnym.

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. Umieść wskaźnik myszy nad `studentQuery3` kodem, aby sprawdzić, czy przypisany typ to `IEnumerable(Of String)` .

3. Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Zwróć uwagę na wyniki w oknie konsoli.

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Aby utworzyć typ anonimowy w klauzuli Wybierz

1. Dodaj kod z tej sekcji, aby zobaczyć, w jaki sposób anonimowe typy są używane w zapytaniach. Są one używane w zapytaniach, gdy chcesz zwrócić kilka pól ze źródła danych, a nie pełne rekordy ( `currentStudent` rekordy w poprzednich przykładach) lub pojedyncze pola ( `First` w poprzedniej sekcji). Zamiast definiować nowy nazwany typ, który zawiera pola, które mają zostać uwzględnione w wyniku, należy określić pola w `Select` klauzuli i kompilator tworzy typ anonimowy z tymi polami jako właściwości. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../language-features/objects-and-classes/anonymous-types.md).

    Poniższy przykład tworzy zapytanie zwracające nazwę i rangę wyższych rangi, których Stopka akademickia jest z zakresu od 1 do 10 w kolejności akademickiej. W tym przykładzie typ `studentQuery4` musi zostać wywnioskowany, ponieważ `Select` klauzula zwraca wystąpienie typu anonimowego, a typ anonimowy nie ma użytecznych nazw.

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5. Zwróć uwagę na wyniki w oknie konsoli.

## <a name="additional-examples"></a>Dodatkowe przykłady

Teraz, po zrozumieniu podstaw, poniżej przedstawiono listę dodatkowych przykładów demonstrujących elastyczność i możliwości zapytań LINQ. Każdy przykład jest poprzedzony krótkim opisem jego działania. Umieść wskaźnik myszy nad zmienną wyników zapytania dla każdego zapytania, aby zobaczyć wnioskowany typ. Użyj `For Each` pętli, aby wygenerować wyniki.

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a>Dodatkowe informacje

Po zapoznaniu się z podstawowymi pojęciami dotyczącymi pracy z zapytaniami możesz zapoznać się z dokumentacją i przykładami dotyczącymi określonego typu dostawcy LINQ:

- [LINQ do obiektów](linq-to-objects.md)

- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)

- [LINQ do XML](linq-to-xml.md)

- [LINQ do DataSet](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a>Zobacz też

- [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](index.md)
- [Wprowadzenie do programu LINQ w Visual Basic](getting-started-with-linq.md)
- [Wnioskowanie o typie lokalnym](../../language-features/variables/local-type-inference.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../language-features/objects-and-classes/anonymous-types.md)
- [Wprowadzenie do LINQ w Visual Basic](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Zapytania](../../../language-reference/queries/index.md)
