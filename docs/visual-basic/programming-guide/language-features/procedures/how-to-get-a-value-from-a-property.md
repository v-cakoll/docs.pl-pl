---
title: 'Porady: pobieranie wartości z właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 2c92cd4a869acbb7c8c52fbf4117112967386498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387897"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="527ff-102">Porady: pobieranie wartości z właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="527ff-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="527ff-103">Wartość właściwości jest pobierana przez dołączenie nazwy właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="527ff-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="527ff-104">`Get`Procedura właściwości Pobiera wartość, ale nie jest jawnie wywoływana przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="527ff-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="527ff-105">Właściwość jest używana tak samo jak w przypadku użycia zmiennej.</span><span class="sxs-lookup"><span data-stu-id="527ff-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="527ff-106">Visual Basic wykonuje wywołania procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="527ff-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="527ff-107">Aby pobrać wartość z właściwości</span><span class="sxs-lookup"><span data-stu-id="527ff-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="527ff-108">Użyj nazwy właściwości w wyrażeniu tak samo jak w przypadku użycia nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="527ff-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="527ff-109">Możesz użyć właściwości wszędzie tam, gdzie można użyć zmiennej lub stałej.</span><span class="sxs-lookup"><span data-stu-id="527ff-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="527ff-110">-lub-</span><span class="sxs-lookup"><span data-stu-id="527ff-110">-or-</span></span>  
  
     <span data-ttu-id="527ff-111">Użyj nazwy właściwości następującego po znaku równości ( `=` ) w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="527ff-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="527ff-112">Poniższy przykład odczytuje wartość `Now` właściwości Visual Basic, niejawnie wywołując swoją `Get` procedurę.</span><span class="sxs-lookup"><span data-stu-id="527ff-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="527ff-113">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów.</span><span class="sxs-lookup"><span data-stu-id="527ff-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="527ff-114">Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="527ff-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="527ff-115">Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="527ff-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="527ff-116">Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.</span><span class="sxs-lookup"><span data-stu-id="527ff-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="527ff-117">Wartość właściwości uczestniczy w wyrażeniu tak samo jak zmienna lub stała lub jest przechowywana we właściwości lub właściwość po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="527ff-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527ff-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="527ff-118">See also</span></span>

- [<span data-ttu-id="527ff-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="527ff-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="527ff-120">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="527ff-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="527ff-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="527ff-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="527ff-122">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="527ff-122">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="527ff-123">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="527ff-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="527ff-124">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="527ff-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="527ff-125">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="527ff-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="527ff-126">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="527ff-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="527ff-127">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="527ff-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="527ff-128">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="527ff-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
