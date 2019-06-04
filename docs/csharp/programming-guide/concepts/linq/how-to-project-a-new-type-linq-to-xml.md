---
title: 'Instrukcje: Projektowanie nowego typu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 70053a2457005f6751075b33e8e49851d7127446
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486584"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Instrukcje: Projektowanie nowego typu (LINQ to XML) (C#)
Inne przykłady w tej sekcji wykazały zapytań, które zwracają wyniki w postaci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, i <xref:System.Collections.Generic.IEnumerable%601> z `int`. Są to typowe typy wyników, ale nie są odpowiednie dla każdego scenariusza. W wielu przypadkach można zapytania do zwrócenia <xref:System.Collections.Generic.IEnumerable%601> z innego typu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpień obiektów w `select` klauzuli. Ten kod najpierw definiuje nową klasę za pomocą konstruktora, a następnie modyfikuje `select` instrukcji, aby wyrażenie jest nowe wystąpienie klasy nowej klasy.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
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
  
 W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metody, która została wprowadzona w temacie [jak: Pobierz jeden typ elementów podrzędnych (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Korzysta również rzutowania można pobrać wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metody.  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  