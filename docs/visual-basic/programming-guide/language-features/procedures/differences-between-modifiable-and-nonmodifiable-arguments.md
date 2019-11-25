---
title: Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 989795ee2cdd3a78b71bad4d95cf9b384c2719bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341390"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="c4424-102">Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4424-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="c4424-103">When you call a procedure, you typically pass one or more arguments to it.</span><span class="sxs-lookup"><span data-stu-id="c4424-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="c4424-104">Each argument corresponds to an underlying programming element.</span><span class="sxs-lookup"><span data-stu-id="c4424-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="c4424-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span><span class="sxs-lookup"><span data-stu-id="c4424-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="c4424-106">Modifiable and Nonmodifiable Elements</span><span class="sxs-lookup"><span data-stu-id="c4424-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="c4424-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span><span class="sxs-lookup"><span data-stu-id="c4424-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="c4424-108">The following table lists modifiable and nonmodifiable programming elements.</span><span class="sxs-lookup"><span data-stu-id="c4424-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="c4424-109">Modifiable elements</span><span class="sxs-lookup"><span data-stu-id="c4424-109">Modifiable elements</span></span>|<span data-ttu-id="c4424-110">Nonmodifiable elements</span><span class="sxs-lookup"><span data-stu-id="c4424-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="c4424-111">Local variables (declared inside procedures), including object variables, except for read-only</span><span class="sxs-lookup"><span data-stu-id="c4424-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="c4424-112">Read-only variables, fields, and properties</span><span class="sxs-lookup"><span data-stu-id="c4424-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="c4424-113">Fields (member variables of modules, classes, and structures), except for read-only</span><span class="sxs-lookup"><span data-stu-id="c4424-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="c4424-114">Constants and literals</span><span class="sxs-lookup"><span data-stu-id="c4424-114">Constants and literals</span></span>|  
|<span data-ttu-id="c4424-115">Properties, except for read-only</span><span class="sxs-lookup"><span data-stu-id="c4424-115">Properties, except for read-only</span></span>|<span data-ttu-id="c4424-116">Enumeration members</span><span class="sxs-lookup"><span data-stu-id="c4424-116">Enumeration members</span></span>|  
|<span data-ttu-id="c4424-117">Array elements</span><span class="sxs-lookup"><span data-stu-id="c4424-117">Array elements</span></span>|<span data-ttu-id="c4424-118">Expressions (even if their elements are modifiable)</span><span class="sxs-lookup"><span data-stu-id="c4424-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="c4424-119">Modifiable and Nonmodifiable Arguments</span><span class="sxs-lookup"><span data-stu-id="c4424-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="c4424-120">A *modifiable argument* is one with a modifiable underlying element.</span><span class="sxs-lookup"><span data-stu-id="c4424-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="c4424-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="c4424-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="c4424-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="c4424-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="c4424-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span><span class="sxs-lookup"><span data-stu-id="c4424-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="c4424-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span><span class="sxs-lookup"><span data-stu-id="c4424-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="c4424-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="c4424-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4424-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4424-126">See also</span></span>

- [<span data-ttu-id="c4424-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="c4424-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c4424-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="c4424-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c4424-129">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="c4424-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="c4424-130">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="c4424-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c4424-131">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="c4424-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="c4424-132">Instrukcje: zmiana wartości argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="c4424-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="c4424-133">Instrukcje: ochrona argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="c4424-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="c4424-134">Instrukcje: wymuszanie przekazywania argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="c4424-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="c4424-135">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="c4424-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="c4424-136">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="c4424-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
