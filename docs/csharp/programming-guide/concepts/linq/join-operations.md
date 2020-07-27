---
title: :::no-loc(Join):::Operacje (C#)
description: Sprzężenie dwóch źródeł danych kojarzy obiekty z obiektami, które współużytkują atrybut w różnych źródłach danych. Dowiedz się więcej o metodach dołączania w strukturze LINQ w języku C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165694"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="ffe0f-104">:::no-loc(Join):::Operacje (C#)</span><span class="sxs-lookup"><span data-stu-id="ffe0f-104">:::no-loc(Join)::: Operations (C#)</span></span>

<span data-ttu-id="ffe0f-105">*Sprzężenie* dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="ffe0f-106">:::no-loc(Join):::w przypadku zapytań, które są przeznaczone dla źródeł danych, których relacje między sobą nie mogą być przestrzegane bezpośrednio, jest ważna operacja.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-106">:::no-loc(Join):::ing is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="ffe0f-107">W programowaniu zorientowanym obiektowo może to oznaczać korelację między obiektami, które nie są modelowane, takimi jak odwrotny kierunek relacji jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="ffe0f-108">Przykładem relacji jednokierunkowej jest Klasa klienta, która ma właściwość typu miasto, ale Klasa miasto nie ma właściwości, która jest kolekcją obiektów klienta.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="ffe0f-109">Jeśli masz listę obiektów miast i chcesz znaleźć wszystkich klientów w poszczególnych miejscowościach, możesz użyć operacji JOIN, aby je znaleźć.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="ffe0f-110">Metody join podane w środowisku LINQ Framework to <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> i <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> .</span><span class="sxs-lookup"><span data-stu-id="ffe0f-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> and <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>.</span></span> <span data-ttu-id="ffe0f-111">Metody te wykonują equijoins lub sprzężeń pasujących do dwóch źródeł danych na podstawie równości kluczy.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="ffe0f-112">(W przypadku porównania język Transact-SQL obsługuje operatory sprzężenia inne niż "Equals", na przykład operator "Less"). W terminologii relacyjnej bazy danych <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implementuje sprzężenie wewnętrzne, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="ffe0f-113"><xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>Metoda nie ma bezpośredniego odpowiednika w warunkach relacyjnych baz danych, ale implementuje nadzbiór sprzężeń wewnętrznych i Lewe sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-113">The <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="ffe0f-114">Lewe sprzężenie zewnętrzne to sprzężenie zwracające każdy element pierwszego (lewego) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="ffe0f-115">Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które znajdują się w sprzężeniu wewnętrznym lub w lewym sprzężeniu zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dwa nakładające się okręgi przedstawiające wewnętrzne&#47;zewnętrzne.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="ffe0f-117">Metody</span><span class="sxs-lookup"><span data-stu-id="ffe0f-117">Methods</span></span>  
  
|<span data-ttu-id="ffe0f-118">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="ffe0f-118">Method Name</span></span>|<span data-ttu-id="ffe0f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ffe0f-119">Description</span></span>|<span data-ttu-id="ffe0f-120">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="ffe0f-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="ffe0f-121">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ffe0f-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|<span data-ttu-id="ffe0f-122">:::no-loc(Join):::s dwie sekwencje oparte na funkcjach selektora kluczy i wyodrębniających pary wartości.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-122">:::no-loc(Join):::s two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|<span data-ttu-id="ffe0f-123">:::no-loc(Join):::s dwie sekwencje oparte na funkcjach selektora kluczy i grupuje wyniki dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="ffe0f-123">:::no-loc(Join):::s two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ffe0f-124">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="ffe0f-124">Query expression syntax examples</span></span>
  
### :::no-loc(Join):::  
  
<span data-ttu-id="ffe0f-125">W poniższym przykładzie zastosowano `join … in … on … equals …` klauzulę, aby dołączyć dwie sekwencje w oparciu o określoną wartość:</span><span class="sxs-lookup"><span data-stu-id="ffe0f-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

<span data-ttu-id="ffe0f-126">W poniższym przykładzie zastosowano `join … in … on … equals … into …` klauzulę, aby przyłączyć dwie sekwencje w oparciu o określoną wartość i grupy wyników dopasowania dla każdego elementu:</span><span class="sxs-lookup"><span data-stu-id="ffe0f-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a><span data-ttu-id="ffe0f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffe0f-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ffe0f-128">Standardowe operatory zapytań — Omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="ffe0f-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ffe0f-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="ffe0f-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="ffe0f-130">Formułowanie :::no-loc(Join)::: zapytań i innych produktów</span><span class="sxs-lookup"><span data-stu-id="ffe0f-130">Formulate :::no-loc(Join):::s and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="ffe0f-131">Klauzula join</span><span class="sxs-lookup"><span data-stu-id="ffe0f-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="ffe0f-132">:::no-loc(Join):::za pomocą kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="ffe0f-132">:::no-loc(Join)::: by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="ffe0f-133">Jak dołączyć zawartość z niepodobnych plików (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ffe0f-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="ffe0f-134">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="ffe0f-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="ffe0f-135">Wykonywanie niestandardowych operacji sprzęgania</span><span class="sxs-lookup"><span data-stu-id="ffe0f-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="ffe0f-136">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="ffe0f-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="ffe0f-137">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="ffe0f-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="ffe0f-138">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="ffe0f-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="ffe0f-139">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ffe0f-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
