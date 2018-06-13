---
title: 'Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6f796bfb8f8b0051af4e31f6e82a503dbfbbc334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318802"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="852fb-102">Porady: znajdowanie atrybutu nadrzędnego (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="852fb-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="852fb-103">W tym temacie przedstawiono sposób przejdź do elementu nadrzędnego i odnalezienia atrybutu o tym.</span><span class="sxs-lookup"><span data-stu-id="852fb-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="852fb-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="852fb-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="852fb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="852fb-105">Example</span></span>  
 <span data-ttu-id="852fb-106">W tym przykładzie najpierw znajduje `Author` elementu.</span><span class="sxs-lookup"><span data-stu-id="852fb-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="852fb-107">Następnie wyszukuje `id` atrybutu elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="852fb-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="852fb-108">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="852fb-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 <span data-ttu-id="852fb-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="852fb-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="852fb-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="852fb-110">See Also</span></span>  
 [<span data-ttu-id="852fb-111">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="852fb-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
