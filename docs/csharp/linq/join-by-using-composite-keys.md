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
# <a name="join-by-using-composite-keys"></a>Sprzęganie za pomocą kluczy złożonych

W tym przykładzie pokazano, jak wykonywać operacje sprzężenia, w których chcesz użyć więcej niż jednego klucza do zdefiniowania dopasowania. Jest to realizowane przy użyciu klucza złożonego. Klucz złożony jest tworzony jako typ anonimowy lub nazwany wpisany z wartościami, które chcesz porównać. Jeśli zmienna kwerendy będą przekazywane przez granice metody, <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> należy użyć nazwanego typu, który zastępuje i dla klucza. Nazwy właściwości i kolejność ich występowania muszą być identyczne w każdym kluczu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać klucza złożonego do łączenia danych z trzech tabel:

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

Wnioskowanie o typie na kluczach złożonych zależy od nazw właściwości w kluczach i kolejności, w jakiej występują. Jeśli właściwości w sekwencjach źródłowych nie mają tych samych nazw, należy przypisać nowe nazwy w kluczach. Na przykład jeśli `Orders` tabela `OrderDetails` i tabela używały różnych nazw dla swoich kolumn, można utworzyć klucze złożone, przypisując identyczne nazwy w typach anonimowych:

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

Klucze złożone mogą być `group` również używane w klauzuli.

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
- [klauzula sprzężenia](../language-reference/keywords/join-clause.md)
- [group, klauzula](../language-reference/keywords/group-clause.md)
