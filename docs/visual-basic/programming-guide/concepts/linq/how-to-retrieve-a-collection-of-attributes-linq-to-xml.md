---
title: 'Porady: pobierania kolekcję atrybutów (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: fdb7f236339de242a887f3040e33b8d24eb114f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641170"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="342c8-102">Porady: pobierania kolekcję atrybutów (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="342c8-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="342c8-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XElement.Attributes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="342c8-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="342c8-104">Ta metoda pobiera atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="342c8-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="342c8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="342c8-105">Example</span></span>  
 <span data-ttu-id="342c8-106">Poniższy przykład pokazuje, jak do iterowania po kolekcji atrybutów elementu.</span><span class="sxs-lookup"><span data-stu-id="342c8-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="342c8-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="342c8-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="342c8-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="342c8-108">See Also</span></span>  
 [<span data-ttu-id="342c8-109">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="342c8-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
