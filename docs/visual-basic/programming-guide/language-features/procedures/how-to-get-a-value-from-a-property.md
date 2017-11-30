---
title: "Porady: pobieranie wartości z właściwości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="19fd5-102">Porady: pobieranie wartości z właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19fd5-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="19fd5-103">Możesz pobrać wartości właściwości, łącznie z nazwą właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="19fd5-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="19fd5-104">Właściwość `Get` procedury pobiera wartość, ale nie zostanie jawnie wywołana go według nazwy.</span><span class="sxs-lookup"><span data-stu-id="19fd5-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="19fd5-105">Użyj właściwości, tak jak w przypadku zmiennej.</span><span class="sxs-lookup"><span data-stu-id="19fd5-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="19fd5-106">wykonywania wywołań do procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="19fd5-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="19fd5-107">Aby pobrać wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="19fd5-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="19fd5-108">Użyj nazwy właściwości w wyrażeniu taki sam sposób, należy użyć nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="19fd5-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="19fd5-109">Można użyć właściwości dowolnym można użyć zmiennej lub stałą.</span><span class="sxs-lookup"><span data-stu-id="19fd5-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="19fd5-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="19fd5-110">-or-</span></span>  
  
     <span data-ttu-id="19fd5-111">Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="19fd5-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="19fd5-112">Poniższy przykład odczytuje wartość [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` właściwości niejawnie wywoływanie jej `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="19fd5-112">The following example reads the value of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  <span data-ttu-id="19fd5-113">Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="19fd5-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="19fd5-114">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="19fd5-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="19fd5-115">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="19fd5-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="19fd5-116">Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="19fd5-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="19fd5-117">Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienną czy stałą lub jest ona przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="19fd5-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fd5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19fd5-118">See Also</span></span>  
 [<span data-ttu-id="19fd5-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="19fd5-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="19fd5-120">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="19fd5-120">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="19fd5-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="19fd5-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="19fd5-122">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="19fd5-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="19fd5-123">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19fd5-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="19fd5-124">Porady: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="19fd5-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="19fd5-125">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="19fd5-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="19fd5-126">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="19fd5-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="19fd5-127">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19fd5-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="19fd5-128">Porady: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="19fd5-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
