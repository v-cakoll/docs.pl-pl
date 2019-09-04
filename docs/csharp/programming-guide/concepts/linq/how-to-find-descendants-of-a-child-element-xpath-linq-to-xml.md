---
title: 'Instrukcje: Znajdź elementy podrzędne elementu podrzędnego (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: f17d723aa03c45daa4e7e741ea6b14c637537ccf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253702"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź elementy podrzędne elementu podrzędnego (XPath-LINQ to XML) (C#)
W tym temacie pokazano, jak uzyskać elementy podrzędne elementu podrzędnego o określonej nazwie.  
  
 Wyrażenie XPath:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Przykład  
 Ten przykład symuluje problemy związane z wyodrębnianiem tekstu z reprezentacji XML dokumentu przetwarzania tekstów. Najpierw zaznacza wszystkie `Paragraph` elementy, a następnie wybiera wszystkie `Text` elementy zależne każdego `Paragraph` elementu. Nie wybrano elementów `Text` `Comment` potomnych elementu.  
  
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
  