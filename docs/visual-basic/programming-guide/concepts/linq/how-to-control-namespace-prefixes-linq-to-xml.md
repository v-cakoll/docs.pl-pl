---
title: 'Instrukcje: Prefiksy Namespace kontroli (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 91117307caf7e55bd8b512fbd841760616f0b2c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623745"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Instrukcje: Prefiksy Namespace kontroli (LINQ to XML) (Visual Basic)
W tym temacie opisano, jak można kontrolować prefiksy przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Ten przykład deklaruje dwie przestrzeni nazw. Określa, że `http://www.adventure-works.com` przestrzeni nazw ma prefiks `aw`oraz że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
