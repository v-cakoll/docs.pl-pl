---
title: 'Porady: znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 3f67ac24d12e7d2fcbd74e2f27a75d982c1cf00b
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2018
ms.locfileid: "42751942"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Porady: znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (Visual Basic)
Wyrażenie XPath umożliwia znajdowanie Unii wyniki z dwóch ścieżek lokalizacji XPath.  
  
 Wyrażenie XPath jest:  
  
 `//Category|//Price`  
  
 Te same wyniki można osiągnąć za pomocą <xref:System.Linq.Enumerable.Concat%2A> standardowego operatora zapytania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje wszystkie `Category` elementy i wszystkie `Price` elementy i łączy je w jedną kolekcję. Należy pamiętać, że [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania wywołania <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> aby uporządkować wyniki. Wynikiem obliczenia wyrażenia XPath są również w kolejności dokumentu.  
  
 W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to XML dla użytkowników metody XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
