---
title: "Wykonanie sprzężeń grupowanych"
description: "Jak wykonanie sprzężeń grupowanych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 5e26473e19a5b6107d7aceea5e9829b48aa522b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="7575f-104">Wykonanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="7575f-104">Perform grouped joins</span></span>

<span data-ttu-id="7575f-105">Dołącz do grupy jest przydatne w przypadku tworzenie struktury hierarchicznej danych.</span><span class="sxs-lookup"><span data-stu-id="7575f-105">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="7575f-106">Każdy element z kolekcji pierwszy zestaw elementów skorelowane z druga kolekcja go pary.</span><span class="sxs-lookup"><span data-stu-id="7575f-106">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="7575f-107">Na przykład klasa lub tabela relacyjnej bazy danych o nazwie `Student` może zawierać dwóch pól: `Id` i `Name`.</span><span class="sxs-lookup"><span data-stu-id="7575f-107">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="7575f-108">Tabela drugiej klasy lub relacyjnej bazy danych o nazwie `Course` może zawierać dwóch pól: `StudentId` i `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="7575f-108">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="7575f-109">Grupowe z tych dwóch źródeł danych, na podstawie zgodności `Student.Id` i `Course.StudentId`, czy grupa Każdy `Student` z kolekcją `Course` obiektów (które mogą być puste).</span><span class="sxs-lookup"><span data-stu-id="7575f-109">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7575f-110">Każdy element pierwszej kolekcji znajduje się w zestawie wyników sprzężenia grupy niezależnie od tego, czy elementy skorelowane znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7575f-110">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="7575f-111">W przypadku których nie skorelowane znaleziono elementów sekwencji skorelowane elementów dla tego elementu jest pusta.</span><span class="sxs-lookup"><span data-stu-id="7575f-111">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="7575f-112">Selektor wynik w związku z tym ma dostęp do każdego elementu pierwszej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7575f-112">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="7575f-113">To różni się od selektora wyniku w sprzężeniu-group, którego nie można uzyskać dostęp do elementów z pierwszej kolekcji, która ma dopasowań w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="7575f-113">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="7575f-114">Pierwszym przykładzie w tym temacie przedstawiono sposób wykonania sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="7575f-114">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="7575f-115">Drugi przykład przedstawia sposób użycia sprzężenia grupy do tworzenia elementów XML.</span><span class="sxs-lookup"><span data-stu-id="7575f-115">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7575f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="7575f-116">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="7575f-117">Przykład grupy</span><span class="sxs-lookup"><span data-stu-id="7575f-117">Group join example</span></span>  
 <span data-ttu-id="7575f-118">Poniższy przykład wykonuje sprzężenie grupy obiektów typu `Person` i `Pet` na podstawie `Person` dopasowania `Pet.Owner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="7575f-118">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="7575f-119">W odróżnieniu od sprzężenia-group dałby w efekcie dwa elementy dla każdego dopasowania, sprzężenia grupy tworzy tylko jeden obiekt wynikowy dla każdego elementu pierwszej kolekcji, czyli w tym przykładzie `Person` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7575f-119">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="7575f-120">Odpowiednie elementy z drugiej kolekcji, które w tym przykładzie są `Pet` obiekty są zgrupowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7575f-120">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="7575f-121">Ponadto funkcja selektora wynik tworzy typu anonimowego dla każdego dopasowanie, które składa się z `Person.FirstName` i Kolekcja `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="7575f-121">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7575f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="7575f-122">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="7575f-123">Aby utworzyć przykład XML łączenie grupowe</span><span class="sxs-lookup"><span data-stu-id="7575f-123">Group join to create XML example</span></span>  
 <span data-ttu-id="7575f-124">Sprzężenia grupowane idealnie nadają się do tworzenia XML za pomocą LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="7575f-124">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="7575f-125">Poniższy przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że zamiast tworzyć typy anonimowe, funkcja selektora wynik tworzy elementów XML, które reprezentują przyłączonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="7575f-125">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="7575f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7575f-126">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="7575f-127">Wykonanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="7575f-127">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="7575f-128">Wykonanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="7575f-128">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="7575f-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7575f-129">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
