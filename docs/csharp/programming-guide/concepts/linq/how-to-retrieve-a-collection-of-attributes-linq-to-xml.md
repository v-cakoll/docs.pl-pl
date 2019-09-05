---
title: 'Instrukcje: Pobieranie kolekcji atrybutów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: b1721de5ac396faab010dab691bfd88991bad638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253437"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="dc8c0-102">Instrukcje: Pobieranie kolekcji atrybutów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dc8c0-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="dc8c0-103">W <xref:System.Xml.Linq.XElement.Attributes%2A> tym temacie przedstawiono metodę.</span><span class="sxs-lookup"><span data-stu-id="dc8c0-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="dc8c0-104">Ta metoda pobiera atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="dc8c0-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8c0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc8c0-105">Example</span></span>  
 <span data-ttu-id="dc8c0-106">Poniższy przykład pokazuje, jak wykonać iterację kolekcji atrybutów elementu.</span><span class="sxs-lookup"><span data-stu-id="dc8c0-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="dc8c0-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="dc8c0-107">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc8c0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc8c0-108">See also</span></span>

- [<span data-ttu-id="dc8c0-109">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="dc8c0-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
