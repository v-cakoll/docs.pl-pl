---
title: 'Instrukcje: Kontrolowanie prefiksów przestrzeni nazw (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 2b89b49aa76df526c08143cad49685386ffd5e7c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709823"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="7a417-102">Instrukcje: Kontrolowanie prefiksów przestrzeni nazw (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7a417-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="7a417-103">W tym temacie opisano sposób kontrolowania prefiksów przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7a417-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a417-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a417-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7a417-105">Opis</span><span class="sxs-lookup"><span data-stu-id="7a417-105">Description</span></span>  
 <span data-ttu-id="7a417-106">Ten przykład deklaruje dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="7a417-106">This example declares two namespaces.</span></span> <span data-ttu-id="7a417-107">Określa, że `http://www.adventure-works.com` przestrzeń nazw ma prefiks `aw`i że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.</span><span class="sxs-lookup"><span data-stu-id="7a417-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7a417-108">Kod</span><span class="sxs-lookup"><span data-stu-id="7a417-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="7a417-109">Komentarze</span><span class="sxs-lookup"><span data-stu-id="7a417-109">Comments</span></span>  
 <span data-ttu-id="7a417-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7a417-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a417-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a417-111">See also</span></span>

- [<span data-ttu-id="7a417-112">Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a417-112">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
