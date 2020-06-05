---
title: Serializowanie przy użyciu deklaracji XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: cd303a800efe42d3fa99d601f25d54320570bed3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411804"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="e7209-102">Serializacja przy użyciu deklaracji XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7209-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="e7209-103">W tym temacie opisano sposób kontrolowania, czy Serializacja generuje deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="e7209-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="e7209-104">Generowanie deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="e7209-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="e7209-105">Serializacja do metody lub metody, <xref:System.IO.File> <xref:System.IO.TextWriter> <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> lub <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> Metoda generuje deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="e7209-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="e7209-106">Podczas serializacji do <xref:System.Xml.XmlWriter> , ustawienia składnika zapisywania (określone w <xref:System.Xml.XmlWriterSettings> obiekcie) określają, czy deklaracja XML jest generowana, czy nie.</span><span class="sxs-lookup"><span data-stu-id="e7209-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="e7209-107">W przypadku serializacji do ciągu przy użyciu `ToString` metody, otrzymany kod XML nie będzie zawierał deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="e7209-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="e7209-108">Serializowanie przy użyciu deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="e7209-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="e7209-109">Poniższy przykład tworzy <xref:System.Xml.Linq.XElement> , zapisuje dokument do pliku, a następnie drukuje plik do konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="e7209-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="e7209-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e7209-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="e7209-111">Serializacja bez deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="e7209-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="e7209-112">Poniższy przykład pokazuje, jak zapisać element <xref:System.Xml.Linq.XElement> w <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e7209-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="e7209-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e7209-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7209-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7209-114">See also</span></span>

- [<span data-ttu-id="e7209-115">Serializowanie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7209-115">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
