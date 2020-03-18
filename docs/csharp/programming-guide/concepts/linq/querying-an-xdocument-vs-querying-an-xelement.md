---
title: Wykonywanie zapytań dotyczących dokumentu XDocument a wykonywanie zapytań dotyczących elementu XElement (C#)
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 475c77934ad535bad9ef79ff58bbddf991dc8f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253141"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a>Wykonywanie zapytań dotyczących dokumentu XDocument a wykonywanie zapytań dotyczących elementu XElement (C#)
Podczas ładowania dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>za pośrednictwem , można zauważyć, że trzeba napisać <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>zapytania nieco inaczej niż podczas ładowania za pośrednictwem .  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porównanie XDocument.Load i XElement.Load  
 Po załadowaniu dokumentu XML <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>do <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement> via, w katalogu głównym drzewa XML zawiera element główny załadowanego dokumentu. Jednak po załadowaniu tego samego <xref:System.Xml.Linq.XDocument> dokumentu <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>XML do via <xref:System.Xml.Linq.XDocument> , katalog główny drzewa jest węzłem, a <xref:System.Xml.Linq.XElement> elementem głównym <xref:System.Xml.Linq.XDocument>załadowanego dokumentu jest jeden dozwolony węzeł podrzędny . Osie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] działają względem węzła głównego.  
  
 W tym pierwszym przykładzie wczytuje drzewo XML przy użyciu . <xref:System.Xml.Linq.XElement.Load%2A> Następnie kwerendy dla elementów podrzędnych katalogu głównego drzewa.  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Zgodnie z oczekiwaniami w tym przykładzie daje następujące dane wyjściowe:  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Poniższy przykład jest taki sam jak powyżej, z wyjątkiem drzewa XML <xref:System.Xml.Linq.XDocument> jest <xref:System.Xml.Linq.XElement>ładowany do zamiast .  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Należy zauważyć, że ta `Root` sama kwerenda zwróciła jeden węzeł zamiast trzech węzłów podrzędnych.  
  
 Jednym z podejść do radzenia <xref:System.Xml.Linq.XDocument.Root%2A> sobie z tym jest użycie właściwości przed dostępem do metod osi, w następujący sposób:  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 Ta kwerenda jest teraz wykonywana w taki sam <xref:System.Xml.Linq.XElement>sposób, jak kwerenda na drzewie zakorzenionym w programie . W przykładzie przedstawiono następujące dane wyjściowe:  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  