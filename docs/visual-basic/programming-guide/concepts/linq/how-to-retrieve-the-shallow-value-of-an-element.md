---
title: 'Instrukcje: pobieranie skróconej wartości elementu'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 7449d6d1230313aef6005284270370bb9d243a3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346908"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>Instrukcje: pobieranie płytki wartości elementu (Visual Basic)

W tym temacie pokazano, jak uzyskać skróconą wartość elementu. Wartość płytki to wartość tylko określonego elementu, a nie wartość Szczegółowa, która obejmuje wartości wszystkich elementów potomnych połączonych w jeden ciąg.

Po pobraniu wartości elementu przy użyciu funkcji rzutowania lub właściwości <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> pobierana jest wartość Szczegółowa. Aby pobrać skróconą wartość, można użyć metody rozszerzenia `ShallowValue`, jak pokazano w poniższym przykładzie. Pobieranie skróconej wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.

Poniższy przykład deklaruje metodę rozszerzenia, która pobiera płytki wartość elementu. Następnie używa metody rozszerzającej w zapytaniu, aby wyświetlić listę wszystkich elementów, które zawierają obliczoną wartość.

## <a name="example"></a>Przykład

Następujący plik tekstowy, Report. XML, jest źródłem dla tego przykładu.

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

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
