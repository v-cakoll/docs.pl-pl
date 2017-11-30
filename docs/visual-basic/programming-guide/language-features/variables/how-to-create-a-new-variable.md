---
title: 'Porady: tworzenie nowej zmiennej (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="51e9d-102">Porady: tworzenie nowej zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51e9d-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="51e9d-103">Utwórz zmienną z [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="51e9d-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="51e9d-104">Aby utworzyć nową zmienną</span><span class="sxs-lookup"><span data-stu-id="51e9d-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="51e9d-105">Deklarowanie zmiennej w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="51e9d-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="51e9d-106">Uwzględnić wymagania dotyczące cech zmiennej, takie jak [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [statycznych](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), lub [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="51e9d-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="51e9d-107">Aby uzyskać więcej informacji, zobacz [zadeklarowana Charakterystyka elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="51e9d-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="51e9d-108">Nie trzeba `Dim` — słowo kluczowe, jeśli używasz innych słów kluczowych w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="51e9d-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="51e9d-109">Wykonaj specyfikacje o nazwie zmiennej, która musi być zgodna [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] reguł i Konwencji.</span><span class="sxs-lookup"><span data-stu-id="51e9d-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rules and conventions.</span></span> <span data-ttu-id="51e9d-110">Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="51e9d-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="51e9d-111">Po nazwie [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli, aby określić typ danych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="51e9d-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="51e9d-112">Jeśli nie określisz typu danych, używa domyślnie: `Object`.</span><span class="sxs-lookup"><span data-stu-id="51e9d-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="51e9d-113">Postępuj zgodnie z `As` klauzuli znakiem równości (`=`) i postępuj zgodnie z znaku równości w początkowej wartości zmiennej.</span><span class="sxs-lookup"><span data-stu-id="51e9d-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="51e9d-114">przypisuje określona wartość do zmiennej w każdym uruchomieniu `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="51e9d-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="51e9d-115">Jeśli nie określisz wartości początkowej, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] przypisuje początkową wartością domyślną dla typu danych, gdy najpierw wprowadza kod, który zawiera `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="51e9d-115">If you do not specify an initial value, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="51e9d-116">Jeśli zmienna jest typem referencyjnym, umieszczając w niej można utworzyć wystąpienia klasy jego [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe w `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="51e9d-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="51e9d-117">Jeśli nie używasz `New`, początkowej wartości zmiennej jest [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="51e9d-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="51e9d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51e9d-118">See Also</span></span>  
 [<span data-ttu-id="51e9d-119">Zmienne</span><span class="sxs-lookup"><span data-stu-id="51e9d-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="51e9d-120">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="51e9d-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="51e9d-121">Zadeklarowane nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="51e9d-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="51e9d-122">Zadeklarowana Charakterystyka elementów</span><span class="sxs-lookup"><span data-stu-id="51e9d-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="51e9d-123">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="51e9d-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="51e9d-124">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="51e9d-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="51e9d-125">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="51e9d-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="51e9d-126">Option Infer — instrukcja</span><span class="sxs-lookup"><span data-stu-id="51e9d-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
