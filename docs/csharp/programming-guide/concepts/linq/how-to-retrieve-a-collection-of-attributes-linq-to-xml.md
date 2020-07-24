---
title: Jak pobrać kolekcję atrybutów (LINQ to XML) (C#)
description: Metoda Attributes w języku C# Pobiera atrybuty elementu. Ten LINQ to XML przykład wykonuje iterację w kolekcji atrybutów elementu.
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103383"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="f9166-104">Jak pobrać kolekcję atrybutów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f9166-104">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f9166-105">W tym temacie przedstawiono <xref:System.Xml.Linq.XElement.Attributes%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="f9166-105">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="f9166-106">Ta metoda pobiera atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="f9166-106">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9166-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9166-107">Example</span></span>  
 <span data-ttu-id="f9166-108">Poniższy przykład pokazuje, jak wykonać iterację kolekcji atrybutów elementu.</span><span class="sxs-lookup"><span data-stu-id="f9166-108">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="f9166-109">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="f9166-109">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9166-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9166-110">See also</span></span>

- [<span data-ttu-id="f9166-111">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f9166-111">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
