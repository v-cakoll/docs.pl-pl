---
title: 'Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: ff260660057c3b75f4cc92c37c67fca0a0b7f192
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347574"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)
W tym temacie przedstawiono metodę <xref:System.Xml.Linq.XElement.Attributes%2A>. Ta metoda pobiera atrybuty elementu.  
  
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
