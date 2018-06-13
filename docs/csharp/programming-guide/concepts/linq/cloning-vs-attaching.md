---
title: Vs w klonowania. Dołączanie (C#)
ms.date: 07/20/2015
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
ms.openlocfilehash: 31b5498e18e63ffba357b34780c7eb388e08b37f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315766"
---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="70ff8-102">Vs w klonowania. Dołączanie (C#)</span><span class="sxs-lookup"><span data-stu-id="70ff8-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="70ff8-103">Podczas dodawania <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty do nowego drzewa, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączyć do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="70ff8-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="70ff8-104">Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, został sklonowany nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="70ff8-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="70ff8-105">Nowo sklonowanego zawartość jest następnie dołączony do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="70ff8-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70ff8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="70ff8-106">Example</span></span>  
 <span data-ttu-id="70ff8-107">Poniższy kod przedstawia zachowanie podczas dodawania elementu nadrzędnego do drzewa i Dodaj element z elementu nadrzędnego do drzewa.</span><span class="sxs-lookup"><span data-stu-id="70ff8-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="70ff8-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="70ff8-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="70ff8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70ff8-109">See Also</span></span>  
 [<span data-ttu-id="70ff8-110">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="70ff8-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
