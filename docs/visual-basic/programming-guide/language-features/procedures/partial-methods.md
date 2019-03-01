---
title: Metody częściowe (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 4b35985aa67cea7b58ddf05611cf4e0813a2d442
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977464"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="e9cdb-102">Metody częściowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9cdb-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="e9cdb-103">Metody częściowe umożliwiają deweloperom Wstawianie niestandardowej logiki do kodu.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="e9cdb-104">Zazwyczaj ten kod jest częścią klasy wygenerowany przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="e9cdb-105">Metody częściowe są zdefiniowane w częściowej klasie, który jest tworzony przez generator kodu, a często są one używane do powiadomienie, że coś, co zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="e9cdb-106">Umożliwiają one dla deweloperów określić zachowanie niestandardowe w odpowiedzi na zmiany.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="e9cdb-107">Projektant generatora kodu definiuje tylko podpis metody i co najmniej jedno wywołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="e9cdb-108">Deweloperzy mogą udzielić im implementacji metody, jeśli chcesz dostosować zachowanie wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="e9cdb-109">Podczas wdrożenia nie zostanie podany, wywołania metody są usuwane przez kompilator, co spowoduje nie dodatkowe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="e9cdb-110">Deklaracja</span><span class="sxs-lookup"><span data-stu-id="e9cdb-110">Declaration</span></span>  
 <span data-ttu-id="e9cdb-111">Wygenerowany kod oznacza definicji metody częściowej poprzez umieszczenie słowa kluczowego `Partial` na początku wiersza podpisu.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="e9cdb-112">Definicja musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="e9cdb-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="e9cdb-113">Metoda musi być `Sub`, a nie `Function`.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="e9cdb-114">Treść metody musi być puste.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="e9cdb-115">Modyfikator dostępu musi być `Private`.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="e9cdb-116">Implementacja</span><span class="sxs-lookup"><span data-stu-id="e9cdb-116">Implementation</span></span>  
 <span data-ttu-id="e9cdb-117">Implementacja składa się przede wszystkim wypełnianie w treści metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="e9cdb-118">Implementacja zwykle znajduje się w osobnej klasy częściowej z definicji i są zapisywane przez dewelopera, który chce rozszerzyć wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="e9cdb-119">Poprzedni przykład duplikuje dokładnie podpisu w deklaracji, ale zmiany są możliwe.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="e9cdb-120">W szczególności innych modyfikatorów można dodać, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="e9cdb-121">Tylko jeden `Overrides` modyfikator jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="e9cdb-122">Aby uzyskać więcej informacji na temat metody Modyfikatory zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e9cdb-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="e9cdb-123">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="e9cdb-123">Use</span></span>  
 <span data-ttu-id="e9cdb-124">Wywołanie metody częściowej, jak każdy inny wywoływałby `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="e9cdb-125">Jeśli metoda został zaimplementowany, argumenty są obliczane i treści metody jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="e9cdb-126">Należy jednak pamiętać, że implementacja metody częściowej jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="e9cdb-127">Jeśli metoda nie jest zaimplementowana, wywołanie go nie ma wpływu, a następnie przekazywane jako argumenty do metody wyrażeń nie są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9cdb-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9cdb-128">Example</span></span>  
 <span data-ttu-id="e9cdb-129">W pliku o nazwie Product.Designer.vb, zdefiniuj `Product` klasy, która ma `Quantity` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="e9cdb-130">W pliku o nazwie Product.vb, należy podać implementacja dla `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="e9cdb-131">Na koniec w metody Main projektu, należy zadeklarować `Product` wystąpienia i podaj wartość początkową dla jego `Quantity` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e9cdb-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="e9cdb-132">Okno komunikatu powinny wyglądać, która wyświetla ten komunikat:</span><span class="sxs-lookup"><span data-stu-id="e9cdb-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="e9cdb-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9cdb-133">See also</span></span>
- [<span data-ttu-id="e9cdb-134">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e9cdb-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="e9cdb-135">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="e9cdb-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e9cdb-136">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e9cdb-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="e9cdb-137">Partial</span><span class="sxs-lookup"><span data-stu-id="e9cdb-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="e9cdb-138">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e9cdb-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="e9cdb-139">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="e9cdb-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
