---
title: 'Instrukcje: Prefiksy Namespace kontroli (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 91117307caf7e55bd8b512fbd841760616f0b2c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623745"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="dc574-102">Instrukcje: Prefiksy Namespace kontroli (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc574-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="dc574-103">W tym temacie opisano, jak można kontrolować prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dc574-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc574-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc574-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dc574-105">Opis</span><span class="sxs-lookup"><span data-stu-id="dc574-105">Description</span></span>  
 <span data-ttu-id="dc574-106">Ten przykład deklaruje dwie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dc574-106">This example declares two namespaces.</span></span> <span data-ttu-id="dc574-107">Określa, że `http://www.adventure-works.com` przestrzeni nazw ma prefiks `aw`oraz że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.</span><span class="sxs-lookup"><span data-stu-id="dc574-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dc574-108">Kod</span><span class="sxs-lookup"><span data-stu-id="dc574-108">Code</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="dc574-109">Komentarze</span><span class="sxs-lookup"><span data-stu-id="dc574-109">Comments</span></span>  
 <span data-ttu-id="dc574-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="dc574-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc574-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc574-111">See also</span></span>
- [<span data-ttu-id="dc574-112">Praca z przestrzeniami nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc574-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
