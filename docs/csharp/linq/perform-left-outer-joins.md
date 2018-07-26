---
title: Wykonanie lewych sprzężeń zewnętrznych (LINQ w C#)
description: Dowiedz się, jak wykonanie lewych sprzężeń zewnętrznych za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 3da144e6e3293d3a4084f7a99f77aec199f7a267
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403856"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="20cb0-103">Wykonanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="20cb0-103">Perform left outer joins</span></span>

<span data-ttu-id="20cb0-104">Lewe sprzężenie zewnętrzne jest elementem sprzężenia, w której każdy element pierwsza kolekcja jest zwracana, niezależnie od tego, czy ma żadnych elementów skorelowane w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20cb0-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="20cb0-105">LINQ umożliwia wykonywanie lewe sprzężenie zewnętrzne, wywołując <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody na wynikach sprzężenie grupy.</span><span class="sxs-lookup"><span data-stu-id="20cb0-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="20cb0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="20cb0-106">Example</span></span>

<span data-ttu-id="20cb0-107">Poniższy przykład pokazuje sposób użycia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody na wynikach sprzężenie grupy do wykonania lewego sprzężenia zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="20cb0-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="20cb0-108">Pierwszym krokiem podczas produkcji lewe sprzężenie zewnętrzne dwóch kolekcji jest wykonywanie sprzężenia wewnętrznego przy użyciu sprzężenie grupy.</span><span class="sxs-lookup"><span data-stu-id="20cb0-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="20cb0-109">(Zobacz [wykonanie sprzężeń wewnętrznych](perform-inner-joins.md) objaśnienia dotyczące tego procesu.) W tym przykładzie lista `Person` obiektów jest wewnętrzny przyłączone do listy `Pet` na podstawie obiektów `Person` obiektu, który odpowiada `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="20cb0-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="20cb0-110">Drugim krokiem jest uwzględnienie każdego elementu pierwszej kolekcji (po lewej stronie) w zestawie, nawet jeśli ten element nie ma żadnych dopasowań w prawo kolekcji wyników.</span><span class="sxs-lookup"><span data-stu-id="20cb0-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="20cb0-111">Jest to realizowane przez wywołanie metody <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na każdej sekwencji zgodnych elementów z sprzężenie grupy.</span><span class="sxs-lookup"><span data-stu-id="20cb0-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="20cb0-112">W tym przykładzie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> jest wywoływana w każdej sekwencji zgodnych `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="20cb0-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="20cb0-113">Metoda zwraca kolekcję, która zawiera pojedynczą, wartość domyślna, jeśli sekwencja zgodnych `Pet` obiektów jest pusta dla żadnego `Person` obiektu, zapewniając, że każdy `Person` obiekt jest reprezentowany w kolekcji wynik.</span><span class="sxs-lookup"><span data-stu-id="20cb0-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="20cb0-114">Wartość domyślna dla typu odwołania to `null`; w związku z tym, przykład sprawdza, czy odwołania zerowego przed uzyskaniem dostępu do każdego elementu `Pet` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="20cb0-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="20cb0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20cb0-115">See also</span></span>

<xref:System.Linq.Enumerable.Join%2A>  
<xref:System.Linq.Enumerable.GroupJoin%2A>  
[<span data-ttu-id="20cb0-116">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="20cb0-116">Perform inner joins</span></span>](perform-inner-joins.md)  
[<span data-ttu-id="20cb0-117">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="20cb0-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
[<span data-ttu-id="20cb0-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="20cb0-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  