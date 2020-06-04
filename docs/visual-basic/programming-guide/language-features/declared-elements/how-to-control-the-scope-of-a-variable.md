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
ms.openlocfilehash: 8b21f22edea84448e3f2969c3e4b07c08a17a338
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357351"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="69379-102">Porady: kontrolowanie zakresu zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69379-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="69379-103">Zwykle zmienna znajduje się w *zakresie*lub jest widoczna dla odwołania w całym regionie, w którym jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="69379-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="69379-104">W niektórych przypadkach *poziom dostępu* zmiennej może mieć wpływ na jego zakres.</span><span class="sxs-lookup"><span data-stu-id="69379-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="69379-105">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](scope.md).</span><span class="sxs-lookup"><span data-stu-id="69379-105">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="69379-106">Zakres na poziomie bloku lub procedury</span><span class="sxs-lookup"><span data-stu-id="69379-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="69379-107">Aby zmienna była widoczna tylko w bloku</span><span class="sxs-lookup"><span data-stu-id="69379-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="69379-108">Umieść [instrukcję Dim](../../../language-reference/statements/dim-statement.md) dla zmiennej między instrukcjami inicjującymi i kończącymi deklaracji tego bloku, na przykład między `For` instrukcjami i a `Next` `For` pętlą.</span><span class="sxs-lookup"><span data-stu-id="69379-108">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="69379-109">Można odwołać się do zmiennej tylko z poziomu bloku.</span><span class="sxs-lookup"><span data-stu-id="69379-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="69379-110">Aby zmienna była widoczna tylko w ramach procedury</span><span class="sxs-lookup"><span data-stu-id="69379-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="69379-111">Umieść `Dim` instrukcję dla zmiennej wewnątrz procedury, ale poza blokami (na przykład `With` blok... `End With` ).</span><span class="sxs-lookup"><span data-stu-id="69379-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="69379-112">Można odwołać się do zmiennej tylko z wewnątrz procedury, w tym w dowolnym bloku zawartym w procedurze.</span><span class="sxs-lookup"><span data-stu-id="69379-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="69379-113">Zakres na poziomie modułu lub przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="69379-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="69379-114">Dla wygody poziom jednoterminowego *modułu* jest stosowany równomiernie dla modułów, klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="69379-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="69379-115">Poziom dostępu zmiennej poziomu modułu określa jej zakres.</span><span class="sxs-lookup"><span data-stu-id="69379-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="69379-116">Przestrzeń nazw, która zawiera moduł, klasę lub strukturę, ma także wpływ na zakres.</span><span class="sxs-lookup"><span data-stu-id="69379-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="69379-117">Aby uczynić zmienną widoczną w całym module, klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="69379-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="69379-118">Umieść `Dim` instrukcję dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.</span><span class="sxs-lookup"><span data-stu-id="69379-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="69379-119">Dołącz [prywatne](../../../language-reference/modifiers/private.md) słowo kluczowe do `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="69379-119">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="69379-120">Możesz odwołać się do zmiennej z dowolnego miejsca w module, klasie lub strukturze, ale nie spoza niej.</span><span class="sxs-lookup"><span data-stu-id="69379-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="69379-121">Aby uczynić zmienną widoczną w całym obszarze nazw</span><span class="sxs-lookup"><span data-stu-id="69379-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="69379-122">Umieść `Dim` instrukcję dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.</span><span class="sxs-lookup"><span data-stu-id="69379-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="69379-123">Dołącz słowo kluczowe [zaprzyjaźnione](../../../language-reference/modifiers/friend.md) lub [publiczne](../../../language-reference/modifiers/public.md) w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="69379-123">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="69379-124">Możesz odwołać się do zmiennej z dowolnego miejsca w przestrzeni nazw zawierającej moduł, klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="69379-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69379-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="69379-125">Example</span></span>  
 <span data-ttu-id="69379-126">Poniższy przykład deklaruje zmienną na poziomie modułu i ogranicza jej widoczność do kodu w module.</span><span class="sxs-lookup"><span data-stu-id="69379-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
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
  
 <span data-ttu-id="69379-127">W poprzednim przykładzie wszystkie procedury zdefiniowane w module `demonstrateScope` mogą odwoływać się do `String` zmiennej `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="69379-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="69379-128">Gdy `usePrivateVariable` procedura jest wywoływana, wyświetla zawartość zmiennej String `strMsg` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="69379-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="69379-129">Przy następujących zmianach do powyższego przykładu zmienna String `strMsg` może być określana przez kod w dowolnym miejscu w przestrzeni nazw swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="69379-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="69379-130">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="69379-130">Robust Programming</span></span>  
 <span data-ttu-id="69379-131">Im węższy zakres zmiennej, tym mniej możliwości odwołujące się do nich zamiast innej zmiennej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="69379-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="69379-132">Możesz również zminimalizować problemy pasujące do odwołania.</span><span class="sxs-lookup"><span data-stu-id="69379-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="69379-133">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="69379-133">.NET Framework Security</span></span>  
 <span data-ttu-id="69379-134">Im węższy zakres zmiennej, tym mniejsze prawdopodobieństwo, że złośliwy kod może być niewłaściwym użyciem.</span><span class="sxs-lookup"><span data-stu-id="69379-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69379-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69379-135">See also</span></span>

- [<span data-ttu-id="69379-136">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69379-136">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="69379-137">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69379-137">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="69379-138">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69379-138">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="69379-139">Zmienne</span><span class="sxs-lookup"><span data-stu-id="69379-139">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="69379-140">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="69379-140">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="69379-141">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69379-141">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
