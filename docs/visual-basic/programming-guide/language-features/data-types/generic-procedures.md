---
title: Procedury ogólne
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
ms.openlocfilehash: 16a629e07cf711778b3d8d1863958ec7a6300649
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350083"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="938ec-102">Procedury ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="938ec-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="938ec-103">*Procedura ogólna*, nazywana również *metodą rodzajową*, jest procedurą zdefiniowaną z co najmniej jednym parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="938ec-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="938ec-104">Dzięki temu kod wywołujący dostosowuje typy danych do swoich wymagań przy każdym wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="938ec-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="938ec-105">Procedura nie jest ogólna po prostu na mocy zdefiniowanej wewnątrz klasy generycznej lub struktury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="938ec-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="938ec-106">Aby być ogólny, procedura musi pobrać co najmniej jeden parametr typu, oprócz wszystkich normalnych parametrów, które może podjąć.</span><span class="sxs-lookup"><span data-stu-id="938ec-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="938ec-107">Ogólna Klasa lub struktura może zawierać procedury nieogólne, a niegeneryczna Klasa, struktura lub moduł mogą zawierać procedury ogólne.</span><span class="sxs-lookup"><span data-stu-id="938ec-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="938ec-108">Procedura ogólna może używać jej parametrów typu na swojej normalnej liście parametrów, w jej typie zwracanym, jeśli ma jeden, i w jego kodzie procedury.</span><span class="sxs-lookup"><span data-stu-id="938ec-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="938ec-109">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="938ec-109">Type Inference</span></span>  
 <span data-ttu-id="938ec-110">Można wywołać procedurę ogólną bez podawania żadnych argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="938ec-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="938ec-111">Jeśli wywołasz ten sposób, kompilator próbuje określić odpowiednie typy danych do przekazania do argumentów typu procedury.</span><span class="sxs-lookup"><span data-stu-id="938ec-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="938ec-112">Jest to nazywane *wnioskami o typie*.</span><span class="sxs-lookup"><span data-stu-id="938ec-112">This is called *type inference*.</span></span> <span data-ttu-id="938ec-113">Poniższy kod pokazuje wywołanie, w którym kompilator uważa, że powinien przekazać typ `String` do `t`parametru typu.</span><span class="sxs-lookup"><span data-stu-id="938ec-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="938ec-114">Jeśli kompilator nie może wywnioskować argumentów typu z kontekstu wywołania, zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="938ec-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="938ec-115">Jedną z możliwych przyczyn tego błędu jest niezgodność rangi tablicy.</span><span class="sxs-lookup"><span data-stu-id="938ec-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="938ec-116">Załóżmy na przykład, że definiujesz normalny parametr jako tablicę parametru typu.</span><span class="sxs-lookup"><span data-stu-id="938ec-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="938ec-117">W przypadku wywołania procedury ogólnej dostarczającej tablicę o innej rangi (liczbie wymiarów) niezgodność powoduje niepowodzenie wnioskowania o typie.</span><span class="sxs-lookup"><span data-stu-id="938ec-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="938ec-118">Poniższy kod pokazuje wywołanie, w którym tablica dwuwymiarowa jest przekazana do procedury, która oczekuje tablicy jednowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="938ec-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="938ec-119">Wnioskowanie o typie można wywołać tylko poprzez pominięcie wszystkich argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="938ec-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="938ec-120">W przypadku podania jednego typu argumentu należy podać wszystkie.</span><span class="sxs-lookup"><span data-stu-id="938ec-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="938ec-121">Wnioskowanie o typie jest obsługiwane tylko dla procedur ogólnych.</span><span class="sxs-lookup"><span data-stu-id="938ec-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="938ec-122">Nie można wywołać wnioskowania o typie dla klas ogólnych, struktur, interfejsów ani delegatów.</span><span class="sxs-lookup"><span data-stu-id="938ec-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="938ec-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="938ec-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="938ec-124">Opis</span><span class="sxs-lookup"><span data-stu-id="938ec-124">Description</span></span>  
 <span data-ttu-id="938ec-125">Poniższy przykład definiuje ogólną procedurę `Function`, aby znaleźć konkretny element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="938ec-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="938ec-126">Definiuje jeden parametr typu i używa go do konstruowania dwóch parametrów na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="938ec-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="938ec-127">Kod</span><span class="sxs-lookup"><span data-stu-id="938ec-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="938ec-128">Komentarze</span><span class="sxs-lookup"><span data-stu-id="938ec-128">Comments</span></span>  
 <span data-ttu-id="938ec-129">Poprzedni przykład wymaga możliwości porównania `searchValue` z każdym elementem `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="938ec-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="938ec-130">Aby zagwarantować tę możliwość, ogranicza parametr typu `T` w celu zaimplementowania interfejsu <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="938ec-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="938ec-131">Kod używa metody <xref:System.IComparable%601.CompareTo%2A> zamiast operatora `=`, ponieważ nie ma gwarancji, że argument typu dostarczony dla `T` obsługuje operatora `=`.</span><span class="sxs-lookup"><span data-stu-id="938ec-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="938ec-132">Procedurę `findElement` można przetestować przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="938ec-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="938ec-133">Poprzednie wywołania `MsgBox` wyświetlają odpowiednio wartości "0", "1" i "-1".</span><span class="sxs-lookup"><span data-stu-id="938ec-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938ec-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="938ec-134">See also</span></span>

- [<span data-ttu-id="938ec-135">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="938ec-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="938ec-136">Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych</span><span class="sxs-lookup"><span data-stu-id="938ec-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="938ec-137">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="938ec-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="938ec-138">Procedury</span><span class="sxs-lookup"><span data-stu-id="938ec-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="938ec-139">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="938ec-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="938ec-140">Lista typów</span><span class="sxs-lookup"><span data-stu-id="938ec-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="938ec-141">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="938ec-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
