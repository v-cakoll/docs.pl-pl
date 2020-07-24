---
title: Jak zaprojektować nowy typ (LINQ to XML) (C#)
description: Dowiedz się, jak tworzyć zapytania w LINQ to XML w języku C#, które zwracają interfejsy IEnumerable <T> typów oprócz XElement, String lub int, które są opisane w innych przykładach.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104644"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Jak zaprojektować nowy typ (LINQ to XML) (C#)

W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki w zakresie od, do <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> `string` i <xref:System.Collections.Generic.IEnumerable%601> `int` . Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza. W wielu przypadkach zapytania będą zwracały <xref:System.Collections.Generic.IEnumerable%601> Inne typy.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w `select` klauzuli. Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `select` instrukcję tak, aby wyrażenie było nowym wystąpieniem nowej klasy.

W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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

W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Element%2A> metody, która została wprowadzona w temacie [jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Używa również rzutowania do pobrania wartości elementów, które są zwracane przez <xref:System.Xml.Linq.XContainer.Element%2A> metodę.  

Ten przykład generuje następujące wyniki:

```output
Lawnmower:1
Baby Monitor:2
```
