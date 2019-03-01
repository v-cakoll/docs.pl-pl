---
title: 'Instrukcje: Umieszczanie wartości we właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 34348d57db0875d9c2c6192ac754b4f83f515ac4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965473"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="ce9ec-102">Instrukcje: Umieszczanie wartości we właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce9ec-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="ce9ec-103">Wartość jest przechowywana we właściwości, umieszczając nazwę właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="ce9ec-104">Właściwości `Set` procedury przechowuje wartość, ale nie zostanie jawnie wywołana je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="ce9ec-105">Użyj właściwości, tak samo, jak należy użyć zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="ce9ec-106">Visual Basic sprawia, że wywołania procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="ce9ec-107">Do przechowywania wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="ce9ec-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="ce9ec-108">Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="ce9ec-109">W poniższym przykładzie ustawiono wartość języka Visual Basic `TimeOfDay` właściwość południe, niejawnie wywoływania jego `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  <span data-ttu-id="ce9ec-110">Jeśli właściwość przyjmuje argumenty, postępuj zgodnie z nazwą właściwości, za pomocą nawiasów, aby ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="ce9ec-111">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="ce9ec-112">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="ce9ec-113">Upewnij się, że podajesz argumentów w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="ce9ec-114">Wartość generowane po prawej stronie instrukcji przypisania są przechowywane we właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce9ec-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9ec-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce9ec-115">See also</span></span>
- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="ce9ec-116">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="ce9ec-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ce9ec-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="ce9ec-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ce9ec-118">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="ce9ec-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="ce9ec-119">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce9ec-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="ce9ec-120">Instrukcje: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="ce9ec-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="ce9ec-121">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="ce9ec-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="ce9ec-122">Instrukcje: Wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="ce9ec-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="ce9ec-123">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce9ec-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="ce9ec-124">Instrukcje: Pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="ce9ec-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
