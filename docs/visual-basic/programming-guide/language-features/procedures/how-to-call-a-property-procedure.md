---
title: 'Porady: wywoływanie procedury właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 006961a0f1d4be6b0d52be5bc273dad9733bfe56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388702"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="e5835-102">Porady: wywoływanie procedury właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5835-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="e5835-103">Wywoływanie procedury właściwości przez zapisanie wartości we właściwości lub pobranie jej wartości.</span><span class="sxs-lookup"><span data-stu-id="e5835-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="e5835-104">Dostęp do właściwości jest taki sam jak w przypadku dostępu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e5835-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="e5835-105">`Set`Procedura właściwości przechowuje wartość, a jej `Get` procedura Pobiera wartość.</span><span class="sxs-lookup"><span data-stu-id="e5835-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="e5835-106">Jednak te procedury nie są jawnie wywoływane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="e5835-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="e5835-107">Używasz właściwości w instrukcji przypisania lub wyrażeniu, tak jak w przypadku przechowywania lub pobierania wartości zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e5835-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="e5835-108">Visual Basic wykonuje wywołania procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5835-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="e5835-109">Aby wywołać procedurę pobierania właściwości</span><span class="sxs-lookup"><span data-stu-id="e5835-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="e5835-110">Użyj nazwy właściwości w wyrażeniu tak samo jak w przypadku użycia nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e5835-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="e5835-111">Możesz użyć właściwości wszędzie tam, gdzie można użyć zmiennej lub stałej.</span><span class="sxs-lookup"><span data-stu-id="e5835-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="e5835-112">-lub-</span><span class="sxs-lookup"><span data-stu-id="e5835-112">-or-</span></span>  
  
     <span data-ttu-id="e5835-113">Użyj nazwy właściwości następującego po znaku równości ( `=` ) w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e5835-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="e5835-114">Poniższy przykład odczytuje wartość <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> właściwości, niejawnie wywołując swoją `Get` procedurę.</span><span class="sxs-lookup"><span data-stu-id="e5835-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="e5835-115">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów.</span><span class="sxs-lookup"><span data-stu-id="e5835-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="e5835-116">Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="e5835-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="e5835-117">Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="e5835-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="e5835-118">Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.</span><span class="sxs-lookup"><span data-stu-id="e5835-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="e5835-119">Wartość właściwości uczestniczy w wyrażeniu tak samo jak zmienna lub stała lub jest przechowywana we właściwości lub właściwość po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e5835-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="e5835-120">Aby wywołać procedurę ustawiania właściwości</span><span class="sxs-lookup"><span data-stu-id="e5835-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="e5835-121">Użyj nazwy właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e5835-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="e5835-122">Poniższy przykład ustawia wartość <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> właściwości, niejawnie wywołując `Set` procedurę.</span><span class="sxs-lookup"><span data-stu-id="e5835-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="e5835-123">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów.</span><span class="sxs-lookup"><span data-stu-id="e5835-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="e5835-124">Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="e5835-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="e5835-125">Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="e5835-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="e5835-126">Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.</span><span class="sxs-lookup"><span data-stu-id="e5835-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="e5835-127">Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5835-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5835-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5835-128">See also</span></span>

- [<span data-ttu-id="e5835-129">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="e5835-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e5835-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="e5835-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e5835-131">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5835-131">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="e5835-132">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5835-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="e5835-133">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="e5835-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="e5835-134">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="e5835-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="e5835-135">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5835-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e5835-136">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="e5835-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="e5835-137">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="e5835-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="e5835-138">Get — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5835-138">Get Statement</span></span>](../../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="e5835-139">Set — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5835-139">Set Statement</span></span>](../../../language-reference/statements/set-statement.md)
