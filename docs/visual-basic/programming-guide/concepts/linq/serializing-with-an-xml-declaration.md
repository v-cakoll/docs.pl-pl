---
title: Serializowanie przy użyciu deklaracji XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: f51dacb0f89e1042ba9875bec10a0cb1fe25f889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786441"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="96211-102">Serializowanie przy użyciu deklaracji XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96211-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="96211-103">W tym temacie opisano sposób kontroluje, czy serializacji generuje deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="96211-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="96211-104">Generowanie deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="96211-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="96211-105">Serializowanie do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy użyciu <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody lub <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="96211-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="96211-106">Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawień edytora (określony w <xref:System.Xml.XmlWriterSettings> obiektu) określić, czy deklaracja XML jest generowany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="96211-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="96211-107">Jeśli są serializacji na ciąg za pośrednictwem `ToString` metody, wynikowy kod XML nie zostaną uwzględnione w deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="96211-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="96211-108">Serializowanie przy użyciu deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="96211-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="96211-109">Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>, zapisuje dokument do pliku, a następnie drukuje pliku do konsoli:</span><span class="sxs-lookup"><span data-stu-id="96211-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="96211-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96211-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="96211-111">Serializacja bez deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="96211-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="96211-112">Poniższy przykład pokazuje, jak zapisać <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="96211-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="96211-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96211-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96211-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96211-114">See also</span></span>

- [<span data-ttu-id="96211-115">Serializowanie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96211-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
