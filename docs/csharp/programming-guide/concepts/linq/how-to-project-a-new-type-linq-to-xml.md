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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="75011-103">Jak zaprojektować nowy typ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="75011-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="75011-104">W innych przykładach w tej sekcji przedstawiono zapytania, które zwracają wyniki w zakresie od, do <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> `string` i <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="75011-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="75011-105">Są to typowe typy wyników, ale nie są one odpowiednie dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="75011-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="75011-106">W wielu przypadkach zapytania będą zwracały <xref:System.Collections.Generic.IEnumerable%601> Inne typy.</span><span class="sxs-lookup"><span data-stu-id="75011-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="75011-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="75011-107">Example</span></span>

<span data-ttu-id="75011-108">Ten przykład pokazuje, jak utworzyć wystąpienie obiektów w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="75011-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="75011-109">Kod najpierw definiuje nową klasę z konstruktorem, a następnie modyfikuje `select` instrukcję tak, aby wyrażenie było nowym wystąpieniem nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="75011-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="75011-110">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="75011-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="75011-111">W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Element%2A> metody, która została wprowadzona w temacie [jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="75011-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="75011-112">Używa również rzutowania do pobrania wartości elementów, które są zwracane przez <xref:System.Xml.Linq.XContainer.Element%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="75011-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="75011-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="75011-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
