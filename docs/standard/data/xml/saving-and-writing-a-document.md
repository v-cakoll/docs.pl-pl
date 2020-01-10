---
title: Zapisywanie dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 0af160b720b9eddd9e72689c920316bffdc6d21e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710222"
---
# <a name="saving-and-writing-a-document"></a>Zapisywanie dokumentu
Podczas ładowania i zapisywania <xref:System.Xml.XmlDocument>zapisany dokument może różnić się od oryginału w następujący sposób:  
  
- Jeśli właściwość <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> jest ustawiona na `true` przed wywołaniem metody <xref:System.Xml.XmlDocument.Save%2A>, biały znak w dokumencie zostanie zachowany w danych wyjściowych. Jeśli ta właściwość jest `false`, <xref:System.Xml.XmlDocument> Automatyczne wcięcia danych wyjściowych.  
  
- Wszystkie odstępy między atrybutami są skracane do pojedynczego znaku spacji.  
  
- Odstęp między elementami jest zmieniany. Znaczący biały znak jest zachowywany i nieznaczący biały znak nie jest. Ale gdy dokument zostanie zapisany, użyje <xref:System.Xml.XmlTextWriter> tryb **wcięcia** domyślnie, aby starannie drukować dane wyjściowe, aby zwiększyć ich czytelność.  
  
- Znak cudzysłowu używany wokół wartości atrybutów jest domyślnie zmieniany na podwójny cudzysłów. Możesz użyć właściwości <xref:System.Xml.XmlTextReader.QuoteChar%2A> w <xref:System.Xml.XmlTextWriter>, aby ustawić znak cudzysłowu na podwójny cudzysłów lub pojedynczy cudzysłów.  
  
- Domyślnie jednostki znaków numerycznych, takie jak `{`, są rozwinięte.  
  
- Znacznik kolejności bajtów znaleziony w dokumencie wejściowym nie jest zachowywany. KOD UCS-2 jest zapisywany jako UTF-8, chyba że jawnie utworzysz deklarację XML, która określa inne kodowanie.  
  
- Jeśli chcesz napisać <xref:System.Xml.XmlDocument> do pliku lub strumienia, wypisane dane wyjściowe są takie same jak zawartość dokumentu. Oznacza to, że <xref:System.Xml.XmlDeclaration> jest napisane tylko wtedy, gdy znajduje się w dokumencie, a kodowanie używane podczas pisania dokumentu jest tym samym kodowaniem podanym w węźle deklaracji.  
  
## <a name="writing-an-xmldeclaration"></a>Pisanie xmldeklaracji  
 <xref:System.Xml.XmlDocument> i <xref:System.Xml.XmlDeclaration> członków <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>i <xref:System.Xml.XmlNode.WriteTo%2A>, oprócz metod <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Save%2A> i <xref:System.Xml.XmlDocument.WriteContentTo%2A>, Utwórz deklarację XML.  
  
 W przypadku <xref:System.Xml.XmlDocument> właściwości <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>oraz metod <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>i <xref:System.Xml.XmlDocument.WriteContentTo%2A>, kodowanie następować w deklaracji XML jest pobierane z węzła <xref:System.Xml.XmlDeclaration>. Jeśli nie ma <xref:System.Xml.XmlDeclaration> węzła, <xref:System.Xml.XmlDeclaration> nie jest zapisywana. Jeśli w węźle <xref:System.Xml.XmlDeclaration> nie ma kodowania, kodowanie nie jest zapisywane w deklaracji XML.  
  
 Metody <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> i <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> zawsze zapisują <xref:System.Xml.XmlDeclaration>. Te metody przyjmują kodowanie z składnika zapisywania, do którego się zapisuje. Oznacza to, że wartość kodowania w składniku zapisywania zastępuje kodowanie w dokumencie i w <xref:System.Xml.XmlDeclaration>. Na przykład poniższy kod nie zapisuje kodowania w deklaracji XML, która znajduje się w pliku wyjściowym `out.xml`.  
  
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
  
 Dla metody <xref:System.Xml.XmlDocument.Save%2A> deklaracja XML jest zapisywana przy użyciu metody <xref:System.Xml.XmlWriter.WriteStartDocument%2A> w klasie <xref:System.Xml.XmlWriter>. W związku z tym zastąpienie metody <xref:System.Xml.XmlWriter.WriteStartDocument%2A> powoduje zmianę sposobu zapisywania początku dokumentu.  
  
 W przypadku <xref:System.Xml.XmlDeclaration> członków <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>i <xref:System.Xml.XmlNode.InnerXml%2A>, jeśli właściwość <xref:System.Xml.XmlDeclaration.Encoding%2A> nie jest ustawiona, kodowanie nie zostanie zapamiętane. W przeciwnym razie kodowanie wpisane w deklaracji XML jest takie samo jak kodowanie znalezione we właściwości <xref:System.Xml.XmlDeclaration.Encoding%2A>.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Zapisywanie zawartości dokumentu przy użyciu właściwości OuterXml  
 Właściwość <xref:System.Xml.XmlNode.OuterXml%2A> jest rozszerzeniem firmy Microsoft dla standardów Document Object Model XML (W3C) organizacja World Wide Web Consortium. Właściwość <xref:System.Xml.XmlNode.OuterXml%2A> służy do uzyskiwania adiustacji całego dokumentu XML lub tylko znaczników jednego węzła i jego węzłów podrzędnych. <xref:System.Xml.XmlNode.OuterXml%2A> zwraca znacznik reprezentujący dany węzeł i wszystkie jego węzły podrzędne.  
  
 Poniższy przykład kodu pokazuje, jak zapisać dokument w całości jako ciąg.  
  
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
  
 Poniższy przykład kodu pokazuje, jak zapisać tylko element dokumentu.  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 Z kolei można użyć właściwości <xref:System.Xml.XmlNode.InnerText%2A>, jeśli chcesz zawartość węzłów podrzędnych.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
