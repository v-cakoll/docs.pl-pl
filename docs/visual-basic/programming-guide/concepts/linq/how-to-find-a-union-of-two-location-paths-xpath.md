---
title: 'Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: db9ba3f66bfa8643738203ec05a106bab4193fda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352983"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (Visual Basic)
Wyrażenie XPath umożliwia znalezienie związku z wynikami dwóch ścieżek lokalizacji XPath.  
  
 Wyrażenie XPath:  
  
 `//Category|//Price`  
  
 Można osiągnąć te same wyniki przy użyciu standardowego operatora zapytań <xref:System.Linq.Enumerable.Concat%2A>.  
  
## <a name="example"></a>Przykład  
 Ten przykład znajduje wszystkie elementy `Category` i wszystkie elementy `Price` i łączy je w jedną kolekcję. Należy zauważyć, że zapytanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołuje <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> w celu uporządkowania wyników. Wyniki obliczania wyrażenia XPath również są w kolejności dokumentu.  
  
 Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
```console
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
