---
title: Serializowanie przy użyciu deklaracji XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4f5dd9a7e392acff30814db4a483b297494b68b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702408"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="fdca7-102">Serializowanie przy użyciu deklaracji XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fdca7-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="fdca7-103">W tym temacie opisano sposób kontroluje, czy serializacji generuje deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fdca7-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="fdca7-104">Generowanie deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="fdca7-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="fdca7-105">Serializowanie do <xref:System.IO.File> lub <xref:System.IO.TextWriter> przy użyciu <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody lub <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fdca7-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="fdca7-106">Podczas serializacji do <xref:System.Xml.XmlWriter>, ustawień edytora (określony w <xref:System.Xml.XmlWriterSettings> obiektu) określić, czy deklaracja XML jest generowany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="fdca7-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="fdca7-107">Jeśli są serializacji na ciąg za pośrednictwem `ToString` metody, wynikowy kod XML nie zostaną uwzględnione w deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fdca7-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="fdca7-108">Serializowanie przy użyciu deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="fdca7-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="fdca7-109">Poniższy przykład tworzy <xref:System.Xml.Linq.XElement>, zapisuje dokument do pliku, a następnie drukuje pliku do konsoli:</span><span class="sxs-lookup"><span data-stu-id="fdca7-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="fdca7-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fdca7-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="fdca7-111">Serializacja bez deklaracji XML</span><span class="sxs-lookup"><span data-stu-id="fdca7-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="fdca7-112">Poniższy przykład pokazuje, jak zapisać <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="fdca7-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="fdca7-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fdca7-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdca7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdca7-114">See also</span></span>

- [<span data-ttu-id="fdca7-115">Serializowanie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fdca7-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
