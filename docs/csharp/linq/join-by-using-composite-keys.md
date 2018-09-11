---
title: Sprzęganie za pomocą kluczy złożonych (LINQ w C#)
description: Dowiedz się, jak sprzęgać za pomocą kluczy złożonych w składniku LINQ.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: ae37d03f996f0b0cc184a86663f16d62e6c29c69
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273219"
---
# <a name="join-by-using-composite-keys"></a>Sprzęganie za pomocą kluczy złożonych

Ten przykład przedstawia sposób wykonywania operacji łączenia, w których chcesz użyć więcej niż jednego klucza do zdefiniowania dopasowania. Jest to realizowane przy użyciu klucza złożonego. Można tworzyć złożonego klucza jako typu anonimowego lub nazwane wpisane wartościami, które chcesz porównać. Jeśli zmienna zapytania zostaną przekazane w granicach metody, należy użyć typu nazwanego, który zastępuje <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> dla klucza. Nazwy właściwości i kolejność, w jakiej występują one muszą być identyczne w każdy klucz.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia klucza złożonego do łączenia danych z trzech tabel:

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

Wnioskowanie o typie na klucze złożone zależy od nazwy właściwości kluczy i kolejności ich występowania. Jeśli właściwości w sekwencji źródłowej nie ma takie same nazwy, należy przypisać nowe nazwy w kluczach. Na przykład jeśli `Orders` tabeli i `OrderDetails` tabeli każdego używać różnych nazw kolumn, można utworzyć kluczy złożonych, przypisując identyczne nazwy typów anonimowych:

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

Klucze złożone, które mogą być również używane w `group` klauzuli.

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)  
- [join, klauzula](../language-reference/keywords/join-clause.md)  
- [group, klauzula](../language-reference/keywords/group-clause.md)  