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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="8dca9-102">Jak projektować nowy typ (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8dca9-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="8dca9-103">Inne przykłady w tej sekcji wykazały zapytania, <xref:System.Collections.Generic.IEnumerable%601> które `string`zwracają <xref:System.Collections.Generic.IEnumerable%601> `int`wyniki <xref:System.Collections.Generic.IEnumerable%601> od <xref:System.Xml.Linq.XElement>, z , i .</span><span class="sxs-lookup"><span data-stu-id="8dca9-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="8dca9-104">Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="8dca9-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="8dca9-105">W wielu przypadkach należy zapytania zwrócić <xref:System.Collections.Generic.IEnumerable%601> innego typu.</span><span class="sxs-lookup"><span data-stu-id="8dca9-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="8dca9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dca9-106">Example</span></span>

<span data-ttu-id="8dca9-107">W tym przykładzie pokazano, jak `select` utworzyć wystąpienia obiektów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8dca9-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="8dca9-108">Kod najpierw definiuje nową klasę z konstruktorem, `select` a następnie modyfikuje instrukcję, tak aby wyrażenie było nowym wystąpieniem nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="8dca9-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="8dca9-109">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="8dca9-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="8dca9-110">W tym <xref:System.Xml.Linq.XContainer.Element%2A> przykładzie użyto metody, która została wprowadzona w temacie [Jak pobrać pojedynczy element podrzędny (LINQ do XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8dca9-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="8dca9-111">Używa również rzutowania do pobierania wartości elementów, które <xref:System.Xml.Linq.XContainer.Element%2A> są zwracane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="8dca9-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="8dca9-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8dca9-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
