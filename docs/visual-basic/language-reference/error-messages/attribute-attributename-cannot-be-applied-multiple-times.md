---
title: Atrybut &#39; &lt;attributename&gt; &#39; nie można zastosować wiele razy
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584862"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="36734-102">Atrybut &#39; &lt;attributename&gt; &#39; nie można zastosować wiele razy</span><span class="sxs-lookup"><span data-stu-id="36734-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="36734-103">Ten atrybut można zastosować tylko raz.</span><span class="sxs-lookup"><span data-stu-id="36734-103">The attribute can only be applied once.</span></span> <span data-ttu-id="36734-104">`AttributeUsage` Atrybut określa, czy atrybut można zastosować więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="36734-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="36734-105">**Identyfikator błędu:** BC30663</span><span class="sxs-lookup"><span data-stu-id="36734-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36734-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="36734-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="36734-107">Upewnij się, że ten atrybut jest stosowana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="36734-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="36734-108">Jeśli korzystasz z atrybutów niestandardowych, które utworzono, należy rozważyć zmianę ich `AttributeUsage` atrybutu aby umożliwić użycie atrybutu wiele, podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="36734-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36734-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36734-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="36734-110">Tworzenie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="36734-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="36734-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="36734-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
