---
title: Sprzęganie za pomocą kluczy złożonych (LINQ w C#)
description: Dowiedz się, jak sprzęgać za pomocą kluczy złożonych w składniku LINQ.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: ae37d03f996f0b0cc184a86663f16d62e6c29c69
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081563"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="062c6-103">Sprzęganie za pomocą kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="062c6-103">Join by using composite keys</span></span>

<span data-ttu-id="062c6-104">Ten przykład przedstawia sposób wykonywania operacji łączenia, w których chcesz użyć więcej niż jednego klucza do zdefiniowania dopasowania.</span><span class="sxs-lookup"><span data-stu-id="062c6-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="062c6-105">Jest to realizowane przy użyciu klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="062c6-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="062c6-106">Można tworzyć złożonego klucza jako typu anonimowego lub nazwane wpisane wartościami, które chcesz porównać.</span><span class="sxs-lookup"><span data-stu-id="062c6-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="062c6-107">Jeśli zmienna zapytania zostaną przekazane w granicach metody, należy użyć typu nazwanego, który zastępuje <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> dla klucza.</span><span class="sxs-lookup"><span data-stu-id="062c6-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="062c6-108">Nazwy właściwości i kolejność, w jakiej występują one muszą być identyczne w każdy klucz.</span><span class="sxs-lookup"><span data-stu-id="062c6-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="062c6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="062c6-109">Example</span></span>

<span data-ttu-id="062c6-110">Poniższy przykład pokazuje sposób użycia klucza złożonego do łączenia danych z trzech tabel:</span><span class="sxs-lookup"><span data-stu-id="062c6-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="062c6-111">Wnioskowanie o typie na klucze złożone zależy od nazwy właściwości kluczy i kolejności ich występowania.</span><span class="sxs-lookup"><span data-stu-id="062c6-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="062c6-112">Jeśli właściwości w sekwencji źródłowej nie ma takie same nazwy, należy przypisać nowe nazwy w kluczach.</span><span class="sxs-lookup"><span data-stu-id="062c6-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="062c6-113">Na przykład jeśli `Orders` tabeli i `OrderDetails` tabeli każdego używać różnych nazw kolumn, można utworzyć kluczy złożonych, przypisując identyczne nazwy typów anonimowych:</span><span class="sxs-lookup"><span data-stu-id="062c6-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="062c6-114">Klucze złożone, które mogą być również używane w `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="062c6-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="062c6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="062c6-115">See also</span></span>

- [<span data-ttu-id="062c6-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="062c6-116">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="062c6-117">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="062c6-117">join clause</span></span>](../language-reference/keywords/join-clause.md)  
- [<span data-ttu-id="062c6-118">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="062c6-118">group clause</span></span>](../language-reference/keywords/group-clause.md)  