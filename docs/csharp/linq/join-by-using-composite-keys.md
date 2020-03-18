---
title: Dołączanie przy użyciu klawiszy złożonych (LINQ w języku C#)
description: Dowiedz się, jak dołączyć przy użyciu kluczy złożonych w LINQ.
ms.date: 12/01/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 460a52da7e0c0a47b77d4c64e76641bae9da7cd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659881"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="76366-103">Sprzęganie za pomocą kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="76366-103">Join by using composite keys</span></span>

<span data-ttu-id="76366-104">W tym przykładzie pokazano, jak wykonywać operacje sprzężenia, w których chcesz użyć więcej niż jednego klucza do zdefiniowania dopasowania.</span><span class="sxs-lookup"><span data-stu-id="76366-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="76366-105">Jest to realizowane przy użyciu klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="76366-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="76366-106">Klucz złożony jest tworzony jako typ anonimowy lub nazwany wpisany z wartościami, które chcesz porównać.</span><span class="sxs-lookup"><span data-stu-id="76366-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="76366-107">Jeśli zmienna kwerendy będą przekazywane przez granice metody, <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> należy użyć nazwanego typu, który zastępuje i dla klucza.</span><span class="sxs-lookup"><span data-stu-id="76366-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="76366-108">Nazwy właściwości i kolejność ich występowania muszą być identyczne w każdym kluczu.</span><span class="sxs-lookup"><span data-stu-id="76366-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="76366-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="76366-109">Example</span></span>

<span data-ttu-id="76366-110">W poniższym przykładzie pokazano, jak używać klucza złożonego do łączenia danych z trzech tabel:</span><span class="sxs-lookup"><span data-stu-id="76366-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="76366-111">Wnioskowanie o typie na kluczach złożonych zależy od nazw właściwości w kluczach i kolejności, w jakiej występują.</span><span class="sxs-lookup"><span data-stu-id="76366-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="76366-112">Jeśli właściwości w sekwencjach źródłowych nie mają tych samych nazw, należy przypisać nowe nazwy w kluczach.</span><span class="sxs-lookup"><span data-stu-id="76366-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="76366-113">Na przykład jeśli `Orders` tabela `OrderDetails` i tabela używały różnych nazw dla swoich kolumn, można utworzyć klucze złożone, przypisując identyczne nazwy w typach anonimowych:</span><span class="sxs-lookup"><span data-stu-id="76366-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="76366-114">Klucze złożone mogą być `group` również używane w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="76366-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="76366-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76366-115">See also</span></span>

- [<span data-ttu-id="76366-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="76366-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="76366-117">klauzula sprzężenia</span><span class="sxs-lookup"><span data-stu-id="76366-117">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="76366-118">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="76366-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
