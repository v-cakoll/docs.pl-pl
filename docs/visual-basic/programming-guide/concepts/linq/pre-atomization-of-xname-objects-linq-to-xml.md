---
title: Wstępne rozproszenie obiektów XName (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: a87a37c5fe2fc29ca980c77d9c775b2b1e909cc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353116"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Rozproszenie obiektów XName (LINQ to XML) (Visual Basic)
Jednym ze sposobów poprawy wydajności LINQ to XML jest wyodrębnić <xref:System.Xml.Linq.XName> obiektów. Rozproszenie oznacza przypisanie ciągu do obiektu <xref:System.Xml.Linq.XName> przed utworzeniem drzewa XML przy użyciu konstruktorów klas <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute>. Następnie zamiast przekazywania ciągu do konstruktora, który mógłby użyć niejawnej konwersji z ciągu na <xref:System.Xml.Linq.XName>, zostanie przekazany zainicjowany <xref:System.Xml.Linq.XName> obiekt.  
  
 Zwiększa to wydajność podczas tworzenia dużego drzewa XML, w którym określone nazwy są powtarzane. W tym celu należy zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiektów przed rozpoczęciem tworzenia drzewa XML, a następnie użyć obiektów <xref:System.Xml.Linq.XName> zamiast określania ciągów nazw elementów i atrybutów. Ta technika może przynieść znaczący wzrost wydajności w przypadku tworzenia dużej liczby elementów (lub atrybutów) o tej samej nazwie.  
  
 Należy przetestować rozproszenie z Twoim scenariuszem, aby zdecydować, czy należy z niego korzystać.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje to.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Poniższy przykład pokazuje tę samą technikę, w której dokument XML znajduje się w przestrzeni nazw:  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Poniższy przykład jest bardziej podobny do tego, co prawdopodobnie napotkasz w świecie rzeczywistym. W tym przykładzie zawartość elementu jest dostarczana przez zapytanie:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Poprzedni przykład wykonuje lepsze niż Poniższy przykład, w którym nazwy nie są wstępnie atomne:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Atomed XName and XNamespace Objects (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
