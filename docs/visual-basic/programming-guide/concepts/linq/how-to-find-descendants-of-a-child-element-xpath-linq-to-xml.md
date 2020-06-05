---
title: 'Instrukcje: znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
ms.openlocfilehash: aa6a66f4a53fc74b5946a395f7b61218e680f530
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405225"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać elementy podrzędne elementu podrzędnego o określonej nazwie.  
  
 Wyrażenie XPath:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Przykład  
 Ten przykład symuluje problemy związane z wyodrębnianiem tekstu z reprezentacji XML dokumentu przetwarzania tekstów. Najpierw zaznacza wszystkie `Paragraph` elementy, a następnie wybiera wszystkie elementy `Text` zależne każdego `Paragraph` elementu. Nie wybrano elementów potomnych `Text` `Comment` elementu.  
  
```vb  
Dim root As XElement = _  
    <Root>  
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
            <Text>This is a second sentence.</Text>  
        </Paragraph>  
    </Root>  
  
' LINQ to XML query  
Dim str1 As String = _  
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _  
    Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
' XPath expression  
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _  
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _  
    .Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
If str1 = str2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(str2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to XML dla użytkowników XPath (Visual Basic)](linq-to-xml-for-xpath-users.md)
