---
title: 'Porady: pobieranie wartości z właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 9f97669e8d18e7fc633cb0e691d973a611a8cea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="660d2-102">Porady: pobieranie wartości z właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="660d2-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="660d2-103">Możesz pobrać wartości właściwości, łącznie z nazwą właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="660d2-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="660d2-104">Właściwość `Get` procedury pobiera wartość, ale nie zostanie jawnie wywołana go według nazwy.</span><span class="sxs-lookup"><span data-stu-id="660d2-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="660d2-105">Użyj właściwości, tak jak w przypadku zmiennej.</span><span class="sxs-lookup"><span data-stu-id="660d2-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="660d2-106">Visual Basic wywołań procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="660d2-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="660d2-107">Aby pobrać wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="660d2-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="660d2-108">Użyj nazwy właściwości w wyrażeniu taki sam sposób, należy użyć nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="660d2-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="660d2-109">Można użyć właściwości dowolnym można użyć zmiennej lub stałą.</span><span class="sxs-lookup"><span data-stu-id="660d2-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="660d2-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="660d2-110">-or-</span></span>  
  
     <span data-ttu-id="660d2-111">Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="660d2-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="660d2-112">Poniższy przykład odczytuje wartość Visual Basic `Now` właściwości niejawnie wywoływanie jej `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="660d2-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  <span data-ttu-id="660d2-113">Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="660d2-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="660d2-114">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="660d2-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="660d2-115">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="660d2-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="660d2-116">Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="660d2-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="660d2-117">Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienną czy stałą lub jest ona przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="660d2-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660d2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="660d2-118">See Also</span></span>  
 [<span data-ttu-id="660d2-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="660d2-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="660d2-120">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="660d2-120">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="660d2-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="660d2-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="660d2-122">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="660d2-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="660d2-123">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="660d2-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="660d2-124">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="660d2-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="660d2-125">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="660d2-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="660d2-126">Instrukcje: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="660d2-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="660d2-127">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="660d2-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="660d2-128">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="660d2-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
