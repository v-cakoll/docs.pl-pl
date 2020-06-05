---
title: Tworzenie zapytań dotyczących elementu XDocument a tworzenie zapytań dotyczących elementu XElement
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396301"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Wykonywanie zapytania dotyczącego elementu XDocument a zapytania dotyczącego elementu XElement (Visual Basic)
Podczas ładowania dokumentu za pośrednictwem programu należy <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> zauważyć, że trzeba pisać zapytania nieco inaczej niż podczas ładowania za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porównanie elementów XDocument. Load i XElement. Load  
 Podczas ładowania dokumentu XML do elementu <xref:System.Xml.Linq.XElement> za pośrednictwem <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement> katalog główny drzewa XML zawiera element główny załadowanego dokumentu. Jednak podczas ładowania tego samego dokumentu XML do elementu <xref:System.Xml.Linq.XDocument> za pośrednictwem <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> katalog główny drzewa jest <xref:System.Xml.Linq.XDocument> węzłem, a głównym elementem załadowanego dokumentu jest jeden dozwolony <xref:System.Xml.Linq.XElement> węzeł podrzędny <xref:System.Xml.Linq.XDocument> . [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Osie działają względem węzła głównego.  
  
 Ten pierwszy przykład ładuje drzewo XML przy użyciu <xref:System.Xml.Linq.XElement.Load%2A> . Następnie wykonuje zapytanie dotyczące elementów podrzędnych katalogu głównego drzewa.  
  
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
  
 Zgodnie z oczekiwaniami ten przykład generuje następujące dane wyjściowe:  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Poniższy przykład jest taki sam jak powyżej, z wyjątkiem tego, że drzewo XML jest załadowane do elementu <xref:System.Xml.Linq.XDocument> zamiast <xref:System.Xml.Linq.XElement> .  
  
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
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Zwróć uwagę, że to samo zapytanie zwróciło jeden `Root` węzeł zamiast trzech węzłów podrzędnych.  
  
 Jednym z metod postępowania z tym jest użycie <xref:System.Xml.Linq.XDocument.Root%2A> Właściwości przed uzyskaniem dostępu do metody osi w następujący sposób:  
  
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
  
 To zapytanie jest teraz wykonywane w taki sam sposób, jak zapytanie w drzewie w katalogu głównym <xref:System.Xml.Linq.XElement> . Przykład generuje następujące dane wyjściowe:  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zapytania podstawowe (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
