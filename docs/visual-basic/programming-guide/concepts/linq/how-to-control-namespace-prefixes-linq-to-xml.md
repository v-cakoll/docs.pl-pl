---
title: 'Instrukcje: kontrolowanie prefiksów przestrzeni nazw (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 5ba415452a8671466c3a4c71a88731e5bd3cda60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348377"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Instrukcje: kontrolowanie prefiksów przestrzeni nazw (Visual Basic) (LINQ to XML)
W tym temacie opisano sposób kontrolowania prefiksów przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Ten przykład deklaruje dwie przestrzenie nazw. Określa, że przestrzeń nazw `http://www.adventure-works.com` ma prefiks `aw`i że przestrzeń nazw `www.fourthcoffee.com` ma prefiks `fc`.  
  
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

- [Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
