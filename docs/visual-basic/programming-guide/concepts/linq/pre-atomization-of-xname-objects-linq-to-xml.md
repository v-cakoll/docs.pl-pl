---
title: "Wstępne Atomizacja XName obiektów (LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 967e41afc70290a4e4bdccabb8f3f4dd4ac4f6ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Wstępne Atomizacja XName obiektów (LINQ do XML) (Visual Basic)
Jednym ze sposobów poprawy wydajności w składniku LINQ to XML ma wstępnie rozproszyć <xref:System.Xml.Linq.XName> obiektów. Wstępne Atomizacja oznacza, że można przypisać ciąg <xref:System.Xml.Linq.XName> obiekt przed utworzeniem drzewa XML za pomocą konstruktorów <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klasy. Następnie, zamiast przekazywanie ciąg konstruktora, który użyć niejawna konwersja z ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowane <xref:System.Xml.Linq.XName> obiektu.  
  
 Poprawia to wydajność, podczas tworzenia dużych drzewa XML, w którym są powtarzane konkretne nazwy. W tym celu należy zadeklarować i zainicjuj <xref:System.Xml.Linq.XName> obiekty przed skonstruuj drzewo XML, a następnie użyć <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów dla nazw elementów i atrybutów. Ta technika może spowodować znaczący wzrost wydajności w przypadku tworzenia dużą liczbę elementów (lub atrybutów) o takiej samej nazwie.  
  
 Należy przetestować przed Atomizacja z danego scenariusza zdecydować, czy należy z niej korzystać.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to.  
  
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
  
 W poniższym przykładzie przedstawiono tę samą metodę, gdy dokument XML jest w przestrzeni nazw:  
  
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
  
 Poniższy przykład przypomina więcej co prawdopodobnie wystąpią w świecie rzeczywistym. W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Poprzedni przykład wykonuje lepszą wydajność niż poniższy przykład, w którym nazwy nie są wstępnie atomized:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomized XName i XNamespace obiektów (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
