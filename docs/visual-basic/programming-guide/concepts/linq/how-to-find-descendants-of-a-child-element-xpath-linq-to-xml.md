---
title: 'Instrukcje: Znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
ms.openlocfilehash: beb949be521bfde70fbcdbcf18cebf49d7cc5a58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344672"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="91882-102">Instrukcje: Znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91882-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="91882-103">W tym temacie pokazano, jak uzyskać elementy podrzędne elementu podrzędnego o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="91882-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="91882-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="91882-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="91882-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="91882-105">Example</span></span>  
 <span data-ttu-id="91882-106">Ten przykład symuluje problemy związane z wyodrębnianiem tekstu z reprezentacji XML dokumentu przetwarzania tekstów.</span><span class="sxs-lookup"><span data-stu-id="91882-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="91882-107">Najpierw zaznacza wszystkie elementy `Paragraph`, a następnie wybiera wszystkie elementy podrzędne `Text` każdego elementu `Paragraph`.</span><span class="sxs-lookup"><span data-stu-id="91882-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="91882-108">Nie spowoduje to zaznaczenia elementów podrzędnych `Text` elementu `Comment`.</span><span class="sxs-lookup"><span data-stu-id="91882-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="91882-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="91882-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="91882-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91882-110">See also</span></span>

- [<span data-ttu-id="91882-111">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91882-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
