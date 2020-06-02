---
title: Mapowanie hierarchii obiektów na dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 8507c4b323f97279c3054b76aaf8d52f14f0d4ad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289138"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="bb9b4-102">Mapowanie hierarchii obiektów na dane XML</span><span class="sxs-lookup"><span data-stu-id="bb9b4-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="bb9b4-103">Gdy dokument XML znajduje się w pamięci, reprezentacja koncepcyjna jest drzewem.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="bb9b4-104">W przypadku programowania istnieje hierarchia obiektów do uzyskiwania dostępu do węzłów drzewa.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="bb9b4-105">W poniższym przykładzie pokazano, jak zawartość XML staną się węzłami.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="bb9b4-106">Ponieważ kod XML jest odczytywany do Document Object Model XML (DOM), fragmenty są tłumaczone na węzły, a te węzły zachowują dodatkowe metadane dotyczące siebie, takie jak typ węzła i wartości.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="bb9b4-107">Typ węzła jest obiektem, co określa, jakie akcje można wykonać i jakie właściwości można ustawić lub pobrać.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="bb9b4-108">Jeśli masz następujący prosty kod XML:</span><span class="sxs-lookup"><span data-stu-id="bb9b4-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="bb9b4-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="bb9b4-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="bb9b4-110">Dane wejściowe są reprezentowane w pamięci jako drzewo węzła z przypisaną właściwością typu węzła:</span><span class="sxs-lookup"><span data-stu-id="bb9b4-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="bb9b4-111">![Przykładowe drzewo węzłów](media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="bb9b4-111">![example node tree](media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="bb9b4-112">Reprezentacja drzewa w drzewie i tytule węzła</span><span class="sxs-lookup"><span data-stu-id="bb9b4-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="bb9b4-113">`book`Element stanie się obiektem **XmlElement** , następny element, `title` , również stanie się **XmlElement**, podczas gdy zawartość elementu stanie się obiektem **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="bb9b4-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="bb9b4-114">W przypadku metod i właściwości **elementu XmlElement** metody i właściwości są inne niż metody i właściwości dostępne w obiekcie **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="bb9b4-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="bb9b4-115">Należy więc znać typ węzła, który ma stać się znacznikiem XML, ponieważ jego typ węzła Określa akcje, które można wykonać.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="bb9b4-116">Poniższy przykład odczytuje dane XML i zapisuje inny tekst w zależności od typu węzła.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="bb9b4-117">Używanie następującego pliku danych XML jako danych wejściowych, **Items. XML**:</span><span class="sxs-lookup"><span data-stu-id="bb9b4-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="bb9b4-118">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="bb9b4-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="bb9b4-119">Poniższy przykład kodu odczytuje plik **Items. XML** i wyświetla informacje dla każdego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="bb9b4-120">Dane wyjściowe z przykładu ujawniają mapowanie danych do typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="bb9b4-121">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="bb9b4-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="bb9b4-122">Po wprowadzeniu jednego wiersza i użyciu danych wyjściowych generowanych na podstawie kodu można użyć poniższej tabeli, aby przeanalizować, który test węzła wygenerował te wiersze danych wyjściowych, a tym samym zrozumieć, jakie dane XML stały się typem węzła.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="bb9b4-123">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="bb9b4-123">Input</span></span>|<span data-ttu-id="bb9b4-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="bb9b4-124">Output</span></span>|<span data-ttu-id="bb9b4-125">Test typu węzła</span><span class="sxs-lookup"><span data-stu-id="bb9b4-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|\<?xml version="1.0"?>|\<?xml version='1.0'?>|<span data-ttu-id="bb9b4-126">XmlNodeType. xmldeklaracji</span><span class="sxs-lookup"><span data-stu-id="bb9b4-126">XmlNodeType.XmlDeclaration</span></span>|  
|\<!-- This is a sample XML document -->|\<!--This is a sample XML document -->|<span data-ttu-id="bb9b4-127">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="bb9b4-127">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="bb9b4-128">\<!DOCTYPE Items [\<!ENTITY number "123">] ></span><span class="sxs-lookup"><span data-stu-id="bb9b4-128">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="bb9b4-129">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="bb9b4-129">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="bb9b4-130">XmlNodeType. DocumentType</span><span class="sxs-lookup"><span data-stu-id="bb9b4-130">XmlNodeType.DocumentType</span></span>|  
|\<Items>|\<Items>|<span data-ttu-id="bb9b4-131">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-131">XmlNodeType.Element</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="bb9b4-132">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-132">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="bb9b4-133">Testowanie przy użyciu jednostki:&number;</span><span class="sxs-lookup"><span data-stu-id="bb9b4-133">Test with an entity: &number;</span></span>|<span data-ttu-id="bb9b4-134">Testowanie przy użyciu jednostki: 123</span><span class="sxs-lookup"><span data-stu-id="bb9b4-134">Test with an entity: 123</span></span>|<span data-ttu-id="bb9b4-135">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-135">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="bb9b4-136">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="bb9b4-136">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="bb9b4-137">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-137">XmNodeType.Element</span></span>|  
|<span data-ttu-id="bb9b4-138">Testowanie przy użyciu elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="bb9b4-138">test with a child element</span></span>|<span data-ttu-id="bb9b4-139">Testowanie przy użyciu elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="bb9b4-139">test with a child element</span></span>|<span data-ttu-id="bb9b4-140">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-140">XmlNodeType.Text</span></span>|  
|\<more>|\<more>|<span data-ttu-id="bb9b4-141">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-141">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="bb9b4-142">rzeczy</span><span class="sxs-lookup"><span data-stu-id="bb9b4-142">stuff</span></span>|<span data-ttu-id="bb9b4-143">rzeczy</span><span class="sxs-lookup"><span data-stu-id="bb9b4-143">stuff</span></span>|<span data-ttu-id="bb9b4-144">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-144">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="bb9b4-145">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="bb9b4-145">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="bb9b4-146">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-146">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="bb9b4-147">Testowanie za pomocą sekcji CDATA</span><span class="sxs-lookup"><span data-stu-id="bb9b4-147">test with a CDATA section</span></span>|<span data-ttu-id="bb9b4-148">Testowanie za pomocą sekcji CDATA</span><span class="sxs-lookup"><span data-stu-id="bb9b4-148">test with a CDATA section</span></span>|<span data-ttu-id="bb9b4-149">Xmltest. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-149">XmlTest.Text</span></span>|  
|<span data-ttu-id="bb9b4-150"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="bb9b4-150"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="bb9b4-151"><! [CDATA [ \<456> ]]\></span><span class="sxs-lookup"><span data-stu-id="bb9b4-151"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="bb9b4-152">Xmltest. CDATA</span><span class="sxs-lookup"><span data-stu-id="bb9b4-152">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="bb9b4-153">DEF</span><span class="sxs-lookup"><span data-stu-id="bb9b4-153">def</span></span>|<span data-ttu-id="bb9b4-154">DEF</span><span class="sxs-lookup"><span data-stu-id="bb9b4-154">def</span></span>|<span data-ttu-id="bb9b4-155">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-155">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="bb9b4-156">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="bb9b4-156">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="bb9b4-157">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-157">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="bb9b4-158">Testowanie za pomocą jednostki char: &\# 65;</span><span class="sxs-lookup"><span data-stu-id="bb9b4-158">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="bb9b4-159">Testowanie za pomocą jednostki char:</span><span class="sxs-lookup"><span data-stu-id="bb9b4-159">Test with a char entity: A</span></span>|<span data-ttu-id="bb9b4-160">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-160">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="bb9b4-161">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="bb9b4-161">XmlNodeType.EndElement</span></span>|  
|\<!-- Fourteen chars in this element.-->|\<--Fourteen chars in this element.-->|<span data-ttu-id="bb9b4-162">XmlNodeType. Comment</span><span class="sxs-lookup"><span data-stu-id="bb9b4-162">XmlNodeType.Comment</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="bb9b4-163">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="bb9b4-163">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="bb9b4-164">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="bb9b4-164">1234567890ABCD</span></span>|<span data-ttu-id="bb9b4-165">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="bb9b4-165">1234567890ABCD</span></span>|<span data-ttu-id="bb9b4-166">XmlNodeType. Text</span><span class="sxs-lookup"><span data-stu-id="bb9b4-166">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="bb9b4-167">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="bb9b4-167">XmlNodeType.EndElement</span></span>|  
|\</Items>|\</Items>|<span data-ttu-id="bb9b4-168">XmlNodeType. EndElement</span><span class="sxs-lookup"><span data-stu-id="bb9b4-168">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="bb9b4-169">Musisz wiedzieć, jaki typ węzła jest przypisany, ponieważ typ węzła kontroluje, jakie rodzaje akcji są prawidłowe i jakie właściwości można ustawić i pobrać.</span><span class="sxs-lookup"><span data-stu-id="bb9b4-169">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="bb9b4-170">Tworzenie węzłów dla białych znaków jest kontrolowane, gdy dane są ładowane do modelu DOM przez flagę **PreserveWhitespace** .</span><span class="sxs-lookup"><span data-stu-id="bb9b4-170">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="bb9b4-171">Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak podczas ładowania modelu dom](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="bb9b4-171">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="bb9b4-172">Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzłów do dokumentu XML](inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bb9b4-172">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="bb9b4-173">Aby usunąć węzły z modelu DOM, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bb9b4-173">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="bb9b4-174">Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [Modyfikowanie węzłów, zawartości i wartości w dokumencie XML](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="bb9b4-174">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9b4-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb9b4-175">See also</span></span>

- [<span data-ttu-id="bb9b4-176">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="bb9b4-176">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
