---
title: 'Porady: umieszczanie wartości we właściwości'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: c0fb3e137010390097a68aea161efcff93839d94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414340"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="6e899-102">Porady: umieszczanie wartości we właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e899-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="6e899-103">Wartość właściwości jest przechowywana przez umieszczenie nazwy właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="6e899-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="6e899-104">`Set`Procedura właściwości przechowuje wartość, ale nie jest jawnie wywoływana przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="6e899-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="6e899-105">Właściwość jest używana tak samo jak w przypadku użycia zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6e899-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="6e899-106">Visual Basic wykonuje wywołania procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e899-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="6e899-107">Aby zapisać wartość w właściwości</span><span class="sxs-lookup"><span data-stu-id="6e899-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="6e899-108">Użyj nazwy właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="6e899-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="6e899-109">Poniższy przykład ustawia wartość `TimeOfDay` właściwości Visual Basic na południe, niejawnie wywołując `Set` procedurę.</span><span class="sxs-lookup"><span data-stu-id="6e899-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="6e899-110">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości z nawiasami, aby umieścić listę argumentów.</span><span class="sxs-lookup"><span data-stu-id="6e899-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="6e899-111">Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="6e899-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="6e899-112">Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6e899-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="6e899-113">Upewnij się, że argumenty są podawane w tej samej kolejności, w której Właściwość definiuje odpowiednie parametry.</span><span class="sxs-lookup"><span data-stu-id="6e899-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="6e899-114">Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e899-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e899-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e899-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="6e899-116">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="6e899-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="6e899-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="6e899-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6e899-118">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e899-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="6e899-119">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e899-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="6e899-120">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="6e899-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="6e899-121">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="6e899-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="6e899-122">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="6e899-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="6e899-123">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e899-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="6e899-124">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="6e899-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
