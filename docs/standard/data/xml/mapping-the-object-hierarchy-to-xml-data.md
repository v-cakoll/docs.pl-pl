---
title: Mapowanie hierarchii obiektów na dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 4ad505749625e22a09406549329179990b81c140
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794393"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapowanie hierarchii obiektów na dane XML
Gdy dokument XML znajduje się w pamięci, reprezentacja koncepcyjna jest drzewem. W przypadku programowania istnieje hierarchia obiektów do uzyskiwania dostępu do węzłów drzewa. W poniższym przykładzie pokazano, jak zawartość XML staną się węzłami.  
  
 Ponieważ kod XML jest odczytywany do Document Object Model XML (DOM), fragmenty są tłumaczone na węzły, a te węzły zachowują dodatkowe metadane dotyczące siebie, takie jak typ węzła i wartości. Typ węzła jest obiektem, co określa, jakie akcje można wykonać i jakie właściwości można ustawić lub pobrać.  
  
 Jeśli masz następujący prosty kod XML:  
  
 **Dane wejściowe**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 Dane wejściowe są reprezentowane w pamięci jako drzewo węzła z przypisaną właściwością typu węzła:  
  
 ![Przykładowe drzewo węzłów](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Reprezentacja drzewa w drzewie i tytule węzła  
  
 `book` Element stanie się obiektem **XmlElement** , następny element, `title`, również stanie się **XmlElement**, podczas gdy zawartość elementu stanie się obiektem **XmlText** . W przypadku metod i właściwości **elementu XmlElement** metody i właściwości są inne niż metody i właściwości dostępne w obiekcie **XmlText** . Należy więc znać typ węzła, który ma stać się znacznikiem XML, ponieważ jego typ węzła Określa akcje, które można wykonać.  
  
 Poniższy przykład odczytuje dane XML i zapisuje inny tekst w zależności od typu węzła. Używanie następującego pliku danych XML jako danych wejściowych, **Items. XML**:  
  
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
  
 Poniższy przykład kodu odczytuje plik **Items. XML** i wyświetla informacje dla każdego typu węzła.  
  
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
  
 Dane wyjściowe z przykładu ujawniają mapowanie danych do typów węzłów.  
  
 **Dane wyjściowe**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 Po wprowadzeniu jednego wiersza i użyciu danych wyjściowych generowanych na podstawie kodu można użyć poniższej tabeli, aby przeanalizować, który test węzła wygenerował te wiersze danych wyjściowych, a tym samym zrozumieć, jakie dane XML stały się typem węzła.  
  
|Dane wejściowe|Dane wyjściowe|Test typu węzła|  
|-----------|------------|--------------------|  
|\<? Wersja XML = "1.0"? >|\<? Wersja XML = "1.0"? >|XmlNodeType. xmldeklaracji|  
|\<!--To jest przykładowy dokument XML-->|\<!--To jest przykładowy dokument XML-->|XmlNodeType. Comment|  
|\<! Elementy DOCTYPE [\<! Numer jednostki "123" >] >|\<! Elementy DOCTYPE [\<! Numer jednostki "123" >]|XmlNodeType. DocumentType|  
|\<Elementy>|\<Elementy>|XmlNodeType. element|  
|\<> elementu|\<> elementu|XmlNodeType. element|  
|Testowanie przy użyciu jednostki:&number;|Testowanie przy użyciu jednostki: 123|XmlNodeType. Text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<> elementu|\<> elementu|XmNodeType. element|  
|Testowanie przy użyciu elementu podrzędnego|Testowanie przy użyciu elementu podrzędnego|XmlNodeType. Text|  
|\<Więcej>|\<Więcej>|XmlNodeType. element|  
|rzeczy|rzeczy|XmlNodeType. Text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<> elementu|\<> elementu|XmlNodeType. element|  
|Testowanie za pomocą sekcji CDATA|Testowanie za pomocą sekcji CDATA|Xmltest. Text|  
|<! [CDATA [\<456>]]\>|<! [CDATA [\<456>]]\>|Xmltest. CDATA|  
|DEF|DEF|XmlNodeType. Text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<> elementu|\<> elementu|XmlNodeType. element|  
|Testowanie za pomocą jednostki char: &\#65;|Testowanie za pomocą jednostki char:|XmlNodeType. Text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\<!--Czternaście znaków w tym elemencie.-->|\<--Czternaście znaków w tym elemencie.-->|XmlNodeType. Comment|  
|\<> elementu|\<> elementu|XmlNodeType. element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType. Text|  
|\</Item>|\</Item>|XmlNodeType. EndElement|  
|\</Items>|\</Items>|XmlNodeType. EndElement|  
  
 Musisz wiedzieć, jaki typ węzła jest przypisany, ponieważ typ węzła kontroluje, jakie rodzaje akcji są prawidłowe i jakie właściwości można ustawić i pobrać.  
  
 Tworzenie węzłów dla białych znaków jest kontrolowane, gdy dane są ładowane do modelu DOM przez flagę **PreserveWhitespace** . Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak podczas ładowania modelu dom](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzłów do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Aby usunąć węzły z modelu DOM, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [Modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
