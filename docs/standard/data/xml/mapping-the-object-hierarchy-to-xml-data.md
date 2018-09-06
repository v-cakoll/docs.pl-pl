---
title: Mapowanie hierarchii obiektów na dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1808121049c6344b72b1c9d99e19c46422dfa0c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042565"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapowanie hierarchii obiektów na dane XML
Po dokumentu XML w pamięci koncepcyjny reprezentacja jest drzewa. Dla programowania, możesz mieć hierarchię obiektów uzyskać dostęp do węzłów w drzewie. Poniższy przykład pokazuje, jak zawartość XML staje się węzły.  
  
 Jako plik XML jest do odczytu do XML Document Object Model (DOM), elementy są tłumaczone na węzłach, a te węzły zachować dodatkowe metadane na temat, takie jak ich typ węzła i wartości. Typ węzła jest obiektem i to, co określa, jakie akcje mogą być wykonywane i właściwości można ustawić lub pobrać.  
  
 Jeśli masz następujące prostego formatu XML:  
  
 **Dane wejściowe**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Wartość wejściowa jest reprezentowany w pamięci następujące drzewo węzła z właściwością typu przypisanym węźle:  
  
 ![przykład węzła drzewa](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Książki i tytuł reprezentacji drzewa węzła  
  
 `book` Element staje się **XmlElement** object, następnego elementu `title`, staje się również **XmlElement**, podczas gdy staje się zawartości elementu **XmlText** obiektu. Patrząc na **XmlElement** metod i właściwości, metod i właściwości różnią się od metod i właściwości dostępnych na **XmlText** obiektu. Tak, wiedząc, jakiego typu węzła staje się znaczników XML jest istotna, ponieważ jego typ węzła Określa akcje, które mogą być wykonywane.  
  
 Poniższy przykład odczytuje w danych XML i zapisuje się inny tekst, w zależności od typu węzła. Przy użyciu następującego pliku XML w danych jako dane wejściowe, **items.xml**:  
  
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
  
 Poniższy kod przykładowy odczyty **items.xml** pliku i wyświetla informacje dla każdego typu węzła.  
  
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
  
 Dane wyjściowe z przykładu, co spowoduje wyświetlenie mapowanie danych do typów węzłów.  
  
 **Output**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Biorąc wejściowych jeden wiersz w danym momencie i używanie danych wyjściowe wygenerowane z kodu, można użyć poniższej tabeli do analizowania jakie test węzłów wygenerowanych danych wyjściowych, które wiersze, w tym samym zrozumienie, jakie dane XML stało się, jakiego typu węzła.  
  
|Dane wejściowe|Dane wyjściowe|Test typ węzła|  
|-----------|------------|--------------------|  
|\<? wersji xml = "1.0"? >|\<? wersji xml = "1.0'? >|XmlNodeType.XmlDeclaration|  
|\<! — Jest to przykładowy dokument XML-->|\<! — Jest to przykładowy dokument XML-->|XmlNodeType.Comment|  
|\<! Elementy DOCTYPE [\<! Numer jednostki "123" >] >|\<! Elementy DOCTYPE [\<! Numer jednostki "123" >]|XmlNodeType.DocumentType|  
|\<Elementy >|\<Elementy >|XmlNodeType.Element|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|Testowanie za pomocą jednostki: &number;|Test z jednostką: 123|XmlNodeType.Text|  
|\</ Element >|\</ Element >|XmlNodeType.EndElement|  
|\<Element >|\<Element >|XmNodeType.Element|  
|Testowanie za pomocą elementu podrzędnego|Testowanie za pomocą elementu podrzędnego|XmlNodeType.Text|  
|\<więcej >|\<więcej >|XmlNodeType.Element|  
|rzeczy|rzeczy|XmlNodeType.Text|  
|\</ Element >|\</ Element >|XmlNodeType.EndElement|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|Testowanie za pomocą sekcji CDATA|Testowanie za pomocą sekcji CDATA|XmlTest.Text|  
|&LT;! [CDATA [\<456 &GT;]]\>|&LT;! [CDATA [\<456 &GT;]]\>|XmlTest.CDATA|  
|DEF|DEF|XmlNodeType.Text|  
|\</ Element >|\</ Element >|XmlNodeType.EndElement|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|Test z jednostką char: &\#65;|Test z jednostką char: A|XmlNodeType.Text|  
|\</ Element >|\</ Element >|XmlNodeType.EndElement|  
|\<!----> Czternastu znaków w tym elemencie.|\<----> Czternastu znaków w tym elemencie.|XmlNodeType.Comment|  
|\<Element >|\<Element >|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Element >|\</ Element >|XmlNodeType.EndElement|  
|\</ Elementy >|\</ Elementy >|XmlNodeType.EndElement|  
  
 Musisz wiedzieć, jakiego typu węzła jest przypisany, jako węzeł typ Określa, jakiego rodzaju akcje są prawidłowe i jakiego rodzaju właściwości umożliwia ustawianie i pobieranie.  
  
 Tworzenie węzła biały znak jest kontrolowany po załadowaniu danych do modelu DOM, **PreserveWhitespace** flagi. Aby uzyskać więcej informacji, zobacz [biały znak i znaczące biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzłów do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Aby usunąć węzły z modelu DOM, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
