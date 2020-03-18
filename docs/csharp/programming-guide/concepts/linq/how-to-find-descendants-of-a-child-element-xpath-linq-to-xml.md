---
title: Jak znaleźć elementy podrzędne elementu podrzędnego (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: fb3e20ce21c1f6d2a71f2f71b8acec7cecf0f3ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141098"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="95cf3-102">Jak znaleźć elementy podrzędne elementu podrzędnego (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="95cf3-102">How to find descendants of a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="95cf3-103">W tym temacie pokazano, jak uzyskać elementy podrzędne elementu podrzędnego o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="95cf3-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="95cf3-104">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="95cf3-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="95cf3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="95cf3-105">Example</span></span>  
 <span data-ttu-id="95cf3-106">W tym przykładzie symuluje problemy z wyodrębnianiem tekstu z reprezentacji XML dokumentu edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="95cf3-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="95cf3-107">Najpierw zaznacza `Paragraph` wszystkie elementy, a następnie `Text` wybiera wszystkie `Paragraph` elementy podrzędne każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="95cf3-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="95cf3-108">Nie oznacza to wybrania elementów `Comment` podrzędnych `Text` elementu.</span><span class="sxs-lookup"><span data-stu-id="95cf3-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="95cf3-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="95cf3-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  