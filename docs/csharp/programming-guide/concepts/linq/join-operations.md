---
title: JoinOperacje (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868008"
---
# <a name="join-operations-c"></a><span data-ttu-id="3e505-102">Dołącz do operacji (C#)</span><span class="sxs-lookup"><span data-stu-id="3e505-102">Join Operations (C#)</span></span>

<span data-ttu-id="3e505-103">*Sprzężenie* dwóch źródeł danych jest skojarzenie m.in.</span><span class="sxs-lookup"><span data-stu-id="3e505-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="3e505-104">Łączenie jest ważną operacją w kwerendach docelowych źródeł danych, których relacje ze sobą nie mogą być śledzone bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="3e505-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="3e505-105">W programowaniu obiektowym może to oznaczać korelację między obiektami, które nie są modelowane, takie jak kierunek wstecz relacji jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="3e505-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="3e505-106">Przykładem relacji jednokierunkowej jest Customer klasy, która ma właściwość typu Miasto, ale City klasa nie ma właściwości, która jest kolekcją Customer obiektów.</span><span class="sxs-lookup"><span data-stu-id="3e505-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="3e505-107">Jeśli masz listę obiektów Miasta i chcesz znaleźć wszystkich klientów w każdym mieście, możesz użyć operacji sprzężenia, aby je znaleźć.</span><span class="sxs-lookup"><span data-stu-id="3e505-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="3e505-108">Metody sprzężenia podane w ramach <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>LINQ są i .</span><span class="sxs-lookup"><span data-stu-id="3e505-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="3e505-109">Metody te wykonują równoprzylega lub łączy, które pasują do dwóch źródeł danych na podstawie równości ich kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e505-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="3e505-110">(Dla porównania Transact-SQL obsługuje operatory sprzężenia inne niż "equals", na przykład operator "mniej niż").) W kategoriach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenia wewnętrznego, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="3e505-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="3e505-111">Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nie ma bezpośredniego odpowiednika w kategoriach relacyjnej bazy danych, ale implementuje nadzbiór sprzężeń wewnętrznych i lewej sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="3e505-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="3e505-112">Sprzężenie zewnętrzne lewe jest sprzężeniem, które zwraca każdy element pierwszego (po lewej) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="3e505-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="3e505-113">Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które są zawarte w sprzężenia wewnętrznym lub lewym sprzężenie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="3e505-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dwa nakładające się okręgi przedstawiające wewnętrzne&#47;zewnętrzne.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="3e505-115">Metody</span><span class="sxs-lookup"><span data-stu-id="3e505-115">Methods</span></span>  
  
|<span data-ttu-id="3e505-116">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3e505-116">Method Name</span></span>|<span data-ttu-id="3e505-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3e505-117">Description</span></span>|<span data-ttu-id="3e505-118">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="3e505-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="3e505-119">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="3e505-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="3e505-120">Łączy dwie sekwencje na podstawie funkcji selektora kluczy i wyodrębnia pary wartości.</span><span class="sxs-lookup"><span data-stu-id="3e505-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="3e505-121">Łączy dwie sekwencje na podstawie funkcji selektora kluczy i grupuje wynikowe dopasowania dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="3e505-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3e505-122">Przykłady składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="3e505-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="3e505-123">W poniższym `join … in … on … equals …` przykładzie użyto klauzuli do przyłączenia dwóch sekwencji na podstawie określonej wartości:</span><span class="sxs-lookup"><span data-stu-id="3e505-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="3e505-124">W poniższym `join … in … on … equals … into …` przykładzie użyto klauzuli do przyłączenia się do dwóch sekwencji na podstawie określonej wartości i grupuje wynikowe dopasowania dla każdego elementu:</span><span class="sxs-lookup"><span data-stu-id="3e505-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="3e505-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e505-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3e505-126">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="3e505-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="3e505-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="3e505-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="3e505-128">Formułowanie połączeń i zapytań między produktami</span><span class="sxs-lookup"><span data-stu-id="3e505-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="3e505-129">klauzula sprzężenia</span><span class="sxs-lookup"><span data-stu-id="3e505-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="3e505-130">[Joinza pomocą klawiszy kompozytowych](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="3e505-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="3e505-131">Jak dołączyć zawartość z różnych plików (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e505-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="3e505-132">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="3e505-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="3e505-133">Wykonywanie niestandardowych operacji sprzęgania</span><span class="sxs-lookup"><span data-stu-id="3e505-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="3e505-134">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="3e505-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="3e505-135">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="3e505-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="3e505-136">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="3e505-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="3e505-137">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e505-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
