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
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="21131-102">Wskazówki: pisanie zapytań w C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="21131-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="21131-103">W C# tym instruktażu przedstawiono funkcje języka, które są używane do pisania wyrażeń zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="21131-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="21131-104">Utwórz projekt C#</span><span class="sxs-lookup"><span data-stu-id="21131-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21131-105">Poniższe instrukcje dotyczą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="21131-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="21131-106">Jeśli używasz innego środowiska programistycznego, Utwórz projekt konsoli z odwołaniem do elementu System. Core. dll i `using` dyrektywie dla przestrzeni nazw <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21131-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="21131-107">Aby utworzyć projekt w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21131-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="21131-108">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="21131-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="21131-109">Na pasku menu wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="21131-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="21131-110">Zostanie otwarte okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="21131-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="21131-111">Rozwiń węzeł **zainstalowane**, rozwiń węzeł **Szablony**, rozwiń węzeł **wizualizacji C#** , a następnie wybierz pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="21131-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="21131-112">W polu tekstowym **Nazwa** wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="21131-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="21131-113">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="21131-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="21131-114">Zwróć uwagę, że projekt zawiera odwołanie do elementu System. Core. dll i dyrektywy `using` dla przestrzeni nazw <xref:System.Linq?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21131-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="21131-115">Utwórz źródło danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="21131-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="21131-116">Źródło danych dla zapytań jest prostą listą obiektów `Student`.</span><span class="sxs-lookup"><span data-stu-id="21131-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="21131-117">Każdy rekord `Student` ma imię, nazwisko i tablicę liczb całkowitych, która reprezentuje wyniki testu w klasie.</span><span class="sxs-lookup"><span data-stu-id="21131-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="21131-118">Skopiuj ten kod do projektu.</span><span class="sxs-lookup"><span data-stu-id="21131-118">Copy this code into your project.</span></span> <span data-ttu-id="21131-119">Należy pamiętać o następujących cechach:</span><span class="sxs-lookup"><span data-stu-id="21131-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="21131-120">Klasa `Student` składa się z właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="21131-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="21131-121">Każdy student na liście jest inicjowany przy użyciu inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="21131-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="21131-122">Sama lista została zainicjowana przy użyciu inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="21131-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="21131-123">Ta cała struktura danych zostanie zainicjowana i utworzona bez jawnych wywołań do jakiegokolwiek konstruktora lub jawnego dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="21131-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="21131-124">Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz [Autozaimplementowane właściwości](../../classes-and-structs/auto-implemented-properties.md) i [obiekty i Inicjatory kolekcji](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="21131-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="21131-125">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="21131-125">To add the data source</span></span>  
  
- <span data-ttu-id="21131-126">Dodaj klasę `Student` i zainicjowaną listę uczniów do klasy `Program` w projekcie.</span><span class="sxs-lookup"><span data-stu-id="21131-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="21131-127">Aby dodać nowego studenta do listy studentów</span><span class="sxs-lookup"><span data-stu-id="21131-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="21131-128">Dodaj nowe `Student` do listy `Students` i użyj wybranych ocen.</span><span class="sxs-lookup"><span data-stu-id="21131-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="21131-129">Spróbuj wpisać wszystkie nowe informacje ucznia, aby lepiej poznać składnię inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="21131-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="21131-130">Utwórz zapytanie</span><span class="sxs-lookup"><span data-stu-id="21131-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="21131-131">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="21131-131">To create a simple query</span></span>  
  
- <span data-ttu-id="21131-132">W metodzie `Main` aplikacji Utwórz proste zapytanie, które po jego wykonaniu spowoduje utworzenie listy wszystkich uczniów, których wynikiem pierwszego testu była większa niż 90.</span><span class="sxs-lookup"><span data-stu-id="21131-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="21131-133">Należy zauważyć, że ponieważ zaznaczony jest cały `Student` obiekt, typ zapytania jest `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="21131-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="21131-134">Chociaż kod może również używać niejawnego wpisywania przy użyciu słowa kluczowego [var](../../../language-reference/keywords/var.md) , jawne wpisywanie jest używane do jasnego ilustrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="21131-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="21131-135">(Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md)).</span><span class="sxs-lookup"><span data-stu-id="21131-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="21131-136">Należy zauważyć, że zmienna zakresu zapytania, `student`, służy jako odwołanie do poszczególnych `Student` w źródle, zapewniając dostęp do elementów członkowskich dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21131-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="21131-137">Wykonanie zapytania</span><span class="sxs-lookup"><span data-stu-id="21131-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="21131-138">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="21131-138">To execute the query</span></span>  
  
1. <span data-ttu-id="21131-139">Teraz napisz pętlę `foreach`, która spowoduje wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="21131-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="21131-140">Zwróć uwagę na następujące informacje dotyczące kodu:</span><span class="sxs-lookup"><span data-stu-id="21131-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="21131-141">Każdy element w zwróconej sekwencji jest dostępny za pomocą zmiennej iteracji w pętli `foreach`.</span><span class="sxs-lookup"><span data-stu-id="21131-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="21131-142">Typ tej zmiennej jest `Student`, a typ zmiennej zapytania jest zgodny, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="21131-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="21131-143">Po dodaniu tego kodu, skompiluj i uruchom aplikację, aby wyświetlić wyniki w oknie **konsoli** .</span><span class="sxs-lookup"><span data-stu-id="21131-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="21131-144">Aby dodać inny warunek filtru</span><span class="sxs-lookup"><span data-stu-id="21131-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="21131-145">Można połączyć wiele warunków logicznych w klauzuli `where`, aby dodatkowo uściślić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="21131-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="21131-146">Poniższy kod dodaje warunek, aby zapytanie zwracało uczniów, których pierwszy wynik był ponad 90 i którego ostatni wynik był mniejszy niż 80.</span><span class="sxs-lookup"><span data-stu-id="21131-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="21131-147">Klauzula `where` powinna wyglądać podobnie do poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="21131-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="21131-148">Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="21131-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="21131-149">Zmodyfikuj zapytanie</span><span class="sxs-lookup"><span data-stu-id="21131-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="21131-150">Aby uporządkować wyniki</span><span class="sxs-lookup"><span data-stu-id="21131-150">To order the results</span></span>  
  
1. <span data-ttu-id="21131-151">Wyszukiwanie wyników będzie łatwiejsze, jeśli są one w pewnym rodzaju kolejności.</span><span class="sxs-lookup"><span data-stu-id="21131-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="21131-152">Zwracaną sekwencję można zamówić według dowolnego dostępnego pola w elementach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="21131-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="21131-153">Na przykład następująca `orderby` klauzula porządkuje wyniki w kolejności alfabetycznej od A do Z w zależności od nazwiska każdego ucznia.</span><span class="sxs-lookup"><span data-stu-id="21131-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="21131-154">Dodaj następującą klauzulę `orderby` do zapytania, bezpośrednio po instrukcji `where` i przed instrukcją `select`:</span><span class="sxs-lookup"><span data-stu-id="21131-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="21131-155">Teraz zmień klauzulę `orderby` tak, aby była uporządkowana w kolejności odwrotnej zgodnie z wynikami pierwszego testu, od najwyższego do najniższego wyniku.</span><span class="sxs-lookup"><span data-stu-id="21131-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="21131-156">Zmień ciąg formatu `WriteLine` tak, aby można było zobaczyć wyniki:</span><span class="sxs-lookup"><span data-stu-id="21131-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="21131-157">Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="21131-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="21131-158">Aby pogrupować wyniki</span><span class="sxs-lookup"><span data-stu-id="21131-158">To group the results</span></span>  
  
1. <span data-ttu-id="21131-159">Grupowanie jest zaawansowaną możliwością w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="21131-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="21131-160">Zapytanie z klauzulą grupy tworzy sekwencję grup, a każda sama grupa zawiera `Key` i sekwencję, która składa się ze wszystkich członków tej grupy.</span><span class="sxs-lookup"><span data-stu-id="21131-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="21131-161">Poniższe nowe zapytanie grupuje uczniów przy użyciu pierwszej litery nazwiska jako klucza.</span><span class="sxs-lookup"><span data-stu-id="21131-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="21131-162">Należy zauważyć, że typ zapytania został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="21131-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="21131-163">Teraz tworzy sekwencję grup, które mają typ `char` jako klucz i sekwencję obiektów `Student`.</span><span class="sxs-lookup"><span data-stu-id="21131-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="21131-164">Ponieważ typ zapytania został zmieniony, poniższy kod zmienia również pętlę wykonywania `foreach`:</span><span class="sxs-lookup"><span data-stu-id="21131-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="21131-165">Uruchom aplikację i Wyświetl wyniki w oknie **konsoli** .</span><span class="sxs-lookup"><span data-stu-id="21131-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="21131-166">Aby uzyskać więcej informacji, zobacz [klauzula](../../../language-reference/keywords/group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="21131-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="21131-167">Aby jawnie wpisać zmienną lokalną</span><span class="sxs-lookup"><span data-stu-id="21131-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="21131-168">Jawne kodowanie `IEnumerables` `IGroupings` może szybko stać się żmudnym.</span><span class="sxs-lookup"><span data-stu-id="21131-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="21131-169">Można napisać to samo zapytanie i `foreach` pętlę znacznie bardziej wygodnie przy użyciu `var`.</span><span class="sxs-lookup"><span data-stu-id="21131-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="21131-170">Słowo kluczowe `var` nie zmienia typów obiektów; po prostu nakazuje kompilatorowi wywnioskowanie typów.</span><span class="sxs-lookup"><span data-stu-id="21131-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="21131-171">Zmień typ `studentQuery` i zmiennej iteracji `group` do `var` i ponownie uruchom zapytanie.</span><span class="sxs-lookup"><span data-stu-id="21131-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="21131-172">Należy zauważyć, że w wewnętrznej pętli `foreach` Zmienna iteracji jest nadal wpisana jako `Student`, a zapytanie działa tak jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="21131-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="21131-173">Zmień `s` zmienną iteracji na `var` i ponownie uruchom zapytanie.</span><span class="sxs-lookup"><span data-stu-id="21131-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="21131-174">Zobaczysz, że uzyskujesz dokładnie te same wyniki.</span><span class="sxs-lookup"><span data-stu-id="21131-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="21131-175">Aby uzyskać więcej informacji na temat funkcji [var](../../../language-reference/keywords/var.md), zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="21131-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="21131-176">Aby uporządkować grupy według kluczy wartości</span><span class="sxs-lookup"><span data-stu-id="21131-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="21131-177">Po uruchomieniu poprzedniej kwerendy należy zauważyć, że grupy nie są w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="21131-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="21131-178">Aby to zmienić, należy podać klauzulę `orderby` po klauzuli `group`.</span><span class="sxs-lookup"><span data-stu-id="21131-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="21131-179">Ale aby użyć klauzuli `orderby`, najpierw potrzebny jest identyfikator, który służy jako odwołanie do grup utworzonych przez klauzulę `group`.</span><span class="sxs-lookup"><span data-stu-id="21131-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="21131-180">Identyfikator można podać za pomocą słowa kluczowego `into` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="21131-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="21131-181">Po uruchomieniu tego zapytania zobaczysz, że grupy są teraz sortowane w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="21131-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="21131-182">Aby wprowadzić identyfikator przy użyciu let</span><span class="sxs-lookup"><span data-stu-id="21131-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="21131-183">Możesz użyć słowa kluczowego `let`, aby wprowadzić identyfikator dowolnego wyniku wyrażenia w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="21131-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="21131-184">Ten identyfikator może być wygodą, tak jak w poniższym przykładzie, lub może zwiększyć wydajność, przechowując wyniki wyrażenia, aby nie trzeba było obliczyć ich wiele razy.</span><span class="sxs-lookup"><span data-stu-id="21131-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="21131-185">Aby uzyskać więcej informacji, zobacz [klauzula Let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="21131-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="21131-186">Aby użyć metody składni w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="21131-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="21131-187">Zgodnie z opisem w składni [zapytania i składni metody w LINQ](./query-syntax-and-method-syntax-in-linq.md), niektóre operacje zapytań można wyrazić tylko przy użyciu składni metody.</span><span class="sxs-lookup"><span data-stu-id="21131-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="21131-188">Poniższy kod oblicza łączny wynik dla każdego `Student` w sekwencji źródłowej, a następnie wywołuje metodę `Average()` dla wyników tego zapytania, aby obliczyć średnią ocenę klasy.</span><span class="sxs-lookup"><span data-stu-id="21131-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="21131-189">Aby przekształcić lub zaprojektować w klauzuli wyboru</span><span class="sxs-lookup"><span data-stu-id="21131-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="21131-190">Jest bardzo często źródłem zapytania, aby utworzyć sekwencję, której elementy różnią się od elementów w sekwencjach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="21131-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="21131-191">Usuń lub Skomentuj poprzednią pętlę zapytania i wykonywania, a następnie zastąp ją poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="21131-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="21131-192">Należy zauważyć, że zapytanie zwraca sekwencję ciągów (nie `Students`), a ten fakt jest odzwierciedlony w pętli `foreach`.</span><span class="sxs-lookup"><span data-stu-id="21131-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="21131-193">Kod we wcześniejszej części tego instruktażu wskazywał, że średni wynik klasy wynosi około 334.</span><span class="sxs-lookup"><span data-stu-id="21131-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="21131-194">Aby utworzyć sekwencję `Students`, której łączny wynik jest większy niż średnia klasy, wraz z ich `Student ID`, można użyć typu anonimowego w instrukcji `select`:</span><span class="sxs-lookup"><span data-stu-id="21131-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="21131-195">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="21131-195">Next Steps</span></span>  
 <span data-ttu-id="21131-196">Po zapoznaniu się z podstawowymi aspektami pracy z zapytaniami w programie C#możesz zapoznać się z dokumentacją i przykładami dotyczącymi określonego typu dostawcy LINQ:</span><span class="sxs-lookup"><span data-stu-id="21131-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="21131-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="21131-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="21131-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="21131-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="21131-199">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="21131-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="21131-200">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="21131-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="21131-201">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21131-201">See also</span></span>

- [<span data-ttu-id="21131-202">Zapytanie zintegrowane z językiem (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="21131-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="21131-203">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="21131-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
