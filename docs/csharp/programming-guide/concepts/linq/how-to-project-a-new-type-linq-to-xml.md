---
title: Jak projektować nowy typ (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 5205a0c56651271dea0181ed96518c0e9d7f95f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168996"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Jak projektować nowy typ (LINQ do XML) (C#)

Inne przykłady w tej sekcji wykazały zapytania, <xref:System.Collections.Generic.IEnumerable%601> które `string`zwracają <xref:System.Collections.Generic.IEnumerable%601> `int`wyniki <xref:System.Collections.Generic.IEnumerable%601> od <xref:System.Xml.Linq.XElement>, z , i . Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza. W wielu przypadkach należy zapytania zwrócić <xref:System.Collections.Generic.IEnumerable%601> innego typu.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak `select` utworzyć wystąpienia obiektów w klauzuli. Kod najpierw definiuje nową klasę z konstruktorem, `select` a następnie modyfikuje instrukcję, tak aby wyrażenie było nowym wystąpieniem nowej klasy.

W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

W tym <xref:System.Xml.Linq.XContainer.Element%2A> przykładzie użyto metody, która została wprowadzona w temacie [Jak pobrać pojedynczy element podrzędny (LINQ do XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Używa również rzutowania do pobierania wartości elementów, które <xref:System.Xml.Linq.XContainer.Element%2A> są zwracane przez metodę.  

Ten przykład generuje następujące wyniki:

```output
Lawnmower:1
Baby Monitor:2
```
