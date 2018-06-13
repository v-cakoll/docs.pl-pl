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
# <a name="join-by-using-composite-keys"></a>Sprzęganie za pomocą kluczy złożonych

Ten przykład przedstawia sposób wykonywania operacji łączenia, w których chcesz użyć więcej niż jednego klucza do definiowania dopasowania. Jest to zrobić za pomocą klucza złożonego. Można tworzyć złożone klucza jako typu anonimowego lub nazwanego typu z wartościami, które chcesz porównać. Jeśli do zmiennej zapytania zostanie przekazany poza granicami metody, użyj typu nazwanego, który zastępuje <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> dla klucza. Nazwy właściwości i kolejność, w którym występują, musi być takie same jak w przypadku każdego klucza.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia klucza złożonego do przyłączenia dane z trzech tabel:  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 Wnioskowanie o typie na klucze złożone zależy od nazw właściwości kluczy i kolejność, w którym występują. Właściwości w sekwencji źródłowej nie ma tej samej nazwy, musisz przypisać nowe nazwy w kluczach. Na przykład jeśli `Orders` tabeli i `OrderDetails` tabeli każdego użyć innej nazwy dla ich kolumn, można utworzyć kluczy złożonych, przypisując identycznych nazw typów anonimowych:  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 Klucze złożone mogą być również używane w `group` klauzuli.  

## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)  
 [join, klauzula](../language-reference/keywords/join-clause.md)  
 [group, klauzula](../language-reference/keywords/group-clause.md)
