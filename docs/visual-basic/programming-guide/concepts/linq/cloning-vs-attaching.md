---
title: Klonowanie a Trwa dołączanie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 59ffedfdbb2820683f1e6cc232154688f5c29fc8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832297"
---
# <a name="cloning-vs-attaching-visual-basic"></a>Klonowanie a Trwa dołączanie (Visual Basic)
Podczas dodawania <xref:System.Xml.Linq.XNode> (w tym <xref:System.Xml.Linq.XElement>) lub <xref:System.Xml.Linq.XAttribute> obiekty do nowego drzewa, w przypadku nowej zawartości nie ma elementu nadrzędnego, obiekty, po prostu są dołączone do drzewa XML. Jeśli już nowej zawartości jest elementem nadrzędnym i jest częścią innego drzewa XML, został sklonowany nowej zawartości. Nowo sklonowanego zawartość jest następnie dołączany do drzewa XML.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje działanie po dodaniu elementu nadrzędnego w drzewie, a podczas dodawania elementu z elementu nadrzędnego na drzewo.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
