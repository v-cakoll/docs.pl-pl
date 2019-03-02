---
title: Przekształcanie danych za pomocą LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: be488b262764480b519e291727a21830d7a18e8f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201433"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="c61a1-102">Przekształcanie danych za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="c61a1-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] <span data-ttu-id="c61a1-103">dotyczy nie tylko podczas pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="c61a1-103">is not only about retrieving data.</span></span> <span data-ttu-id="c61a1-104">Należy również zaawansowane narzędzie do przekształcania danych.</span><span class="sxs-lookup"><span data-stu-id="c61a1-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="c61a1-105">Za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, można użyć sekwencji źródłowej, jak dane wejściowe i zmodyfikuj go na wiele sposobów, aby utworzyć nową sekwencję danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c61a1-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="c61a1-106">Można zmodyfikować sekwencji bez modyfikowania samych elementów, sortowania i grupowania.</span><span class="sxs-lookup"><span data-stu-id="c61a1-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="c61a1-107">Ale być może z najbardziej zaawansowanych funkcji [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania jest możliwość tworzenia nowych typów.</span><span class="sxs-lookup"><span data-stu-id="c61a1-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="c61a1-108">Jest to realizowane w [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c61a1-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="c61a1-109">Na przykład należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c61a1-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="c61a1-110">Scala wiele sekwencji wejściowych sekwencja pojedynczego wyjścia, która ma nowego typu.</span><span class="sxs-lookup"><span data-stu-id="c61a1-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="c61a1-111">Utwórz sekwencje danych wyjściowych, której elementy składają się z tylko jednego lub kilku właściwości każdego elementu w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c61a1-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="c61a1-112">Utwórz sekwencje danych wyjściowych, której elementy składają się z wyniki operacji wykonywanych na danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="c61a1-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="c61a1-113">Tworzenie sekwencji wyjścia w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="c61a1-113">Create output sequences in a different format.</span></span> <span data-ttu-id="c61a1-114">Na przykład można przekształcać dane z wierszy SQL lub pliki tekstowe, w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="c61a1-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="c61a1-115">Są to tylko kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="c61a1-115">These are just several examples.</span></span> <span data-ttu-id="c61a1-116">Oczywiście można połączyć te przekształcenia na różne sposoby, w tym samym zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="c61a1-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="c61a1-117">Ponadto sekwencja wyjścia jedno zapytanie może służyć jako sekwencji wejściowych dla nowego zapytania.</span><span class="sxs-lookup"><span data-stu-id="c61a1-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="c61a1-118">Łączenie wielu danych wejściowych w jedną sekwencję wyjściową</span><span class="sxs-lookup"><span data-stu-id="c61a1-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="c61a1-119">Możesz użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie, aby utworzyć sekwencję wyjściową, który zawiera elementy z więcej niż jednej sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="c61a1-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="c61a1-120">Poniższy przykład pokazuje, jak połączyć dwie struktury danych w pamięci, ale te same zasady można zastosować do łączenia danych ze źródła XML lub SQL lub zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="c61a1-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="c61a1-121">Załóżmy następujące typy dwóch klas:</span><span class="sxs-lookup"><span data-stu-id="c61a1-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="c61a1-122">Poniższy kod przedstawia zapytanie:</span><span class="sxs-lookup"><span data-stu-id="c61a1-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="c61a1-123">Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md) i [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c61a1-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="c61a1-124">Wybranie podzestawu każdego elementu źródłowego</span><span class="sxs-lookup"><span data-stu-id="c61a1-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="c61a1-125">Istnieją dwa podstawowe sposoby, aby wybrać podzestawu każdego elementu w sekwencji źródłowej:</span><span class="sxs-lookup"><span data-stu-id="c61a1-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1.  <span data-ttu-id="c61a1-126">Aby wybrać tylko jeden element członkowski elementu źródłowego, należy użyć operacji kropka.</span><span class="sxs-lookup"><span data-stu-id="c61a1-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="c61a1-127">W poniższym przykładzie przyjęto założenie, że `Customer` obiekt zawiera kilka właściwości publicznej, w tym ciągu o nazwie `City`.</span><span class="sxs-lookup"><span data-stu-id="c61a1-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="c61a1-128">Po wykonaniu tego zapytania powoduje wygenerowanie danych wyjściowych sekwencją ciągów.</span><span class="sxs-lookup"><span data-stu-id="c61a1-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  <span data-ttu-id="c61a1-129">Aby utworzyć elementów, które zawierają więcej niż jedną właściwość z elementu źródłowego, należy użyć inicjatora obiektów, przy użyciu nazwanego obiektu lub typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="c61a1-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="c61a1-130">Poniższy przykład pokazuje użycie typu anonimowego do hermetyzacji dwie właściwości każdego z nich `Customer` elementu:</span><span class="sxs-lookup"><span data-stu-id="c61a1-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="c61a1-131">Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) i [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="c61a1-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="c61a1-132">Przekształcanie obiektów w pamięci do formatu XML</span><span class="sxs-lookup"><span data-stu-id="c61a1-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="c61a1-133">zapytania ułatwiają do przekształcania danych między strukturami danych w pamięci, baz danych SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawów danych i XML strumienie lub dokumenty.</span><span class="sxs-lookup"><span data-stu-id="c61a1-133">queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="c61a1-134">Poniższy przykład przekształca obiektów w strukturze danych w pamięci do elementów XML.</span><span class="sxs-lookup"><span data-stu-id="c61a1-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="c61a1-135">Kod generuje następujące dane wyjściowe XML:</span><span class="sxs-lookup"><span data-stu-id="c61a1-135">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="c61a1-136">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML w języku C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="c61a1-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="c61a1-137">Wykonywanie operacji na elementach źródłowych</span><span class="sxs-lookup"><span data-stu-id="c61a1-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="c61a1-138">Sekwencja wyjścia może nie zawierać żadnych elementów ani właściwości elementów z sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c61a1-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="c61a1-139">Dane wyjściowe mogą być sekwencja wartości, która jest obliczana przy użyciu elementów źródła jako argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="c61a1-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="c61a1-140">Następujące prostego zapytania, gdy jest wykonywany, generuje sekwencją ciągów, w których wartości reprezentują obliczenia oparte na sekwencję źródłową elementów typu `double`.</span><span class="sxs-lookup"><span data-stu-id="c61a1-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c61a1-141">Wywoływanie metod w wyrażeniach zapytań nie jest obsługiwana, jeśli zapytanie zostanie zamieniona na innej domeny.</span><span class="sxs-lookup"><span data-stu-id="c61a1-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="c61a1-142">Na przykład nie można wywołać zwykłych metodę języka C# w [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ponieważ program SQL Server ma Brak kontekstu dla niego.</span><span class="sxs-lookup"><span data-stu-id="c61a1-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="c61a1-143">Można jednak procedurom składowanym w mapie do metod i wywołać te.</span><span class="sxs-lookup"><span data-stu-id="c61a1-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="c61a1-144">Aby uzyskać więcej informacji, zobacz [procedur składowanych](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c61a1-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="c61a1-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c61a1-145">See also</span></span>

- [<span data-ttu-id="c61a1-146">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c61a1-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="c61a1-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c61a1-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="c61a1-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c61a1-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="c61a1-149">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c61a1-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [<span data-ttu-id="c61a1-150">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="c61a1-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="c61a1-151">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="c61a1-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
