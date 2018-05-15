---
title: Mapowanie hierarchii obiektów do danych XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f39701d409ba76e3c3f428f484b6fd5e538fbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="72c1f-102">Mapowanie hierarchii obiektów do danych XML</span><span class="sxs-lookup"><span data-stu-id="72c1f-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="72c1f-103">Gdy dokument XML znajduje się w pamięci, koncepcyjnego reprezentacja jest drzewa.</span><span class="sxs-lookup"><span data-stu-id="72c1f-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="72c1f-104">Programowania, musisz mieć hierarchię obiektów, uzyskać dostęp do węzłów drzewa.</span><span class="sxs-lookup"><span data-stu-id="72c1f-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="72c1f-105">Poniższy przykład przedstawia sposób zawartości XML staje się węzłów.</span><span class="sxs-lookup"><span data-stu-id="72c1f-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="72c1f-106">Kod XML jest w trybie odczytu do XML modelu DOM (Document Object), elementy są tłumaczone na węzły, a te węzły zachować dodatkowe metadane na temat, takie jak ich typ węzła i wartości.</span><span class="sxs-lookup"><span data-stu-id="72c1f-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="72c1f-107">Typ węzła jest obiektem i co określa, jakie akcje mogą być wykonywane i właściwości, które można ustawić ani pobrać.</span><span class="sxs-lookup"><span data-stu-id="72c1f-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="72c1f-108">Jeśli masz następujące prostego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="72c1f-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="72c1f-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="72c1f-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="72c1f-110">Dane wejściowe jest reprezentowany w pamięci następujące drzewo węzła z właściwością typu węzła przypisanej:</span><span class="sxs-lookup"><span data-stu-id="72c1f-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="72c1f-111">![przykład węzła drzewa](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="72c1f-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="72c1f-112">Reprezentacja drzewa węzła książki i tytuł</span><span class="sxs-lookup"><span data-stu-id="72c1f-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="72c1f-113">`book` Element staje się **XmlElement** obiektu, następnym elementem `title`, staje się również **XmlElement**, podczas gdy staje się zawartość elementu **XmlText** obiektu.</span><span class="sxs-lookup"><span data-stu-id="72c1f-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="72c1f-114">Patrząc na **XmlElement** metody i właściwości, metody i właściwości są inne niż metody i właściwości dostępne w **XmlText** obiektu.</span><span class="sxs-lookup"><span data-stu-id="72c1f-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="72c1f-115">Dlatego znajomość typ węzła znaczników XML staje się ważne jest, ponieważ jego typ węzła Określa akcje, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="72c1f-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="72c1f-116">Poniższy przykład odczytuje w danych XML i zapisuje się inny tekst, w zależności od typu węzła.</span><span class="sxs-lookup"><span data-stu-id="72c1f-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="72c1f-117">Przy użyciu następującego pliku danych XML jako dane wejściowe, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="72c1f-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="72c1f-118">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="72c1f-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="72c1f-119">Poniższy kod przykładowy odczyty **items.xml** plików i wyświetla informacje dla każdego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="72c1f-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="72c1f-120">Dane wyjściowe z przykładu ujawnia mapowanie danych do typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="72c1f-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="72c1f-121">**Output**</span><span class="sxs-lookup"><span data-stu-id="72c1f-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="72c1f-122">Biorąc wejściowych jeden wiersz w czasie i przy użyciu dane wyjściowe wygenerowane z kodu, można użyć poniższej tabeli do analizowania, jakie testu węzła wygenerowanych danych wyjściowych, które linie co zrozumienie, jakie dane XML stał się jakiego rodzaju typu węzła.</span><span class="sxs-lookup"><span data-stu-id="72c1f-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="72c1f-123">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="72c1f-123">Input</span></span>|<span data-ttu-id="72c1f-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="72c1f-124">Output</span></span>|<span data-ttu-id="72c1f-125">Test typu węzła</span><span class="sxs-lookup"><span data-stu-id="72c1f-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="72c1f-126">\<? wersji xml = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="72c1f-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="72c1f-127">\<? wersji xml = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="72c1f-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="72c1f-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="72c1f-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="72c1f-129">\<!--To jest przykładowy dokument XML--></span><span class="sxs-lookup"><span data-stu-id="72c1f-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="72c1f-130">\<!--To jest przykładowy dokument XML--></span><span class="sxs-lookup"><span data-stu-id="72c1f-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="72c1f-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="72c1f-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="72c1f-132">\<! Elementy DOCTYPE [\<! Liczba jednostek "123" >] ></span><span class="sxs-lookup"><span data-stu-id="72c1f-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="72c1f-133">\<! Elementy DOCTYPE [\<! Liczba jednostek "123" >]</span><span class="sxs-lookup"><span data-stu-id="72c1f-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="72c1f-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="72c1f-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="72c1f-135">\<Elementy ></span><span class="sxs-lookup"><span data-stu-id="72c1f-135">\<Items></span></span>|<span data-ttu-id="72c1f-136">\<Elementy ></span><span class="sxs-lookup"><span data-stu-id="72c1f-136">\<Items></span></span>|<span data-ttu-id="72c1f-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-138">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-138">\<Item></span></span>|<span data-ttu-id="72c1f-139">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-139">\<Item></span></span>|<span data-ttu-id="72c1f-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-141">Test z jednostką: &number;</span><span class="sxs-lookup"><span data-stu-id="72c1f-141">Test with an entity: &number;</span></span>|<span data-ttu-id="72c1f-142">Test z jednostką: 123</span><span class="sxs-lookup"><span data-stu-id="72c1f-142">Test with an entity: 123</span></span>|<span data-ttu-id="72c1f-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="72c1f-144">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-144">\</Item></span></span>|<span data-ttu-id="72c1f-145">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-145">\</Item></span></span>|<span data-ttu-id="72c1f-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="72c1f-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="72c1f-147">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-147">\<Item></span></span>|<span data-ttu-id="72c1f-148">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-148">\<Item></span></span>|<span data-ttu-id="72c1f-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-150">Test z elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="72c1f-150">test with a child element</span></span>|<span data-ttu-id="72c1f-151">Test z elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="72c1f-151">test with a child element</span></span>|<span data-ttu-id="72c1f-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="72c1f-153">\<więcej ></span><span class="sxs-lookup"><span data-stu-id="72c1f-153">\<more></span></span>|<span data-ttu-id="72c1f-154">\<więcej ></span><span class="sxs-lookup"><span data-stu-id="72c1f-154">\<more></span></span>|<span data-ttu-id="72c1f-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-156">rzeczy</span><span class="sxs-lookup"><span data-stu-id="72c1f-156">stuff</span></span>|<span data-ttu-id="72c1f-157">rzeczy</span><span class="sxs-lookup"><span data-stu-id="72c1f-157">stuff</span></span>|<span data-ttu-id="72c1f-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="72c1f-159">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-159">\</Item></span></span>|<span data-ttu-id="72c1f-160">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-160">\</Item></span></span>|<span data-ttu-id="72c1f-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="72c1f-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="72c1f-162">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-162">\<Item></span></span>|<span data-ttu-id="72c1f-163">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-163">\<Item></span></span>|<span data-ttu-id="72c1f-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-165">Testowanie przy sekcja CDATA</span><span class="sxs-lookup"><span data-stu-id="72c1f-165">test with a CDATA section</span></span>|<span data-ttu-id="72c1f-166">Testowanie przy sekcja CDATA</span><span class="sxs-lookup"><span data-stu-id="72c1f-166">test with a CDATA section</span></span>|<span data-ttu-id="72c1f-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="72c1f-168">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="72c1f-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="72c1f-169">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="72c1f-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="72c1f-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="72c1f-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="72c1f-171">DEF</span><span class="sxs-lookup"><span data-stu-id="72c1f-171">def</span></span>|<span data-ttu-id="72c1f-172">DEF</span><span class="sxs-lookup"><span data-stu-id="72c1f-172">def</span></span>|<span data-ttu-id="72c1f-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="72c1f-174">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-174">\</Item></span></span>|<span data-ttu-id="72c1f-175">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-175">\</Item></span></span>|<span data-ttu-id="72c1f-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="72c1f-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="72c1f-177">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-177">\<Item></span></span>|<span data-ttu-id="72c1f-178">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-178">\<Item></span></span>|<span data-ttu-id="72c1f-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-180">Test z jednostką char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="72c1f-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="72c1f-181">Test z jednostką char: A</span><span class="sxs-lookup"><span data-stu-id="72c1f-181">Test with a char entity: A</span></span>|<span data-ttu-id="72c1f-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="72c1f-183">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-183">\</Item></span></span>|<span data-ttu-id="72c1f-184">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-184">\</Item></span></span>|<span data-ttu-id="72c1f-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="72c1f-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="72c1f-186">\<!----> Czternastu znaków w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="72c1f-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="72c1f-187">\<----> Czternastu znaków w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="72c1f-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="72c1f-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="72c1f-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="72c1f-189">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-189">\<Item></span></span>|<span data-ttu-id="72c1f-190">\<Element ></span><span class="sxs-lookup"><span data-stu-id="72c1f-190">\<Item></span></span>|<span data-ttu-id="72c1f-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="72c1f-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="72c1f-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="72c1f-192">1234567890ABCD</span></span>|<span data-ttu-id="72c1f-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="72c1f-193">1234567890ABCD</span></span>|<span data-ttu-id="72c1f-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="72c1f-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="72c1f-195">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-195">\</Item></span></span>|<span data-ttu-id="72c1f-196">\</ Elementu ></span><span class="sxs-lookup"><span data-stu-id="72c1f-196">\</Item></span></span>|<span data-ttu-id="72c1f-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="72c1f-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="72c1f-198">\</ Elementy ></span><span class="sxs-lookup"><span data-stu-id="72c1f-198">\</Items></span></span>|<span data-ttu-id="72c1f-199">\</ Elementy ></span><span class="sxs-lookup"><span data-stu-id="72c1f-199">\</Items></span></span>|<span data-ttu-id="72c1f-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="72c1f-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="72c1f-201">Musi wiedzieć, jaki typ węzła jest przypisany, jako węzeł typ Określa, jakie akcje są prawidłowe i jakiego rodzaju właściwości można ustawić i pobrać.</span><span class="sxs-lookup"><span data-stu-id="72c1f-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="72c1f-202">Tworzenie węzła dla biały znak jest kontrolowany podczas ładowania danych do modelu DOM przez **PreserveWhitespace** flagi.</span><span class="sxs-lookup"><span data-stu-id="72c1f-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="72c1f-203">Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="72c1f-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="72c1f-204">Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzły w dokumencie XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="72c1f-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="72c1f-205">Do usuwania węzłów z modelu DOM, zobacz [wartości z dokumentu XML, zawartość i usuwanie węzłów](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="72c1f-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="72c1f-206">Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [modyfikowanie węzłów, zawartość i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="72c1f-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c1f-207">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72c1f-207">See Also</span></span>  
 [<span data-ttu-id="72c1f-208">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="72c1f-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
