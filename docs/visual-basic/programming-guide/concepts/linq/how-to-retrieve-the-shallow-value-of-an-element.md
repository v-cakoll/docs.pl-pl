---
title: 'Porady: pobieranie skrócona wartość elementu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 228afa6cd4bf0599bf7bd63afff17014799ef1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>Porady: pobieranie skrócona wartość elementu (Visual Basic)
W tym temacie pokazano, jak pobrać pobieżną wartości elementu. Skrócona wartość jest wartością tylko określonego elementu zamiast dokładnego wartość, która zawiera wartości wszystkich elementów podrzędnych połączone w jeden ciąg.  
  
 Podczas pobierania wartości elementu przy użyciu albo rzutowanie lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości, można pobrać wartości bezpośrednich. Aby pobrać pobieżną wartości, można użyć `ShallowValue` — metoda rozszerzenia, jak pokazano w przykładzie Oto. Pobieranie pobieżną wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.  
  
 Poniższy przykład deklaruje metodę rozszerzenia, która pobiera skrócona wartość elementu. Następnie używa metody rozszerzenia w zapytaniu Aby wyświetlić listę wszystkich elementów, które zawierają obliczonej wartości.  
  
## <a name="example"></a>Przykład  
 Następujący plik tekstowy, Report.xml, jest źródła w ramach tego przykładu.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
