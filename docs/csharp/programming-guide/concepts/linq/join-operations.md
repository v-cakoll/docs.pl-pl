---
title: Operacje Join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868008"
---
# <a name="join-operations-c"></a><span data-ttu-id="9eb69-102">Operacje join (C#)</span><span class="sxs-lookup"><span data-stu-id="9eb69-102">Join Operations (C#)</span></span>

<span data-ttu-id="9eb69-103">*Sprzężenie* dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="9eb69-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="9eb69-104">Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, których relacje między sobą nie mogą być bezpośrednio używane.</span><span class="sxs-lookup"><span data-stu-id="9eb69-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="9eb69-105">W programowaniu zorientowanym obiektowo może to oznaczać korelację między obiektami, które nie są modelowane, takimi jak odwrotny kierunek relacji jednokierunkowej.</span><span class="sxs-lookup"><span data-stu-id="9eb69-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="9eb69-106">Przykładem relacji jednokierunkowej jest Klasa klienta, która ma właściwość typu miasto, ale Klasa miasto nie ma właściwości, która jest kolekcją obiektów klienta.</span><span class="sxs-lookup"><span data-stu-id="9eb69-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="9eb69-107">Jeśli masz listę obiektów miast i chcesz znaleźć wszystkich klientów w poszczególnych miejscowościach, możesz użyć operacji JOIN, aby je znaleźć.</span><span class="sxs-lookup"><span data-stu-id="9eb69-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="9eb69-108">Metody join podane w środowisku LINQ Framework są <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="9eb69-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="9eb69-109">Metody te wykonują equijoins lub sprzężeń pasujących do dwóch źródeł danych na podstawie równości kluczy.</span><span class="sxs-lookup"><span data-stu-id="9eb69-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="9eb69-110">(W przypadku porównania język Transact-SQL obsługuje operatory sprzężenia inne niż "Equals", na przykład operator "Less"). W terminologii relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenie wewnętrzne, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="9eb69-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="9eb69-111">Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nie ma bezpośredniego odpowiednika w warunkach relacyjnej bazy danych, ale implementuje nadzbiór sprzężeń wewnętrznych i Lewe sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="9eb69-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="9eb69-112">Lewe sprzężenie zewnętrzne to sprzężenie zwracające każdy element pierwszego (lewego) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="9eb69-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="9eb69-113">Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które znajdują się w sprzężeniu wewnętrznym lub w lewym sprzężeniu zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="9eb69-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dwa nakładające się okręgi&#47;pokazujące wewnętrzną zewnętrzną.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="9eb69-115">Metody</span><span class="sxs-lookup"><span data-stu-id="9eb69-115">Methods</span></span>  
  
|<span data-ttu-id="9eb69-116">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="9eb69-116">Method Name</span></span>|<span data-ttu-id="9eb69-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9eb69-117">Description</span></span>|<span data-ttu-id="9eb69-118">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="9eb69-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="9eb69-119">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="9eb69-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="9eb69-120">Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i wyodrębnia pary wartości.</span><span class="sxs-lookup"><span data-stu-id="9eb69-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="9eb69-121">Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i grupuje wyniki dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="9eb69-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="9eb69-122">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="9eb69-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="9eb69-123">W poniższym przykładzie zastosowano klauzulę `join … in … on … equals …`, aby dołączyć dwie sekwencje w oparciu o określoną wartość:</span><span class="sxs-lookup"><span data-stu-id="9eb69-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="9eb69-124">W poniższym przykładzie zastosowano klauzulę `join … in … on … equals … into …`, aby przyłączyć dwie sekwencje w oparciu o określoną wartość i grupy wyników dopasowania dla każdego elementu:</span><span class="sxs-lookup"><span data-stu-id="9eb69-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="9eb69-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9eb69-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9eb69-126">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="9eb69-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="9eb69-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9eb69-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="9eb69-128">Formułowanie połączeń i zapytań między produktami</span><span class="sxs-lookup"><span data-stu-id="9eb69-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="9eb69-129">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="9eb69-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="9eb69-130">[Join przy użyciu kluczy złożonych](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="9eb69-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="9eb69-131">Jak dołączyć zawartość z niepodobnych plików (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9eb69-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="9eb69-132">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="9eb69-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="9eb69-133">Wykonywanie niestandardowych operacji łączenia</span><span class="sxs-lookup"><span data-stu-id="9eb69-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="9eb69-134">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="9eb69-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="9eb69-135">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="9eb69-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="9eb69-136">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="9eb69-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="9eb69-137">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9eb69-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
