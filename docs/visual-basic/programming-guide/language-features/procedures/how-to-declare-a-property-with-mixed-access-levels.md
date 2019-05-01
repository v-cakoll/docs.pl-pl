---
title: 'Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)'
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
ms.openlocfilehash: e899b57e02f492b0e4909aca84c069e5b7688618
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863691"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="35c92-102">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35c92-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="35c92-103">Jeśli chcesz `Get` i `Set` procedury dotyczące właściwości, aby mieć różne poziomy dostępu, możesz użyć mniej ograniczająca poziom w `Property` instrukcji i bardziej restrykcyjny poziom albo `Get` lub `Set` Instrukcja.</span><span class="sxs-lookup"><span data-stu-id="35c92-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="35c92-104">Za pomocą mieszanymi poziomami dostępu we właściwości niektórych części kodu, aby można było pobrać wartości właściwości, a niektóre części kodu, aby można było zmienić wartość.</span><span class="sxs-lookup"><span data-stu-id="35c92-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="35c92-105">Aby uzyskać więcej informacji na temat poziomów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="35c92-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="35c92-106">Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="35c92-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="35c92-107">Zadeklaruj właściwość w normalny sposób i określić poziom dostępu mniej restrykcyjny (takie jak `Public`) w `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="35c92-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="35c92-108">Zadeklaruj jedną `Get` lub `Set` procedurę, określając bardziej restrykcyjny poziom dostępu (takich jak `Friend`).</span><span class="sxs-lookup"><span data-stu-id="35c92-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="35c92-109">Na innej procedury właściwość nie zostanie określony poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="35c92-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="35c92-110">Przyjęto założenie, poziom dostępu, zadeklarowany w `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="35c92-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="35c92-111">Możesz ograniczyć dostęp tylko dla jednej z procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="35c92-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="35c92-112">W poprzednim przykładzie `Get` procedura ma taką samą `Protected` dostępu jako właściwość, podczas gdy `Set` procedura ma `Private` dostępu.</span><span class="sxs-lookup"><span data-stu-id="35c92-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="35c92-113">Klasa pochodząca z `employee` może odczytywać `salary` wartość, ale tylko `employee` klasy można ustawić go.</span><span class="sxs-lookup"><span data-stu-id="35c92-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c92-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35c92-114">See also</span></span>

- [<span data-ttu-id="35c92-115">Procedury</span><span class="sxs-lookup"><span data-stu-id="35c92-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="35c92-116">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="35c92-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="35c92-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="35c92-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="35c92-118">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="35c92-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="35c92-119">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35c92-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="35c92-120">Instrukcje: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="35c92-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="35c92-121">Instrukcje: Wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="35c92-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="35c92-122">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35c92-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="35c92-123">Instrukcje: Umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="35c92-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="35c92-124">Instrukcje: Pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="35c92-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
