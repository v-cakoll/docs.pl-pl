---
title: Wykonanie lewych sprzężeń zewnętrznych
description: Jak wykonanie lewych sprzężeń zewnętrznych.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: aacab1ac6f4ab2c10b393cf0b2c578a13d9b9306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284280"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="9121d-103">Wykonanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="9121d-103">Perform left outer joins</span></span>
<span data-ttu-id="9121d-104">Lewe sprzężenie zewnętrzne jest sprzężenia, w której każdy element pierwsza kolekcja jest zwracany, niezależnie od tego, czy ma żadnych elementów skorelowane w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="9121d-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="9121d-105">LINQ umożliwia wykonywanie lewe sprzężenie zewnętrzne, wywołując <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody w wynikach sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="9121d-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9121d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9121d-106">Example</span></span>  
 <span data-ttu-id="9121d-107">W poniższym przykładzie pokazano sposób użycia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody w wynikach sprzężenia grupy, aby wykonać lewe sprzężenie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="9121d-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="9121d-108">Pierwszym etapem produkujących lewe sprzężenie zewnętrzne dwóch kolekcji ma wykonywać sprzężenie wewnętrzne za pomocą sprzężenia grupy.</span><span class="sxs-lookup"><span data-stu-id="9121d-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="9121d-109">(Zobacz [wykonanie sprzężeń wewnętrznych](perform-inner-joins.md) opis tego procesu.) W tym przykładzie lista `Person` obiektów jest wewnętrzny przyłączonych do listy `Pet` obiektów na podstawie `Person` obiektu, który odpowiada `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="9121d-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="9121d-110">Drugim krokiem jest uwzględnienie każdego elementu pierwszej kolekcji (lewych) w zestawie nawet wtedy, gdy ten element nie ma żadnych wyników w kolekcja prawa wyników.</span><span class="sxs-lookup"><span data-stu-id="9121d-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="9121d-111">Jest to osiągane przez wywołanie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na poszczególnych sekwencji zgodnych elementów z grupy sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="9121d-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="9121d-112">W tym przykładzie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> zostanie wywołany dla poszczególnych sekwencji zgodnych `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="9121d-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="9121d-113">Metoda zwraca kolekcję, która zawiera pojedynczą, wartość domyślną, jeśli sekwencja zgodnych `Pet` obiektów jest pusta dla żadnego `Person` obiektu, zapewniając, że każdy `Person` obiektu jest reprezentowana w zbiorze wyników.</span><span class="sxs-lookup"><span data-stu-id="9121d-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9121d-114">Wartość domyślna dla typu odwołania to `null`; w związku z tym przykładzie wyszukuje odwołanie o wartości null przed uzyskaniem dostępu do każdego elementu `Pet` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9121d-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="9121d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9121d-115">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="9121d-116">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="9121d-116">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="9121d-117">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="9121d-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="9121d-118">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9121d-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
