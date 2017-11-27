---
title: "Porady: umieszczanie wartości we właściwości (Visual Basic)"
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
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44e7c4a92ea3d087c12e74aa2ede33a52c8730cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="d4dba-102">Porady: umieszczanie wartości we właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4dba-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="d4dba-103">Wartości są przechowywane we właściwości ustawiając właściwości nazwy po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="d4dba-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="d4dba-104">Właściwość `Set` procedury przechowuje wartość, ale nie zostanie jawnie wywołana go według nazwy.</span><span class="sxs-lookup"><span data-stu-id="d4dba-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="d4dba-105">Użyj właściwości, tak jak w przypadku zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d4dba-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="d4dba-106">wykonywania wywołań do procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="d4dba-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="d4dba-107">Do przechowywania wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="d4dba-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="d4dba-108">Po lewej stronie instrukcji przypisania, należy użyć nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="d4dba-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="d4dba-109">W poniższym przykładzie ustawiono wartość [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` właściwości południe niejawnie wywoływanie jej `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="d4dba-109">The following example sets the value of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="d4dba-110">Jeśli właściwość przyjmuje argumenty, wykonaj nazwa właściwości w nawiasach należy ująć listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="d4dba-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d4dba-111">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="d4dba-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="d4dba-112">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="d4dba-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d4dba-113">Upewnij się, że podać argumenty w tej samej kolejności, że właściwość definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="d4dba-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="d4dba-114">Generowane po prawej stronie instrukcji przypisania wartość jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="d4dba-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4dba-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4dba-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="d4dba-116">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="d4dba-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="d4dba-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="d4dba-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d4dba-118">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="d4dba-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="d4dba-119">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4dba-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="d4dba-120">Porady: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="d4dba-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="d4dba-121">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="d4dba-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="d4dba-122">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="d4dba-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="d4dba-123">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4dba-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="d4dba-124">Porady: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="d4dba-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
