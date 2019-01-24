---
title: 'Instrukcje: Znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: ac5be4acc7d90dcbae3596f6fd253025ae4577b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708460"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="67f72-102">Instrukcje: Znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="67f72-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="67f72-103">W tym temacie pokazano, jak można pobrać elementów podrzędnych elementu podrzędnego o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="67f72-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="67f72-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="67f72-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="67f72-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="67f72-105">Example</span></span>  
 <span data-ttu-id="67f72-106">W tym przykładzie symuluje problemów możliwości wyodrębniania tekstu z Reprezentacja XML dokumentu tekstów.</span><span class="sxs-lookup"><span data-stu-id="67f72-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="67f72-107">Wybiera pierwszy wszystkie `Paragraph` zaznacza wszystkie elementy, a następnie `Text` elementów podrzędnych każdego `Paragraph` elementu.</span><span class="sxs-lookup"><span data-stu-id="67f72-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="67f72-108">To nie wybierze obiekt podrzędny `Text` elementy `Comment` elementu.</span><span class="sxs-lookup"><span data-stu-id="67f72-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="67f72-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="67f72-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="67f72-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67f72-110">See also</span></span>

- [<span data-ttu-id="67f72-111">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="67f72-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
