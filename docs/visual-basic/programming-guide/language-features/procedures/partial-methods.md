---
title: Metody częściowe
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
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352633"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="772e5-102">Metody częściowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="772e5-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="772e5-103">Metody częściowe umożliwiają deweloperom Wstawianie niestandardowych logiki do kodu.</span><span class="sxs-lookup"><span data-stu-id="772e5-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="772e5-104">Zazwyczaj kod jest częścią klasy generowanej przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="772e5-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="772e5-105">Metody częściowe są zdefiniowane w klasie częściowej, która jest tworzona przez generator kodu i często są używane do dostarczania powiadomienia, że coś uległo zmianie.</span><span class="sxs-lookup"><span data-stu-id="772e5-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="772e5-106">Umożliwiają deweloperowi określenie zachowania niestandardowego w reakcji na zmianę.</span><span class="sxs-lookup"><span data-stu-id="772e5-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="772e5-107">Projektant generatora kodu definiuje tylko sygnaturę metody i jedno lub więcej wywołań metody.</span><span class="sxs-lookup"><span data-stu-id="772e5-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="772e5-108">Deweloperzy mogą następnie podać implementacje dla metody, jeśli chcą dostosować zachowanie wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="772e5-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="772e5-109">Gdy implementacja nie zostanie dostarczona, wywołania metody są usuwane przez kompilator, co spowodowało brak dodatkowych obciążeń związanych z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="772e5-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="772e5-110">Oświadczeń</span><span class="sxs-lookup"><span data-stu-id="772e5-110">Declaration</span></span>  
 <span data-ttu-id="772e5-111">Wygenerowany kod oznacza definicję metody częściowej poprzez umieszczenie słowa kluczowego `Partial` na początku wiersza podpisu.</span><span class="sxs-lookup"><span data-stu-id="772e5-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="772e5-112">Definicja musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="772e5-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="772e5-113">Metoda musi być `Sub`, a nie `Function`.</span><span class="sxs-lookup"><span data-stu-id="772e5-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="772e5-114">Treść metody musi pozostać pusta.</span><span class="sxs-lookup"><span data-stu-id="772e5-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="772e5-115">Modyfikator dostępu musi być `Private`.</span><span class="sxs-lookup"><span data-stu-id="772e5-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="772e5-116">Implementacja</span><span class="sxs-lookup"><span data-stu-id="772e5-116">Implementation</span></span>  
 <span data-ttu-id="772e5-117">Implementacja składa się głównie z wypełniania treści metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="772e5-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="772e5-118">Implementacja zazwyczaj należy do oddzielnej klasy częściowej z definicji i jest zapisywana przez dewelopera, który chce zwiększyć wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="772e5-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="772e5-119">Poprzedni przykład duplikuje sygnaturę w deklaracji dokładnie, ale możliwe jest zróżnicowanie.</span><span class="sxs-lookup"><span data-stu-id="772e5-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="772e5-120">W szczególności można dodać inne modyfikatory, takie jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="772e5-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="772e5-121">Dozwolony jest tylko jeden modyfikator `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="772e5-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="772e5-122">Aby uzyskać więcej informacji na temat modyfikatorów metod, zobacz [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="772e5-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="772e5-123">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="772e5-123">Use</span></span>  
 <span data-ttu-id="772e5-124">Metodę częściową należy wywołać, ponieważ wywołamy dowolną inną procedurę `Sub`.</span><span class="sxs-lookup"><span data-stu-id="772e5-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="772e5-125">Jeśli metoda została zaimplementowana, argumenty są oceniane i jest wykonywana treść metody.</span><span class="sxs-lookup"><span data-stu-id="772e5-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="772e5-126">Należy jednak pamiętać, że implementacja metody częściowej jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="772e5-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="772e5-127">Jeśli metoda nie jest zaimplementowana, wywołanie jej nie ma żadnego wpływu, a wyrażenia przekazane jako argumenty metody nie są oceniane.</span><span class="sxs-lookup"><span data-stu-id="772e5-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="772e5-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="772e5-128">Example</span></span>  
 <span data-ttu-id="772e5-129">W pliku o nazwie Product. Designer. vb Zdefiniuj klasę `Product`, która ma właściwość `Quantity`.</span><span class="sxs-lookup"><span data-stu-id="772e5-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="772e5-130">W pliku o nazwie Product. vb wprowadź implementację `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="772e5-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="772e5-131">Na koniec w głównej metodzie projektu Zadeklaruj wystąpienie `Product` i podaj wartość początkową dla swojej właściwości `Quantity`.</span><span class="sxs-lookup"><span data-stu-id="772e5-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="772e5-132">Zostanie wyświetlone okno komunikatu z komunikatem:</span><span class="sxs-lookup"><span data-stu-id="772e5-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="772e5-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="772e5-133">See also</span></span>

- [<span data-ttu-id="772e5-134">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="772e5-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="772e5-135">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="772e5-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="772e5-136">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="772e5-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="772e5-137">Partial</span><span class="sxs-lookup"><span data-stu-id="772e5-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="772e5-138">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="772e5-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="772e5-139">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="772e5-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
