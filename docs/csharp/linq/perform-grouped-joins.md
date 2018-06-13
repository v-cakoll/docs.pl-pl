---
title: Wykonanie sprzężeń grupowanych
description: Jak wykonanie sprzężeń grupowanych.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288180"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="99070-103">Wykonanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="99070-103">Perform grouped joins</span></span>

<span data-ttu-id="99070-104">Dołącz do grupy jest przydatne w przypadku tworzenie struktury hierarchicznej danych.</span><span class="sxs-lookup"><span data-stu-id="99070-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="99070-105">Każdy element z kolekcji pierwszy zestaw elementów skorelowane z druga kolekcja go pary.</span><span class="sxs-lookup"><span data-stu-id="99070-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="99070-106">Na przykład klasa lub tabela relacyjnej bazy danych o nazwie `Student` może zawierać dwóch pól: `Id` i `Name`.</span><span class="sxs-lookup"><span data-stu-id="99070-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="99070-107">Tabela drugiej klasy lub relacyjnej bazy danych o nazwie `Course` może zawierać dwóch pól: `StudentId` i `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="99070-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="99070-108">Grupowe z tych dwóch źródeł danych, na podstawie zgodności `Student.Id` i `Course.StudentId`, czy grupa Każdy `Student` z kolekcją `Course` obiektów (które mogą być puste).</span><span class="sxs-lookup"><span data-stu-id="99070-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99070-109">Każdy element pierwszej kolekcji znajduje się w zestawie wyników sprzężenia grupy niezależnie od tego, czy elementy skorelowane znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99070-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="99070-110">W przypadku których nie skorelowane znaleziono elementów sekwencji skorelowane elementów dla tego elementu jest pusta.</span><span class="sxs-lookup"><span data-stu-id="99070-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="99070-111">Selektor wynik w związku z tym ma dostęp do każdego elementu pierwszej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99070-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="99070-112">To różni się od selektora wyniku w sprzężeniu-group, którego nie można uzyskać dostęp do elementów z pierwszej kolekcji, która ma dopasowań w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="99070-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="99070-113">Pierwszym przykładzie w tym temacie przedstawiono sposób wykonania sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="99070-113">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="99070-114">Drugi przykład przedstawia sposób użycia sprzężenia grupy do tworzenia elementów XML.</span><span class="sxs-lookup"><span data-stu-id="99070-114">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99070-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="99070-115">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="99070-116">Przykład grupy</span><span class="sxs-lookup"><span data-stu-id="99070-116">Group join example</span></span>  
 <span data-ttu-id="99070-117">Poniższy przykład wykonuje sprzężenie grupy obiektów typu `Person` i `Pet` na podstawie `Person` dopasowania `Pet.Owner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="99070-117">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="99070-118">W odróżnieniu od sprzężenia-group dałby w efekcie dwa elementy dla każdego dopasowania, sprzężenia grupy tworzy tylko jeden obiekt wynikowy dla każdego elementu pierwszej kolekcji, czyli w tym przykładzie `Person` obiektu.</span><span class="sxs-lookup"><span data-stu-id="99070-118">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="99070-119">Odpowiednie elementy z drugiej kolekcji, które w tym przykładzie są `Pet` obiekty są zgrupowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99070-119">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="99070-120">Ponadto funkcja selektora wynik tworzy typu anonimowego dla każdego dopasowanie, które składa się z `Person.FirstName` i Kolekcja `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="99070-120">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="99070-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="99070-121">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="99070-122">Aby utworzyć przykład XML łączenie grupowe</span><span class="sxs-lookup"><span data-stu-id="99070-122">Group join to create XML example</span></span>  
 <span data-ttu-id="99070-123">Sprzężenia grupowane idealnie nadają się do tworzenia XML za pomocą LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="99070-123">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="99070-124">Poniższy przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że zamiast tworzyć typy anonimowe, funkcja selektora wynik tworzy elementów XML, które reprezentują przyłączonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="99070-124">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="99070-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99070-125">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="99070-126">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="99070-126">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="99070-127">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="99070-127">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="99070-128">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="99070-128">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
