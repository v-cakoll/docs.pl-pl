---
title: 'Instrukcje: Tworzenie nowej zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: db317b160a27c7e38bddba82eb4eac3088886705
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506891"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="99023-102">Instrukcje: Tworzenie nowej zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99023-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="99023-103">Utwórz zmienną za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="99023-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="99023-104">Aby utworzyć nową zmienną</span><span class="sxs-lookup"><span data-stu-id="99023-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="99023-105">Zadeklaruj zmienną w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99023-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="99023-106">Uwzględnić wymagania dotyczące cech zmiennej, takie jak [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [statyczne](../../../../visual-basic/language-reference/modifiers/static.md), [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md), lub [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="99023-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="99023-107">Aby uzyskać więcej informacji, zobacz [zadeklarowana Charakterystyka elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="99023-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="99023-108">Nie ma potrzeby `Dim` — słowo kluczowe, jeśli używasz innych słów kluczowych w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="99023-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="99023-109">Postępuj zgodnie z specyfikacją o nazwie zmiennej, która musi być zgodna reguły Visual Basic i konwencje.</span><span class="sxs-lookup"><span data-stu-id="99023-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="99023-110">Aby uzyskać więcej informacji, zobacz [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) (Deklarowane nazwy elementów).</span><span class="sxs-lookup"><span data-stu-id="99023-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="99023-111">Postępuj zgodnie z nazwą [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli, aby określić typ danych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="99023-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="99023-112">Jeśli nie określisz typ danych, wykorzystuje wartość domyślna: `Object`.</span><span class="sxs-lookup"><span data-stu-id="99023-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="99023-113">Postępuj zgodnie z `As` klauzuli znakiem równości (`=`) i postępuj zgodnie z równości z wartością początkową zmiennej.</span><span class="sxs-lookup"><span data-stu-id="99023-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="99023-114">Visual Basic przypisuje określoną wartość do zmiennej za każdym razem, gdy działa `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99023-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="99023-115">Jeśli nie określisz wartości początkowej, Visual Basic po raz pierwszy najedzie kodu, który zawiera, przypisuje początkowa wartość domyślna dla typu danych zmiennej `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99023-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="99023-116">Jeśli zmienna jest typem referencyjnym, można utworzyć wystąpienia klasy, umieszczając [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe w `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="99023-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="99023-117">Jeśli nie używasz `New`, jest wartością początkową zmiennej [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="99023-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99023-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99023-118">See also</span></span>
- [<span data-ttu-id="99023-119">Zmienne</span><span class="sxs-lookup"><span data-stu-id="99023-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="99023-120">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="99023-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="99023-121">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="99023-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="99023-122">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="99023-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="99023-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="99023-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="99023-124">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="99023-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="99023-125">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="99023-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="99023-126">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="99023-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
