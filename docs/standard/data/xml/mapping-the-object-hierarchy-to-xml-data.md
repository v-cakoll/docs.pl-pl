---
title: Mapowanie hierarchii obiektów na dane XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 642a7e5321d0150865f74a66a811914bc9f5d21d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160030"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="e7b07-102">Mapowanie hierarchii obiektów na dane XML</span><span class="sxs-lookup"><span data-stu-id="e7b07-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="e7b07-103">Gdy dokument XML znajduje się w pamięci, reprezentacja koncepcyjna jest drzewem.</span><span class="sxs-lookup"><span data-stu-id="e7b07-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="e7b07-104">W przypadku programowania istnieje hierarchia obiektów do uzyskiwania dostępu do węzłów drzewa.</span><span class="sxs-lookup"><span data-stu-id="e7b07-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="e7b07-105">W poniższym przykładzie pokazano, jak zawartość XML staną się węzłami.</span><span class="sxs-lookup"><span data-stu-id="e7b07-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="e7b07-106">Ponieważ kod XML jest odczytywany do Document Object Model XML (DOM), fragmenty są tłumaczone na węzły, a te węzły zachowują dodatkowe metadane dotyczące siebie, takie jak typ węzła i wartości.</span><span class="sxs-lookup"><span data-stu-id="e7b07-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="e7b07-107">Typ węzła jest obiektem, co określa, jakie akcje można wykonać i jakie właściwości można ustawić lub pobrać.</span><span class="sxs-lookup"><span data-stu-id="e7b07-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="e7b07-108">Jeśli masz następujący prosty kod XML:</span><span class="sxs-lookup"><span data-stu-id="e7b07-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="e7b07-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="e7b07-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="e7b07-110">Dane wejściowe są reprezentowane w pamięci jako drzewo węzła z przypisaną właściwością typu węzła:</span><span class="sxs-lookup"><span data-stu-id="e7b07-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="e7b07-111">![Przykładowe drzewo węzłów](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="e7b07-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="e7b07-112">Reprezentacja drzewa w drzewie i tytule węzła</span><span class="sxs-lookup"><span data-stu-id="e7b07-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="e7b07-113">Element `book` stanie się obiektem **XmlElement** , a następny element, `title`, również stanie się **XmlElement**, natomiast zawartość elementu stanie się obiektem **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="e7b07-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="e7b07-114">W przypadku metod i właściwości **elementu XmlElement** metody i właściwości są inne niż metody i właściwości dostępne w obiekcie **XmlText** .</span><span class="sxs-lookup"><span data-stu-id="e7b07-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="e7b07-115">Należy więc znać typ węzła, który ma stać się znacznikiem XML, ponieważ jego typ węzła Określa akcje, które można wykonać.</span><span class="sxs-lookup"><span data-stu-id="e7b07-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="e7b07-116">Poniższy przykład odczytuje dane XML i zapisuje inny tekst w zależności od typu węzła.</span><span class="sxs-lookup"><span data-stu-id="e7b07-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="e7b07-117">Używanie następującego pliku danych XML jako danych wejściowych, **Items. XML**:</span><span class="sxs-lookup"><span data-stu-id="e7b07-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="e7b07-118">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="e7b07-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="e7b07-119">Poniższy przykład kodu odczytuje plik **Items. XML** i wyświetla informacje dla każdego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="e7b07-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="e7b07-120">Dane wyjściowe z przykładu ujawniają mapowanie danych do typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="e7b07-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="e7b07-121">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="e7b07-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="e7b07-122">Po wprowadzeniu jednego wiersza i użyciu danych wyjściowych generowanych na podstawie kodu można użyć poniższej tabeli, aby przeanalizować, który test węzła wygenerował te wiersze danych wyjściowych, a tym samym zrozumieć, jakie dane XML stały się typem węzła.</span><span class="sxs-lookup"><span data-stu-id="e7b07-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="e7b07-123">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="e7b07-123">Input</span></span>|<span data-ttu-id="e7b07-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e7b07-124">Output</span></span>|<span data-ttu-id="e7b07-125">Test typu węzła</span><span class="sxs-lookup"><span data-stu-id="e7b07-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="e7b07-126">\<? wersja XML = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="e7b07-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="e7b07-127">\<? wersja XML = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="e7b07-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="e7b07-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="e7b07-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="e7b07-129">\<!--jest to przykładowy dokument XML--></span><span class="sxs-lookup"><span data-stu-id="e7b07-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="e7b07-130">\<!--jest to przykładowy dokument XML--></span><span class="sxs-lookup"><span data-stu-id="e7b07-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="e7b07-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="e7b07-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="e7b07-132">\<! Elementy DOCTYPE [\<! Numer jednostki "123" >] ></span><span class="sxs-lookup"><span data-stu-id="e7b07-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="e7b07-133">\<! Elementy DOCTYPE [\<! Numer jednostki "123" >]</span><span class="sxs-lookup"><span data-stu-id="e7b07-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="e7b07-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="e7b07-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="e7b07-135">\<elementy ></span><span class="sxs-lookup"><span data-stu-id="e7b07-135">\<Items></span></span>|<span data-ttu-id="e7b07-136">\<elementy ></span><span class="sxs-lookup"><span data-stu-id="e7b07-136">\<Items></span></span>|<span data-ttu-id="e7b07-137">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-138">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-138">\<Item></span></span>|<span data-ttu-id="e7b07-139">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-139">\<Item></span></span>|<span data-ttu-id="e7b07-140">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-141">Testowanie przy użyciu jednostki: &number;</span><span class="sxs-lookup"><span data-stu-id="e7b07-141">Test with an entity: &number;</span></span>|<span data-ttu-id="e7b07-142">Testowanie przy użyciu jednostki: 123</span><span class="sxs-lookup"><span data-stu-id="e7b07-142">Test with an entity: 123</span></span>|<span data-ttu-id="e7b07-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="e7b07-144">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-144">\</Item></span></span>|<span data-ttu-id="e7b07-145">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-145">\</Item></span></span>|<span data-ttu-id="e7b07-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="e7b07-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="e7b07-147">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-147">\<Item></span></span>|<span data-ttu-id="e7b07-148">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-148">\<Item></span></span>|<span data-ttu-id="e7b07-149">XmNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-150">Testowanie przy użyciu elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="e7b07-150">test with a child element</span></span>|<span data-ttu-id="e7b07-151">Testowanie przy użyciu elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="e7b07-151">test with a child element</span></span>|<span data-ttu-id="e7b07-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="e7b07-153">\<więcej ></span><span class="sxs-lookup"><span data-stu-id="e7b07-153">\<more></span></span>|<span data-ttu-id="e7b07-154">\<więcej ></span><span class="sxs-lookup"><span data-stu-id="e7b07-154">\<more></span></span>|<span data-ttu-id="e7b07-155">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-156">rzeczy</span><span class="sxs-lookup"><span data-stu-id="e7b07-156">stuff</span></span>|<span data-ttu-id="e7b07-157">rzeczy</span><span class="sxs-lookup"><span data-stu-id="e7b07-157">stuff</span></span>|<span data-ttu-id="e7b07-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="e7b07-159">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-159">\</Item></span></span>|<span data-ttu-id="e7b07-160">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-160">\</Item></span></span>|<span data-ttu-id="e7b07-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="e7b07-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="e7b07-162">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-162">\<Item></span></span>|<span data-ttu-id="e7b07-163">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-163">\<Item></span></span>|<span data-ttu-id="e7b07-164">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-165">Testowanie za pomocą sekcji CDATA</span><span class="sxs-lookup"><span data-stu-id="e7b07-165">test with a CDATA section</span></span>|<span data-ttu-id="e7b07-166">Testowanie za pomocą sekcji CDATA</span><span class="sxs-lookup"><span data-stu-id="e7b07-166">test with a CDATA section</span></span>|<span data-ttu-id="e7b07-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="e7b07-168"><! [CDATA [\<456 >]]\></span><span class="sxs-lookup"><span data-stu-id="e7b07-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="e7b07-169"><! [CDATA [\<456 >]]\></span><span class="sxs-lookup"><span data-stu-id="e7b07-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="e7b07-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="e7b07-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="e7b07-171">rozdzielczości</span><span class="sxs-lookup"><span data-stu-id="e7b07-171">def</span></span>|<span data-ttu-id="e7b07-172">rozdzielczości</span><span class="sxs-lookup"><span data-stu-id="e7b07-172">def</span></span>|<span data-ttu-id="e7b07-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="e7b07-174">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-174">\</Item></span></span>|<span data-ttu-id="e7b07-175">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-175">\</Item></span></span>|<span data-ttu-id="e7b07-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="e7b07-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="e7b07-177">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-177">\<Item></span></span>|<span data-ttu-id="e7b07-178">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-178">\<Item></span></span>|<span data-ttu-id="e7b07-179">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-180">Testowanie za pomocą jednostki char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="e7b07-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="e7b07-181">Testowanie za pomocą jednostki char:</span><span class="sxs-lookup"><span data-stu-id="e7b07-181">Test with a char entity: A</span></span>|<span data-ttu-id="e7b07-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="e7b07-183">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-183">\</Item></span></span>|<span data-ttu-id="e7b07-184">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-184">\</Item></span></span>|<span data-ttu-id="e7b07-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="e7b07-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="e7b07-186">\<!--czternaście znaków w tym elemencie.--></span><span class="sxs-lookup"><span data-stu-id="e7b07-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="e7b07-187">\<--czternaście znaków w tym elemencie.--></span><span class="sxs-lookup"><span data-stu-id="e7b07-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="e7b07-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="e7b07-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="e7b07-189">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-189">\<Item></span></span>|<span data-ttu-id="e7b07-190">Element \<></span><span class="sxs-lookup"><span data-stu-id="e7b07-190">\<Item></span></span>|<span data-ttu-id="e7b07-191">XmlNodeType. element</span><span class="sxs-lookup"><span data-stu-id="e7b07-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="e7b07-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="e7b07-192">1234567890ABCD</span></span>|<span data-ttu-id="e7b07-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="e7b07-193">1234567890ABCD</span></span>|<span data-ttu-id="e7b07-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="e7b07-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="e7b07-195">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-195">\</Item></span></span>|<span data-ttu-id="e7b07-196">\</Item ></span><span class="sxs-lookup"><span data-stu-id="e7b07-196">\</Item></span></span>|<span data-ttu-id="e7b07-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="e7b07-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="e7b07-198">\</Items ></span><span class="sxs-lookup"><span data-stu-id="e7b07-198">\</Items></span></span>|<span data-ttu-id="e7b07-199">\</Items ></span><span class="sxs-lookup"><span data-stu-id="e7b07-199">\</Items></span></span>|<span data-ttu-id="e7b07-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="e7b07-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="e7b07-201">Musisz wiedzieć, jaki typ węzła jest przypisany, ponieważ typ węzła kontroluje, jakie rodzaje akcji są prawidłowe i jakie właściwości można ustawić i pobrać.</span><span class="sxs-lookup"><span data-stu-id="e7b07-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="e7b07-202">Tworzenie węzłów dla białych znaków jest kontrolowane, gdy dane są ładowane do modelu DOM przez flagę **PreserveWhitespace** .</span><span class="sxs-lookup"><span data-stu-id="e7b07-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="e7b07-203">Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak podczas ładowania modelu dom](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="e7b07-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="e7b07-204">Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzłów do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="e7b07-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="e7b07-205">Aby usunąć węzły z modelu DOM, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="e7b07-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="e7b07-206">Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [Modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="e7b07-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b07-207">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7b07-207">See also</span></span>

- [<span data-ttu-id="e7b07-208">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="e7b07-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
