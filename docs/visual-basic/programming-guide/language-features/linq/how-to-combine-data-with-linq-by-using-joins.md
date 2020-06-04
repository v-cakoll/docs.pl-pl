---
title: 'Instrukcje: łączenie danych w LINQ za pomocą sprzężeń'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: de8c4ec3ab8a0f2335c034231c661380420fd31b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405007"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="d9952-102">Porady: łączenie danych w LINQ za pomocą sprzężeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9952-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="d9952-103">Visual Basic zawiera `Join` `Group Join` klauzule i zapytania umożliwiające połączenie zawartości wielu kolekcji na podstawie wspólnych wartości między kolekcjami.</span><span class="sxs-lookup"><span data-stu-id="d9952-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="d9952-104">Te wartości są znane jako wartości *klucza* .</span><span class="sxs-lookup"><span data-stu-id="d9952-104">These values are known as *key* values.</span></span> <span data-ttu-id="d9952-105">Deweloperzy znający koncepcje relacyjnych baz danych będą rozpoznawać `Join` klauzulę jako sprzężenie wewnętrzne i `Group Join` klauzulę jako, jak skutecznie, lewe sprzężenie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="d9952-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="d9952-106">Przykłady w tym temacie przedstawiają kilka sposobów łączenia danych przy użyciu `Join` `Group Join` klauzul zapytania i.</span><span class="sxs-lookup"><span data-stu-id="d9952-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="d9952-107">Tworzenie projektu i Dodawanie przykładowych danych</span><span class="sxs-lookup"><span data-stu-id="d9952-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="d9952-108">Aby utworzyć projekt zawierający przykładowe dane i typy</span><span class="sxs-lookup"><span data-stu-id="d9952-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="d9952-109">Aby uruchomić przykłady w tym temacie, Otwórz program Visual Studio i Dodaj nowy projekt aplikacji konsolowej Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9952-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="d9952-110">Kliknij dwukrotnie plik Module1. vb utworzony przez Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9952-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="d9952-111">Przykłady w tym temacie używają typów i `Person` `Pet` danych z następującego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="d9952-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="d9952-112">Skopiuj ten kod do domyślnego `Module1` modułu utworzonego przez Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9952-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="d9952-113">Wykonywanie sprzężenia wewnętrznego przy użyciu klauzuli join</span><span class="sxs-lookup"><span data-stu-id="d9952-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="d9952-114">SPRZĘŻENIe wewnętrzne łączy dane z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d9952-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="d9952-115">Elementy, dla których są uwzględniane określone wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="d9952-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="d9952-116">Wszystkie elementy z kolekcji, które nie mają pasującego elementu w innej kolekcji, są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="d9952-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="d9952-117">W Visual Basic LINQ oferuje dwie opcje wykonywania SPRZĘŻENIa wewnętrznego: niejawne sprzężenie i jawne sprzężenie.</span><span class="sxs-lookup"><span data-stu-id="d9952-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="d9952-118">Niejawne sprzężenie określa kolekcje, które mają być sprzężone w `From` klauzuli i identyfikuje pola klucza pasujące w `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d9952-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="d9952-119">Visual Basic niejawnie sprzęga dwie kolekcje na podstawie określonych pól kluczy.</span><span class="sxs-lookup"><span data-stu-id="d9952-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="d9952-120">Możesz określić jawne sprzężenie przy użyciu klauzuli, `Join` gdy chcesz, aby były specyficzne dla pól klucza do użycia w sprzężeniu.</span><span class="sxs-lookup"><span data-stu-id="d9952-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="d9952-121">W takim przypadku `Where` klauzula może nadal służyć do filtrowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="d9952-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="d9952-122">Aby wykonać sprzężenie wewnętrzne przy użyciu klauzuli join</span><span class="sxs-lookup"><span data-stu-id="d9952-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="d9952-123">Dodaj następujący kod do `Module1` modułu w projekcie, aby zobaczyć przykłady zarówno niejawnego, jak i jawnego sprzężenia wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d9952-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="d9952-124">Wykonaj lewe sprzężenie zewnętrzne przy użyciu klauzuli Group Join</span><span class="sxs-lookup"><span data-stu-id="d9952-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="d9952-125">LEWE SPRZĘŻENIe zewnętrzne obejmuje wszystkie elementy z kolekcji po lewej stronie sprzężenia i tylko pasujące wartości z kolekcji po prawej stronie sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="d9952-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="d9952-126">Wszystkie elementy z kolekcji po prawej stronie sprzężenia, które nie mają pasującego elementu w kolekcji po lewej stronie, są wykluczone z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="d9952-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="d9952-127">`Group Join`Klauzula wykonuje w efekcie lewe sprzężenie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="d9952-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="d9952-128">Różnica między tym, co jest zwykle znane jako lewe SPRZĘŻENIe zewnętrzne i co `Group Join` zwraca klauzula, jest to, że `Group Join` klauzula grupuje wyniki z kolekcji po prawej stronie sprzężenia dla każdego elementu w kolekcji po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="d9952-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="d9952-129">W relacyjnej bazie danych lewe SPRZĘŻENIe zewnętrzne zwraca niezgrupowane wyniki, w których każdy element w wyniku zapytania zawiera pasujące elementy z obu kolekcji w sprzężeniu.</span><span class="sxs-lookup"><span data-stu-id="d9952-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="d9952-130">W tym przypadku elementy z kolekcji po lewej stronie sprzężenia są powtórzone dla każdego pasującego elementu z kolekcji po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="d9952-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="d9952-131">Po zakończeniu następnej procedury zobaczysz, jak to wygląda.</span><span class="sxs-lookup"><span data-stu-id="d9952-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="d9952-132">Wyniki zapytania można pobrać `Group Join` jako niepogrupowany wynik, rozszerzając zapytanie w celu zwrócenia elementu dla każdego pogrupowanego wyniku kwerendy.</span><span class="sxs-lookup"><span data-stu-id="d9952-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="d9952-133">Aby to osiągnąć, należy się upewnić, że zawarto zapytania dotyczące `DefaultIfEmpty` metody zgrupowanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d9952-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="d9952-134">Dzięki temu elementy z kolekcji po lewej stronie sprzężenia są nadal uwzględniane w wynikach zapytania, nawet jeśli nie mają pasujących wyników z kolekcji po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="d9952-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="d9952-135">Możesz dodać kod do zapytania, aby podać domyślną wartość wynikową, gdy nie ma pasującej wartości z kolekcji po prawej stronie sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="d9952-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="d9952-136">Aby wykonać lewe sprzężenie zewnętrzne przy użyciu klauzuli Group Join</span><span class="sxs-lookup"><span data-stu-id="d9952-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="d9952-137">Dodaj następujący kod do `Module1` modułu w projekcie, aby zobaczyć przykłady pogrupowanego lewego sprzężenia zewnętrznego i niezgrupowanego sprzężenia zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d9952-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="d9952-138">Wykonywanie sprzężenia przy użyciu klucza złożonego</span><span class="sxs-lookup"><span data-stu-id="d9952-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="d9952-139">Możesz użyć `And` słowa kluczowego w `Join` klauzuli OR, `Group Join` Aby zidentyfikować wiele pól klucza do użycia podczas dopasowywania wartości z kolekcji, które są sprzężone.</span><span class="sxs-lookup"><span data-stu-id="d9952-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="d9952-140">`And`Słowo kluczowe Określa, że wszystkie określone pola kluczy muszą być zgodne dla elementów do przyłączenia.</span><span class="sxs-lookup"><span data-stu-id="d9952-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="d9952-141">Aby wykonać sprzężenie przy użyciu klucza złożonego</span><span class="sxs-lookup"><span data-stu-id="d9952-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="d9952-142">Dodaj następujący kod do `Module1` modułu w projekcie, aby zobaczyć przykłady sprzężenia korzystającego z klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="d9952-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="d9952-143">Uruchom kod</span><span class="sxs-lookup"><span data-stu-id="d9952-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="d9952-144">Aby dodać kod do uruchamiania przykładów</span><span class="sxs-lookup"><span data-stu-id="d9952-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="d9952-145">Zastąp `Sub Main` w `Module1` module w projekcie następującym kodem, aby uruchomić przykłady w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d9952-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="d9952-146">Naciśnij klawisz F5, aby uruchomić przykłady.</span><span class="sxs-lookup"><span data-stu-id="d9952-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9952-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9952-147">See also</span></span>

- [<span data-ttu-id="d9952-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="d9952-148">LINQ</span></span>](index.md)
- [<span data-ttu-id="d9952-149">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9952-149">Introduction to LINQ in Visual Basic</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="d9952-150">Klauzula join</span><span class="sxs-lookup"><span data-stu-id="d9952-150">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="d9952-151">Group Join. klauzula</span><span class="sxs-lookup"><span data-stu-id="d9952-151">Group Join Clause</span></span>](../../../language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="d9952-152">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="d9952-152">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="d9952-153">Klauzula WHERE</span><span class="sxs-lookup"><span data-stu-id="d9952-153">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="d9952-154">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d9952-154">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="d9952-155">Przekształcanie danych za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d9952-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
