---
title: "Porady: łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="bc575-102">Porady: łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc575-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="bc575-103">Visual Basic zapewnia `Join` i `Group Join` zapytania klauzule umożliwiają łączenie zawartości wielu kolekcji na podstawie wartości typowych między kolekcjami.</span><span class="sxs-lookup"><span data-stu-id="bc575-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="bc575-104">Te wartości są określane jako *klucza* wartości.</span><span class="sxs-lookup"><span data-stu-id="bc575-104">These values are known as *key* values.</span></span> <span data-ttu-id="bc575-105">Rozpozna znasz koncepcji relacyjnej bazy danych dla deweloperów `Join` klauzuli jako INNER JOIN i `Group Join` klauzuli jako efektywnie LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="bc575-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="bc575-106">W przykładach w tym temacie przedstawiono kilka sposobów na łączenie danych za pomocą `Join` i `Group Join` klauzule zapytań.</span><span class="sxs-lookup"><span data-stu-id="bc575-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="bc575-107">Tworzenie projektu i Dodawanie przykładowych danych</span><span class="sxs-lookup"><span data-stu-id="bc575-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="bc575-108">Aby utworzyć projekt, który zawiera przykładowych danych i typów</span><span class="sxs-lookup"><span data-stu-id="bc575-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="bc575-109">Aby uruchomić przykłady w tym temacie, Otwórz program Visual Studio i dodać nowy projekt aplikacji konsoli języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bc575-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="bc575-110">Kliknij dwukrotnie plik Module1.vb utworzony przez program Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bc575-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="bc575-111">Przykłady w tym temacie `Person` i `Pet` typów i danych w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="bc575-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="bc575-112">Skopiuj ten kod do domyślnej `Module1` modułu utworzony przez program Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bc575-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="bc575-113">Przeprowadzanie sprzężenie wewnętrzne przy użyciu klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="bc575-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="bc575-114">SPRZĘŻENIA wewnętrznego łączy dane z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bc575-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="bc575-115">Uwzględniane są elementy, dla których określonej wartości klucza są zgodne.</span><span class="sxs-lookup"><span data-stu-id="bc575-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="bc575-116">Wszystkie elementy z jednej kolekcji, które nie ma pasującego elementu w innej kolekcji są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="bc575-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="bc575-117">W języku Visual Basic LINQ są dostępne dwie opcje umożliwiające wykonywanie sprzężenie wewnętrzne: sprzężenie niejawnych i jawnych sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="bc575-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="bc575-118">Sprzężenie niejawne określa kolekcje, które ma zostać umieszczony `From` klauzuli i identyfikuje dopasowania pól kluczy w `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc575-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="bc575-119">Visual Basic niejawnie łączy dwie kolekcje, w oparciu o określone pola klucza.</span><span class="sxs-lookup"><span data-stu-id="bc575-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="bc575-120">Można określić jawnego sprzężenia przy użyciu `Join` klauzuli umożliwia konkretnym klucz, do którego pola, aby użyć sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="bc575-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="bc575-121">W takim przypadku `Where` nadal można używać klauzuli mają być filtrowane wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="bc575-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="bc575-122">Do wykonania sprzężenia wewnętrznego przy użyciu klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="bc575-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="bc575-123">Dodaj następujący kod do `Module1` modułu w projekcie, aby wyświetlić przykłady obu jawne i niejawne sprzężenia wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="bc575-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="bc575-124">Przeprowadź lewe sprzężenie zewnętrzne, używając Group Join — klauzula</span><span class="sxs-lookup"><span data-stu-id="bc575-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="bc575-125">LEWE sprzężenie zewnętrzne zawiera wszystkie elementy z kolekcji po lewej stronie, a tylko do pasujących wartości z kolekcji po prawej stronie sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="bc575-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="bc575-126">Wszystkie elementy z kolekcji po prawej stronie sprzężenia, które nie ma pasującego elementu w kolekcji po lewej stronie są wykluczane z wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="bc575-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="bc575-127">`Group Join` Klauzuli wykonuje w efekcie LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="bc575-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="bc575-128">Różnica między co to jest często nazywana jest LEWE sprzężenie zewnętrzne, a co `Group Join` klauzula zwraca jest to, że `Group Join` klauzuli grupy wyników z kolekcji po prawej stronie sprzężenia dla każdego elementu w kolekcji po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc575-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="bc575-129">W relacyjnej bazie danych LEWE sprzężenie zewnętrzne zwraca wynik niezgrupowane powoduje każdego elementu w zapytaniu zawiera pasujących elementów z obu kolekcji sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="bc575-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="bc575-130">W takim przypadku elementów z kolekcji po lewej stronie sprzężenia są powtarzane dla każdego pasującego elementu z kolekcji po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc575-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="bc575-131">Pojawi się to wygląd po zakończeniu następnej procedury.</span><span class="sxs-lookup"><span data-stu-id="bc575-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="bc575-132">Można pobrać wyniki `Group Join` zapytania niezgrupowane wyniku rozszerzając zapytania do zwrócenia elementu dla każdego wyniku grupowanych zapytania.</span><span class="sxs-lookup"><span data-stu-id="bc575-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="bc575-133">W tym celu należy upewnić się, że zapytania na `DefaultIfEmpty` metody zgrupowaną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="bc575-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="bc575-134">Daje to pewność, że elementy z kolekcji po lewej stronie sprzężenia nadal są uwzględniane w wyniku zapytania, nawet jeśli ma zgodnych wyników z kolekcji po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc575-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="bc575-135">Kod można dodać do zapytania udzielać wynik domyślnie nie istnieje wartość zgodną z kolekcji po prawej stronie sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="bc575-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="bc575-136">Aby wykonać Left Outer Join przy użyciu klauzuli Join grupy</span><span class="sxs-lookup"><span data-stu-id="bc575-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="bc575-137">Dodaj następujący kod do `Module1` modułu w projekcie, aby wyświetlić przykłady grupowanych lewe sprzężenie zewnętrzne, jak i niezgrupowane lewe sprzężenie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="bc575-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="bc575-138">Przeprowadź sprzężenia, używając klucz złożony</span><span class="sxs-lookup"><span data-stu-id="bc575-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="bc575-139">Można użyć `And` — słowo kluczowe w `Join` lub `Group Join` klauzuli do identyfikowania wielu pól klucza do użycia podczas dopasowywania wartości z kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="bc575-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="bc575-140">`And` — Słowo kluczowe Określa, że wszystkie określone pola klucza musi być zgodna dla elementów, które ma zostać umieszczony.</span><span class="sxs-lookup"><span data-stu-id="bc575-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="bc575-141">Aby wykonać sprzężenia przy użyciu klucza złożonego</span><span class="sxs-lookup"><span data-stu-id="bc575-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="bc575-142">Dodaj następujący kod do `Module1` modułu w projekcie, aby wyświetlić przykłady sprzężenia, który używa klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="bc575-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="bc575-143">Kod uruchomienia</span><span class="sxs-lookup"><span data-stu-id="bc575-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="bc575-144">Aby dodać kod do uruchamiania przykładów</span><span class="sxs-lookup"><span data-stu-id="bc575-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="bc575-145">Zastąp `Sub Main` w `Module1` modułu w projekcie z następujący kod, aby uruchomić przykłady w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="bc575-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="bc575-146">Naciśnij klawisz F5, aby uruchomić przykłady.</span><span class="sxs-lookup"><span data-stu-id="bc575-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc575-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc575-147">See Also</span></span>  
 [<span data-ttu-id="bc575-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="bc575-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="bc575-149">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc575-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="bc575-150">JOIN — klauzula</span><span class="sxs-lookup"><span data-stu-id="bc575-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="bc575-151">Group Join — klauzula</span><span class="sxs-lookup"><span data-stu-id="bc575-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="bc575-152">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="bc575-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="bc575-153">Gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="bc575-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="bc575-154">Zapytania</span><span class="sxs-lookup"><span data-stu-id="bc575-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="bc575-155">Przekształcanie danych za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="bc575-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
