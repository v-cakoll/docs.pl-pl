---
title: Zapisywanie i zapisywania dokumentu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad656e2db17e44733b5718fe2e3a2a48afcb1381
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-writing-a-document"></a>Zapisywanie i zapisywania dokumentu
Podczas ładowania i zapisać <xref:System.Xml.XmlDocument>, zapisanego dokumentu może różnić się od oryginału w następujący sposób:  
  
-   Jeśli <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> właściwość jest ustawiona na `true` przed <xref:System.Xml.XmlDocument.Save%2A> metoda jest wywoływana, biały znak w dokumencie są zachowywane w danych wyjściowych; Jeśli ta właściwość jest `false`, <xref:System.Xml.XmlDocument> wcięć automatycznie dane wyjściowe.  
  
-   Wszystkie biały znak między atrybutami, zostanie zmniejszona do pojedynczego spacją.  
  
-   Biały znak między elementami zostanie zmieniona. Znaczący biały znak są zachowywane i nie jest nieważny biały znak. Po zapisaniu dokumentu zostanie użyty, ale <xref:System.Xml.XmlTextWriter> **Indenting** tryb domyślnie starannie wydrukować dane wyjściowe, aby był bardziej czytelny.  
  
-   Znak cudzysłowu wokół wartości atrybutu jest zmieniany na podwójnego cudzysłowu domyślnie. Można użyć <xref:System.Xml.XmlTextReader.QuoteChar%2A> właściwość <xref:System.Xml.XmlTextWriter> można ustawić znaku cudzysłowu podwójnego cudzysłowu lub pojedynczy cudzysłów.  
  
-   Domyślnie, takich jak jednostki znaku numerycznego `{` zostaną rozwinięte.  
  
-   Znacznik kolejności bajtów w dokument wejściowy nie są zachowywane. UCS-2 jest zapisywany jako UTF-8, chyba że jawnie tworzenia deklaracji XML, który określa inne kodowanie.  
  
-   Jeśli chcesz zapisać <xref:System.Xml.XmlDocument> do pliku lub strumienia wyjściowego zapisany jest taka sama jak zawartość dokumentu. Oznacza to, że <xref:System.Xml.XmlDeclaration> jest zapisywane tylko jeśli jest zawarte w dokumencie i kodowanie używane podczas zapisywania dokumentu jest tej samej kodowanie podane w węźle deklaracji.  
  
## <a name="writing-an-xmldeclaration"></a>Zapisywanie XmlDeclaration  
 <xref:System.Xml.XmlDocument> i <xref:System.Xml.XmlDeclaration> członkami <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, i <xref:System.Xml.XmlNode.WriteTo%2A>, oprócz <xref:System.Xml.XmlDocument> metody <xref:System.Xml.XmlDocument.Save%2A> i <xref:System.Xml.XmlDocument.WriteContentTo%2A>, Utwórz deklarację XML.  
  
 Dla <xref:System.Xml.XmlDocument> właściwości <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>i <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, i <xref:System.Xml.XmlDocument.WriteContentTo%2A> metod, kodowanie zapisana w deklaracji XML jest pobierana z <xref:System.Xml.XmlDeclaration> węzła. W przypadku nie <xref:System.Xml.XmlDeclaration> węzła, <xref:System.Xml.XmlDeclaration> nie jest zapisywany. Jeśli istnieje bez kodowania w <xref:System.Xml.XmlDeclaration> węzła, kodowanie jest nie zapisana w deklaracji XML.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> i <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> metody zawsze zapisać <xref:System.Xml.XmlDeclaration>. Te metody przyjmują kodowaniem edytor, który jest zapisywania. Oznacza to, że wartość kodowania w edytorze zastępuje kodowania dokumentu, a następnie w <xref:System.Xml.XmlDeclaration>. Na przykład następujący kod nie zapisuje kodowanie w deklaracji XML znaleziono w pliku wyjściowym `out.xml`.  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 Dla <xref:System.Xml.XmlDocument.Save%2A> metody deklaracja XML jest zapisywany przy użyciu <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda <xref:System.Xml.XmlWriter> klasy. W związku z tym zastępowanie <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda zmienia sposób zapisywania początku dokumentu.  
  
 Dla <xref:System.Xml.XmlDeclaration> członkami <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, i <xref:System.Xml.XmlNode.InnerXml%2A>, jeśli <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwość nie jest ustawiona, bez kodowania jest zapisywany. W przeciwnym razie kodowanie zapisana w deklaracji XML jest taki sam jak kodowanie znalezione w <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwości.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Zapisywanie zawartości dokumentu za pomocą właściwości OuterXml  
 <xref:System.Xml.XmlNode.OuterXml%2A> Właściwości to rozszerzenie Microsoft standardy sieci World Wide Web konsorcjum W3C XML modelu DOM (Document Object). <xref:System.Xml.XmlNode.OuterXml%2A> Właściwość jest używana do pobrania znaczników całego dokumentu w formacie XML lub po prostu znaczników jeden węzeł i jego podrzędny węzłów. <xref:System.Xml.XmlNode.OuterXml%2A>Zwraca kod znaczników reprezentujący Podany węzeł i wszystkich jego węzłów podrzędnych.  
  
 Poniższy przykładowy kod przedstawia sposób zapisywania dokumentu w całości w postaci ciągu.  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 Poniższy przykład kodu pokazuje, jak zapisać element dokumentu.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Z kolei umożliwia <xref:System.Xml.XmlNode.InnerText%2A> właściwości, jeśli chcesz, aby zawartość węzłów podrzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
