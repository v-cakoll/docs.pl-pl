---
title: 'Porady: kontrolowanie prefiksy Namespace (LINQ do XML) (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a48feeb25cc8d28d57edc7421f73b2829f8c19ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="5920f-102">Porady: kontrolowanie prefiksy Namespace (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5920f-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="5920f-103">W tym temacie opisano, jak można kontrolować prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5920f-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5920f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5920f-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5920f-105">Opis</span><span class="sxs-lookup"><span data-stu-id="5920f-105">Description</span></span>  
 <span data-ttu-id="5920f-106">W tym przykładzie deklaruje dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="5920f-106">This example declares two namespaces.</span></span> <span data-ttu-id="5920f-107">Określa, że `http://www.adventure-works.com` przestrzeń nazw ma prefiks `aw`oraz że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.</span><span class="sxs-lookup"><span data-stu-id="5920f-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5920f-108">Kod</span><span class="sxs-lookup"><span data-stu-id="5920f-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="5920f-109">Komentarze</span><span class="sxs-lookup"><span data-stu-id="5920f-109">Comments</span></span>  
 <span data-ttu-id="5920f-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5920f-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5920f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5920f-111">See Also</span></span>  
 [<span data-ttu-id="5920f-112">Praca z przestrzeni nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5920f-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
