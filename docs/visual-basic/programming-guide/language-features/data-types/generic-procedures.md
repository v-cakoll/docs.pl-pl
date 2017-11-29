---
title: "Procedury ogólne w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e019ca32277f93f798e99e996a3670c8302ba9b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="5ba6a-102">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ba6a-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="5ba6a-103">A *ogólnego procedury*, nazywany również *Metoda ogólna*, jest to procedura zdefiniowane z co najmniej jeden typ parametru.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="5ba6a-104">Dzięki temu kod wywołujący dostosować typy danych do jej wymagania dotyczące zawsze wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="5ba6a-105">Procedura nie jest rodzajowa po prostu z definiowany wewnątrz klasy ogólnej lub to struktura generyczna.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="5ba6a-106">Aby wartość była ogólna, procedurę należy wykonać co najmniej jeden parametr typu, oprócz parametry normalnej, może to potrwać.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="5ba6a-107">Ogólny klasy lub struktury może zawierać procedury nierodzajowe i nierodzajowe klasy, struktury, lub moduł może zawierać procedury ogólne.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="5ba6a-108">Procedury ogólne można użyć swoich parametrów typu liście jego normalnej parametru, jego typ zwracany, jeśli ma ona jedną i w jego procedury kodu.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="5ba6a-109">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="5ba6a-109">Type Inference</span></span>  
 <span data-ttu-id="5ba6a-110">Procedury ogólne można wywołać bez podawania żadnych argumentów typu na wszystkich.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="5ba6a-111">Jeśli należy wywołać go w ten sposób, kompilator spróbuje określić typy odpowiednie dane do przekazania do procedury argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="5ba6a-112">Ta metoda jest wywoływana *wnioskowanie typu*.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-112">This is called *type inference*.</span></span> <span data-ttu-id="5ba6a-113">Poniższy kod przedstawia wywołanie w którym kompilator ustala, że należy przekazać typ `String` do parametru typu `t`.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="5ba6a-114">Jeśli kompilator nie można wywnioskować argumentów typu z kontekstu wywołania, zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="5ba6a-115">Jedną z możliwych przyczyn takiego błędu jest niezgodność rangi tablicy.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="5ba6a-116">Załóżmy na przykład zdefiniować normalne parametr jako tablica parametru typu.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="5ba6a-117">Wywołanie procedury ogólne na tablicę rangi różnych (liczba wymiarów), udostępnia niezgodność powoduje, że wnioskowanie o typie się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="5ba6a-118">Poniższy kod przedstawia wywołanie, w którym jest tablicą dwuwymiarową jest przekazany do procedury, która oczekuje tablicą jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 <span data-ttu-id="5ba6a-119">Wnioskowanie o typie można wywołać tylko przez pominięcie wszystkich argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="5ba6a-120">Jeśli podasz jeden argument typu, należy podać je wszystkie.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="5ba6a-121">Wnioskowanie o typie jest obsługiwana tylko dla ogólnych procedurach.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="5ba6a-122">Nie można wywołać wnioskowanie o typie na ogólne klasy, struktury, interfejsy lub delegatów.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ba6a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ba6a-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5ba6a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="5ba6a-124">Description</span></span>  
 <span data-ttu-id="5ba6a-125">W poniższym przykładzie zdefiniowano ogólnego `Function` procedurę, aby znaleźć określony element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="5ba6a-126">Definiuje jeden parametr typu, a używa go do utworzenia dwóch parametrów na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5ba6a-127">Kod</span><span class="sxs-lookup"><span data-stu-id="5ba6a-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="5ba6a-128">Komentarze</span><span class="sxs-lookup"><span data-stu-id="5ba6a-128">Comments</span></span>  
 <span data-ttu-id="5ba6a-129">Powyższy przykład wymaga możliwości porównania `searchValue` względem każdego elementu `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="5ba6a-130">Aby zagwarantować tę możliwość, jego ogranicza parametr typu `T` do zaimplementowania <xref:System.IComparable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="5ba6a-131">W kodzie użyto <xref:System.IComparable%601.CompareTo%2A> zamiast metody `=` operatora, ponieważ nie ma gwarancji, że podany argument typu dla `T` obsługuje `=` operatora.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="5ba6a-132">Możesz przetestować `findElement` procedury z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5ba6a-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="5ba6a-133">Poprzedni wywołań `MsgBox` wyświetlić odpowiednio "0", "1" i "-1".</span><span class="sxs-lookup"><span data-stu-id="5ba6a-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba6a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ba6a-134">See Also</span></span>  
 [<span data-ttu-id="5ba6a-135">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ba6a-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="5ba6a-136">Porady: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych</span><span class="sxs-lookup"><span data-stu-id="5ba6a-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="5ba6a-137">Porady: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="5ba6a-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="5ba6a-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="5ba6a-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="5ba6a-139">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="5ba6a-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5ba6a-140">Lista typów</span><span class="sxs-lookup"><span data-stu-id="5ba6a-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="5ba6a-141">Listy parametrów</span><span class="sxs-lookup"><span data-stu-id="5ba6a-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
