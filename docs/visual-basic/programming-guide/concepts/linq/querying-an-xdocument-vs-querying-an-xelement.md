---
title: Podczas badania elementu XDocument a. Podczas badania XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 6bc7af08544f00a87246b748d0419f11b57ed2da
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220938"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Podczas badania elementu XDocument a. Podczas badania XElement (Visual Basic)
Podczas ładowania dokumentu za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, zauważysz, trzeba nieco inaczej niż podczas ładowania za pośrednictwem pisać zapytania <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porównanie XDocument.Load i XElement.Load  
 Podczas ładowania dokumentu XML do <xref:System.Xml.Linq.XElement> za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> w katalogu głównym pliku XML drzewo zawiera element główny dokumentu załadowane. Jednak podczas ładowania tego samego dokumentu XML do <xref:System.Xml.Linq.XDocument> za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, katalog główny drzewa jest <xref:System.Xml.Linq.XDocument> węzłem, a element główny dokumentu załadować jest jeden element podrzędny z dozwolonych <xref:System.Xml.Linq.XElement> węzła <xref:System.Xml.Linq.XDocument>. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osi działać względem węzła głównego.  
  
 W pierwszym przykładzie ładuje drzewa XML przy użyciu <xref:System.Xml.Linq.XElement.Load%2A>. Następnie zapytania dotyczące elementów podrzędnych katalogu głównego drzewa.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Zgodnie z oczekiwaniami, ten przykład generuje następujące wyniki:  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Poniższy przykład jest taki sam jak ten powyżej, z wyjątkiem, że drzewa XML jest ładowany do <xref:System.Xml.Linq.XDocument> zamiast <xref:System.Xml.Linq.XElement>.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Zwróć uwagę, tego samego zapytania zwrócony jeden `Root` węzła zamiast trzech węzłów podrzędnych.  
  
 Jedno z podejść do radzenia sobie z tym jest użycie <xref:System.Xml.Linq.XDocument.Root%2A> właściwości przed uzyskaniem dostępu do metody osi:  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 To zapytanie wykonuje teraz w taki sam sposób jak zapytania drzewa osadzonego w <xref:System.Xml.Linq.XElement>. Przykład generuje następujące wyniki:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe zapytania (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
