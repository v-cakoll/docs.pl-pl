---
title: 'Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: ff260660057c3b75f4cc92c37c67fca0a0b7f192
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347574"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="bc723-102">Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc723-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bc723-103">W tym temacie przedstawiono metodę <xref:System.Xml.Linq.XElement.Attributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc723-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="bc723-104">Ta metoda pobiera atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="bc723-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc723-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc723-105">Example</span></span>  
 <span data-ttu-id="bc723-106">Poniższy przykład pokazuje, jak wykonać iterację kolekcji atrybutów elementu.</span><span class="sxs-lookup"><span data-stu-id="bc723-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 <span data-ttu-id="bc723-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bc723-107">This code produces the following output:</span></span>  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc723-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc723-108">See also</span></span>

- [<span data-ttu-id="bc723-109">Osie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc723-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
