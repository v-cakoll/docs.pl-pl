---
title: 'Instrukcje: Pobieranie wartości z właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302936"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="85038-102">Instrukcje: Pobieranie wartości z właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85038-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="85038-103">Możesz pobrać wartości właściwości, łącznie z nazwą właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="85038-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="85038-104">Właściwości `Get` procedury pobiera wartość, ale nie zostanie jawnie wywołana je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="85038-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="85038-105">Użyj właściwości, tak samo, jak należy użyć zmiennej.</span><span class="sxs-lookup"><span data-stu-id="85038-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="85038-106">Visual Basic sprawia, że wywołania procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="85038-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="85038-107">Do pobierania wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="85038-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="85038-108">Użyj nazwy właściwości w wyrażeniu taki sam sposób użyje nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="85038-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="85038-109">Można użyć właściwości wszędzie można użyć zmienną lub stałą.</span><span class="sxs-lookup"><span data-stu-id="85038-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="85038-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="85038-110">-or-</span></span>  
  
     <span data-ttu-id="85038-111">Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="85038-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="85038-112">Poniższy przykład odczytuje wartość języka Visual Basic `Now` właściwości i niejawne wywoływanie jej `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="85038-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="85038-113">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="85038-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="85038-114">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="85038-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="85038-115">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="85038-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="85038-116">Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="85038-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="85038-117">Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienna będzie — stała lub jest on przechowywany w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="85038-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85038-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85038-118">See also</span></span>

- [<span data-ttu-id="85038-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="85038-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="85038-120">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="85038-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="85038-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="85038-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="85038-122">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="85038-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="85038-123">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85038-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="85038-124">Instrukcje: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="85038-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="85038-125">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="85038-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="85038-126">Instrukcje: Wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="85038-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="85038-127">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85038-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="85038-128">Instrukcje: Umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="85038-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
