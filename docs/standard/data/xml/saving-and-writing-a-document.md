---
title: Zapisywanie i zapisywania dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83aad5d45dda1784069839662486f7dbcc307542
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879519"
---
# <a name="saving-and-writing-a-document"></a>Zapisywanie i zapisywania dokumentu
Podczas ładowania i Zapisz <xref:System.Xml.XmlDocument>, zapisany dokument może różnić się od oryginału, w następujący sposób:  
  
-   Jeśli <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> właściwość jest ustawiona na `true` przed <xref:System.Xml.XmlDocument.Save%2A> metoda jest wywoływana, biały znak w dokumencie są zachowywane w danych wyjściowych; Jeśli ta właściwość jest `false`, <xref:System.Xml.XmlDocument> automatycznie wcięcia danych wyjściowych.  
  
-   Wszelkie odstępy między atrybutami jest redukowana do pojedynczy znak.  
  
-   Odstępy między elementami została zmieniona. Istotnych białych są zachowywane i nie jest nieważny biały znak. Po zapisaniu dokumentu będą używać <xref:System.Xml.XmlTextWriter> **Indenting** tryb domyślnie starannego drukowanie danych wyjściowych, aby był bardziej czytelny.  
  
-   Znak cudzysłowu wokół wartości atrybutów zostanie zmieniony na podwójnego cudzysłowu w domyślnie. Możesz użyć <xref:System.Xml.XmlTextReader.QuoteChar%2A> właściwość <xref:System.Xml.XmlTextWriter> można ustawić znaku cudzysłowu podwójnego cudzysłowu lub pojedynczy cudzysłów.  
  
-   Domyślnie encje znaków numerycznych, takich jak `{` zostaną rozwinięte.  
  
-   Znacznika kolejności bajtów w dokumencie wejściowym nie są zachowywane. UCS-2 jest zapisywany jako UTF-8, chyba że jawnie Utwórz deklaracji XML, który określa innego kodowania.  
  
-   Jeśli chcesz zapisać <xref:System.Xml.XmlDocument> do pliku lub strumienia danych wyjściowych zapisywanych w jest taka sama jak zawartości dokumentu. Oznacza to, że <xref:System.Xml.XmlDeclaration> jest zapisywany tylko jeśli znajduje się w dokumencie i kodowanie używane podczas zapisywania na poziomie dokumentu jest tym samym kodowaniem podane w węźle deklaracji.  
  
## <a name="writing-an-xmldeclaration"></a>Zapisywanie XmlDeclaration  
 <xref:System.Xml.XmlDocument> i <xref:System.Xml.XmlDeclaration> członkowie <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, i <xref:System.Xml.XmlNode.WriteTo%2A>, oprócz <xref:System.Xml.XmlDocument> metody <xref:System.Xml.XmlDocument.Save%2A> i <xref:System.Xml.XmlDocument.WriteContentTo%2A>, Utwórz deklarację XML.  
  
 Aby uzyskać <xref:System.Xml.XmlDocument> właściwości <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>i <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, i <xref:System.Xml.XmlDocument.WriteContentTo%2A> metod, kodowanie, napisanych w deklaracji XML jest pobierana z <xref:System.Xml.XmlDeclaration> węzła. Jeśli ma nie <xref:System.Xml.XmlDeclaration> węzła <xref:System.Xml.XmlDeclaration> nie jest zapisywany. W przypadku bez kodowania w <xref:System.Xml.XmlDeclaration> węzła, kodowanie jest nie napisanych w deklaracji XML.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> i <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> metody zawsze zapisać <xref:System.Xml.XmlDeclaration>. Te metody przyjmują kodowanie za pomocą składnika zapisywania programu jest zapisywania. Oznacza to, że wartości kodowania w edytorze zastępuje kodowania dokumentu i w <xref:System.Xml.XmlDeclaration>. Na przykład, poniższy kod nie zapisuje kodowanie w deklaracji XML, znaleziono w pliku wyjściowym `out.xml`.  
  
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
  
 Dla <xref:System.Xml.XmlDocument.Save%2A> metody deklaracja XML jest zapisywany przy użyciu <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in Class metoda <xref:System.Xml.XmlWriter> klasy. W związku z tym, zastępując <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metoda zmienia sposób zapisywania początku dokumentu.  
  
 Aby uzyskać <xref:System.Xml.XmlDeclaration> członkowie <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, i <xref:System.Xml.XmlNode.InnerXml%2A>, jeśli <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwość nie jest ustawiona, bez kodowania jest zapisywany. W przeciwnym razie kodowanie napisanych w deklaracji XML jest taki sam jak kodowanie znaleziony w <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwości.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Zapisywanie zawartości dokumentu przy użyciu właściwości OuterXml  
 <xref:System.Xml.XmlNode.OuterXml%2A> Właściwość jest rozszerzeniem firmy Microsoft ze standardami World Wide Web Consortium (W3C) XML Document Object Model (DOM). <xref:System.Xml.XmlNode.OuterXml%2A> Właściwość jest używana do pobrania znaczników całego dokumentu w formacie XML lub tylko znaczniki jeden węzeł i jego podrzędnych węzłów. <xref:System.Xml.XmlNode.OuterXml%2A> Zwraca kod znaczników, reprezentujący Podany węzeł i wszystkich jego węzłów podrzędnych.  
  
 Poniższy przykład kodu pokazuje, jak zapisać dokument w całości w postaci ciągu.  
  
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
  
 Z kolei umożliwia <xref:System.Xml.XmlNode.InnerText%2A> właściwość, jeśli chcesz, aby zawartość węzłów podrzędnych.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
