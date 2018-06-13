---
title: 'Porady: projekt nowy typ (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: f9a46e78a0f80f33764e9f87e3e8ce3560a8e0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323774"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="ab079-102">Porady: projekt nowy typ (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ab079-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ab079-103">Inne przykłady w tej sekcji wykazały zapytań, które zwracają wyniki w postaci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, i <xref:System.Collections.Generic.IEnumerable%601> z `int`.</span><span class="sxs-lookup"><span data-stu-id="ab079-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="ab079-104">Te są popularne typy wyników, ale nie są odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="ab079-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="ab079-105">W wielu przypadkach można zapytania do zwrócenia <xref:System.Collections.Generic.IEnumerable%601> z innego typu.</span><span class="sxs-lookup"><span data-stu-id="ab079-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab079-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab079-106">Example</span></span>  
 <span data-ttu-id="ab079-107">W tym przykładzie przedstawiono sposób tworzenia wystąpienia obiektów w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ab079-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="ab079-108">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `select` instrukcji, aby wyrażenie jest nowe wystąpienie klasy nowa klasa.</span><span class="sxs-lookup"><span data-stu-id="ab079-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="ab079-109">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="ab079-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="ab079-110">W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metodę, która została wprowadzona w temacie [porady: pobieranie pojedynczego elementu podrzędnego (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ab079-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="ab079-111">Ponadto użyto rzutowania można pobrać wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metody.</span><span class="sxs-lookup"><span data-stu-id="ab079-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="ab079-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ab079-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab079-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab079-113">See Also</span></span>  
 [<span data-ttu-id="ab079-114">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ab079-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
