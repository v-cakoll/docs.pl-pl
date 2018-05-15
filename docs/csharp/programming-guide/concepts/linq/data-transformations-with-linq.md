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
ms.openlocfilehash: c165f78c53cec0417d39320580b812ff01fef68b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="236d4-102">Przekształcanie danych za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="236d4-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]<span data-ttu-id="236d4-103"> dotyczy nie tylko pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="236d4-103"> is not only about retrieving data.</span></span> <span data-ttu-id="236d4-104">Istnieje również zaawansowane narzędzia do przekształcania danych.</span><span class="sxs-lookup"><span data-stu-id="236d4-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="236d4-105">Za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy, można użyć sekwencji źródłowej, jak dane wejściowe, a następnie zmodyfikować go na wiele sposobów, aby utworzyć nową sekwencję danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="236d4-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="236d4-106">Można zmodyfikować sekwencji bez modyfikowania ze sobą elementy sortowania i grupowania.</span><span class="sxs-lookup"><span data-stu-id="236d4-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="236d4-107">Być może z najbardziej zaawansowanych funkcji, ale [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania jest możliwość tworzenia nowych typów.</span><span class="sxs-lookup"><span data-stu-id="236d4-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="236d4-108">Jest to realizowane w [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="236d4-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="236d4-109">Na przykład można wykonywać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="236d4-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="236d4-110">Scala wiele sekwencji wejściowych sekwencji pojedynczym wyjściowym zawierającej nowego typu.</span><span class="sxs-lookup"><span data-stu-id="236d4-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="236d4-111">Tworzenie sekwencji danych wyjściowych, której elementy składają się z tylko jednego lub kilku właściwości każdego elementu w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="236d4-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="236d4-112">Tworzenie sekwencji dane wyjściowe, której elementy zawierać wyniki operacji wykonywanych na źródle danych.</span><span class="sxs-lookup"><span data-stu-id="236d4-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="236d4-113">Tworzenie sekwencji dane wyjściowe w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="236d4-113">Create output sequences in a different format.</span></span> <span data-ttu-id="236d4-114">Na przykład można przekształcać dane z plików tekstowych lub wierszy SQL w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="236d4-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="236d4-115">Są to tylko kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="236d4-115">These are just several examples.</span></span> <span data-ttu-id="236d4-116">Oczywiście przekształcenia te można łączyć w różny sposób w jednym zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="236d4-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="236d4-117">Ponadto sekwencję wyjściową jednego zapytania może służyć jako sekwencja wejściowa dla nowego zapytania.</span><span class="sxs-lookup"><span data-stu-id="236d4-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="236d4-118">Łączenie wielu danych wejściowych w jedną sekwencję wyjściową</span><span class="sxs-lookup"><span data-stu-id="236d4-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="236d4-119">Można użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie w celu utworzenia sekwencji danych wyjściowych, która zawiera elementy z więcej niż jeden sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="236d4-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="236d4-120">Poniższy przykład pokazuje, jak połączyć dwóch struktury danych w pamięci, ale te same zasady mogą być stosowane do łączenia danych ze źródeł XML lub SQL lub zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="236d4-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="236d4-121">Załóżmy następujące dwie klasy:</span><span class="sxs-lookup"><span data-stu-id="236d4-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 <span data-ttu-id="236d4-122">W poniższym przykładzie przedstawiono zapytania:</span><span class="sxs-lookup"><span data-stu-id="236d4-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 <span data-ttu-id="236d4-123">Aby uzyskać więcej informacji, zobacz [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md) i [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="236d4-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="236d4-124">Wybranie podzestawu każdego elementu źródłowego</span><span class="sxs-lookup"><span data-stu-id="236d4-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="236d4-125">Istnieją dwa podstawowe sposoby wybierać podzestaw każdego elementu w sekwencji źródłowej:</span><span class="sxs-lookup"><span data-stu-id="236d4-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1.  <span data-ttu-id="236d4-126">Aby wybrać tylko jeden element członkowski elementu źródłowego, za pomocą operacji kropki.</span><span class="sxs-lookup"><span data-stu-id="236d4-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="236d4-127">W poniższym przykładzie przyjęto założenie, że `Customer` obiekt zawiera kilka właściwości publicznej, w tym ciągu o nazwie `City`.</span><span class="sxs-lookup"><span data-stu-id="236d4-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="236d4-128">Podczas wykonywania tego zapytania spowoduje utworzenie danych wyjściowych sekwencję ciągów.</span><span class="sxs-lookup"><span data-stu-id="236d4-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  <span data-ttu-id="236d4-129">Do tworzenia elementów, które zawierają więcej niż jedną właściwość z elementu źródłowego, używając inicjatora obiektów nazwanego obiektu lub typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="236d4-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="236d4-130">W poniższym przykładzie przedstawiono użycie typu anonimowego w celu hermetyzacji dwie właściwości z każdej `Customer` elementu:</span><span class="sxs-lookup"><span data-stu-id="236d4-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="236d4-131">Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) i [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="236d4-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="236d4-132">Przekształcanie obiektów w pamięci do formatu XML</span><span class="sxs-lookup"><span data-stu-id="236d4-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="236d4-133"> zapytania ułatwiają przekształcania danych między struktury danych w pamięci, baz danych, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawów danych i XML strumieni lub dokumenty.</span><span class="sxs-lookup"><span data-stu-id="236d4-133"> queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="236d4-134">Poniższy przykład do elementów XML przy użyciu obiektów w strukturze danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="236d4-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 <span data-ttu-id="236d4-135">Kod tworzy następujące dane wyjściowe XML:</span><span class="sxs-lookup"><span data-stu-id="236d4-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="236d4-136">Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML w języku C# (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="236d4-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="236d4-137">Wykonywanie operacji na elementach źródłowych</span><span class="sxs-lookup"><span data-stu-id="236d4-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="236d4-138">Sekwencja wyjścia nie może zawierać wszystkie elementy lub właściwości elementu w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="236d4-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="236d4-139">Dane wyjściowe mogą być sekwencję wartości, która jest obliczana przy użyciu elementów źródła jako argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="236d4-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="236d4-140">Następujące zapytanie proste, po jego wykonaniu danych wyjściowych sekwencję ciągów, którego wartości reprezentują obliczenia na podstawie sekwencji źródło elementów typu `double`.</span><span class="sxs-lookup"><span data-stu-id="236d4-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="236d4-141">Wywołanie metody w wyrażeniach zapytań nie jest obsługiwane, jeśli zapytanie zostanie zamieniona na innej domeny.</span><span class="sxs-lookup"><span data-stu-id="236d4-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="236d4-142">Na przykład nie można wywołać zwykłej metody C# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ponieważ program SQL Server ma Brak kontekstu dla niego.</span><span class="sxs-lookup"><span data-stu-id="236d4-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="236d4-143">Można jednak mapowanie procedur składowanych do metody i te wywołania.</span><span class="sxs-lookup"><span data-stu-id="236d4-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="236d4-144">Aby uzyskać więcej informacji, zobacz [procedur składowanych](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="236d4-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="236d4-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="236d4-145">See Also</span></span>  
 [<span data-ttu-id="236d4-146">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="236d4-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="236d4-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="236d4-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="236d4-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="236d4-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
 [<span data-ttu-id="236d4-149">LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="236d4-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [<span data-ttu-id="236d4-150">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="236d4-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="236d4-151">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="236d4-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
