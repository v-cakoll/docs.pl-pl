---
title: Sprzęganie za pomocą kluczy złożonych
description: Jak dołączyć za pomocą kluczy złożonych.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: e40f4d147886c07913c761bb5df83ee34d23eaba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271217"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="7abf2-103">Sprzęganie za pomocą kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="7abf2-103">Join by using composite keys</span></span>

<span data-ttu-id="7abf2-104">Ten przykład przedstawia sposób wykonywania operacji łączenia, w których chcesz użyć więcej niż jednego klucza do definiowania dopasowania.</span><span class="sxs-lookup"><span data-stu-id="7abf2-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="7abf2-105">Jest to zrobić za pomocą klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="7abf2-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="7abf2-106">Można tworzyć złożone klucza jako typu anonimowego lub nazwanego typu z wartościami, które chcesz porównać.</span><span class="sxs-lookup"><span data-stu-id="7abf2-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="7abf2-107">Jeśli do zmiennej zapytania zostanie przekazany poza granicami metody, użyj typu nazwanego, który zastępuje <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> dla klucza.</span><span class="sxs-lookup"><span data-stu-id="7abf2-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="7abf2-108">Nazwy właściwości i kolejność, w którym występują, musi być takie same jak w przypadku każdego klucza.</span><span class="sxs-lookup"><span data-stu-id="7abf2-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7abf2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7abf2-109">Example</span></span>  
 <span data-ttu-id="7abf2-110">W poniższym przykładzie pokazano sposób użycia klucza złożonego do przyłączenia dane z trzech tabel:</span><span class="sxs-lookup"><span data-stu-id="7abf2-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="7abf2-111">Wnioskowanie o typie na klucze złożone zależy od nazw właściwości kluczy i kolejność, w którym występują.</span><span class="sxs-lookup"><span data-stu-id="7abf2-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="7abf2-112">Właściwości w sekwencji źródłowej nie ma tej samej nazwy, musisz przypisać nowe nazwy w kluczach.</span><span class="sxs-lookup"><span data-stu-id="7abf2-112">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="7abf2-113">Na przykład jeśli `Orders` tabeli i `OrderDetails` tabeli każdego użyć innej nazwy dla ich kolumn, można utworzyć kluczy złożonych, przypisując identycznych nazw typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="7abf2-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="7abf2-114">Klucze złożone mogą być również używane w `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7abf2-114">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="7abf2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7abf2-115">See also</span></span>  
 [<span data-ttu-id="7abf2-116">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="7abf2-116">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="7abf2-117">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="7abf2-117">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="7abf2-118">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="7abf2-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
