---
title: Serializacja za pomocą deklaracji XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483485"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="bed55-102">Serializacja za pomocą deklaracji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bed55-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="bed55-103">W tym temacie opisano, jak kontrolować, czy serializacja generuje deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="bed55-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="bed55-104">Generowanie deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="bed55-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="bed55-105">Serializacji do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> użyciu <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metody lub metody generuje deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="bed55-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="bed55-106">Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawienia modułu zapisu <xref:System.Xml.XmlWriterSettings> (określone w obiekcie) określić, czy deklaracja XML jest generowany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="bed55-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="bed55-107">Jeśli serializacji do ciągu przy `ToString` użyciu metody, wynikowy Kod XML nie będzie zawierać deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="bed55-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="bed55-108">Serializowanie przy użyciu deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="bed55-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="bed55-109">Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>plik , zapisuje dokument w pliku, a następnie drukuje plik na konsoli:</span><span class="sxs-lookup"><span data-stu-id="bed55-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="bed55-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="bed55-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="bed55-111">Serializacja bez deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="bed55-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="bed55-112">W poniższym przykładzie pokazano, jak zapisać do <xref:System.Xml.Linq.XElement> . <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="bed55-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="bed55-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="bed55-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bed55-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bed55-114">See also</span></span>

- [<span data-ttu-id="bed55-115">Serializujące drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bed55-115">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
