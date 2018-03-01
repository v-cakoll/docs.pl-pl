---
title: "Atrybut &#39; &lt;attributename&gt;&#39; nie można zastosować wiele razy"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="d1b03-102">Atrybut &#39; &lt;attributename&gt;&#39; nie można zastosować wiele razy</span><span class="sxs-lookup"><span data-stu-id="d1b03-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="d1b03-103">Ten atrybut można zastosować tylko raz.</span><span class="sxs-lookup"><span data-stu-id="d1b03-103">The attribute can only be applied once.</span></span> <span data-ttu-id="d1b03-104">`AttributeUsage` Atrybut określa, czy atrybut można zastosować więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="d1b03-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="d1b03-105">**Identyfikator błędu:** BC30663</span><span class="sxs-lookup"><span data-stu-id="d1b03-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1b03-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d1b03-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="d1b03-107">Upewnij się, że ten atrybut jest stosowana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="d1b03-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="d1b03-108">Jeśli korzystasz z atrybutów niestandardowych, które utworzono, należy rozważyć zmianę ich `AttributeUsage` atrybutu aby umożliwić użycie atrybutu wiele, podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d1b03-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1b03-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1b03-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="d1b03-110">Tworzenie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d1b03-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="d1b03-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="d1b03-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
