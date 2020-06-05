---
title: 'Porady: deklarowanie właściwości z mieszanymi poziomami dostępu'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: f0f7aba25888544dfcc093906850ae7ada621182
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388248"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="87211-102">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87211-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="87211-103">Jeśli chcesz, `Get` `Set` aby procedury i dla właściwości miały różne poziomy dostępu, możesz użyć poziomu bardziej ograniczającego w `Property` instrukcji i bardziej restrykcyjnego poziomu w `Get` `Set` instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="87211-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="87211-104">Możesz użyć mieszanych poziomów dostępu dla właściwości, jeśli chcesz, aby niektóre części kodu mogły uzyskać wartość właściwości, a niektóre inne części kodu, aby można było zmienić wartość.</span><span class="sxs-lookup"><span data-stu-id="87211-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="87211-105">Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy dostępu w Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="87211-105">For more information on access levels, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="87211-106">Aby zadeklarować właściwość z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="87211-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="87211-107">Zadeklaruj właściwość w normalny sposób i określ mniej restrykcyjny poziom dostępu (na przykład `Public` ) w `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="87211-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="87211-108">Zadeklaruj albo `Get` `Set` procedurę określającą bardziej restrykcyjny poziom dostępu (na przykład `Friend` ).</span><span class="sxs-lookup"><span data-stu-id="87211-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="87211-109">Nie określaj poziomu dostępu dla innej procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="87211-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="87211-110">Przyjęto założenie poziomu dostępu zadeklarowanego w `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="87211-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="87211-111">Można ograniczyć dostęp tylko do jednej z procedur dotyczących właściwości.</span><span class="sxs-lookup"><span data-stu-id="87211-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="87211-112">W poprzednim przykładzie `Get` procedura ma taki sam `Protected` dostęp jak sama właściwość, podczas gdy `Set` procedura ma `Private` dostęp.</span><span class="sxs-lookup"><span data-stu-id="87211-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="87211-113">Klasa pochodna `employee` może odczytać `salary` wartość, ale `employee` można ją ustawić tylko przez klasę.</span><span class="sxs-lookup"><span data-stu-id="87211-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87211-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87211-114">See also</span></span>

- [<span data-ttu-id="87211-115">Procedury</span><span class="sxs-lookup"><span data-stu-id="87211-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="87211-116">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="87211-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="87211-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="87211-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="87211-118">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="87211-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="87211-119">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87211-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="87211-120">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="87211-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="87211-121">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="87211-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="87211-122">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87211-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="87211-123">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="87211-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="87211-124">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="87211-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
