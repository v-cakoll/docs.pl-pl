---
title: Wykonywanie sprzężeń lewych zewnętrznych (LINQ w języku C)Perform left outer joins (LINQ in C#)
description: Dowiedz się, jak wykonywać sprzężenia zewnętrzne lewe przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688582"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="0aafd-103">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="0aafd-103">Perform left outer joins</span></span>

<span data-ttu-id="0aafd-104">Sprzężenie zewnętrzne lewe jest sprzężenie, w którym każdy element pierwszej kolekcji jest zwracany, niezależnie od tego, czy ma żadnych skorelowanych elementów w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0aafd-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="0aafd-105">Linq służy do wykonywania sprzężenia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> zewnętrznego w lewo, wywołując metodę na wyniki sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="0aafd-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="0aafd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0aafd-106">Example</span></span>

<span data-ttu-id="0aafd-107">W poniższym przykładzie pokazano, jak używać <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody na wyniki sprzężenia grupy do wykonywania sprzężenia zewnętrznego lewej.</span><span class="sxs-lookup"><span data-stu-id="0aafd-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="0aafd-108">Pierwszym krokiem w produkcji lewego sprzężenia zewnętrznego dwóch kolekcji jest wykonanie sprzężenia wewnętrznego przy użyciu sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="0aafd-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="0aafd-109">(Zobacz [Wykonywanie sprzężeń wewnętrznych,](perform-inner-joins.md) aby uzyskać wyjaśnienie tego procesu). W tym przykładzie lista `Person` obiektów jest wewnętrznie przyłączona do listy `Pet` obiektów na podstawie `Person` obiektu, który pasuje `Pet.Owner`do .</span><span class="sxs-lookup"><span data-stu-id="0aafd-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="0aafd-110">Drugim krokiem jest uwzględnienie każdego elementu pierwszej (po lewej) kolekcji w zestawie wyników, nawet jeśli ten element nie ma żadnych dopasowań w prawej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0aafd-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="0aafd-111">Jest to realizowane <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> przez wywołanie każdej sekwencji pasujących elementów z grupy sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="0aafd-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="0aafd-112">W tym <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> przykładzie jest wywoływana `Pet` na każdej sekwencji pasujących obiektów.</span><span class="sxs-lookup"><span data-stu-id="0aafd-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="0aafd-113">Metoda zwraca kolekcję, która zawiera pojedynczą, wartość `Pet` domyślną, `Person` jeśli sekwencja pasujących `Person` obiektów jest pusta dla dowolnego obiektu, zapewniając w ten sposób, że każdy obiekt jest reprezentowany w kolekcji wyników.</span><span class="sxs-lookup"><span data-stu-id="0aafd-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="0aafd-114">Wartością domyślną dla `null`typu odwołania jest; w związku z tym przykład sprawdza dla odwołania `Pet` null przed uzyskując dostęp do każdego elementu każdej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0aafd-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="0aafd-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0aafd-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="0aafd-116">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="0aafd-116">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="0aafd-117">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="0aafd-117">Perform grouped joins</span></span>](perform-grouped-joins.md)
- [<span data-ttu-id="0aafd-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="0aafd-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
