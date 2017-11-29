---
title: "Sprzęganie za pomocą kluczy złożonych"
description: "Jak dołączyć za pomocą kluczy złożonych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="2092f-104">Sprzęganie za pomocą kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="2092f-104">Join by using composite keys</span></span>

<span data-ttu-id="2092f-105">Ten przykład przedstawia sposób wykonywania operacji łączenia, w których chcesz użyć więcej niż jednego klucza do definiowania dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2092f-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="2092f-106">Jest to zrobić za pomocą klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="2092f-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="2092f-107">Można tworzyć złożone klucza jako typu anonimowego lub nazwanego typu z wartościami, które chcesz porównać.</span><span class="sxs-lookup"><span data-stu-id="2092f-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="2092f-108">Jeśli do zmiennej zapytania zostanie przekazany poza granicami metody, użyj typu nazwanego, który zastępuje <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> dla klucza.</span><span class="sxs-lookup"><span data-stu-id="2092f-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="2092f-109">Nazwy właściwości i kolejność, w którym występują, musi być takie same jak w przypadku każdego klucza.</span><span class="sxs-lookup"><span data-stu-id="2092f-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2092f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2092f-110">Example</span></span>  
 <span data-ttu-id="2092f-111">W poniższym przykładzie pokazano sposób użycia klucza złożonego do przyłączenia dane z trzech tabel:</span><span class="sxs-lookup"><span data-stu-id="2092f-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="2092f-112">Wnioskowanie o typie na klucze złożone zależy od nazw właściwości kluczy i kolejność, w którym występują.</span><span class="sxs-lookup"><span data-stu-id="2092f-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="2092f-113">Właściwości w sekwencji źródłowej nie ma tej samej nazwy, musisz przypisać nowe nazwy w kluczach.</span><span class="sxs-lookup"><span data-stu-id="2092f-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="2092f-114">Na przykład jeśli `Orders` tabeli i `OrderDetails` tabeli każdego użyć innej nazwy dla ich kolumn, można utworzyć kluczy złożonych, przypisując identycznych nazw typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="2092f-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="2092f-115">Klucze złożone mogą być również używane w `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2092f-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="2092f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2092f-116">See also</span></span>  
 [<span data-ttu-id="2092f-117">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="2092f-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="2092f-118">JOIN — klauzula</span><span class="sxs-lookup"><span data-stu-id="2092f-118">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="2092f-119">Group — klauzula</span><span class="sxs-lookup"><span data-stu-id="2092f-119">group clause</span></span>](../language-reference/keywords/group-clause.md)
