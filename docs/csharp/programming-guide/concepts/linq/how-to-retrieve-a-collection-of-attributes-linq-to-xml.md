---
title: 'Porady: pobierania kolekcję atrybutów (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 73e548b100893652b63dfcc69669eabce655efa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317846"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="93560-102">Porady: pobierania kolekcję atrybutów (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="93560-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="93560-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XElement.Attributes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="93560-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="93560-104">Ta metoda pobiera atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="93560-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93560-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="93560-105">Example</span></span>  
 <span data-ttu-id="93560-106">Poniższy przykład pokazuje, jak do iterowania po kolekcji atrybutów elementu.</span><span class="sxs-lookup"><span data-stu-id="93560-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="93560-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="93560-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="93560-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93560-108">See Also</span></span>  
 [<span data-ttu-id="93560-109">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="93560-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
