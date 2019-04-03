---
title: 'Instrukcje: Wywoływanie procedury właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 7b85239f80b4bfa87d1dbb1e3207e63d0cef7eeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827214"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="a4c9d-102">Instrukcje: Wywoływanie procedury właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4c9d-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="a4c9d-103">Przechowywanie wartości we właściwości lub pobieranie jej wartość jest wywoływanie procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="a4c9d-104">Możesz uzyskać dostęp do właściwości taki sam sposób, dostęp do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="a4c9d-105">Właściwości `Set` procedury przechowuje wartość, a jego `Get` procedury pobiera wartość.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="a4c9d-106">Jednakże nie zostanie jawnie wywołana tych procedur według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="a4c9d-107">Używasz właściwości w instrukcji przypisania lub wyrażenie, tak jak będzie zapisanie lub pobranie wartości zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="a4c9d-108">Visual Basic sprawia, że wywołania procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="a4c9d-109">Aby wywołać procedura Get właściwości</span><span class="sxs-lookup"><span data-stu-id="a4c9d-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="a4c9d-110">Użyj nazwy właściwości w wyrażeniu taki sam sposób użyje nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="a4c9d-111">Można użyć właściwości wszędzie można użyć zmienną lub stałą.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="a4c9d-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="a4c9d-112">-or-</span></span>  
  
     <span data-ttu-id="a4c9d-113">Użyj nazwy właściwości po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="a4c9d-114">Poniższy przykład odczytuje wartość <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> właściwości i niejawne wywoływanie jej `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2.  <span data-ttu-id="a4c9d-115">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a4c9d-116">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="a4c9d-117">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a4c9d-118">Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="a4c9d-119">Wartość właściwości uczestniczy w wyrażeniu tylko jako zmienna będzie — stała lub jest on przechowywany w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="a4c9d-120">Aby wywołać właściwości ustawione przez procedurę</span><span class="sxs-lookup"><span data-stu-id="a4c9d-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="a4c9d-121">Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="a4c9d-122">W poniższym przykładzie ustawiono wartość <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> właściwości i niejawne wywoływanie `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  <span data-ttu-id="a4c9d-123">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a4c9d-124">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="a4c9d-125">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a4c9d-126">Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="a4c9d-127">Wartość generowane po prawej stronie instrukcji przypisania są przechowywane we właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c9d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4c9d-128">See also</span></span>

- [<span data-ttu-id="a4c9d-129">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="a4c9d-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a4c9d-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="a4c9d-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a4c9d-131">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="a4c9d-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="a4c9d-132">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4c9d-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="a4c9d-133">Instrukcje: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="a4c9d-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="a4c9d-134">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="a4c9d-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="a4c9d-135">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4c9d-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="a4c9d-136">Instrukcje: Umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="a4c9d-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="a4c9d-137">Instrukcje: Pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="a4c9d-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="a4c9d-138">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a4c9d-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="a4c9d-139">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a4c9d-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
