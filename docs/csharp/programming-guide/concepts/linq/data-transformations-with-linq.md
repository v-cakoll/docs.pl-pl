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
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635954"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="3994f-102">Przekształcanie danych za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3994f-102">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="3994f-103">Zapytanie zintegrowane z językiem (LINQ) to nie tylko pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="3994f-103">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="3994f-104">Jest to również potężne narzędzie do przekształcania danych.</span><span class="sxs-lookup"><span data-stu-id="3994f-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="3994f-105">Za pomocą kwerendy LINQ, można użyć sekwencji źródłowej jako dane wejściowe i zmodyfikować go na wiele sposobów, aby utworzyć nową sekwencję danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3994f-105">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="3994f-106">Można zmodyfikować samą sekwencję bez modyfikowania samych elementów, sortując i grupując.</span><span class="sxs-lookup"><span data-stu-id="3994f-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="3994f-107">Ale być może najpotężniejszą cechą zapytań LINQ jest możliwość tworzenia nowych typów.</span><span class="sxs-lookup"><span data-stu-id="3994f-107">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="3994f-108">Odbywa się to w [select](../../../language-reference/keywords/select-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3994f-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="3994f-109">Na przykład można wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="3994f-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="3994f-110">Scalanie wielu sekwencji wejściowych w jedną sekwencję danych wyjściowych, która ma nowy typ.</span><span class="sxs-lookup"><span data-stu-id="3994f-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="3994f-111">Tworzenie sekwencji wyjściowych, których elementy składają się tylko z jednej lub kilku właściwości każdego elementu w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="3994f-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="3994f-112">Tworzenie sekwencji wyjściowych, których elementy składają się z wyników operacji wykonywanych na danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="3994f-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="3994f-113">Tworzenie sekwencji wyjściowych w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="3994f-113">Create output sequences in a different format.</span></span> <span data-ttu-id="3994f-114">Na przykład można przekształcić dane z wierszy SQL lub plików tekstowych w XML.</span><span class="sxs-lookup"><span data-stu-id="3994f-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="3994f-115">To tylko kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="3994f-115">These are just several examples.</span></span> <span data-ttu-id="3994f-116">Oczywiście te przekształcenia mogą być łączone na różne sposoby w tej samej kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="3994f-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="3994f-117">Ponadto sekwencji wyjściowej jednej kwerendy może służyć jako sekwencji wejściowej dla nowej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="3994f-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="3994f-118">Łączenie wielu danych wejściowych w jedną sekwencję wyjściową</span><span class="sxs-lookup"><span data-stu-id="3994f-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="3994f-119">Za pomocą kwerendy LINQ można utworzyć sekwencję danych wyjściowych, która zawiera elementy z więcej niż jednej sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="3994f-119">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="3994f-120">W poniższym przykładzie pokazano, jak połączyć dwie struktury danych w pamięci, ale te same zasady mogą być stosowane do łączenia danych ze źródeł XML lub SQL lub DataSet.</span><span class="sxs-lookup"><span data-stu-id="3994f-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="3994f-121">Załóżmy, że następujące dwa typy klas:</span><span class="sxs-lookup"><span data-stu-id="3994f-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="3994f-122">W poniższym przykładzie przedstawiono kwerendę:</span><span class="sxs-lookup"><span data-stu-id="3994f-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="3994f-123">Aby uzyskać więcej informacji, zobacz [join klauzuli](../../../language-reference/keywords/join-clause.md) i [wybierz klauzulę](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3994f-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="3994f-124">Wybranie podzestawu każdego elementu źródłowego</span><span class="sxs-lookup"><span data-stu-id="3994f-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="3994f-125">Istnieją dwa podstawowe sposoby wyboru podzbioru każdego elementu w sekwencji źródłowej:</span><span class="sxs-lookup"><span data-stu-id="3994f-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="3994f-126">Aby wybrać tylko jeden element członkowski elementu źródłowego, należy użyć operacji kropka.</span><span class="sxs-lookup"><span data-stu-id="3994f-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="3994f-127">W poniższym przykładzie załóżmy, że `Customer` obiekt zawiera `City`kilka właściwości publicznych, w tym ciąg o nazwie .</span><span class="sxs-lookup"><span data-stu-id="3994f-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="3994f-128">Po wykonaniu ta kwerenda spowoduje wygenerowanie sekwencji wyjściowej ciągów.</span><span class="sxs-lookup"><span data-stu-id="3994f-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="3994f-129">Aby utworzyć elementy, które zawierają więcej niż jedną właściwość z elementu źródłowego, można użyć inicjatora obiektu z nazwanym obiektem lub typem anonimowym.</span><span class="sxs-lookup"><span data-stu-id="3994f-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="3994f-130">W poniższym przykładzie przedstawiono użycie typu anonimowego do hermetyzacji dwóch właściwości z każdego `Customer` elementu:</span><span class="sxs-lookup"><span data-stu-id="3994f-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="3994f-131">Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md) oraz [typy anonimowe](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="3994f-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="3994f-132">Przekształcanie obiektów w pamięci do formatu XML</span><span class="sxs-lookup"><span data-stu-id="3994f-132">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="3994f-133">Kwerendy LINQ ułatwiają przekształcanie danych między strukturami danych w pamięci, bazami danych SQL, ADO.NET zestawami danych i strumieniami xml lub dokumentami.</span><span class="sxs-lookup"><span data-stu-id="3994f-133">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="3994f-134">Poniższy przykład przekształca obiekty w strukturze danych w pamięci do elementów XML.</span><span class="sxs-lookup"><span data-stu-id="3994f-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="3994f-135">Kod generuje następujące dane wyjściowe XML:</span><span class="sxs-lookup"><span data-stu-id="3994f-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="3994f-136">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML w języku C# (LINQ do XML)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="3994f-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="3994f-137">Wykonywanie operacji na elementach źródłowych</span><span class="sxs-lookup"><span data-stu-id="3994f-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="3994f-138">Sekwencja danych wyjściowych może nie zawierać żadnych elementów lub właściwości elementu z sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="3994f-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="3994f-139">Dane wyjściowe mogą być zamiast tego sekwencji wartości, które są obliczane przy użyciu elementów źródłowych jako argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="3994f-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="3994f-140">Następujące proste zapytanie, gdy jest wykonywana, generuje sekwencję ciągów, których wartości reprezentują `double`obliczenia oparte na sekwencji źródłowej elementów typu .</span><span class="sxs-lookup"><span data-stu-id="3994f-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3994f-141">Wywoływanie metod w wyrażeniach kwerendy nie jest obsługiwane, jeśli kwerenda zostanie przetłumaczona na inną domenę.</span><span class="sxs-lookup"><span data-stu-id="3994f-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="3994f-142">Na przykład nie można wywołać zwykłej [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] metody Języka C#, ponieważ program SQL Server nie ma dla niej kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3994f-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="3994f-143">Można jednak mapować procedury przechowywane do metod i wywołać te.</span><span class="sxs-lookup"><span data-stu-id="3994f-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="3994f-144">Aby uzyskać więcej informacji, zobacz [Procedury składowane](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3994f-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="3994f-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3994f-145">See also</span></span>

- [<span data-ttu-id="3994f-146">Zapytanie zintegrowane z językiem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3994f-146">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="3994f-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3994f-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="3994f-148">LINQ do DataSet</span><span class="sxs-lookup"><span data-stu-id="3994f-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="3994f-149">LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3994f-149">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="3994f-150">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="3994f-150">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="3994f-151">klauzula wyboru</span><span class="sxs-lookup"><span data-stu-id="3994f-151">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
