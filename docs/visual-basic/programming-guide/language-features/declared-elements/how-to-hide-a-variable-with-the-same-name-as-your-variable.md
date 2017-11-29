---
title: "Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af031f3ef134b2a509922e6ada28aa5b2b80d641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="f12e6-102">Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f12e6-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="f12e6-103">Można ukryć zmiennej przez *przesłanianie* go, czyli przy ponownym zdefiniowaniem go za pomocą zmiennych o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f12e6-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="f12e6-104">Można obserwować zmiennej, którą chcesz ukryć na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="f12e6-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="f12e6-105">**Cieniowania przez zakres.**</span><span class="sxs-lookup"><span data-stu-id="f12e6-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="f12e6-106">Można obserwować go za pomocą zakresu przez ponownego deklarowania go wewnątrz regionu, regionu zawierający zmiennej, którą chcesz ukryć.</span><span class="sxs-lookup"><span data-stu-id="f12e6-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="f12e6-107">**Przesłanianie przez dziedziczenie.**</span><span class="sxs-lookup"><span data-stu-id="f12e6-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="f12e6-108">Jeśli chcesz ukryć zmienna jest zdefiniowana na poziomie klasy, można obserwować go poprzez dziedziczenie przez ponownego deklarowania go przy użyciu [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f12e6-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="f12e6-109">Dwa sposoby ukrywanie zmiennej</span><span class="sxs-lookup"><span data-stu-id="f12e6-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="f12e6-110">Aby ukryć przez przesłanianie go za pomocą zakresu zmiennej</span><span class="sxs-lookup"><span data-stu-id="f12e6-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="f12e6-111">Określanie obszaru Definiowanie zmiennej, którą chcesz ukryć i określ dla regionu, w którym można zdefiniować ją ponownie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f12e6-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="f12e6-112">Region zmiennej</span><span class="sxs-lookup"><span data-stu-id="f12e6-112">Variable's region</span></span>|<span data-ttu-id="f12e6-113">Podregion dopuszczalny dla ponownym zdefiniowaniem go</span><span class="sxs-lookup"><span data-stu-id="f12e6-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="f12e6-114">Moduł</span><span class="sxs-lookup"><span data-stu-id="f12e6-114">Module</span></span>|<span data-ttu-id="f12e6-115">Klasa modułu</span><span class="sxs-lookup"><span data-stu-id="f12e6-115">A class within the module</span></span>|  
    |<span data-ttu-id="f12e6-116">Class</span><span class="sxs-lookup"><span data-stu-id="f12e6-116">Class</span></span>|<span data-ttu-id="f12e6-117">Podklasa klasy</span><span class="sxs-lookup"><span data-stu-id="f12e6-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="f12e6-118">Procedury w ramach klasy</span><span class="sxs-lookup"><span data-stu-id="f12e6-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="f12e6-119">Nie można zmienić procedury zmiennej w bloku, w ramach tej procedury, na przykład w `If`... `End If` konstrukcji lub `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="f12e6-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="f12e6-120">Jeśli jeszcze nie istnieje, należy utworzyć regionu.</span><span class="sxs-lookup"><span data-stu-id="f12e6-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="f12e6-121">W obrębie regionu, zapisać [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarowanie zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="f12e6-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="f12e6-122">Gdy kodu wewnątrz regionu odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="f12e6-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="f12e6-123">Poniższy przykład przedstawia cieniowania przez zakres, a także omija przesłanianie odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f12e6-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     <span data-ttu-id="f12e6-124">Powyższy przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w procedurze `show`).</span><span class="sxs-lookup"><span data-stu-id="f12e6-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="f12e6-125">Zmienna lokalna `num` zasłania zmiennej poziom modułu `num` w `show`, więc zmiennej lokalnej jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="f12e6-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="f12e6-126">Jednak nie ma żadnych zmiennej lokalnej na tle `num` w `useModuleLevelNum` procedury.</span><span class="sxs-lookup"><span data-stu-id="f12e6-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="f12e6-127">W związku z tym `useModuleLevelNum` ustawia wartość zmiennej modułu poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="f12e6-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="f12e6-128">`MsgBox` Wywołać wewnątrz `show` pomija przesłaniania mechanizm przez kwalifikowanie `num` z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="f12e6-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="f12e6-129">W związku z tym Wyświetla zmiennej poziom modułu zamiast zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f12e6-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="f12e6-130">Aby ukryć zmiennej przez przesłanianie go poprzez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="f12e6-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="f12e6-131">Upewnij się, że zmiennej, którą chcesz ukryć jest zadeklarowana w klasie i na poziomie klasy (poza dowolnej procedury).</span><span class="sxs-lookup"><span data-stu-id="f12e6-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="f12e6-132">W przeciwnym razie nie można go cienia przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="f12e6-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="f12e6-133">Zdefiniuj klasę pochodzącą od klasy zmiennej, jeśli już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f12e6-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="f12e6-134">W klasie pochodnej zapisu `Dim` instrukcji deklarowanie zmiennej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f12e6-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="f12e6-135">Obejmują [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f12e6-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="f12e6-136">Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f12e6-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="f12e6-137">Poniższy przykład przedstawia cieniowania przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="f12e6-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="f12e6-138">Powoduje to dodanie dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i jedną omija cieniowania.</span><span class="sxs-lookup"><span data-stu-id="f12e6-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="f12e6-139">Powyższy przykład deklaruje zmienną `shadowString` w klasie podstawowej i przesłania go w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f12e6-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="f12e6-140">Procedura `showStrings` w klasie pochodnej Wyświetla wersję przesłaniania ciągu gdy nazwa `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="f12e6-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="f12e6-141">Następnie wyświetla zasłonięty wersji podczas `shadowString` jest kwalifikowana z `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f12e6-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f12e6-142">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f12e6-142">Robust Programming</span></span>  
 <span data-ttu-id="f12e6-143">Przesłanianie wprowadza więcej niż jedną wersję zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f12e6-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="f12e6-144">Gdy instrukcję kodu odwołuje się do nazwy zmiennej, wersji, do którego kompilator usuwa odwołanie zależy od czynników, takich jak lokalizacja instrukcji kodu oraz występowania ciągu kwalifikujących.</span><span class="sxs-lookup"><span data-stu-id="f12e6-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="f12e6-145">Może to zwiększyć ryzyko wystąpienia odwołujących się do wersji niezamierzone zmiennej zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="f12e6-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="f12e6-146">Można zmniejszyć ryzyko przez pełni kwalifikowanie wszystkie odwołania do zmiennej zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="f12e6-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12e6-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f12e6-147">See Also</span></span>  
 [<span data-ttu-id="f12e6-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="f12e6-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="f12e6-149">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f12e6-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="f12e6-150">Różnice pomiędzy przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="f12e6-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="f12e6-151">Porady: ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="f12e6-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="f12e6-152">Porady: dostęp do zmiennej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="f12e6-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="f12e6-153">Zastąpienia</span><span class="sxs-lookup"><span data-stu-id="f12e6-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="f12e6-154">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="f12e6-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="f12e6-155">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="f12e6-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
