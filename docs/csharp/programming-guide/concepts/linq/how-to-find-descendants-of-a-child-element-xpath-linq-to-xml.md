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
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Jak znaleźć elementy podrzędne elementu podrzędnego (XPath-LINQ do XML) (C#)
W tym temacie pokazano, jak uzyskać elementy podrzędne elementu podrzędnego o określonej nazwie.  
  
 Wyrażenie XPath jest następujące:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie symuluje problemy z wyodrębnianiem tekstu z reprezentacji XML dokumentu edytora tekstu. Najpierw zaznacza `Paragraph` wszystkie elementy, a następnie `Text` wybiera wszystkie `Paragraph` elementy podrzędne każdego elementu. Nie oznacza to wybrania elementów `Comment` podrzędnych `Text` elementu.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  