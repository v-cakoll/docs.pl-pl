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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="7b3c0-102">Instrukcje: Nowy typ projektu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7b3c0-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="7b3c0-103">W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają <xref:System.Collections.Generic.IEnumerable%601> wyniki <xref:System.Xml.Linq.XElement>w <xref:System.Collections.Generic.IEnumerable%601> `string`zakresie od, <xref:System.Collections.Generic.IEnumerable%601> do `int`i.</span><span class="sxs-lookup"><span data-stu-id="7b3c0-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="7b3c0-104">Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="7b3c0-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="7b3c0-105">W wielu przypadkach zapytania będą zwracały <xref:System.Collections.Generic.IEnumerable%601> inne typy.</span><span class="sxs-lookup"><span data-stu-id="7b3c0-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="7b3c0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b3c0-106">Example</span></span>

<span data-ttu-id="7b3c0-107">Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7b3c0-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="7b3c0-108">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `select` instrukcję tak, aby wyrażenie było nowym wystąpieniem nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="7b3c0-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="7b3c0-109">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="7b3c0-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="7b3c0-110">W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Element%2A> metody, która została wprowadzona w temacie [How to: Pobierz pojedynczy element podrzędny (LINQ to XML) (C#).](how-to-retrieve-a-single-child-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="7b3c0-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="7b3c0-111">Używa również rzutowania do pobrania wartości elementów, które są zwracane przez <xref:System.Xml.Linq.XContainer.Element%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="7b3c0-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="7b3c0-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7b3c0-112">This example produces the following output:</span></span>

```console
Lawnmower:1
Baby Monitor:2
```
