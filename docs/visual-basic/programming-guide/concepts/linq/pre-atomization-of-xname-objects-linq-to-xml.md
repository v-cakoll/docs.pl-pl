---
title: Wstępne rozproszenie obiektów XName (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819297"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Wstępne rozproszenie obiektów XName (LINQ to XML) (Visual Basic)
Jednym ze sposobów, aby zwiększyć wydajność w składniku LINQ to XML jest wstępnie wyodrębnić <xref:System.Xml.Linq.XName> obiektów. Wstępne rozproszenie oznacza, że możesz przypisać ciąg <xref:System.Xml.Linq.XName> obiekt przed przystąpieniem do tworzenia drzewa XML za pomocą konstruktorów z <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klasy. Następnie, zamiast przekazywać ciąg do konstruktora, który użyć niejawna konwersja ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowanej <xref:System.Xml.Linq.XName> obiektu.  
  
 Poprawia to wydajność, podczas tworzenia dużych drzewa XML, w którym są powtarzane określonej nazwy. Aby to zrobić, możesz zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiektów przed konstruowania drzewa XML, a następnie użyj <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów nazw elementów i atrybutów. Ta technika może przynieść znaczący wzrost wydajności w przypadku tworzenia dużej liczby elementów (lub atrybutów) o takiej samej nazwie.  
  
 Wstępne rozproszenie należy przetestować przy użyciu danego scenariusza, aby zdecydować, czy należy jej używać.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia to.  
  
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
  
 Poniższy przykład pokazuje tę samą technikę, w którym dokument XML jest w przestrzeni nazw:  
  
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
  
 Poniższy przykład jest bardziej przypominające, co prawdopodobnie wystąpi w świecie rzeczywistym. W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Poprzedni przykład działa lepiej niż poniższy przykład, w których nazwy są nie wstępnie rozproszone obiekty:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Rozproszone obiekty XName i Xnamespace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
