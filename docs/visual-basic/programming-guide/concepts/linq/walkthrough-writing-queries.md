---
title: Pisanie zapytań w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: ac654701a459b57e7121cb82f4cf53941bcf15e0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578943"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="7ef33-102">Wskazówki: Pisanie zapytań w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ef33-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="7ef33-103">W tym instruktażu pokazano, jak za pomocą funkcji języka Visual Basic pisać [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia zapytań.</span><span class="sxs-lookup"><span data-stu-id="7ef33-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query expressions.</span></span> <span data-ttu-id="7ef33-104">W tym przewodniku pokazano, jak tworzyć zapytania na liście obiektów uczniów, jak uruchamiać zapytania i jak je modyfikować.</span><span class="sxs-lookup"><span data-stu-id="7ef33-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="7ef33-105">Zapytania obejmują kilka funkcji, w tym Inicjatory obiektów, wnioskowanie typu lokalnego i typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="7ef33-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="7ef33-106">Po ukończeniu tego przewodnika będziesz mieć możliwość przejścia do przykładów i dokumentacji dotyczącej konkretnego dostawcy [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ef33-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="7ef33-107">dostawcy obejmują [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ef33-107">providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="7ef33-108">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="7ef33-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="7ef33-109">Aby utworzyć projekt aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="7ef33-109">To create a console application project</span></span>

1. <span data-ttu-id="7ef33-110">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ef33-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="7ef33-111">W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="7ef33-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="7ef33-112">Na liście **zainstalowane szablony** kliknij pozycję **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="7ef33-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="7ef33-113">Na liście typów projektów kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="7ef33-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="7ef33-114">W polu **Nazwa** wpisz nazwę projektu, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7ef33-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="7ef33-115">Projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="7ef33-115">A project is created.</span></span> <span data-ttu-id="7ef33-116">Domyślnie zawiera odwołanie do System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="7ef33-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="7ef33-117">Ponadto lista **zaimportowanych obszarów nazw** na [stronie odwołania, projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) zawiera przestrzeń nazw <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ef33-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="7ef33-118">Na [stronie kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)upewnij się, że **opcja wnioskowanie** jest ustawiona na wartość **włączone**.</span><span class="sxs-lookup"><span data-stu-id="7ef33-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="7ef33-119">Dodaj źródło danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="7ef33-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="7ef33-120">Źródło danych dla zapytań w tym instruktażu jest listą obiektów `Student`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="7ef33-121">Każdy obiekt `Student` zawiera imię, nazwisko, rok klasy i ocenę rangi w treści ucznia.</span><span class="sxs-lookup"><span data-stu-id="7ef33-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="7ef33-122">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="7ef33-122">To add the data source</span></span>

- <span data-ttu-id="7ef33-123">Zdefiniuj klasę `Student` i Utwórz listę wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="7ef33-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="7ef33-124">Kod wymagany do zdefiniowania klasy `Student` i utworzenia listy używanej w przykładach instruktażu znajduje się w temacie [How to: Create a list items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="7ef33-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="7ef33-125">Możesz skopiować go z tego miejsca i wkleić do projektu.</span><span class="sxs-lookup"><span data-stu-id="7ef33-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="7ef33-126">Nowy kod zastępuje kod, który pojawił się podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="7ef33-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="7ef33-127">Aby dodać nowego studenta do listy studentów</span><span class="sxs-lookup"><span data-stu-id="7ef33-127">To add a new student to the students list</span></span>

- <span data-ttu-id="7ef33-128">Postępuj zgodnie ze wzorcem w metodzie `getStudents`, aby dodać kolejne wystąpienie klasy `Student` do listy.</span><span class="sxs-lookup"><span data-stu-id="7ef33-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="7ef33-129">Dodanie ucznia spowoduje wprowadzenie do inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ef33-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="7ef33-130">Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7ef33-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="7ef33-131">Tworzenie zapytania</span><span class="sxs-lookup"><span data-stu-id="7ef33-131">Create a Query</span></span>

<span data-ttu-id="7ef33-132">Po wykonaniu zapytanie dodane w tej sekcji tworzy listę studentów, których ranga akademickia umieszcza je w górnej części.</span><span class="sxs-lookup"><span data-stu-id="7ef33-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="7ef33-133">Ponieważ zapytanie wybiera kompletny obiekt `Student` za każdym razem, typ wyniku zapytania jest `IEnumerable(Of Student)`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="7ef33-134">Jednak typ zapytania zazwyczaj nie jest określony w definicjach zapytań.</span><span class="sxs-lookup"><span data-stu-id="7ef33-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="7ef33-135">Zamiast tego kompilator używa wnioskowania typu lokalnego, aby określić typ.</span><span class="sxs-lookup"><span data-stu-id="7ef33-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="7ef33-136">Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7ef33-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="7ef33-137">Zmienna zakresu zapytania, `currentStudent`, służy jako odwołanie do każdego `Student` wystąpienia w źródle, `students`, zapewniając dostęp do właściwości każdego obiektu w `students`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="7ef33-138">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="7ef33-138">To create a simple query</span></span>

1. <span data-ttu-id="7ef33-139">Znajdź miejsce w `Main` metodzie projektu, który jest oznaczony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7ef33-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="7ef33-140">Skopiuj poniższy kod i wklej go w.</span><span class="sxs-lookup"><span data-stu-id="7ef33-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="7ef33-141">Umieść wskaźnik myszy nad `studentQuery` w kodzie, aby upewnić się, że typ przypisany do kompilatora jest `IEnumerable(Of Student)`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="7ef33-142">Uruchom zapytanie</span><span class="sxs-lookup"><span data-stu-id="7ef33-142">Run the Query</span></span>

<span data-ttu-id="7ef33-143">Zmienna `studentQuery` zawiera definicję zapytania, a nie wyniki wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="7ef33-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="7ef33-144">Typowym mechanizmem uruchamiania zapytania jest pętla `For Each`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="7ef33-145">Każdy element w zwróconej sekwencji jest dostępny za pomocą zmiennej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="7ef33-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="7ef33-146">Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="7ef33-146">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="7ef33-147">Aby uruchomić zapytanie</span><span class="sxs-lookup"><span data-stu-id="7ef33-147">To run the query</span></span>

1. <span data-ttu-id="7ef33-148">Dodaj następującą `For Each` pętlę poniżej zapytania w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7ef33-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="7ef33-149">Umieść wskaźnik myszy nad zmienną sterującą pętli `studentRecord`, aby zobaczyć jej typ danych.</span><span class="sxs-lookup"><span data-stu-id="7ef33-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="7ef33-150">Typ `studentRecord` jest wywnioskowany do `Student`, ponieważ `studentQuery` zwraca kolekcję wystąpień `Student`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="7ef33-151">Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7ef33-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7ef33-152">Zwróć uwagę na wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7ef33-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="7ef33-153">Zmodyfikuj zapytanie</span><span class="sxs-lookup"><span data-stu-id="7ef33-153">Modify the Query</span></span>

<span data-ttu-id="7ef33-154">Można łatwiej skanować wyniki zapytania, jeśli znajdują się one w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="7ef33-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="7ef33-155">Zwracaną sekwencję można posortować na podstawie dowolnego dostępnego pola.</span><span class="sxs-lookup"><span data-stu-id="7ef33-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="7ef33-156">Aby uporządkować wyniki</span><span class="sxs-lookup"><span data-stu-id="7ef33-156">To order the results</span></span>

1. <span data-ttu-id="7ef33-157">Dodaj następującą klauzulę `Order By` między instrukcją `Where` i instrukcją `Select` zapytania.</span><span class="sxs-lookup"><span data-stu-id="7ef33-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="7ef33-158">Klauzula `Order By` porządkuje wyniki w porządku alfabetycznym od A do Z, zgodnie z nazwiskiem każdego ucznia.</span><span class="sxs-lookup"><span data-stu-id="7ef33-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="7ef33-159">Aby zamówić według imienia i nazwiska, Dodaj oba pola do zapytania:</span><span class="sxs-lookup"><span data-stu-id="7ef33-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="7ef33-160">Możesz również określić, `Descending` mają być uporządkowane od z do A.</span><span class="sxs-lookup"><span data-stu-id="7ef33-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="7ef33-161">Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7ef33-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7ef33-162">Zwróć uwagę na wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7ef33-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="7ef33-163">Aby wprowadzić identyfikator lokalny</span><span class="sxs-lookup"><span data-stu-id="7ef33-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="7ef33-164">Dodaj kod w tej sekcji, aby wprowadzić identyfikator lokalny w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="7ef33-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="7ef33-165">Identyfikator lokalny będzie przechowywać wynik pośredni.</span><span class="sxs-lookup"><span data-stu-id="7ef33-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="7ef33-166">W poniższym przykładzie `name` jest identyfikatorem, który posiada połączenie imion i nazwisk studenta.</span><span class="sxs-lookup"><span data-stu-id="7ef33-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="7ef33-167">Identyfikatora lokalnego można użyć dla wygody lub zwiększyć wydajność, przechowując wyniki wyrażenia, które w przeciwnym razie można obliczyć wiele razy.</span><span class="sxs-lookup"><span data-stu-id="7ef33-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="7ef33-168">Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7ef33-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7ef33-169">Zwróć uwagę na wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7ef33-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="7ef33-170">Aby zaprojektować jedno pole w klauzuli Wybierz</span><span class="sxs-lookup"><span data-stu-id="7ef33-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="7ef33-171">Dodaj zapytanie i pętlę `For Each` z tej sekcji, aby utworzyć zapytanie, które tworzy sekwencję, której elementy różnią się od elementów w źródle.</span><span class="sxs-lookup"><span data-stu-id="7ef33-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="7ef33-172">W poniższym przykładzie źródłem jest kolekcja obiektów `Student`, ale tylko jeden element członkowski każdego obiektu jest zwracany: imię i nazwisko uczniów, których nazwisko to Garcia.</span><span class="sxs-lookup"><span data-stu-id="7ef33-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="7ef33-173">Ponieważ `currentStudent.First` jest ciągiem, typem danych sekwencji zwracanej przez `studentQuery3` jest `IEnumerable(Of String)`, sekwencję ciągów.</span><span class="sxs-lookup"><span data-stu-id="7ef33-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="7ef33-174">Jak w poprzednich przykładach przypisanie typu danych dla `studentQuery3` jest pozostawiane kompilatorowi do określenia przy użyciu wnioskowania typu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7ef33-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="7ef33-175">Umieść wskaźnik myszy nad `studentQuery3` w kodzie, aby sprawdzić, czy przypisany typ jest `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="7ef33-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="7ef33-176">Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7ef33-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7ef33-177">Zwróć uwagę na wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7ef33-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="7ef33-178">Aby utworzyć typ anonimowy w klauzuli Wybierz</span><span class="sxs-lookup"><span data-stu-id="7ef33-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="7ef33-179">Dodaj kod z tej sekcji, aby zobaczyć, w jaki sposób anonimowe typy są używane w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="7ef33-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="7ef33-180">Są one używane w zapytaniach, gdy chcesz zwrócić kilka pól ze źródła danych, a nie pełne rekordy (`currentStudent` rekordy w poprzednich przykładach) lub pojedyncze pola (`First` w poprzedniej sekcji).</span><span class="sxs-lookup"><span data-stu-id="7ef33-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="7ef33-181">Zamiast definiować nowy nazwany typ, który zawiera pola, które mają zostać uwzględnione w wyniku, należy określić pola w klauzuli `Select` i kompilator tworzy typ anonimowy z tymi polami jako właściwości.</span><span class="sxs-lookup"><span data-stu-id="7ef33-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="7ef33-182">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7ef33-182">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="7ef33-183">Poniższy przykład tworzy zapytanie zwracające nazwę i rangę wyższych rangi, których Stopka akademickia jest z zakresu od 1 do 10 w kolejności akademickiej.</span><span class="sxs-lookup"><span data-stu-id="7ef33-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="7ef33-184">W tym przykładzie typ `studentQuery4` musi zostać wywnioskowany, ponieważ klauzula `Select` zwraca wystąpienie typu anonimowego, a typ anonimowy nie ma użytecznych nazw.</span><span class="sxs-lookup"><span data-stu-id="7ef33-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="7ef33-185">Skompiluj i uruchom aplikację, naciskając klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="7ef33-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7ef33-186">Zwróć uwagę na wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7ef33-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="7ef33-187">Dodatkowe przykłady</span><span class="sxs-lookup"><span data-stu-id="7ef33-187">Additional Examples</span></span>

<span data-ttu-id="7ef33-188">Teraz, po zrozumieniu podstaw, poniżej przedstawiono listę dodatkowych przykładów demonstrujących elastyczność i możliwości zapytań [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ef33-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="7ef33-189">Każdy przykład jest poprzedzony krótkim opisem jego działania.</span><span class="sxs-lookup"><span data-stu-id="7ef33-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="7ef33-190">Umieść wskaźnik myszy nad zmienną wyników zapytania dla każdego zapytania, aby zobaczyć wnioskowany typ.</span><span class="sxs-lookup"><span data-stu-id="7ef33-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="7ef33-191">Użyj pętli `For Each`, aby wygenerować wyniki.</span><span class="sxs-lookup"><span data-stu-id="7ef33-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="7ef33-192">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="7ef33-192">Additional Information</span></span>

<span data-ttu-id="7ef33-193">Po zapoznaniu się z podstawowymi pojęciami dotyczącymi pracy z zapytaniami możesz zapoznać się z dokumentacją i przykładami dotyczącymi określonego typu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy:</span><span class="sxs-lookup"><span data-stu-id="7ef33-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider that you are interested in:</span></span>

- [<span data-ttu-id="7ef33-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="7ef33-194">LINQ to Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [<span data-ttu-id="7ef33-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7ef33-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="7ef33-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="7ef33-196">LINQ to XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [<span data-ttu-id="7ef33-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7ef33-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="7ef33-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ef33-198">See also</span></span>

- [<span data-ttu-id="7ef33-199">Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ef33-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="7ef33-200">Wprowadzenie ze składnikami LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ef33-200">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="7ef33-201">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="7ef33-201">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7ef33-202">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="7ef33-202">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="7ef33-203">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7ef33-203">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="7ef33-204">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ef33-204">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7ef33-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="7ef33-205">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="7ef33-206">Zapytania</span><span class="sxs-lookup"><span data-stu-id="7ef33-206">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
