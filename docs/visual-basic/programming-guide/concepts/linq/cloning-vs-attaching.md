---
title: Klonowanie a Trwa dołączanie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 59ffedfdbb2820683f1e6cc232154688f5c29fc8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832297"
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="aae97-102">Klonowanie a Trwa dołączanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aae97-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="aae97-103">Podczas dodawania <xref:System.Xml.Linq.XNode> (w tym <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty do nowego drzewa, w przypadku nowej zawartości nie ma elementu nadrzędnego, obiekty, po prostu są dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="aae97-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="aae97-104">Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, został sklonowany nowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="aae97-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="aae97-105">Nowo sklonowanego zawartość jest następnie dołączany do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="aae97-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae97-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="aae97-106">Example</span></span>  
 <span data-ttu-id="aae97-107">Poniższy przykład demonstruje działanie po dodaniu elementu nadrzędnego w drzewie, a podczas dodawania elementu z elementu nadrzędnego na drzewo.</span><span class="sxs-lookup"><span data-stu-id="aae97-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="aae97-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="aae97-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="aae97-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aae97-109">See also</span></span>

- [<span data-ttu-id="aae97-110">Tworzenie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aae97-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
