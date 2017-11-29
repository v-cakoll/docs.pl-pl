---
title: 'Porady: kontrolowanie zakresu zmiennej (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7284d344e3bf0fdd0f900f2a820d6c8db4a4bf74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="01ca5-102">Porady: kontrolowanie zakresu zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ca5-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="01ca5-103">Zazwyczaj jest zmienną w *zakres*, czy widoczny dla odwołania w całym regionie ją zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="01ca5-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="01ca5-104">W niektórych przypadkach zmiennej w *poziom dostępu* mogą mieć wpływ na jego zakres.</span><span class="sxs-lookup"><span data-stu-id="01ca5-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="01ca5-105">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="01ca5-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="01ca5-106">Zakres na poziomie procedurę lub blok</span><span class="sxs-lookup"><span data-stu-id="01ca5-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="01ca5-107">Aby wyświetlić tylko w bloku zmiennej</span><span class="sxs-lookup"><span data-stu-id="01ca5-107">To make a variable visible only within a block</span></span>  
  
-   <span data-ttu-id="01ca5-108">Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej między inicjowanie i kończenie instrukcji deklaracji tego bloku, na przykład między `For` i `Next` instrukcje `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="01ca5-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="01ca5-109">Mogą odwoływać się do zmiennej tylko z wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="01ca5-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="01ca5-110">Aby wyświetlić tylko w obrębie procedury zmiennej</span><span class="sxs-lookup"><span data-stu-id="01ca5-110">To make a variable visible only within a procedure</span></span>  
  
-   <span data-ttu-id="01ca5-111">Miejsce `Dim` instrukcji dla zmiennej wewnątrz procedury, ale poza bloku (takich jak `With`... `End With` bloku).</span><span class="sxs-lookup"><span data-stu-id="01ca5-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="01ca5-112">Mogą odwoływać się do zmiennej tylko z wewnątrz procedury, między innymi wewnątrz bloku zawarty w procedurze.</span><span class="sxs-lookup"><span data-stu-id="01ca5-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="01ca5-113">Zakres na poziomie Namespace lub modułu</span><span class="sxs-lookup"><span data-stu-id="01ca5-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="01ca5-114">Dla wygody pojedynczy termin *poziom modułu* dotyczą modułów, klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="01ca5-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="01ca5-115">Poziom dostępu do zmiennej poziomu modułu określa jej zakres.</span><span class="sxs-lookup"><span data-stu-id="01ca5-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="01ca5-116">Przestrzeń nazw, który zawiera modułu, klasy lub struktury wpływ również zakres.</span><span class="sxs-lookup"><span data-stu-id="01ca5-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="01ca5-117">Aby wyświetlić zmiennej w całym modułu, klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="01ca5-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1.  <span data-ttu-id="01ca5-118">Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="01ca5-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="01ca5-119">Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="01ca5-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="01ca5-120">Można odwołać się do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nią.</span><span class="sxs-lookup"><span data-stu-id="01ca5-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="01ca5-121">Aby zmienna widoczne w przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="01ca5-121">To make a variable visible throughout a namespace</span></span>  
  
1.  <span data-ttu-id="01ca5-122">Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="01ca5-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="01ca5-123">Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="01ca5-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="01ca5-124">Mogą odwoływać się do zmiennej z dowolnego miejsca w przestrzeni nazw zawierającej modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="01ca5-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ca5-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="01ca5-125">Example</span></span>  
 <span data-ttu-id="01ca5-126">W poniższym przykładzie deklaruje zmienną na poziomie modułu i ogranicza ich widoczność jej do kodu w module.</span><span class="sxs-lookup"><span data-stu-id="01ca5-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
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
  
 <span data-ttu-id="01ca5-127">W poprzednim przykładzie wszystkie procedury zdefiniowanego w module `demonstrateScope` mogą odwoływać się do `String` zmiennej `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="01ca5-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="01ca5-128">Gdy `usePrivateVariable` procedura jest wywoływana, wyświetla zawartość zmiennej ciągu `strMsg` w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="01ca5-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="01ca5-129">Z następującą modyfikacją jak w poprzednim przykładzie zmienna string `strMsg` mogą być przywoływane przez kod w dowolnym miejscu jego deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="01ca5-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="01ca5-130">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="01ca5-130">Robust Programming</span></span>  
 <span data-ttu-id="01ca5-131">Im bardziej doprecyzowane zakres zmiennej mniej możliwości, jakie masz przypadkowo odwołujące się do niego zamiast inna zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="01ca5-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="01ca5-132">Można również zminimalizować problemy odwołanie do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="01ca5-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="01ca5-133">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="01ca5-133">.NET Framework Security</span></span>  
 <span data-ttu-id="01ca5-134">Im bardziej doprecyzowane zakresu zmiennej z niego korzystać im mniejsza ryzyko, które złośliwy kod może wykonać niewłaściwy.</span><span class="sxs-lookup"><span data-stu-id="01ca5-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ca5-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01ca5-135">See Also</span></span>  
 [<span data-ttu-id="01ca5-136">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01ca5-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="01ca5-137">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01ca5-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="01ca5-138">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01ca5-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="01ca5-139">Zmienne</span><span class="sxs-lookup"><span data-stu-id="01ca5-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="01ca5-140">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="01ca5-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="01ca5-141">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="01ca5-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
