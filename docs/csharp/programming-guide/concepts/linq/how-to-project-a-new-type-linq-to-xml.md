---
title: 'Instrukcje: Nowy typ projektu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 2bb521d1445dcecdad8b9c7b28bed90e1e38c8e8
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012931"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Instrukcje: Nowy typ projektu (LINQ to XML) (C#)

W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają <xref:System.Collections.Generic.IEnumerable%601> wyniki <xref:System.Xml.Linq.XElement>w <xref:System.Collections.Generic.IEnumerable%601> `string`zakresie od, <xref:System.Collections.Generic.IEnumerable%601> do `int`i. Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza. W wielu przypadkach zapytania będą zwracały <xref:System.Collections.Generic.IEnumerable%601> inne typy.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w `select` klauzuli. Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `select` instrukcję tak, aby wyrażenie było nowym wystąpieniem nowej klasy.

W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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

W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Element%2A> metody, która została wprowadzona w temacie [How to: Pobierz pojedynczy element podrzędny (LINQ to XML) (C#).](how-to-retrieve-a-single-child-element-linq-to-xml.md) Używa również rzutowania do pobrania wartości elementów, które są zwracane przez <xref:System.Xml.Linq.XContainer.Element%2A> metodę.  

Ten przykład generuje następujące wyniki:

```console
Lawnmower:1
Baby Monitor:2
```
