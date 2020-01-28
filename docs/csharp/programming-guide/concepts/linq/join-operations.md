---
title: Operacje Join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: d4bf9fe76238d8824c5255df8910c1000503dcdf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746959"
---
# <a name="opno-locjoin-operations-c"></a><span data-ttu-id="f90b6-102">Operacje [!OP.NO-LOC(Join)] (C#)</span><span class="sxs-lookup"><span data-stu-id="f90b6-102">[!OP.NO-LOC(Join)] Operations (C#)</span></span>
<span data-ttu-id="f90b6-103">*Sprzężenie* dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="f90b6-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="f90b6-104">Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, których relacje między sobą nie mogą być bezpośrednio używane.</span><span class="sxs-lookup"><span data-stu-id="f90b6-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="f90b6-105">W programowaniu zorientowanym obiektowo może to oznaczać korelację między obiektami, które nie są modelowane, takimi jak odwrotny kierunek relacji jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="f90b6-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="f90b6-106">Przykładem relacji jednokierunkowej jest Klasa klienta, która ma właściwość typu miasto, ale Klasa miasto nie ma właściwości, która jest kolekcją obiektów klienta.</span><span class="sxs-lookup"><span data-stu-id="f90b6-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="f90b6-107">Jeśli masz listę obiektów miast i chcesz znaleźć wszystkich klientów w poszczególnych miejscowościach, możesz użyć operacji JOIN, aby je znaleźć.</span><span class="sxs-lookup"><span data-stu-id="f90b6-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="f90b6-108">Metody join podane w środowisku LINQ Framework są <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> i <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>.</span><span class="sxs-lookup"><span data-stu-id="f90b6-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> and <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>.</span></span> <span data-ttu-id="f90b6-109">Metody te wykonują equijoins lub sprzężeń pasujących do dwóch źródeł danych na podstawie równości kluczy.</span><span class="sxs-lookup"><span data-stu-id="f90b6-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="f90b6-110">(W przypadku porównania język Transact-SQL obsługuje operatory sprzężenia inne niż "Equals", na przykład operator "Less"). W terminologii relacyjnej bazy danych <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implementuje sprzężenie wewnętrzne, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="f90b6-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="f90b6-111">Metoda <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> nie ma bezpośredniego odpowiednika w warunkach relacyjnej bazy danych, ale implementuje nadzbiór sprzężeń wewnętrznych i Lewe sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="f90b6-111">The <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="f90b6-112">Lewe sprzężenie zewnętrzne to sprzężenie zwracające każdy element pierwszego (lewego) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="f90b6-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="f90b6-113">Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które znajdują się w sprzężeniu wewnętrznym lub w lewym sprzężeniu zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="f90b6-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dwa nakładające się okręgi&#47;pokazujące wewnętrzną zewnętrzną.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="f90b6-115">Metody</span><span class="sxs-lookup"><span data-stu-id="f90b6-115">Methods</span></span>  
  
|<span data-ttu-id="f90b6-116">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="f90b6-116">Method Name</span></span>|<span data-ttu-id="f90b6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f90b6-117">Description</span></span>|<span data-ttu-id="f90b6-118">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="f90b6-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="f90b6-119">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="f90b6-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="f90b6-120">Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i wyodrębnia pary wartości.</span><span class="sxs-lookup"><span data-stu-id="f90b6-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="f90b6-121">Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i grupuje wyniki dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="f90b6-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f90b6-122">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="f90b6-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="f90b6-123">W poniższym przykładzie zastosowano klauzulę `join … in … on … equals …`, aby dołączyć dwie sekwencje w oparciu o określoną wartość:</span><span class="sxs-lookup"><span data-stu-id="f90b6-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="f90b6-124">W poniższym przykładzie zastosowano klauzulę `join … in … on … equals … into …`, aby przyłączyć dwie sekwencje w oparciu o określoną wartość i grupy wyników dopasowania dla każdego elementu:</span><span class="sxs-lookup"><span data-stu-id="f90b6-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="f90b6-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f90b6-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f90b6-126">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="f90b6-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="f90b6-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="f90b6-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="f90b6-128">Formułowanie połączeń i zapytań między produktami</span><span class="sxs-lookup"><span data-stu-id="f90b6-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="f90b6-129">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="f90b6-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="f90b6-130">[Join przy użyciu kluczy złożonych](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="f90b6-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="f90b6-131">Jak dołączyć zawartość z niepodobnych plików (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f90b6-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="f90b6-132">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="f90b6-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="f90b6-133">Wykonywanie niestandardowych operacji łączenia</span><span class="sxs-lookup"><span data-stu-id="f90b6-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="f90b6-134">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="f90b6-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="f90b6-135">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="f90b6-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="f90b6-136">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="f90b6-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="f90b6-137">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f90b6-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
