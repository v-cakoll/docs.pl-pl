---
title: 'Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: 7c0f809c5a0707f2e6575cb8bca1b2a312f6daeb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321325"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)
W tym temacie wprowadzono metodę <xref:System.Xml.Linq.XElement.Attributes%2A>. Ta metoda pobiera atrybuty elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację kolekcji atrybutów elementu.  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
