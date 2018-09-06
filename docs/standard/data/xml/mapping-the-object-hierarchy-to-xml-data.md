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
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="4fd77-102">Mapowanie hierarchii obiektów na dane XML</span><span class="sxs-lookup"><span data-stu-id="4fd77-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="4fd77-103">Po dokumentu XML w pamięci koncepcyjny reprezentacja jest drzewa.</span><span class="sxs-lookup"><span data-stu-id="4fd77-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="4fd77-104">Dla programowania, możesz mieć hierarchię obiektów uzyskać dostęp do węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="4fd77-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="4fd77-105">Poniższy przykład pokazuje, jak zawartość XML staje się węzły.</span><span class="sxs-lookup"><span data-stu-id="4fd77-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="4fd77-106">Jako plik XML jest do odczytu do XML Document Object Model (DOM), elementy są tłumaczone na węzłach, a te węzły zachować dodatkowe metadane na temat, takie jak ich typ węzła i wartości.</span><span class="sxs-lookup"><span data-stu-id="4fd77-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="4fd77-107">Typ węzła jest obiektem i to, co określa, jakie akcje mogą być wykonywane i właściwości można ustawić lub pobrać.</span><span class="sxs-lookup"><span data-stu-id="4fd77-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="4fd77-108">Jeśli masz następujące prostego formatu XML:</span><span class="sxs-lookup"><span data-stu-id="4fd77-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="4fd77-109">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="4fd77-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="4fd77-110">Wartość wejściowa jest reprezentowany w pamięci następujące drzewo węzła z właściwością typu przypisanym węźle:</span><span class="sxs-lookup"><span data-stu-id="4fd77-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="4fd77-111">![przykład węzła drzewa](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="4fd77-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="4fd77-112">Książki i tytuł reprezentacji drzewa węzła</span><span class="sxs-lookup"><span data-stu-id="4fd77-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="4fd77-113">`book` Element staje się **XmlElement** object, następnego elementu `title`, staje się również **XmlElement**, podczas gdy staje się zawartości elementu **XmlText** obiektu.</span><span class="sxs-lookup"><span data-stu-id="4fd77-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="4fd77-114">Patrząc na **XmlElement** metod i właściwości, metod i właściwości różnią się od metod i właściwości dostępnych na **XmlText** obiektu.</span><span class="sxs-lookup"><span data-stu-id="4fd77-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="4fd77-115">Tak, wiedząc, jakiego typu węzła staje się znaczników XML jest istotna, ponieważ jego typ węzła Określa akcje, które mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="4fd77-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="4fd77-116">Poniższy przykład odczytuje w danych XML i zapisuje się inny tekst, w zależności od typu węzła.</span><span class="sxs-lookup"><span data-stu-id="4fd77-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="4fd77-117">Przy użyciu następującego pliku XML w danych jako dane wejściowe, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="4fd77-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="4fd77-118">**Dane wejściowe**</span><span class="sxs-lookup"><span data-stu-id="4fd77-118">**Input**</span></span>  
  
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
  
 <span data-ttu-id="4fd77-119">Poniższy kod przykładowy odczyty **items.xml** pliku i wyświetla informacje dla każdego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="4fd77-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
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
  
 <span data-ttu-id="4fd77-120">Dane wyjściowe z przykładu, co spowoduje wyświetlenie mapowanie danych do typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="4fd77-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="4fd77-121">**Output**</span><span class="sxs-lookup"><span data-stu-id="4fd77-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="4fd77-122">Biorąc wejściowych jeden wiersz w danym momencie i używanie danych wyjściowe wygenerowane z kodu, można użyć poniższej tabeli do analizowania jakie test węzłów wygenerowanych danych wyjściowych, które wiersze, w tym samym zrozumienie, jakie dane XML stało się, jakiego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="4fd77-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="4fd77-123">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="4fd77-123">Input</span></span>|<span data-ttu-id="4fd77-124">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4fd77-124">Output</span></span>|<span data-ttu-id="4fd77-125">Test typ węzła</span><span class="sxs-lookup"><span data-stu-id="4fd77-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="4fd77-126">\<? wersji xml = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="4fd77-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="4fd77-127">\<? wersji xml = "1.0'? ></span><span class="sxs-lookup"><span data-stu-id="4fd77-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="4fd77-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="4fd77-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="4fd77-129">\<! — Jest to przykładowy dokument XML--></span><span class="sxs-lookup"><span data-stu-id="4fd77-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="4fd77-130">\<! — Jest to przykładowy dokument XML--></span><span class="sxs-lookup"><span data-stu-id="4fd77-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="4fd77-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="4fd77-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="4fd77-132">\<! Elementy DOCTYPE [\<! Numer jednostki "123" >] ></span><span class="sxs-lookup"><span data-stu-id="4fd77-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="4fd77-133">\<! Elementy DOCTYPE [\<! Numer jednostki "123" >]</span><span class="sxs-lookup"><span data-stu-id="4fd77-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="4fd77-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="4fd77-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="4fd77-135">\<Elementy ></span><span class="sxs-lookup"><span data-stu-id="4fd77-135">\<Items></span></span>|<span data-ttu-id="4fd77-136">\<Elementy ></span><span class="sxs-lookup"><span data-stu-id="4fd77-136">\<Items></span></span>|<span data-ttu-id="4fd77-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-138">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-138">\<Item></span></span>|<span data-ttu-id="4fd77-139">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-139">\<Item></span></span>|<span data-ttu-id="4fd77-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-141">Testowanie za pomocą jednostki: &number;</span><span class="sxs-lookup"><span data-stu-id="4fd77-141">Test with an entity: &number;</span></span>|<span data-ttu-id="4fd77-142">Test z jednostką: 123</span><span class="sxs-lookup"><span data-stu-id="4fd77-142">Test with an entity: 123</span></span>|<span data-ttu-id="4fd77-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4fd77-144">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-144">\</Item></span></span>|<span data-ttu-id="4fd77-145">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-145">\</Item></span></span>|<span data-ttu-id="4fd77-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4fd77-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4fd77-147">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-147">\<Item></span></span>|<span data-ttu-id="4fd77-148">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-148">\<Item></span></span>|<span data-ttu-id="4fd77-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-150">Testowanie za pomocą elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="4fd77-150">test with a child element</span></span>|<span data-ttu-id="4fd77-151">Testowanie za pomocą elementu podrzędnego</span><span class="sxs-lookup"><span data-stu-id="4fd77-151">test with a child element</span></span>|<span data-ttu-id="4fd77-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4fd77-153">\<więcej ></span><span class="sxs-lookup"><span data-stu-id="4fd77-153">\<more></span></span>|<span data-ttu-id="4fd77-154">\<więcej ></span><span class="sxs-lookup"><span data-stu-id="4fd77-154">\<more></span></span>|<span data-ttu-id="4fd77-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-156">rzeczy</span><span class="sxs-lookup"><span data-stu-id="4fd77-156">stuff</span></span>|<span data-ttu-id="4fd77-157">rzeczy</span><span class="sxs-lookup"><span data-stu-id="4fd77-157">stuff</span></span>|<span data-ttu-id="4fd77-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4fd77-159">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-159">\</Item></span></span>|<span data-ttu-id="4fd77-160">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-160">\</Item></span></span>|<span data-ttu-id="4fd77-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4fd77-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4fd77-162">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-162">\<Item></span></span>|<span data-ttu-id="4fd77-163">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-163">\<Item></span></span>|<span data-ttu-id="4fd77-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-165">Testowanie za pomocą sekcji CDATA</span><span class="sxs-lookup"><span data-stu-id="4fd77-165">test with a CDATA section</span></span>|<span data-ttu-id="4fd77-166">Testowanie za pomocą sekcji CDATA</span><span class="sxs-lookup"><span data-stu-id="4fd77-166">test with a CDATA section</span></span>|<span data-ttu-id="4fd77-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="4fd77-168">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="4fd77-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="4fd77-169">&LT;! [CDATA [\<456 &GT;]]\></span><span class="sxs-lookup"><span data-stu-id="4fd77-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="4fd77-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="4fd77-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="4fd77-171">DEF</span><span class="sxs-lookup"><span data-stu-id="4fd77-171">def</span></span>|<span data-ttu-id="4fd77-172">DEF</span><span class="sxs-lookup"><span data-stu-id="4fd77-172">def</span></span>|<span data-ttu-id="4fd77-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4fd77-174">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-174">\</Item></span></span>|<span data-ttu-id="4fd77-175">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-175">\</Item></span></span>|<span data-ttu-id="4fd77-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4fd77-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4fd77-177">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-177">\<Item></span></span>|<span data-ttu-id="4fd77-178">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-178">\<Item></span></span>|<span data-ttu-id="4fd77-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-180">Test z jednostką char: &\#65;</span><span class="sxs-lookup"><span data-stu-id="4fd77-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="4fd77-181">Test z jednostką char: A</span><span class="sxs-lookup"><span data-stu-id="4fd77-181">Test with a char entity: A</span></span>|<span data-ttu-id="4fd77-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4fd77-183">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-183">\</Item></span></span>|<span data-ttu-id="4fd77-184">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-184">\</Item></span></span>|<span data-ttu-id="4fd77-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4fd77-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4fd77-186">\<!----> Czternastu znaków w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="4fd77-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="4fd77-187">\<----> Czternastu znaków w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="4fd77-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="4fd77-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="4fd77-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="4fd77-189">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-189">\<Item></span></span>|<span data-ttu-id="4fd77-190">\<Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-190">\<Item></span></span>|<span data-ttu-id="4fd77-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4fd77-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4fd77-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="4fd77-192">1234567890ABCD</span></span>|<span data-ttu-id="4fd77-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="4fd77-193">1234567890ABCD</span></span>|<span data-ttu-id="4fd77-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4fd77-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4fd77-195">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-195">\</Item></span></span>|<span data-ttu-id="4fd77-196">\</ Element ></span><span class="sxs-lookup"><span data-stu-id="4fd77-196">\</Item></span></span>|<span data-ttu-id="4fd77-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4fd77-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4fd77-198">\</ Elementy ></span><span class="sxs-lookup"><span data-stu-id="4fd77-198">\</Items></span></span>|<span data-ttu-id="4fd77-199">\</ Elementy ></span><span class="sxs-lookup"><span data-stu-id="4fd77-199">\</Items></span></span>|<span data-ttu-id="4fd77-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4fd77-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="4fd77-201">Musisz wiedzieć, jakiego typu węzła jest przypisany, jako węzeł typ Określa, jakiego rodzaju akcje są prawidłowe i jakiego rodzaju właściwości umożliwia ustawianie i pobieranie.</span><span class="sxs-lookup"><span data-stu-id="4fd77-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="4fd77-202">Tworzenie węzła biały znak jest kontrolowany po załadowaniu danych do modelu DOM, **PreserveWhitespace** flagi.</span><span class="sxs-lookup"><span data-stu-id="4fd77-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="4fd77-203">Aby uzyskać więcej informacji, zobacz [biały znak i znaczące biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="4fd77-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="4fd77-204">Aby dodać nowe węzły do modelu DOM, zobacz [Wstawianie węzłów do dokumentu XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4fd77-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="4fd77-205">Aby usunąć węzły z modelu DOM, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4fd77-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="4fd77-206">Aby zmodyfikować zawartość węzłów w modelu DOM, zobacz [modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4fd77-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd77-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fd77-207">See also</span></span>

- [<span data-ttu-id="4fd77-208">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="4fd77-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
