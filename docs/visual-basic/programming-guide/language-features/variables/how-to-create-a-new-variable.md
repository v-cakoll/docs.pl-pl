---
title: 'Porady: tworzenie nowej zmiennej'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410532"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="ecdff-102">Porady: tworzenie nowej zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecdff-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="ecdff-103">Tworzysz zmienną za pomocą [instrukcji Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ecdff-103">You create a variable with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="ecdff-104">Aby utworzyć nową zmienną</span><span class="sxs-lookup"><span data-stu-id="ecdff-104">To create a new variable</span></span>

1. <span data-ttu-id="ecdff-105">Zadeklaruj zmienną w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ecdff-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="ecdff-106">Zawierają specyfikacje dla charakterystyki zmiennej, takie jak [Private](../../../language-reference/modifiers/private.md), [static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md)lub [WithEvents](../../../language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="ecdff-106">Include specifications for the variable's characteristics, such as [Private](../../../language-reference/modifiers/private.md), [Static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md), or [WithEvents](../../../language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="ecdff-107">Aby uzyskać więcej informacji, zobacz [deklarowane cechy elementu](../declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="ecdff-107">For more information, see [Declared Element Characteristics](../declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="ecdff-108">Słowo kluczowe nie jest potrzebne, `Dim` Jeśli używasz innych słów kluczowych w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ecdff-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="ecdff-109">Postępuj zgodnie ze specyfikacją, podając nazwę zmiennej, która musi być zgodna z regułami i konwencjami Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ecdff-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="ecdff-110">Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ecdff-110">For more information, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="ecdff-111">Użyj nazwy z klauzulą [as](../../../language-reference/statements/as-clause.md) , aby określić typ danych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ecdff-111">Follow the name with the [As](../../../language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="ecdff-112">Jeśli nie określisz typu danych, zostanie użyta wartość domyślna: `Object` .</span><span class="sxs-lookup"><span data-stu-id="ecdff-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="ecdff-113">Postępuj zgodnie z `As` klauzulą znaku równości ( `=` ) i obserwuj znak równości ze początkową wartością zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ecdff-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="ecdff-114">Visual Basic przypisuje określoną wartość do zmiennej przy każdym uruchomieniu `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ecdff-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="ecdff-115">Jeśli nie określisz wartości początkowej, Visual Basic przypisze domyślną wartość początkową dla typu danych zmiennej, gdy po raz pierwszy wprowadzi kod, który zawiera `Dim` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="ecdff-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="ecdff-116">Jeśli zmienna jest typem referencyjnym, można utworzyć wystąpienie klasy, dołączając słowo kluczowe [new operatora](../../../language-reference/operators/new-operator.md) w `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ecdff-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="ecdff-117">Jeśli nie używasz `New` , początkowa wartość zmiennej to [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="ecdff-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="ecdff-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecdff-118">See also</span></span>

- [<span data-ttu-id="ecdff-119">Zmienne</span><span class="sxs-lookup"><span data-stu-id="ecdff-119">Variables</span></span>](index.md)
- [<span data-ttu-id="ecdff-120">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="ecdff-120">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="ecdff-121">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="ecdff-121">Declared Element Names</span></span>](../declared-elements/declared-element-names.md)
- [<span data-ttu-id="ecdff-122">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="ecdff-122">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="ecdff-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="ecdff-123">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="ecdff-124">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="ecdff-124">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="ecdff-125">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="ecdff-125">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="ecdff-126">Option Infer — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ecdff-126">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
