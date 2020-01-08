---
title: Tworzenie projektu nowego typu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 3a54677fa0fa2845dd635f89ddb7ed1c5c279e03
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345718"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Tworzenie projektu nowego typu (LINQ to XML) (C#)

W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> `string`i <xref:System.Collections.Generic.IEnumerable%601> `int`. Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza. W wielu przypadkach zapytania będą zwracać <xref:System.Collections.Generic.IEnumerable%601> innego typu.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w klauzuli `select`. Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje instrukcję `select` tak, aby wyrażenie było nowym wystąpieniem nowej klasy.

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

W tym przykładzie użyto metody <xref:System.Xml.Linq.XContainer.Element%2A>, która została wprowadzona w temacie [jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Używa również rzutowania do pobrania wartości elementów, które są zwracane przez metodę <xref:System.Xml.Linq.XContainer.Element%2A>.  

Ten przykład generuje następujące wyniki:

```output
Lawnmower:1
Baby Monitor:2
```
