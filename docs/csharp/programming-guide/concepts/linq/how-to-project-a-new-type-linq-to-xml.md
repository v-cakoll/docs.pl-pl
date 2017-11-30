---
title: 'Porady: projekt nowy typ (LINQ do XML) (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d3deb826bdccdc2a24db84c006fe317a2321442
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="2f9c6-102">Porady: projekt nowy typ (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f9c6-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2f9c6-103">Inne przykłady w tej sekcji wykazały zapytań, które zwracają wyniki w postaci <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, i <xref:System.Collections.Generic.IEnumerable%601> z `int`.</span><span class="sxs-lookup"><span data-stu-id="2f9c6-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="2f9c6-104">Te są popularne typy wyników, ale nie są odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="2f9c6-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="2f9c6-105">W wielu przypadkach można zapytania do zwrócenia <xref:System.Collections.Generic.IEnumerable%601> z innego typu.</span><span class="sxs-lookup"><span data-stu-id="2f9c6-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f9c6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f9c6-106">Example</span></span>  
 <span data-ttu-id="2f9c6-107">W tym przykładzie przedstawiono sposób tworzenia wystąpienia obiektów w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2f9c6-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="2f9c6-108">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `select` instrukcji, aby wyrażenie jest nowe wystąpienie klasy nowa klasa.</span><span class="sxs-lookup"><span data-stu-id="2f9c6-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="2f9c6-109">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="2f9c6-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="2f9c6-110">W tym przykładzie użyto `M:System.Xml.Linq.XElement.Element` metodę, która została wprowadzona w temacie [porady: pobieranie pojedynczego elementu podrzędnego (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2f9c6-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="2f9c6-111">Ponadto użyto rzutowania można pobrać wartości elementów, które są zwracane przez `M:System.Xml.Linq.XElement.Element` metody.</span><span class="sxs-lookup"><span data-stu-id="2f9c6-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="2f9c6-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2f9c6-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f9c6-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f9c6-113">See Also</span></span>  
 [<span data-ttu-id="2f9c6-114">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f9c6-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
