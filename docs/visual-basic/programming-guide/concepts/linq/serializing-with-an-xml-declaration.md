---
title: "Serializacja z deklaracją XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8544157104b202a36f2ef75b069bcdd297b9158
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="fd9ff-102">Serializacja z deklaracją XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="fd9ff-103">W tym temacie opisano sposób kontrolowania, czy serializacji generuje deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="fd9ff-104">Generowanie deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="fd9ff-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="fd9ff-105">Serializacja do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy użyciu <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody lub <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="fd9ff-106">Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawień edytora (określony w <xref:System.Xml.XmlWriterSettings> obiektu) ustalić, czy deklaracja XML jest generowany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="fd9ff-107">Jeśli są serializacji przy użyciu ciągu `ToString` metody, wynikowy kod XML nie zostaną uwzględnione w deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="fd9ff-108">Serializacja z deklaracją XML</span><span class="sxs-lookup"><span data-stu-id="fd9ff-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="fd9ff-109">Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>, dokument jest zapisywany do pliku i następnie drukuje plik do konsoli:</span><span class="sxs-lookup"><span data-stu-id="fd9ff-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="fd9ff-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fd9ff-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="fd9ff-111">Serializacja bez deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="fd9ff-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="fd9ff-112">Poniższy przykład przedstawia sposób zapisania <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="fd9ff-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fd9ff-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd9ff-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd9ff-114">See Also</span></span>  
 [<span data-ttu-id="fd9ff-115">Serializacja drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
