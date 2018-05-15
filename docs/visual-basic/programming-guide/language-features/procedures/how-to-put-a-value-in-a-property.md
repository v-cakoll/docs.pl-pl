---
title: 'Porady: umieszczanie wartości we właściwości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="2e113-102">Porady: umieszczanie wartości we właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e113-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="2e113-103">Wartości są przechowywane we właściwości ustawiając właściwości nazwy po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="2e113-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="2e113-104">Właściwość `Set` procedury przechowuje wartość, ale nie zostanie jawnie wywołana go według nazwy.</span><span class="sxs-lookup"><span data-stu-id="2e113-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="2e113-105">Użyj właściwości, tak jak w przypadku zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2e113-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="2e113-106">Visual Basic wywołań procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e113-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="2e113-107">Do przechowywania wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="2e113-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="2e113-108">Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e113-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="2e113-109">W poniższym przykładzie ustawiono wartość Visual Basic `TimeOfDay` właściwości południe niejawnie wywoływanie jej `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="2e113-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="2e113-110">Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="2e113-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2e113-111">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="2e113-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="2e113-112">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="2e113-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2e113-113">Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="2e113-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="2e113-114">Generowane po prawej stronie instrukcji przypisania wartość jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e113-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e113-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e113-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="2e113-116">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="2e113-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="2e113-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="2e113-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2e113-118">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2e113-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="2e113-119">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e113-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="2e113-120">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="2e113-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="2e113-121">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="2e113-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="2e113-122">Instrukcje: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="2e113-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="2e113-123">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e113-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="2e113-124">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="2e113-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
