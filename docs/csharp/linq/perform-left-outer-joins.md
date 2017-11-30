---
title: "Wykonanie lewych sprzężeń zewnętrznych"
description: "Jak wykonanie lewych sprzężeń zewnętrznych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 0c28c85bf933a411403aefcb91801d28fe1c268e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="a3c94-104">Wykonanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="a3c94-104">Perform left outer joins</span></span>
<span data-ttu-id="a3c94-105">Lewe sprzężenie zewnętrzne jest sprzężenia, w której każdy element pierwsza kolekcja jest zwracany, niezależnie od tego, czy ma żadnych elementów skorelowane w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="a3c94-105">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="a3c94-106">LINQ umożliwia wykonywanie lewe sprzężenie zewnętrzne, wywołując <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody w wynikach sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="a3c94-106">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3c94-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3c94-107">Example</span></span>  
 <span data-ttu-id="a3c94-108">W poniższym przykładzie pokazano sposób użycia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody w wynikach sprzężenia grupy, aby wykonać lewe sprzężenie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="a3c94-108">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="a3c94-109">Pierwszym etapem produkujących lewe sprzężenie zewnętrzne dwóch kolekcji ma wykonywać sprzężenie wewnętrzne za pomocą sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="a3c94-109">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="a3c94-110">(Zobacz [wykonanie sprzężeń wewnętrznych](perform-inner-joins.md) opis tego procesu.) W tym przykładzie lista `Person` obiektów jest wewnętrzny przyłączonych do listy `Pet` obiektów na podstawie `Person` obiektu, który odpowiada `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="a3c94-110">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="a3c94-111">Drugim krokiem jest uwzględnienie każdego elementu pierwszej kolekcji (lewych) w zestawie nawet wtedy, gdy ten element nie ma żadnych wyników w kolekcja prawa wyników.</span><span class="sxs-lookup"><span data-stu-id="a3c94-111">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="a3c94-112">Jest to osiągane przez wywołanie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na poszczególnych sekwencji zgodnych elementów z grupy sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="a3c94-112">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="a3c94-113">W tym przykładzie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> zostanie wywołany dla poszczególnych sekwencji zgodnych `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="a3c94-113">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="a3c94-114">Metoda zwraca kolekcję, która zawiera pojedynczą, wartość domyślną, jeśli sekwencja zgodnych `Pet` obiektów jest pusta dla żadnego `Person` obiektu, zapewniając, że każdy `Person` obiektu jest reprezentowana w zbiorze wyników.</span><span class="sxs-lookup"><span data-stu-id="a3c94-114">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3c94-115">Wartość domyślna dla typu odwołania to `null`; w związku z tym przykładzie wyszukuje odwołanie o wartości null przed uzyskaniem dostępu do każdego elementu `Pet` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3c94-115">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="a3c94-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3c94-116">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="a3c94-117">Wykonanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="a3c94-117">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="a3c94-118">Wykonanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="a3c94-118">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="a3c94-119">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="a3c94-119">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
