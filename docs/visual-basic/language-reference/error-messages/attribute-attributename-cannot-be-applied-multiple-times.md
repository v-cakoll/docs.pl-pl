---
title: Nie można wielokrotnie zastosować atrybutu „<attributename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: da4a766e2617308cb33b9673a88db9e7a954152a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304301"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="e96ea-102">Atrybut "\<attributename >" nie można zastosować wiele razy</span><span class="sxs-lookup"><span data-stu-id="e96ea-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="e96ea-103">Ten atrybut można zastosować tylko raz.</span><span class="sxs-lookup"><span data-stu-id="e96ea-103">The attribute can only be applied once.</span></span> <span data-ttu-id="e96ea-104">`AttributeUsage` Atrybut określa, czy atrybut można zastosować więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="e96ea-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="e96ea-105">**Identyfikator błędu:** BC30663</span><span class="sxs-lookup"><span data-stu-id="e96ea-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e96ea-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e96ea-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e96ea-107">Upewnij się, że ten atrybut jest stosowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="e96ea-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="e96ea-108">Jeśli używasz atrybutów niestandardowych, które utworzono, należy rozważyć zmianę ich `AttributeUsage` atrybutu, aby zezwolić na użycie wielu atrybutu, podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e96ea-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e96ea-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e96ea-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="e96ea-110">Tworzenie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e96ea-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="e96ea-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="e96ea-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
