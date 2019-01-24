---
title: 'Instrukcje: Pobieranie kolekcji atrybutów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: d535f56507812855f08b31417124b4408dfea017
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599819"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="13d6e-102">Instrukcje: Pobieranie kolekcji atrybutów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="13d6e-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="13d6e-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XElement.Attributes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13d6e-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="13d6e-104">Ta metoda pobiera atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="13d6e-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13d6e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="13d6e-105">Example</span></span>  
 <span data-ttu-id="13d6e-106">Poniższy przykład pokazuje, jak do iteracji przez kolekcję atrybutów elementu.</span><span class="sxs-lookup"><span data-stu-id="13d6e-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="13d6e-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="13d6e-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="13d6e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13d6e-108">See also</span></span>

- [<span data-ttu-id="13d6e-109">LINQ do XML osi (C#)</span><span class="sxs-lookup"><span data-stu-id="13d6e-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
