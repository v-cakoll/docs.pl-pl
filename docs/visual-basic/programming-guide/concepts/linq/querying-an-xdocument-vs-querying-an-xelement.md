---
title: Kwerenda vs klasy XDocument. Wykonywanie zapytania XElement (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ee3c0c1cda12a74f50b4937263d80f526b5d7ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Kwerenda vs klasy XDocument. Wykonywanie zapytania XElement (Visual Basic)
Podczas ładowania dokumentu za pomocą <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, zauważysz, trzeba pisać zapytania nieco inaczej niż podczas ładowania za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porównanie XDocument.Load i XElement.Load  
 Podczas ładowania dokumentu XML do <xref:System.Xml.Linq.XElement> za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> w katalogu głównym pliku XML drzewo zawiera element główny załadowanego dokumentu. Jednak podczas ładowania tego samego dokumentu XML do <xref:System.Xml.Linq.XDocument> za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, katalog główny drzewa jest <xref:System.Xml.Linq.XDocument> węzła i element główny załadowanego dokumentu jest jeden element podrzędny dozwolonych <xref:System.Xml.Linq.XElement> węzła <xref:System.Xml.Linq.XDocument>. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osie działać względem węzła głównego.  
  
 W tym przykładzie pierwsze ładuje drzewa XML przy użyciu <xref:System.Xml.Linq.XElement.Load%2A>. Następnie zapytania dotyczące elementów podrzędnych katalogu głównego drzewa.  
  
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
  
 Zgodnie z oczekiwaniami, w tym przykładzie tworzy następujące dane wyjściowe:  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Poniższy przykład jest taki sam, jak powyżej, z wyjątkiem ładowanej drzewa XML do <xref:System.Xml.Linq.XDocument> zamiast <xref:System.Xml.Linq.XElement>.  
  
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
  
 Zwróć uwagę, samo zapytanie zwrócony jeden `Root` węzła zamiast trzech węzłów podrzędnych.  
  
 Jeden ze sposobów postępowania z tym jest użycie <xref:System.Xml.Linq.XDocument.Root%2A> właściwości przed uzyskaniem dostępu do metody osi w następujący sposób:  
  
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
  
 To zapytanie wykonuje obecnie w taki sam sposób jak zapytania na drzewo umieszczone w <xref:System.Xml.Linq.XElement>. Przykład tworzy następujące dane wyjściowe:  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe zapytania (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
