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
ms.locfileid: "33340414"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="aabd8-102">Wskazówki: pisanie zapytań w C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="aabd8-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="aabd8-103">W tym przewodniku przedstawiono funkcji języka C#, które są używane do zapisu wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="aabd8-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="aabd8-104">Utwórz projekt C#</span><span class="sxs-lookup"><span data-stu-id="aabd8-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aabd8-105">Poniższe instrukcje dotyczą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aabd8-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="aabd8-106">Jeśli używasz Środowisko deweloperskie innego, tworzenie projektu konsoli z odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="aabd8-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="aabd8-107">Aby utworzyć projekt w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aabd8-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="aabd8-108">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aabd8-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="aabd8-109">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="aabd8-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="aabd8-110">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="aabd8-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="aabd8-111">Rozwiń węzeł **zainstalowana**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="aabd8-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="aabd8-112">W **nazwa** polu tekstowym Wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="aabd8-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="aabd8-113">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="aabd8-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="aabd8-114">Powiadomienie, że projekt zawiera odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="aabd8-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="aabd8-115">Utwórz źródło danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="aabd8-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="aabd8-116">Źródło danych zapytania jest to prosta lista `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="aabd8-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="aabd8-117">Każdy `Student` rekord zawiera imię, nazwisko i tablicę liczb całkowitych, która reprezentuje wyniki testu w klasie.</span><span class="sxs-lookup"><span data-stu-id="aabd8-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="aabd8-118">Skopiuj ten kod do projektu.</span><span class="sxs-lookup"><span data-stu-id="aabd8-118">Copy this code into your project.</span></span> <span data-ttu-id="aabd8-119">Należy uwzględnić następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="aabd8-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="aabd8-120">`Student` Klasy składa się z właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="aabd8-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="aabd8-121">Na liście użytkowników jest inicjowana przy użyciu inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="aabd8-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="aabd8-122">Samej listy został zainicjowany przy użyciu inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="aabd8-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="aabd8-123">Ta struktura danych całego zostanie zainicjowany i wystąpienia bez jawnego wywołania konstruktora lub jawnego członka dostępu.</span><span class="sxs-lookup"><span data-stu-id="aabd8-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="aabd8-124">Aby uzyskać więcej informacji na temat nowych funkcji, zobacz [właściwości Auto-Implemented](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="aabd8-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="aabd8-125">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="aabd8-125">To add the data source</span></span>  
  
-   <span data-ttu-id="aabd8-126">Dodaj `Student` klasy i zainicjowane listę studentom / `Program` klasy w projekcie.</span><span class="sxs-lookup"><span data-stu-id="aabd8-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="aabd8-127">Aby dodać nowego studenta do listy studentów</span><span class="sxs-lookup"><span data-stu-id="aabd8-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="aabd8-128">Dodaj nową `Student` do `Students` listy i użyj nazwy i wyniki dowolnego testu.</span><span class="sxs-lookup"><span data-stu-id="aabd8-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="aabd8-129">Spróbuj wpisać wszystkie nowe informacje dla użytkowników domowych, aby lepiej informacje składni inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="aabd8-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="aabd8-130">Utwórz zapytanie</span><span class="sxs-lookup"><span data-stu-id="aabd8-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="aabd8-131">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="aabd8-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="aabd8-132">W aplikacji `Main` metody tworzenia prostego zapytania, który, po jego wykonaniu utworzy listę wszystkich studentów, którego wynik na pierwszego testu była większa niż 90.</span><span class="sxs-lookup"><span data-stu-id="aabd8-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="aabd8-133">Należy pamiętać, że ponieważ cały `Student` obiektu jest zaznaczona, jest typu zapytania `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="aabd8-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="aabd8-134">Mimo że kod można również użyć niejawnego wpisanie przy użyciu [var](../../../../csharp/language-reference/keywords/var.md) — słowo kluczowe, wpisując jawne jest używana do wyraźnie zilustrowania wyniki.</span><span class="sxs-lookup"><span data-stu-id="aabd8-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="aabd8-135">(Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="aabd8-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="aabd8-136">Należy zauważyć, że kwerendy zmiennej zakresu `student`, służy jako punkt odniesienia do każdego `Student` w źródle, zapewniając dostęp do elementu członkowskiego dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="aabd8-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="aabd8-137">Wykonanie zapytania</span><span class="sxs-lookup"><span data-stu-id="aabd8-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="aabd8-138">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="aabd8-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="aabd8-139">Teraz zapisać `foreach` pętli, które spowodują wykonanie zapytania w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="aabd8-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="aabd8-140">Należy pamiętać, że o kodzie:</span><span class="sxs-lookup"><span data-stu-id="aabd8-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="aabd8-141">Każdy element zwrócony sekwencji jest dostępny za pośrednictwem zmiennej iteracji w `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="aabd8-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="aabd8-142">Ta zmienna jest `Student`, i typu zmienną zapytania jest zgodny, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="aabd8-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="aabd8-143">Po dodaniu tego kodu, skompiluj i uruchom aplikację, aby zobaczyć wyniki w **konsoli** okna.</span><span class="sxs-lookup"><span data-stu-id="aabd8-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="aabd8-144">Aby dodać inny warunek filtru</span><span class="sxs-lookup"><span data-stu-id="aabd8-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="aabd8-145">Można połączyć wiele warunków logicznych w `where` klauzuli celu uściślenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="aabd8-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="aabd8-146">Poniższy kod dodaje warunek tak, aby zapytanie zwraca tych studentów których pierwszy wynik został ponad 90 i których ostatni wynik był mniejszy niż 80.</span><span class="sxs-lookup"><span data-stu-id="aabd8-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="aabd8-147">`where` Klauzuli powinien przypominać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="aabd8-147">The `where` clause should resemble the following code.</span></span>  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="aabd8-148">Aby uzyskać więcej informacji, zobacz [gdzie klauzuli](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aabd8-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="aabd8-149">Zmodyfikuj zapytanie</span><span class="sxs-lookup"><span data-stu-id="aabd8-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="aabd8-150">Aby uporządkować wyniki</span><span class="sxs-lookup"><span data-stu-id="aabd8-150">To order the results</span></span>  
  
1.  <span data-ttu-id="aabd8-151">Będzie bardziej czytelne wyniki, jeśli są one w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="aabd8-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="aabd8-152">Można zamówić sekwencja zwrócony przez wszystkie dostępne pola w elementy źródłowe.</span><span class="sxs-lookup"><span data-stu-id="aabd8-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="aabd8-153">Na przykład następująca `orderby` klauzuli porządkuje wyniki w kolejności alfabetycznej z zakresu od A do Z zgodnie z ostatnią nazwy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="aabd8-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="aabd8-154">Dodaj następujące `orderby` klauzuli do zapytania, prawy po `where` instrukcji i przed `select` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="aabd8-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="aabd8-155">Teraz zmienić `orderby` klauzulę, tak że porządkuje wyniki w kolejności odwrotnej zgodnie z wynik na pierwszego testu z najwyższym wynik do najmniejszej liczby punktów.</span><span class="sxs-lookup"><span data-stu-id="aabd8-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="aabd8-156">Zmień `WriteLine` ciąg formatu, tak aby były widoczne wyniki:</span><span class="sxs-lookup"><span data-stu-id="aabd8-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="aabd8-157">Aby uzyskać więcej informacji, zobacz [klauzula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aabd8-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="aabd8-158">Aby pogrupować wyniki</span><span class="sxs-lookup"><span data-stu-id="aabd8-158">To group the results</span></span>  
  
1.  <span data-ttu-id="aabd8-159">Metoda grupowania jest przydatna możliwość w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="aabd8-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="aabd8-160">Zapytań z klauzulą grupy tworzy sekwencję grup, a każda grupa sam zawiera `Key` i sekwencji, która składa się z wszystkich członków tej grupy.</span><span class="sxs-lookup"><span data-stu-id="aabd8-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="aabd8-161">Następujące nowe zapytanie grupuje studentów przy użyciu pierwszą literę ich nazwiska jako klucza.</span><span class="sxs-lookup"><span data-stu-id="aabd8-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  <span data-ttu-id="aabd8-162">Należy pamiętać, że typ zapytania zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="aabd8-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="aabd8-163">Teraz tworzy sekwencję grupy, które mają `char` typu jako klucza i sekwencji `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="aabd8-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="aabd8-164">Ponieważ typ zapytania został zmieniony, poniższy kod zmiany `foreach` wykonywania pętli również:</span><span class="sxs-lookup"><span data-stu-id="aabd8-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  <span data-ttu-id="aabd8-165">Uruchom aplikację i wyświetlić wyniki w **konsoli** okna.</span><span class="sxs-lookup"><span data-stu-id="aabd8-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="aabd8-166">Aby uzyskać więcej informacji, zobacz [klauzuli group](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aabd8-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="aabd8-167">Aby jawnie wpisać zmienną lokalną</span><span class="sxs-lookup"><span data-stu-id="aabd8-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="aabd8-168">Jawnie kodowania `IEnumerables` z `IGroupings` może szybko stać się nużące.</span><span class="sxs-lookup"><span data-stu-id="aabd8-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="aabd8-169">Można zapisać tego samego zapytania i `foreach` pętli znacznie ułatwia przy użyciu `var`.</span><span class="sxs-lookup"><span data-stu-id="aabd8-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="aabd8-170">`var` — Słowo kluczowe nie zmienia typy obiektów; właśnie nakazuje kompilatorowi wnioskowanie typów.</span><span class="sxs-lookup"><span data-stu-id="aabd8-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="aabd8-171">Zmień typ `studentQuery` i zmiennej iteracji `group` do `var` i ponownie uruchom zapytanie.</span><span class="sxs-lookup"><span data-stu-id="aabd8-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="aabd8-172">Należy pamiętać, że w wewnętrznej `foreach` pętli, zmiennej iteracji jest nadal typu `Student`, a zapytanie działa tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="aabd8-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="aabd8-173">Zmień `s` zmiennej iteracji `var` i ponownie uruchom zapytanie.</span><span class="sxs-lookup"><span data-stu-id="aabd8-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="aabd8-174">Możesz sprawdzić, czy pobrać dokładnie takie same wyniki.</span><span class="sxs-lookup"><span data-stu-id="aabd8-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     <span data-ttu-id="aabd8-175">Aby uzyskać więcej informacji na temat [var](../../../../csharp/language-reference/keywords/var.md), zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="aabd8-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="aabd8-176">Aby uporządkować grupy według kluczy wartości</span><span class="sxs-lookup"><span data-stu-id="aabd8-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="aabd8-177">Uruchomienie poprzedniego zapytania, można zauważyć, że grupy nie są w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="aabd8-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="aabd8-178">Aby zmienić to ustawienie, musisz podać `orderby` klauzula po `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="aabd8-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="aabd8-179">Do użycia, ale `orderby` klauzuli, należy najpierw identyfikator, który służy jako punkt odniesienia dla grup utworzonych przez `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="aabd8-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="aabd8-180">Podaj identyfikator przy użyciu `into` — słowo kluczowe, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="aabd8-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     <span data-ttu-id="aabd8-181">Po uruchomieniu tego zapytania, pojawi się, że grupy teraz są sortowane w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="aabd8-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="aabd8-182">Aby wprowadzić identyfikator przy użyciu let</span><span class="sxs-lookup"><span data-stu-id="aabd8-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="aabd8-183">Można użyć `let` — słowo kluczowe wprowadzić identyfikator dowolny wynik wyrażenia w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="aabd8-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="aabd8-184">Ten identyfikator może być wygody, jak w poniższym przykładzie lub go poprawić wydajność dzięki przechowywaniu wynik wyrażenia, aby nie ma zostać obliczona wiele razy.</span><span class="sxs-lookup"><span data-stu-id="aabd8-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     <span data-ttu-id="aabd8-185">Aby uzyskać więcej informacji, zobacz [klauzula let](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aabd8-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="aabd8-186">Aby użyć metody składni w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="aabd8-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="aabd8-187">Zgodnie z opisem w [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), niektóre operacje zapytań można wyrazić tylko przy użyciu składni metody.</span><span class="sxs-lookup"><span data-stu-id="aabd8-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="aabd8-188">Poniższy kod oblicza łączny wynik dla każdego `Student` w sekwencji źródłowej, a następnie wywołania `Average()` metody wyników zapytania do obliczania średniej wyniku klasy.</span><span class="sxs-lookup"><span data-stu-id="aabd8-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span> <span data-ttu-id="aabd8-189">Należy pamiętać, umieszczania nawiasy otaczające wyrażenie zapytania.</span><span class="sxs-lookup"><span data-stu-id="aabd8-189">Note the placement of parentheses around the query expression.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="aabd8-190">Aby przekształcić lub zaprojektować w klauzuli wyboru</span><span class="sxs-lookup"><span data-stu-id="aabd8-190">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="aabd8-191">Jest bardzo często zapytanie w celu utworzenia sekwencji, której elementy różnią się od elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="aabd8-191">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="aabd8-192">Usuń lub komentarz z poprzednich zapytań i wykonywania pętli i zastąp go następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="aabd8-192">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="aabd8-193">Należy pamiętać, że zapytanie zwraca sekwencję ciągów (nie `Students`), a fakt ten jest odzwierciedlone w `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="aabd8-193">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  <span data-ttu-id="aabd8-194">Kodu we wcześniejszej części tego przewodnika wykazały, że wynik średniej klasy jest około 334.</span><span class="sxs-lookup"><span data-stu-id="aabd8-194">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="aabd8-195">Aby utworzyć sekwencję `Students` których łączny wynik jest większa niż klasa średnią wraz z ich `Student ID`, można użyć typu anonimowego w `select` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="aabd8-195">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a><span data-ttu-id="aabd8-196">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="aabd8-196">Next Steps</span></span>  
 <span data-ttu-id="aabd8-197">Po zapoznaniu się z podstawowej aspektów pracy z kwerendy w języku C#, możesz przystąpić do odczytu dokumentacja i przykłady dla określonego typu dostawcy LINQ, które planuje się:</span><span class="sxs-lookup"><span data-stu-id="aabd8-197">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="aabd8-198">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="aabd8-198">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="aabd8-199">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="aabd8-199">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="aabd8-200">LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="aabd8-200">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="aabd8-201">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="aabd8-201">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="aabd8-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aabd8-202">See Also</span></span>  
 [<span data-ttu-id="aabd8-203">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aabd8-203">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="aabd8-204">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="aabd8-204">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="aabd8-205">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="aabd8-205">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
