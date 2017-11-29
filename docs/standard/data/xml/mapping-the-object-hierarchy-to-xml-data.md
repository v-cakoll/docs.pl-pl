---
title: "Mapowanie hierarchii obiektów do danych XML"
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
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bf43922fb702988e9057f541833cd58d33c820a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapowanie hierarchii obiektów do danych XML
Gdy dokument XML znajduje się w pamięci, koncepcyjnego reprezentacja jest drzewa. Programowania, musisz mieć hierarchię obiektów, uzyskać dostęp do węzłów drzewa. Poniższy przykład przedstawia sposób zawartości XML staje się węzłów.  
  
 Kod XML jest w trybie odczytu do XML modelu DOM (Document Object), elementy są tłumaczone na węzły, a te węzły zachować dodatkowe metadane na temat, takie jak ich typ węzła i wartości. Typ węzła jest obiektem i co określa, jakie akcje mogą być wykonywane i właściwości, które można ustawić ani pobrać.  
  
 Jeśli masz następujące prostego kodu XML:  
  
 **Dane wejściowe**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Dane wejściowe jest reprezentowany w pamięci następujące drzewo węzła z właściwością typu węzła przypisanej:  
  
 ![przykład węzła drzewa](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Reprezentacja drzewa węzła książki i tytuł  
  
 `book` Element staje się **XmlElement** obiektu, następnym elementem `title`, staje się również **XmlElement**, podczas gdy staje się zawartość elementu **XmlText** obiektu. Patrząc na **XmlElement** metody i właściwości, metody i właściwości są inne niż metody i właściwości dostępne w **XmlText** obiektu. Dlatego znajomość typ węzła znaczników XML staje się ważne jest, ponieważ jego typ węzła Określa akcje, które mogą być wykonywane.  
  
 Poniższy przykład odczytuje w danych XML i zapisuje się inny tekst, w zależności od typu węzła. Przy użyciu następującego pliku danych XML jako dane wejściowe, **items.xml**:  
  
 **Dane wejściowe**  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 Poniższy kod przykładowy odczyty **items.xml** plików i wyświetla informacje dla każdego typu węzła.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 Dane wyjściowe z przykładu ujawnia mapowanie danych do typów węzłów.  
  
 **Dane wyjściowe**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Biorąc wejściowych jeden wiersz w czasie i przy użyciu dane wyjściowe wygenerowane z kodu, można użyć poniższej tabeli do analizowania, jakie testu węzła wygenerowanych danych wyjściowych, które linie co zrozumienie, jakie dane XML stał się jakiego rodzaju typu węzła.  
  
|Dane wejściowe|Dane wyjściowe|Test typu węzła|  
|-----------|------------|--------------------|  
|\<? wersji xml = "1.0"? >|\<? wersji xml = "1.0"? >|XmlNodeType.XmlDeclaration|  
|\<!--To jest przykładowy dokument XML-->|\<!--To jest przykładowy dokument XML-->|XmlNodeType.Comment|  
|\<! Elementy DOCTYPE [\<! Liczba jednostek "123" >] >|\<! Elementy DOCTYPE [\<! Liczba jednostek "123" >]|XmlNodeType.DocumentType|  
|\<Elementy >|\<Elementy >|XmlNodeType.Element|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|Test z jednostką:&number;|Test z jednostką: 123|XmlNodeType.Text|  
|\</ Elementu >|\</ Elementu >|XmlNodeType.EndElement|  
|\<Element >|\<Element >|XmNodeType.Element|  
|Test z elementu podrzędnego|Test z elementu podrzędnego|XmlNodeType.Text|  
|\<więcej >|\<więcej >|XmlNodeType.Element|  
|rzeczy|rzeczy|XmlNodeType.Text|  
|\</ Elementu >|\</ Elementu >|XmlNodeType.EndElement|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|Testowanie przy sekcja CDATA|Testowanie przy sekcja CDATA|XmlTest.Text|  
|<! [CDATA [\<456 >]]\>|<! [CDATA [\<456 >]]\>|XmlTest.CDATA|  
|DEF|DEF|XmlNodeType.Text|  
|\</ Elementu >|\</ Elementu >|XmlNodeType.EndElement|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|Test z jednostką char: &\#65;|Test z jednostką char: A|XmlNodeType.Text|  
|\</ Elementu >|\</ Elementu >|XmlNodeType.EndElement|  
|\<!----> Czternastu znaków w tym elemencie.|\<----> Czternastu znaków w tym elemencie.|XmlNodeType.Comment|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Elementu >|\</ Elementu >|XmlNodeType.EndElement|  
|\</ Elementy >|\</ Elementy >|XmlNodeType.EndElement|  
  
 Musi wiedzieć, jaki typ węzła jest przypisany, jako węzeł typ Określa, jakie akcje są prawidłowe i jakiego rodzaju właściwości można ustawić i pobrać.  
  
 Tworzenie węzła dla biały znak jest kontrolowany podczas ładowania danych do modelu DOM przez **PreserveWhitespace** flagi. Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzły w dokumencie XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Do usuwania węzłów z modelu DOM, zobacz [wartości z dokumentu XML, zawartość i usuwanie węzłów](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [modyfikowanie węzłów, zawartość i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
