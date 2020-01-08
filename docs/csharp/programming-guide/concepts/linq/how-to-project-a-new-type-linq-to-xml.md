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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="82a99-102">Tworzenie projektu nowego typu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="82a99-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="82a99-103">W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> `string`i <xref:System.Collections.Generic.IEnumerable%601> `int`.</span><span class="sxs-lookup"><span data-stu-id="82a99-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="82a99-104">Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="82a99-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="82a99-105">W wielu przypadkach zapytania będą zwracać <xref:System.Collections.Generic.IEnumerable%601> innego typu.</span><span class="sxs-lookup"><span data-stu-id="82a99-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="82a99-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="82a99-106">Example</span></span>

<span data-ttu-id="82a99-107">Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w klauzuli `select`.</span><span class="sxs-lookup"><span data-stu-id="82a99-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="82a99-108">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje instrukcję `select` tak, aby wyrażenie było nowym wystąpieniem nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="82a99-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="82a99-109">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="82a99-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="82a99-110">W tym przykładzie użyto metody <xref:System.Xml.Linq.XContainer.Element%2A>, która została wprowadzona w temacie [jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="82a99-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="82a99-111">Używa również rzutowania do pobrania wartości elementów, które są zwracane przez metodę <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="82a99-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="82a99-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="82a99-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
