---
title: Nie można wielokrotnie zastosować atrybutu „<attributename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968224"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="33e05-102">Nie można wielokrotnie zastosować atrybutu "\<AttributeName >"</span><span class="sxs-lookup"><span data-stu-id="33e05-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="33e05-103">Ten atrybut może być stosowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="33e05-103">The attribute can only be applied once.</span></span> <span data-ttu-id="33e05-104">Atrybut `AttributeUsage` określa, czy atrybut może być stosowany więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="33e05-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="33e05-105">**Identyfikator błędu:** BC30663</span><span class="sxs-lookup"><span data-stu-id="33e05-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33e05-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="33e05-106">To correct this error</span></span>  
  
1. <span data-ttu-id="33e05-107">Upewnij się, że atrybut jest stosowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="33e05-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="33e05-108">Jeśli używasz niestandardowych atrybutów, Rozważ zmianę ich atrybutu `AttributeUsage`, aby zezwolić na użycie wielu atrybutów, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="33e05-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33e05-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33e05-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="33e05-110">Tworzenie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="33e05-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="33e05-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="33e05-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
