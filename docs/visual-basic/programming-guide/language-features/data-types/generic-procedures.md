---
title: Procedury ogólne w Visual Basic
ms.date: 07/20/2015
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
ms.openlocfilehash: 0f2a0c646b5af91d5296bafb01f5261d7ee6b9fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574316"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="269ef-102">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="269ef-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="269ef-103">A *ogólna procedura*, nazywane również *metody ogólnej*, jest to procedura zdefiniowany co najmniej jednego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="269ef-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="269ef-104">Dzięki temu kod wywołujący, aby dostosować typy danych do ich wymagania dotyczące zawsze wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="269ef-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="269ef-105">Procedura nie jest ogólna po prostu wynoszącą definiowanego wewnątrz Ogólna klasa lub Struktura ogólna.</span><span class="sxs-lookup"><span data-stu-id="269ef-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="269ef-106">Aby być ogólna, procedurę należy wykonać co najmniej jeden parametr typu, oprócz normalnych parametrów, może to potrwać.</span><span class="sxs-lookup"><span data-stu-id="269ef-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="269ef-107">Ogólna klasa lub struktura może zawierać procedury nierodzajowymi i nierodzajowymi klasy, struktury lub modułu może zawierać procedury ogólne.</span><span class="sxs-lookup"><span data-stu-id="269ef-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="269ef-108">Procedury ogólne użyć jego parametrów typu w jego listę parametrów normalne, jego typem zwracanym, jeśli ma on jeden, a w jego procedury kodu.</span><span class="sxs-lookup"><span data-stu-id="269ef-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="269ef-109">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="269ef-109">Type Inference</span></span>  
 <span data-ttu-id="269ef-110">Ogólna procedura można wywołać bez podawania żadnych argumentów typu w ogóle.</span><span class="sxs-lookup"><span data-stu-id="269ef-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="269ef-111">Jeśli wywołasz ją w ten sposób, kompilator spróbuje określić typy odpowiednie dane do przekazania do procedury argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="269ef-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="269ef-112">Jest to nazywane *wnioskowanie o typie*.</span><span class="sxs-lookup"><span data-stu-id="269ef-112">This is called *type inference*.</span></span> <span data-ttu-id="269ef-113">Poniższy kod ilustruje sposób wywoływania, w którym kompilator ustala, powinna przekazać typ `String` na parametr typu `t`.</span><span class="sxs-lookup"><span data-stu-id="269ef-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="269ef-114">Jeśli kompilator nie można wywnioskować argumentów typu z kontekstu wywołania, zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="269ef-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="269ef-115">Jedną z możliwych przyczyn takiego komunikatu o błędzie jest niezgodność rangi tablicy.</span><span class="sxs-lookup"><span data-stu-id="269ef-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="269ef-116">Na przykład załóżmy, że zdefiniujesz normalne parametr jako tablicę z parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="269ef-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="269ef-117">Jeśli wywołanie procedury ogólne dostarczanie tablicy o innej randze (liczba wymiarów), niezgodność powoduje, że wnioskowanie o typie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="269ef-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="269ef-118">Poniższy kod ilustruje sposób wywoływania, w którym tablicy dwuwymiarowej jest przekazywany do procedury, która oczekuje Jednowymiarowa tablica.</span><span class="sxs-lookup"><span data-stu-id="269ef-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="269ef-119">Wnioskowanie o typie można wywoływać, pomijając wszystkich argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="269ef-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="269ef-120">Jeśli podasz jeden argument typu, należy podać je wszystkie.</span><span class="sxs-lookup"><span data-stu-id="269ef-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="269ef-121">Wnioskowanie o typie jest obsługiwana tylko w przypadku ogólnych procedurach.</span><span class="sxs-lookup"><span data-stu-id="269ef-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="269ef-122">Nie można wywołać wnioskowanie o typie na klasy ogólne, struktur, interfejsów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="269ef-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="269ef-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="269ef-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="269ef-124">Opis</span><span class="sxs-lookup"><span data-stu-id="269ef-124">Description</span></span>  
 <span data-ttu-id="269ef-125">W poniższym przykładzie zdefiniowano ogólnego `Function` procedurze, aby znaleźć określony element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="269ef-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="269ef-126">On definiuje jeden parametr typu i używa ich do utworzenia dwóch parametrów na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="269ef-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="269ef-127">Kod</span><span class="sxs-lookup"><span data-stu-id="269ef-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="269ef-128">Komentarze</span><span class="sxs-lookup"><span data-stu-id="269ef-128">Comments</span></span>  
 <span data-ttu-id="269ef-129">Poprzedni przykład wymaga możliwości porównywania `searchValue` względem każdego elementu `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="269ef-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="269ef-130">Aby zagwarantować tę możliwość, jego ogranicza parametr typu `T` do zaimplementowania <xref:System.IComparable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="269ef-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="269ef-131">Kod używa <xref:System.IComparable%601.CompareTo%2A> zamiast metody `=` operatora, ponieważ nie ma żadnej gwarancji, że argument typu dostarczane na potrzeby `T` obsługuje `=` operatora.</span><span class="sxs-lookup"><span data-stu-id="269ef-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="269ef-132">Możesz przetestować `findElement` procedury z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="269ef-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="269ef-133">Poprzedniego wywołania `MsgBox` odpowiednio wyświetlane "0", "1" i "-1".</span><span class="sxs-lookup"><span data-stu-id="269ef-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269ef-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="269ef-134">See also</span></span>
- [<span data-ttu-id="269ef-135">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="269ef-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="269ef-136">Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych</span><span class="sxs-lookup"><span data-stu-id="269ef-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="269ef-137">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="269ef-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="269ef-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="269ef-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="269ef-139">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="269ef-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="269ef-140">Lista typów</span><span class="sxs-lookup"><span data-stu-id="269ef-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="269ef-141">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="269ef-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
