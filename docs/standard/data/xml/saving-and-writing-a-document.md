---
title: Zapisywanie dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 40d031c06f0b76668a634fac46b8defccce62f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289047"
---
# <a name="saving-and-writing-a-document"></a>Zapisywanie dokumentu
Podczas ładowania i zapisywania <xref:System.Xml.XmlDocument> , zapisany dokument może różnić się od oryginału w następujący sposób:  
  
- Jeśli <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> Właściwość jest ustawiona na `true` przed <xref:System.Xml.XmlDocument.Save%2A> wywołaniem metody, biały znak w dokumencie jest zachowywany w danych wyjściowych; Jeśli ta właściwość ma wartość `false` , <xref:System.Xml.XmlDocument> Funkcja autowcięć wyprowadza dane wyjściowe.  
  
- Wszystkie odstępy między atrybutami są skracane do pojedynczego znaku spacji.  
  
- Odstęp między elementami jest zmieniany. Znaczący biały znak jest zachowywany i nieznaczący biały znak nie jest. Ale gdy dokument zostanie zapisany, będzie używać <xref:System.Xml.XmlTextWriter> trybu **wcięć** domyślnie, aby starannie drukować dane wyjściowe, aby zwiększyć jego czytelność.  
  
- Znak cudzysłowu używany wokół wartości atrybutów jest domyślnie zmieniany na podwójny cudzysłów. Można użyć <xref:System.Xml.XmlTextReader.QuoteChar%2A> właściwości w <xref:System.Xml.XmlTextWriter> celu ustawienia znaku cudzysłowu na podwójny cudzysłów lub pojedynczy cudzysłów.  
  
- Domyślnie jednostki znaków numerycznych, takie jak `{` są rozwinięte.  
  
- Znacznik kolejności bajtów znaleziony w dokumencie wejściowym nie jest zachowywany. KOD UCS-2 jest zapisywany jako UTF-8, chyba że jawnie utworzysz deklarację XML, która określa inne kodowanie.  
  
- Jeśli chcesz zapisać do <xref:System.Xml.XmlDocument> pliku lub strumienia, wypisane dane wyjściowe są takie same jak zawartość dokumentu. Oznacza to, że <xref:System.Xml.XmlDeclaration> jest napisane tylko wtedy, gdy znajduje się w dokumencie, a kodowanie używane podczas pisania dokumentu jest tym samym kodowaniem, które znajduje się w węźle deklaracji.  
  
## <a name="writing-an-xmldeclaration"></a>Pisanie xmldeklaracji  
 <xref:System.Xml.XmlDocument>I <xref:System.Xml.XmlDeclaration> elementy członkowskie <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlNode.InnerXml%2A> , i <xref:System.Xml.XmlNode.WriteTo%2A> , oprócz <xref:System.Xml.XmlDocument> metod <xref:System.Xml.XmlDocument.Save%2A> i <xref:System.Xml.XmlDocument.WriteContentTo%2A> , tworzą deklarację XML.  
  
 Dla <xref:System.Xml.XmlDocument> właściwości <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDocument.InnerXml%2A> , i metody,, <xref:System.Xml.XmlDocument.Save%2A> <xref:System.Xml.XmlDocument.WriteTo%2A> i,,, i,,, i,,,,,,,, i,,,,,,,,, i, <xref:System.Xml.XmlDocument.WriteContentTo%2A> są pobierane <xref:System.Xml.XmlDeclaration> Jeśli nie ma <xref:System.Xml.XmlDeclaration> węzła, <xref:System.Xml.XmlDeclaration> nie jest zapisywana. Jeśli w węźle nie ma kodowania <xref:System.Xml.XmlDeclaration> , kodowanie nie jest zapisywane w deklaracji XML.  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType>Metody i <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> zawsze zapisują <xref:System.Xml.XmlDeclaration> . Te metody przyjmują kodowanie z składnika zapisywania, do którego się zapisuje. Oznacza to, że wartość kodowania w składniku zapisywania zastępuje kodowanie w dokumencie i w <xref:System.Xml.XmlDeclaration> . Na przykład poniższy kod nie zapisuje kodowania w deklaracji XML, która znajduje się w pliku wyjściowym `out.xml` .  
  
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
  
 Dla <xref:System.Xml.XmlDocument.Save%2A> metody, deklaracja XML jest zapisywana przy użyciu <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metody w <xref:System.Xml.XmlWriter> klasie. W związku z tym, zastąpienie <xref:System.Xml.XmlWriter.WriteStartDocument%2A> metody powoduje zmianę sposobu zapisywania początku dokumentu.  
  
 W przypadku <xref:System.Xml.XmlDeclaration> elementów członkowskich <xref:System.Xml.XmlNode.OuterXml%2A> , <xref:System.Xml.XmlDeclaration.WriteTo%2A> , i <xref:System.Xml.XmlNode.InnerXml%2A> , jeśli <xref:System.Xml.XmlDeclaration.Encoding%2A> Właściwość nie jest ustawiona, kodowanie nie jest zapisywana. W przeciwnym razie kodowanie wpisane w deklaracji XML jest takie samo jak kodowanie znalezione we <xref:System.Xml.XmlDeclaration.Encoding%2A> właściwości.  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>Zapisywanie zawartości dokumentu przy użyciu właściwości OuterXml  
 <xref:System.Xml.XmlNode.OuterXml%2A>Właściwość jest rozszerzeniem Microsoft dla standardów Document Object Model XML (organizacja World Wide Web Consortium W3C). <xref:System.Xml.XmlNode.OuterXml%2A>Właściwość służy do uzyskiwania adiustacji całego dokumentu XML lub tylko znaczników jednego węzła i jego węzłów podrzędnych. <xref:System.Xml.XmlNode.OuterXml%2A>zwraca znacznik reprezentujący dany węzeł i wszystkie jego węzły podrzędne.  
  
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
  
 Z kolei można użyć <xref:System.Xml.XmlNode.InnerText%2A> właściwości, jeśli chcesz, aby zawartość węzłów podrzędnych.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
