---
title: 'Wskazówki: pisanie zapytań w C# (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: 2cac07c8eb02465334af47fd46702b60f1371c68
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745326"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="feb43-102">Wskazówki: pisanie zapytań w C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="feb43-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="feb43-103">W tym instruktażu przedstawiono funkcji języka C#, które służy do zapisywania wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="feb43-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="feb43-104">Utwórz projekt C#</span><span class="sxs-lookup"><span data-stu-id="feb43-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feb43-105">Poniższe instrukcje dotyczą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="feb43-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="feb43-106">Jeśli używasz środowiska deweloperskiego różnych, Utwórz projekt konsoli za pomocą odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="feb43-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="feb43-107">Aby utworzyć projekt w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="feb43-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="feb43-108">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="feb43-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="feb43-109">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="feb43-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="feb43-110">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="feb43-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="feb43-111">Rozwiń **zainstalowane**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="feb43-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="feb43-112">W **nazwa** polu tekstowym Wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="feb43-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="feb43-113">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="feb43-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="feb43-114">Zwróć uwagę, że projekt zawiera odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="feb43-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="feb43-115">Utwórz źródło danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="feb43-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="feb43-116">Źródło danych dla zapytania jest prostą listę `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="feb43-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="feb43-117">Każdy `Student` rekord zawiera imię, nazwisko i tablicy liczb całkowitych, reprezentujący ich wyniki testów w klasie.</span><span class="sxs-lookup"><span data-stu-id="feb43-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="feb43-118">Skopiuj ten kod do projektu.</span><span class="sxs-lookup"><span data-stu-id="feb43-118">Copy this code into your project.</span></span> <span data-ttu-id="feb43-119">Należy zwrócić uwagę następujących właściwości:</span><span class="sxs-lookup"><span data-stu-id="feb43-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="feb43-120">`Student` Klasy składa się z właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="feb43-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="feb43-121">Każdy uczeń, na liście jest inicjowany za pomocą inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="feb43-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="feb43-122">Samej listy jest inicjowany za pomocą inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="feb43-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="feb43-123">Tej struktury danych całego zostanie zainicjowana i tworzone bez jawnego wywołania konstruktora lub jawny element członkowski dostępu.</span><span class="sxs-lookup"><span data-stu-id="feb43-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="feb43-124">Aby uzyskać więcej informacji o tych nowych funkcjach, zobacz [implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="feb43-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="feb43-125">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="feb43-125">To add the data source</span></span>  
  
-   <span data-ttu-id="feb43-126">Dodaj `Student` klasy i zainicjowany listę uczniów `Program` klasy w projekcie.</span><span class="sxs-lookup"><span data-stu-id="feb43-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="feb43-127">Aby dodać nowego studenta do listy studentów</span><span class="sxs-lookup"><span data-stu-id="feb43-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="feb43-128">Dodaj nową `Student` do `Students` listy i użyj nazwy i wyniki dowolnego testu.</span><span class="sxs-lookup"><span data-stu-id="feb43-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="feb43-129">Spróbuj wpisać wszystkie nowe informacje dla uczniów, aby lepiej Poznaj składnię dla inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="feb43-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="feb43-130">Utwórz zapytanie</span><span class="sxs-lookup"><span data-stu-id="feb43-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="feb43-131">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="feb43-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="feb43-132">Przy stosowaniu `Main` metody tworzenia prostego zapytania, które, gdy jest wykonywany, generuje listę wszystkich uczniów, którego wynik pierwszego testu była większa niż 90.</span><span class="sxs-lookup"><span data-stu-id="feb43-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="feb43-133">Należy pamiętać, że ponieważ cały `Student` obiekt jest wybrany, jest typ zapytania `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="feb43-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="feb43-134">Mimo że kod można również użyć niejawnego wpisywania, za pomocą [var](../../../../csharp/language-reference/keywords/var.md) — słowo kluczowe, jawnych typowań służy do wyraźnie przedstawiają wyniki.</span><span class="sxs-lookup"><span data-stu-id="feb43-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="feb43-135">(Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="feb43-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="feb43-136">Należy zauważyć, że zapytania zmienna zakresu `student`, służy jako punkt odniesienia do każdego `Student` w źródle, zapewniając dostęp do elementu członkowskiego dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="feb43-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="feb43-137">Wykonanie zapytania</span><span class="sxs-lookup"><span data-stu-id="feb43-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="feb43-138">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="feb43-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="feb43-139">Teraz zapisać `foreach` pętli, która spowoduje, że kwerenda do wykonania.</span><span class="sxs-lookup"><span data-stu-id="feb43-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="feb43-140">Należy pamiętać o następujących o kodzie:</span><span class="sxs-lookup"><span data-stu-id="feb43-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="feb43-141">Każdy element w zwracanej sekwencji jest dostępny za pośrednictwem zmiennej iteracji w `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="feb43-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="feb43-142">Typ tej zmiennej jest `Student`, a typ zmiennej zapytania jest zgodny, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="feb43-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="feb43-143">Po dodaniu tego kodu, skompilować i uruchomić aplikację, aby zobaczyć wyniki w parametrze **konsoli** okna.</span><span class="sxs-lookup"><span data-stu-id="feb43-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="feb43-144">Aby dodać inny warunek filtru</span><span class="sxs-lookup"><span data-stu-id="feb43-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="feb43-145">Można połączyć wiele warunków logicznych w `where` klauzulę, aby dalej zawęzić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="feb43-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="feb43-146">Poniższy kod dodaje warunek, dlatego, że zapytanie zwraca tych studentów, którego wynik pierwszego był ponad 90 i którego ostatni wynik był mniejszy niż 80.</span><span class="sxs-lookup"><span data-stu-id="feb43-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="feb43-147">`where` Klauzuli powinien przypominać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="feb43-147">The `where` clause should resemble the following code.</span></span>  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="feb43-148">Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="feb43-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="feb43-149">Zmodyfikuj zapytanie</span><span class="sxs-lookup"><span data-stu-id="feb43-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="feb43-150">Aby uporządkować wyniki</span><span class="sxs-lookup"><span data-stu-id="feb43-150">To order the results</span></span>  
  
1.  <span data-ttu-id="feb43-151">Będzie można ją łatwiej wyników skanowania, jeśli są one w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="feb43-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="feb43-152">Może zamówić łączność obejmującą zwracanej sekwencji według dowolnego pola dostępne w elementy źródłowe.</span><span class="sxs-lookup"><span data-stu-id="feb43-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="feb43-153">Na przykład następująca `orderby` klauzuli zamówienia wyniki w kolejności alfabetycznej od A do Z, zgodnie z ostatnio nazwę każdego ucznia.</span><span class="sxs-lookup"><span data-stu-id="feb43-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="feb43-154">Dodaj następujący kod `orderby` klauzuli do kwerendy, zaraz po `where` instrukcji i przed `select` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="feb43-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="feb43-155">Teraz Zmień `orderby` klauzuli, tak że porządkuje wyniki w odwrotnej kolejności według oceny pierwszego testu z najwyższym wynikiem do najmniejszej liczby punktów.</span><span class="sxs-lookup"><span data-stu-id="feb43-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="feb43-156">Zmiana `WriteLine` ciąg formatu, dzięki czemu można zobaczyć wyniki:</span><span class="sxs-lookup"><span data-stu-id="feb43-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="feb43-157">Aby uzyskać więcej informacji, zobacz [klauzuli orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="feb43-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="feb43-158">Aby pogrupować wyniki</span><span class="sxs-lookup"><span data-stu-id="feb43-158">To group the results</span></span>  
  
1.  <span data-ttu-id="feb43-159">Grupowanie jest zaawansowaną możliwością w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="feb43-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="feb43-160">Zapytanie z klauzulą grupy tworzy sekwencję grup, a każda grupa sam zawiera `Key` i sekwencji, który składa się z wszystkich członków tej grupy.</span><span class="sxs-lookup"><span data-stu-id="feb43-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="feb43-161">Następujące zapytanie nowe grupy uczniów przy użyciu pierwszej litery swoje nazwisko jako klucz.</span><span class="sxs-lookup"><span data-stu-id="feb43-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  <span data-ttu-id="feb43-162">Należy pamiętać, że typ zapytania zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="feb43-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="feb43-163">Teraz wytwarza sekwencję grupy, które mają `char` typ jako klucz i sekwencję `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="feb43-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="feb43-164">Ponieważ typ zapytania została zmieniona, poniższy kod zmiany `foreach` wykonywania pętli również:</span><span class="sxs-lookup"><span data-stu-id="feb43-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  <span data-ttu-id="feb43-165">Uruchom aplikację i wyświetlić wyniki w **konsoli** okna.</span><span class="sxs-lookup"><span data-stu-id="feb43-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="feb43-166">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="feb43-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="feb43-167">Aby jawnie wpisać zmienną lokalną</span><span class="sxs-lookup"><span data-stu-id="feb43-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="feb43-168">Jawne kodowania `IEnumerables` z `IGroupings` może szybko stać się uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="feb43-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="feb43-169">Można napisać tego samego zapytania i `foreach` pętli za pomocą znacznie więcej wygodnie `var`.</span><span class="sxs-lookup"><span data-stu-id="feb43-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="feb43-170">`var` — Słowo kluczowe nie zmienia typów obiektów; po prostu nakazuje kompilatorowi wywnioskowania typów.</span><span class="sxs-lookup"><span data-stu-id="feb43-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="feb43-171">Zmiana rodzaju `studentQuery` , a zmienna iteracji `group` do `var` i ponownie uruchom zapytanie.</span><span class="sxs-lookup"><span data-stu-id="feb43-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="feb43-172">Należy pamiętać, że w wewnętrzny `foreach` pętli, Zmienna iteracji nadal jest wpisana jako `Student`, a zapytanie działa tak jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="feb43-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="feb43-173">Zmiana `s` zmiennej iteracji w celu `var` i ponownie uruchom zapytanie.</span><span class="sxs-lookup"><span data-stu-id="feb43-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="feb43-174">Zobaczysz, że uzyskać te same wyniki.</span><span class="sxs-lookup"><span data-stu-id="feb43-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     <span data-ttu-id="feb43-175">Aby uzyskać więcej informacji na temat [var](../../../../csharp/language-reference/keywords/var.md), zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="feb43-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="feb43-176">Aby uporządkować grupy według kluczy wartości</span><span class="sxs-lookup"><span data-stu-id="feb43-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="feb43-177">Po uruchomieniu poprzednie zapytanie, można zauważyć, że grupy nie są w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="feb43-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="feb43-178">Aby zmienić to ustawienie, należy podać `orderby` klauzula po `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="feb43-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="feb43-179">Do użycia, ale `orderby` klauzuli, musisz najpierw identyfikator, który służy jako punkt odniesienia do grup utworzonych przez `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="feb43-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="feb43-180">Podaj identyfikator przy użyciu `into` — słowo kluczowe w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="feb43-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     <span data-ttu-id="feb43-181">Po uruchomieniu tego zapytania, widoczne będą grupy teraz są sortowane w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="feb43-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="feb43-182">Aby wprowadzić identyfikator przy użyciu let</span><span class="sxs-lookup"><span data-stu-id="feb43-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="feb43-183">Możesz użyć `let` — słowo kluczowe, aby wprowadzić identyfikator dla dowolnego wyniku wyrażenia w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="feb43-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="feb43-184">Ten identyfikator może być udogodnienie, jak w poniższym przykładzie, lub można go zwiększyć wydajność dzięki przechowywaniu wyniki wyrażenia, tak aby nie ma zostać obliczona wiele razy.</span><span class="sxs-lookup"><span data-stu-id="feb43-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     <span data-ttu-id="feb43-185">Aby uzyskać więcej informacji, zobacz [let, klauzula](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="feb43-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="feb43-186">Aby użyć metody składni w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="feb43-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="feb43-187">Zgodnie z opisem w [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), niektórych operacji zapytań może być wyrażone tylko przy użyciu składni metody.</span><span class="sxs-lookup"><span data-stu-id="feb43-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="feb43-188">Poniższy kod oblicza łączny wynik dla każdego `Student` w sekwencji źródłowej, a następnie wywołania `Average()` metody wyników tej kwerendy, aby obliczyć średnią ocenę klasy.</span><span class="sxs-lookup"><span data-stu-id="feb43-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span> <span data-ttu-id="feb43-189">Należy pamiętać, umieszczania nawiasów wokół wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="feb43-189">Note the placement of parentheses around the query expression.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="feb43-190">Aby przekształcić lub zaprojektować w klauzuli wyboru</span><span class="sxs-lookup"><span data-stu-id="feb43-190">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="feb43-191">Jest bardzo często zapytanie w celu utworzenia sekwencji, w której elementy różnią się od elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="feb43-191">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="feb43-192">Usuń komentarz z poprzedniej kwerendy i wykonywanie pętlę metodyki lub zastąp go następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="feb43-192">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="feb43-193">Należy pamiętać, że zapytanie zwraca sekwencję ciągów (nie `Students`), a ten fakt znajduje odzwierciedlenie w `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="feb43-193">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  <span data-ttu-id="feb43-194">Kodu we wcześniejszej części tego przewodnika wskazane, to około 334 wynik klasy średniej.</span><span class="sxs-lookup"><span data-stu-id="feb43-194">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="feb43-195">Aby utworzyć sekwencję `Students` których łączny wynik jest większa niż średnia klasy wraz z ich `Student ID`, można użyć typu anonimowego w `select` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="feb43-195">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a><span data-ttu-id="feb43-196">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="feb43-196">Next Steps</span></span>  
 <span data-ttu-id="feb43-197">Po przejściu na podstawowych aspektów pracy z zapytaniami w języku C#, jesteś gotowy do odczytu, dokumentację i przykłady dla określonego typu dostawcy LINQ, który Cię interesuje:</span><span class="sxs-lookup"><span data-stu-id="feb43-197">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="feb43-198">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="feb43-198">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="feb43-199">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="feb43-199">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="feb43-200">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="feb43-200">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="feb43-201">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="feb43-201">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="feb43-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="feb43-202">See Also</span></span>

- [<span data-ttu-id="feb43-203">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="feb43-203">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="feb43-204">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="feb43-204">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [<span data-ttu-id="feb43-205">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="feb43-205">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
