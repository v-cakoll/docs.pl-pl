---
title: 'Porady: definiowanie operatora konwersji'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 53b0211c6304625edd7ac24fa52ff0c051d8f0a0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388092"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="c7fde-102">Porady: definiowanie operatora konwersji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7fde-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="c7fde-103">Jeśli zdefiniowano klasę lub strukturę, można zdefiniować Operator konwersji typu między typem klasy lub struktury a innym typem danych (np `Integer` `Double` ., lub `String` ).</span><span class="sxs-lookup"><span data-stu-id="c7fde-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="c7fde-104">Zdefiniuj konwersję typu jako procedurę [funkcji CType](../../../language-reference/functions/ctype-function.md) w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="c7fde-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="c7fde-105">Wszystkie procedury konwersji muszą mieć `Public Shared` wartość, a każdy z nich musi określać [rozszerzanie](../../../language-reference/modifiers/widening.md) lub [zwężanie](../../../language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="c7fde-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="c7fde-106">Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.</span><span class="sxs-lookup"><span data-stu-id="c7fde-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7fde-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7fde-107">Example</span></span>  
 <span data-ttu-id="c7fde-108">Poniższy przykład definiuje operatory konwersji między strukturą o nazwie `digit` i a `Byte` .</span><span class="sxs-lookup"><span data-stu-id="c7fde-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="c7fde-109">Możesz przetestować strukturę `digit` przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="c7fde-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="c7fde-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7fde-110">See also</span></span>

- [<span data-ttu-id="c7fde-111">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="c7fde-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c7fde-112">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="c7fde-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="c7fde-113">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="c7fde-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="c7fde-114">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="c7fde-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="c7fde-115">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="c7fde-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c7fde-116">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="c7fde-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c7fde-117">Instrukcje: Deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="c7fde-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="c7fde-118">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c7fde-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c7fde-119">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="c7fde-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
