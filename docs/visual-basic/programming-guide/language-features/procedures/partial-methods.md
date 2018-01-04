---
title: "Metody częściowe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33e34c63988e74be2c22cb7b1358f5e8b04048c6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="76be3-102">Metody częściowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76be3-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="76be3-103">Metody częściowe umożliwiają deweloperom Wstawianie niestandardowej logiki do kodu.</span><span class="sxs-lookup"><span data-stu-id="76be3-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="76be3-104">Zazwyczaj kod jest częścią klasy wygenerowany przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="76be3-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="76be3-105">Metody częściowe są zdefiniowane w klasie częściowej utworzonego przez generator kodu, a często są one używane do o tym, że element został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="76be3-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="76be3-106">Umożliwiają one developer do określania zachowania niestandardowego w odpowiedzi na zmianę.</span><span class="sxs-lookup"><span data-stu-id="76be3-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="76be3-107">Projektant generatora kodu definiuje tylko podpis metody i co najmniej jednego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="76be3-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="76be3-108">Deweloperzy mogą udzielić im implementacji metody, jeśli chcesz dostosować zachowanie wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="76be3-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="76be3-109">Gdy implementacja nie została podana, wywołania metody zostaną usunięte przez kompilator, co powoduje nie dodatkowe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="76be3-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="76be3-110">Deklaracja</span><span class="sxs-lookup"><span data-stu-id="76be3-110">Declaration</span></span>  
 <span data-ttu-id="76be3-111">Wygenerowany kod oznacza definicję metody częściowej przez umieszczenie kluczowego `Partial` na początku wiersza podpisu.</span><span class="sxs-lookup"><span data-stu-id="76be3-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="76be3-112">Definicja musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="76be3-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="76be3-113">Metoda musi być `Sub`, a nie `Function`.</span><span class="sxs-lookup"><span data-stu-id="76be3-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="76be3-114">Treść metody muszą być puste.</span><span class="sxs-lookup"><span data-stu-id="76be3-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="76be3-115">Modyfikator dostępu musi być `Private`.</span><span class="sxs-lookup"><span data-stu-id="76be3-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="76be3-116">Implementacja</span><span class="sxs-lookup"><span data-stu-id="76be3-116">Implementation</span></span>  
 <span data-ttu-id="76be3-117">Implementacja obejmuje głównie wypełnianie w treści metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="76be3-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="76be3-118">Implementacja zazwyczaj znajduje się w osobnej częściowej klasy z definicji i są zapisywane przez deweloperów, którzy chcą rozszerzyć wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="76be3-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="76be3-119">Poprzedni przykład duplikatów podpisie w deklaracji dokładnie, ale zmiany są możliwe.</span><span class="sxs-lookup"><span data-stu-id="76be3-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="76be3-120">W szczególności innych modyfikatorów można dodawać, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="76be3-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="76be3-121">Tylko jeden `Overrides` modyfikator jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="76be3-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="76be3-122">Aby uzyskać więcej informacji na temat Modyfikatory metody, zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="76be3-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="76be3-123">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="76be3-123">Use</span></span>  
 <span data-ttu-id="76be3-124">Wywołanie metody częściowej, jak można wywołać żadnej innej `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="76be3-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="76be3-125">Jeśli zaimplementowano metody argumenty są oceniane i wykonaniu treści metody.</span><span class="sxs-lookup"><span data-stu-id="76be3-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="76be3-126">Należy jednak pamiętać, że metoda częściowa implementacja jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="76be3-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="76be3-127">Jeśli metoda nie jest zaimplementowana, wywołanie jej nie ma wpływu, a nie są oceniane wyrażenia przekazywane jako argumenty do metody.</span><span class="sxs-lookup"><span data-stu-id="76be3-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76be3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="76be3-128">Example</span></span>  
 <span data-ttu-id="76be3-129">W pliku o nazwie Product.Designer.vb, zdefiniuj `Product` klasy, która ma `Quantity` właściwości.</span><span class="sxs-lookup"><span data-stu-id="76be3-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="76be3-130">W pliku o nazwie Product.vb zapewniać implementację dla `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="76be3-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="76be3-131">Ponadto w metody Main projektu, należy zadeklarować `Product` wystąpienia i podaj wartość początkową dla jego `Quantity` właściwości.</span><span class="sxs-lookup"><span data-stu-id="76be3-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="76be3-132">Okno komunikatu powinno się, że wyświetla ten komunikat:</span><span class="sxs-lookup"><span data-stu-id="76be3-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="76be3-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76be3-133">See Also</span></span>  
 [<span data-ttu-id="76be3-134">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="76be3-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="76be3-135">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="76be3-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="76be3-136">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="76be3-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="76be3-137">Partial</span><span class="sxs-lookup"><span data-stu-id="76be3-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="76be3-138">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="76be3-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="76be3-139">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="76be3-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
