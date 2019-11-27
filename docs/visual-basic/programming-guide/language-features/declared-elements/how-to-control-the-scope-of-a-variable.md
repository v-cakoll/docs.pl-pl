---
title: 'Porady: kontrolowanie zakresu zmiennej'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345376"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="89b1e-102">Porady: kontrolowanie zakresu zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89b1e-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="89b1e-103">Zwykle zmienna znajduje się w *zakresie*lub jest widoczna dla odwołania w całym regionie, w którym jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="89b1e-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="89b1e-104">W niektórych przypadkach *poziom dostępu* zmiennej może mieć wpływ na jego zakres.</span><span class="sxs-lookup"><span data-stu-id="89b1e-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="89b1e-105">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="89b1e-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="89b1e-106">Zakres na poziomie bloku lub procedury</span><span class="sxs-lookup"><span data-stu-id="89b1e-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="89b1e-107">Aby zmienna była widoczna tylko w bloku</span><span class="sxs-lookup"><span data-stu-id="89b1e-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="89b1e-108">Umieść [instrukcję Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) dla zmiennej między instrukcjami inicjującymi i kończącymi deklaracji tego bloku, na przykład między instrukcjami `For` i `Next` pętli `For`.</span><span class="sxs-lookup"><span data-stu-id="89b1e-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="89b1e-109">Można odwołać się do zmiennej tylko z poziomu bloku.</span><span class="sxs-lookup"><span data-stu-id="89b1e-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="89b1e-110">Aby zmienna była widoczna tylko w ramach procedury</span><span class="sxs-lookup"><span data-stu-id="89b1e-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="89b1e-111">Umieść instrukcję `Dim` dla zmiennej wewnątrz procedury, ale poza blokami (takimi jak `With`...`End With` bloku).</span><span class="sxs-lookup"><span data-stu-id="89b1e-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="89b1e-112">Można odwołać się do zmiennej tylko z wewnątrz procedury, w tym w dowolnym bloku zawartym w procedurze.</span><span class="sxs-lookup"><span data-stu-id="89b1e-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="89b1e-113">Zakres na poziomie modułu lub przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="89b1e-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="89b1e-114">Dla wygody poziom jednoterminowego *modułu* jest stosowany równomiernie dla modułów, klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="89b1e-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="89b1e-115">Poziom dostępu zmiennej poziomu modułu określa jej zakres.</span><span class="sxs-lookup"><span data-stu-id="89b1e-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="89b1e-116">Przestrzeń nazw, która zawiera moduł, klasę lub strukturę, ma także wpływ na zakres.</span><span class="sxs-lookup"><span data-stu-id="89b1e-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="89b1e-117">Aby uczynić zmienną widoczną w całym module, klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="89b1e-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="89b1e-118">Umieść instrukcję `Dim` dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.</span><span class="sxs-lookup"><span data-stu-id="89b1e-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="89b1e-119">Dołącz [prywatne](../../../../visual-basic/language-reference/modifiers/private.md) słowo kluczowe do instrukcji `Dim`.</span><span class="sxs-lookup"><span data-stu-id="89b1e-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="89b1e-120">Możesz odwołać się do zmiennej z dowolnego miejsca w module, klasie lub strukturze, ale nie spoza niej.</span><span class="sxs-lookup"><span data-stu-id="89b1e-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="89b1e-121">Aby uczynić zmienną widoczną w całym obszarze nazw</span><span class="sxs-lookup"><span data-stu-id="89b1e-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="89b1e-122">Umieść instrukcję `Dim` dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.</span><span class="sxs-lookup"><span data-stu-id="89b1e-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="89b1e-123">Dołącz słowo kluczowe [zaprzyjaźnione](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publiczne](../../../../visual-basic/language-reference/modifiers/public.md) w instrukcji `Dim`.</span><span class="sxs-lookup"><span data-stu-id="89b1e-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="89b1e-124">Możesz odwołać się do zmiennej z dowolnego miejsca w przestrzeni nazw zawierającej moduł, klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="89b1e-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89b1e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="89b1e-125">Example</span></span>  
 <span data-ttu-id="89b1e-126">Poniższy przykład deklaruje zmienną na poziomie modułu i ogranicza jej widoczność do kodu w module.</span><span class="sxs-lookup"><span data-stu-id="89b1e-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="89b1e-127">W poprzednim przykładzie wszystkie procedury zdefiniowane w module `demonstrateScope` mogą odwoływać się do zmiennej `String` `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="89b1e-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="89b1e-128">Po wywołaniu procedury `usePrivateVariable` zostanie wyświetlona zawartość zmiennej ciągu `strMsg` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="89b1e-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="89b1e-129">Przy następujących zmianach do poprzedniego przykładu zmienna ciągu `strMsg` może być określana przez kod w dowolnym miejscu w przestrzeni nazw swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="89b1e-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="89b1e-130">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="89b1e-130">Robust Programming</span></span>  
 <span data-ttu-id="89b1e-131">Im węższy zakres zmiennej, tym mniej możliwości odwołujące się do nich zamiast innej zmiennej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="89b1e-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="89b1e-132">Możesz również zminimalizować problemy pasujące do odwołania.</span><span class="sxs-lookup"><span data-stu-id="89b1e-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="89b1e-133">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="89b1e-133">.NET Framework Security</span></span>  
 <span data-ttu-id="89b1e-134">Im węższy zakres zmiennej, tym mniejsze prawdopodobieństwo, że złośliwy kod może być niewłaściwym użyciem.</span><span class="sxs-lookup"><span data-stu-id="89b1e-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b1e-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89b1e-135">See also</span></span>

- [<span data-ttu-id="89b1e-136">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89b1e-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="89b1e-137">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89b1e-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="89b1e-138">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89b1e-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="89b1e-139">Zmienne</span><span class="sxs-lookup"><span data-stu-id="89b1e-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="89b1e-140">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="89b1e-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="89b1e-141">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89b1e-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
