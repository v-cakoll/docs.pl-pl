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
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="4238b-102">Wskazówki: pisanie zapytań w C# (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4238b-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="4238b-103">W tym instruktażeniu przedstawiono funkcje języka Języka C#, które są używane do pisania wyrażeń zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="4238b-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="4238b-104">Utwórz projekt C#</span><span class="sxs-lookup"><span data-stu-id="4238b-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4238b-105">Poniższe instrukcje są dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4238b-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="4238b-106">Jeśli używasz innego środowiska programistycznego, utwórz projekt konsoli z odwołaniem `using` do pliku <xref:System.Linq?displayProperty=nameWithType> System.Core.dll i dyrektywy dla obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="4238b-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="4238b-107">Aby utworzyć projekt w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4238b-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="4238b-108">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4238b-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="4238b-109">Na pasku menu wybierz pozycję **Plik**, **Nowy**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="4238b-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="4238b-110">Zostanie otwarte okno dialogowe **Nowy projekt.**</span><span class="sxs-lookup"><span data-stu-id="4238b-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="4238b-111">Rozwiń **pozycję Zainstalowane**, rozwiń **rozwiń pozycję Szablony**, rozwiń węzeł **Visual C#,** a następnie wybierz pozycję **Aplikacja konsoli**.</span><span class="sxs-lookup"><span data-stu-id="4238b-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="4238b-112">W polu tekstowym **Nazwa** wprowadź inną nazwę lub zaakceptuj nazwę domyślną, a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="4238b-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="4238b-113">Nowy projekt pojawi się w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4238b-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="4238b-114">Należy zauważyć, że projekt ma odwołanie do System.Core.dll i dyrektywy `using` dla obszaru <xref:System.Linq?displayProperty=nameWithType> nazw.</span><span class="sxs-lookup"><span data-stu-id="4238b-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="4238b-115">Utwórz źródło danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="4238b-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="4238b-116">Źródłem danych dla zapytań jest `Student` prosta lista obiektów.</span><span class="sxs-lookup"><span data-stu-id="4238b-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="4238b-117">Każdy `Student` rekord ma imię, nazwisko i tablicę liczb całkowitych, która reprezentuje ich wyniki testów w klasie.</span><span class="sxs-lookup"><span data-stu-id="4238b-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="4238b-118">Skopiuj ten kod do projektu.</span><span class="sxs-lookup"><span data-stu-id="4238b-118">Copy this code into your project.</span></span> <span data-ttu-id="4238b-119">Należy zwrócić uwagę na następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="4238b-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="4238b-120">Klasa `Student` składa się z właściwości implementowanych automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4238b-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="4238b-121">Każdy uczeń na liście jest inicjowany za pomocą inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="4238b-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="4238b-122">Sama lista jest inicjowana za pomocą inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4238b-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="4238b-123">Ta cała struktura danych zostanie zainicjowana i uprzedzona bez jawnych wywołań do dowolnego konstruktora lub jawnego dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="4238b-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="4238b-124">Aby uzyskać więcej informacji na temat tych nowych funkcji, zobacz [Właściwości autoimplementowane](../../classes-and-structs/auto-implemented-properties.md) oraz [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="4238b-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="4238b-125">Aby dodać źródło danych</span><span class="sxs-lookup"><span data-stu-id="4238b-125">To add the data source</span></span>  
  
- <span data-ttu-id="4238b-126">Dodaj `Student` klasę i iizapoczątkowaną `Program` listę uczniów do klasy w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4238b-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="4238b-127">Aby dodać nowego studenta do listy studentów</span><span class="sxs-lookup"><span data-stu-id="4238b-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="4238b-128">Dodaj nowy `Student` do `Students` listy i użyj nazwy i wyników testów do wyboru.</span><span class="sxs-lookup"><span data-stu-id="4238b-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="4238b-129">Spróbuj wpisać wszystkie nowe informacje o uczniach, aby lepiej nauczyć się składni inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="4238b-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="4238b-130">Utwórz zapytanie</span><span class="sxs-lookup"><span data-stu-id="4238b-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="4238b-131">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="4238b-131">To create a simple query</span></span>  
  
- <span data-ttu-id="4238b-132">W `Main` metodzie aplikacji utwórz prostą kwerendę, która po wykonaniu stworzy listę wszystkich uczniów, których wynik w pierwszym teście był większy niż 90.</span><span class="sxs-lookup"><span data-stu-id="4238b-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="4238b-133">Należy zauważyć, `Student` że ponieważ cały obiekt jest zaznaczony, typem kwerendy jest `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="4238b-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="4238b-134">Chociaż kod może również używać niejawnego pisania przy użyciu [var](../../../language-reference/keywords/var.md) słowa kluczowego, jawne wpisywanie jest używany do wyraźnego zilustrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="4238b-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="4238b-135">(Aby uzyskać `var`więcej informacji na temat , zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="4238b-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="4238b-136">Należy również zauważyć, że zmienna zakresu `student`kwerendy, `Student` służy jako odwołanie do każdego w źródle, zapewniając dostęp do elementów członkowskich dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4238b-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="4238b-137">Wykonanie zapytania</span><span class="sxs-lookup"><span data-stu-id="4238b-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="4238b-138">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="4238b-138">To execute the query</span></span>  
  
1. <span data-ttu-id="4238b-139">Teraz napisz `foreach` pętlę, która spowoduje wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="4238b-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="4238b-140">Należy zwrócić uwagę na następujące informacje dotyczące kodu:</span><span class="sxs-lookup"><span data-stu-id="4238b-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="4238b-141">Każdy element w zwróconej sekwencji jest dostępny za `foreach` pośrednictwem zmiennej iteracji w pętli.</span><span class="sxs-lookup"><span data-stu-id="4238b-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="4238b-142">Typ tej zmiennej `Student`jest , a typ zmiennej `IEnumerable<Student>`kwerendy jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="4238b-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="4238b-143">Po dodaniu tego kodu skompiluj i uruchom aplikację, aby wyświetlić wyniki w oknie **Konsoli.**</span><span class="sxs-lookup"><span data-stu-id="4238b-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="4238b-144">Aby dodać inny warunek filtru</span><span class="sxs-lookup"><span data-stu-id="4238b-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="4238b-145">Można połączyć wiele warunków logicznych w klauzuli `where` w celu dalszego uściślania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="4238b-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="4238b-146">Poniższy kod dodaje warunek, tak aby kwerenda zwraca tych uczniów, których pierwszy wynik był ponad 90 i których ostatni wynik był mniejszy niż 80.</span><span class="sxs-lookup"><span data-stu-id="4238b-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="4238b-147">Klauzula `where` powinna przypominać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="4238b-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="4238b-148">Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4238b-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="4238b-149">Zmodyfikuj zapytanie</span><span class="sxs-lookup"><span data-stu-id="4238b-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="4238b-150">Aby uporządkować wyniki</span><span class="sxs-lookup"><span data-stu-id="4238b-150">To order the results</span></span>  
  
1. <span data-ttu-id="4238b-151">Łatwiej będzie skanować wyniki, jeśli są one w jakiejś kolejności.</span><span class="sxs-lookup"><span data-stu-id="4238b-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="4238b-152">Zwracaną sekwencję można zamówić za pomocą dowolnego dostępnego pola w elementach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="4238b-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="4238b-153">Na przykład następująca `orderby` klauzula porządkuje wyniki w kolejności alfabetycznej od A do Z zgodnie z nazwiskiem każdego ucznia.</span><span class="sxs-lookup"><span data-stu-id="4238b-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="4238b-154">Dodaj następującą `orderby` klauzulę do `where` zapytania, zaraz `select` po instrukcji i przed instrukcją:</span><span class="sxs-lookup"><span data-stu-id="4238b-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="4238b-155">Teraz zmień `orderby` klauzulę tak, aby uporządkowała wyniki w odwrotnej kolejności zgodnie z wynikiem w pierwszym teście, od najwyższego wyniku do najniższego wyniku.</span><span class="sxs-lookup"><span data-stu-id="4238b-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="4238b-156">Zmień `WriteLine` ciąg formatu, aby zobaczyć wyniki:</span><span class="sxs-lookup"><span data-stu-id="4238b-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="4238b-157">Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4238b-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="4238b-158">Aby pogrupować wyniki</span><span class="sxs-lookup"><span data-stu-id="4238b-158">To group the results</span></span>  
  
1. <span data-ttu-id="4238b-159">Grupowanie jest zaawansowaną możliwością w wyrażeniach kwerend.</span><span class="sxs-lookup"><span data-stu-id="4238b-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="4238b-160">Kwerenda z klauzulą grupy tworzy sekwencję grup, a `Key` każda grupa sama zawiera sekwencję i sekwencję składającą się ze wszystkich członków tej grupy.</span><span class="sxs-lookup"><span data-stu-id="4238b-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="4238b-161">Następujące nowe zapytania grupują uczniów przy użyciu pierwszej litery ich nazwiska jako klucza.</span><span class="sxs-lookup"><span data-stu-id="4238b-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="4238b-162">Należy zauważyć, że typ kwerendy został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="4238b-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="4238b-163">Teraz tworzy sekwencję grup, które `char` mają typ jako klucz `Student` i sekwencję obiektów.</span><span class="sxs-lookup"><span data-stu-id="4238b-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="4238b-164">Ponieważ typ kwerendy uległ zmianie, następujący `foreach` kod zmienia również pętlę wykonywania:</span><span class="sxs-lookup"><span data-stu-id="4238b-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="4238b-165">Uruchom aplikację i wyświetl wyniki w oknie **Konsoli.**</span><span class="sxs-lookup"><span data-stu-id="4238b-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="4238b-166">Aby uzyskać więcej informacji, zobacz [klauzulę group](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4238b-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="4238b-167">Aby jawnie wpisać zmienną lokalną</span><span class="sxs-lookup"><span data-stu-id="4238b-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="4238b-168">Jawne `IEnumerables` kodowanie `IGroupings` może szybko stać się nużące.</span><span class="sxs-lookup"><span data-stu-id="4238b-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="4238b-169">Możesz napisać to samo `foreach` zapytanie i pętli `var`znacznie wygodniej za pomocą .</span><span class="sxs-lookup"><span data-stu-id="4238b-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="4238b-170">Słowo `var` kluczowe nie zmienia typów obiektów; po prostu instruuje kompilator, aby wywnioskować typy.</span><span class="sxs-lookup"><span data-stu-id="4238b-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="4238b-171">Zmień typ `studentQuery` i zmienną `group` iteracji i `var` ponownie uruchom kwerendę.</span><span class="sxs-lookup"><span data-stu-id="4238b-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="4238b-172">Należy zauważyć, `foreach` że w pętli wewnętrznej zmienna iteracji jest nadal wpisywana jako `Student`, a kwerenda działa tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="4238b-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="4238b-173">Zmień `s` zmienną iteracji i `var` uruchom kwerendę ponownie.</span><span class="sxs-lookup"><span data-stu-id="4238b-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="4238b-174">Widzisz, że masz dokładnie takie same wyniki.</span><span class="sxs-lookup"><span data-stu-id="4238b-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="4238b-175">Aby uzyskać więcej informacji na temat [var](../../../language-reference/keywords/var.md), zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="4238b-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="4238b-176">Aby uporządkować grupy według kluczy wartości</span><span class="sxs-lookup"><span data-stu-id="4238b-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="4238b-177">Po uruchomieniu poprzedniej kwerendy można zauważyć, że grupy nie są w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="4238b-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="4238b-178">Aby to zmienić, należy `orderby` podać `group` klauzulę po klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4238b-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="4238b-179">Ale aby `orderby` użyć klauzuli, najpierw potrzebujesz identyfikatora, który służy jako `group` odwołanie do grup utworzonych przez klauzulę.</span><span class="sxs-lookup"><span data-stu-id="4238b-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="4238b-180">Identyfikator należy podać przy `into` użyciu słowa kluczowego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4238b-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="4238b-181">Po uruchomieniu tej kwerendy zobaczysz, że grupy są teraz sortowane w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="4238b-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="4238b-182">Aby wprowadzić identyfikator przy użyciu let</span><span class="sxs-lookup"><span data-stu-id="4238b-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="4238b-183">Za pomocą `let` słowa kluczowego można wprowadzić identyfikator dla dowolnego wyniku wyrażenia w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="4238b-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="4238b-184">Ten identyfikator może być wygodą, jak w poniższym przykładzie lub może zwiększyć wydajność, przechowując wyniki wyrażenia, dzięki czemu nie muszą być obliczane wiele razy.</span><span class="sxs-lookup"><span data-stu-id="4238b-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="4238b-185">Aby uzyskać więcej informacji, zobacz [klauzulę let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4238b-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="4238b-186">Aby użyć metody składni w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="4238b-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="4238b-187">Zgodnie z opisem w [składni kwerendy i składni metody w LINQ,](./query-syntax-and-method-syntax-in-linq.md)niektóre operacje kwerendy mogą być wyrażone tylko przy użyciu składni metody.</span><span class="sxs-lookup"><span data-stu-id="4238b-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="4238b-188">Poniższy kod oblicza całkowity wynik `Student` dla każdego w sekwencji `Average()` źródłowej, a następnie wywołuje metodę na wyniki tej kwerendy, aby obliczyć średni wynik klasy.</span><span class="sxs-lookup"><span data-stu-id="4238b-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="4238b-189">Aby przekształcić lub zaprojektować w klauzuli wyboru</span><span class="sxs-lookup"><span data-stu-id="4238b-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="4238b-190">Jest bardzo często dla kwerendy do tworzenia sekwencji, których elementy różnią się od elementów w sekwencji źródłowych.</span><span class="sxs-lookup"><span data-stu-id="4238b-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="4238b-191">Usuń lub skomentuj poprzednią pętlę zapytania i wykonywania i zastąp ją następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4238b-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="4238b-192">Należy zauważyć, że kwerenda zwraca `Students`sekwencję ciągów (nie `foreach` ), a ten fakt jest odzwierciedlony w pętli.</span><span class="sxs-lookup"><span data-stu-id="4238b-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="4238b-193">Kod wcześniej w tym instruktażu wskazał, że średni wynik klasy wynosi około 334.</span><span class="sxs-lookup"><span data-stu-id="4238b-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="4238b-194">Aby utworzyć `Students` sekwencję, której całkowity wynik jest większy `Student ID`niż średnia klasa, wraz `select` z ich , można użyć typu anonimowego w instrukcji:</span><span class="sxs-lookup"><span data-stu-id="4238b-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="4238b-195">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4238b-195">Next Steps</span></span>  
 <span data-ttu-id="4238b-196">Po zapoznaniu się z podstawowymi aspektami pracy z zapytaniami w języku C#, można przystąpić do zapoznania się z dokumentacją i przykładami dla określonego typu dostawcy LINQ, który Cię interesuje:</span><span class="sxs-lookup"><span data-stu-id="4238b-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="4238b-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4238b-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="4238b-198">LINQ do DataSet</span><span class="sxs-lookup"><span data-stu-id="4238b-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="4238b-199">LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4238b-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="4238b-200">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="4238b-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="4238b-201">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4238b-201">See also</span></span>

- [<span data-ttu-id="4238b-202">Zapytanie zintegrowane z językiem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4238b-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="4238b-203">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="4238b-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
