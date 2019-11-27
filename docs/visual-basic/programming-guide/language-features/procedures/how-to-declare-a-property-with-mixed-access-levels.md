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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349693"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="53788-102">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53788-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="53788-103">Jeśli chcesz, aby procedury `Get` i `Set` na właściwości miały różne poziomy dostępu, możesz użyć poziomu bardziej ograniczającego w instrukcji `Property` i bardziej restrykcyjnego poziomu w instrukcji `Get` lub `Set`.</span><span class="sxs-lookup"><span data-stu-id="53788-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="53788-104">Możesz użyć mieszanych poziomów dostępu dla właściwości, jeśli chcesz, aby niektóre części kodu mogły uzyskać wartość właściwości, a niektóre inne części kodu, aby można było zmienić wartość.</span><span class="sxs-lookup"><span data-stu-id="53788-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="53788-105">Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="53788-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="53788-106">Aby zadeklarować właściwość z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="53788-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="53788-107">Zadeklaruj właściwość w normalny sposób i określ mniej restrykcyjny poziom dostępu (taki jak `Public`) w instrukcji `Property`.</span><span class="sxs-lookup"><span data-stu-id="53788-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="53788-108">Zadeklaruj `Get` lub procedurę `Set` określającą bardziej restrykcyjny poziom dostępu (na przykład `Friend`).</span><span class="sxs-lookup"><span data-stu-id="53788-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="53788-109">Nie określaj poziomu dostępu dla innej procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="53788-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="53788-110">Przyjęto założenie poziomu dostępu zadeklarowanego w instrukcji `Property`.</span><span class="sxs-lookup"><span data-stu-id="53788-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="53788-111">Można ograniczyć dostęp tylko do jednej z procedur dotyczących właściwości.</span><span class="sxs-lookup"><span data-stu-id="53788-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="53788-112">W poprzednim przykładzie procedura `Get` ma taki sam `Protected` dostęp jak sama właściwość, podczas gdy procedura `Set` ma `Private` dostępu.</span><span class="sxs-lookup"><span data-stu-id="53788-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="53788-113">Klasa pochodna `employee` może odczytać wartość `salary`, ale można ją ustawić tylko przez klasę `employee`.</span><span class="sxs-lookup"><span data-stu-id="53788-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53788-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53788-114">See also</span></span>

- [<span data-ttu-id="53788-115">Procedury</span><span class="sxs-lookup"><span data-stu-id="53788-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="53788-116">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="53788-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="53788-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="53788-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="53788-118">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="53788-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="53788-119">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53788-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="53788-120">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="53788-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="53788-121">Instrukcje: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="53788-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="53788-122">Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53788-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="53788-123">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="53788-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="53788-124">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="53788-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
