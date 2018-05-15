---
title: 'Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: a7ebc4eb44592800decd5ef943750f0cd845afb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="c90fc-102">Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c90fc-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="c90fc-103">Można ukryć zmiennej przez *przesłanianie* go, czyli przy ponownym zdefiniowaniem go za pomocą zmiennych o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c90fc-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="c90fc-104">Można obserwować zmiennej, którą chcesz ukryć na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="c90fc-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="c90fc-105">**Cieniowania przez zakres.**</span><span class="sxs-lookup"><span data-stu-id="c90fc-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="c90fc-106">Można obserwować go za pomocą zakresu przez ponownego deklarowania go wewnątrz regionu, regionu zawierający zmiennej, którą chcesz ukryć.</span><span class="sxs-lookup"><span data-stu-id="c90fc-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="c90fc-107">**Przesłanianie przez dziedziczenie.**</span><span class="sxs-lookup"><span data-stu-id="c90fc-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="c90fc-108">Jeśli chcesz ukryć zmienna jest zdefiniowana na poziomie klasy, można obserwować go poprzez dziedziczenie przez ponownego deklarowania go przy użyciu [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c90fc-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="c90fc-109">Dwa sposoby ukrywanie zmiennej</span><span class="sxs-lookup"><span data-stu-id="c90fc-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="c90fc-110">Aby ukryć przez przesłanianie go za pomocą zakresu zmiennej</span><span class="sxs-lookup"><span data-stu-id="c90fc-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="c90fc-111">Określanie obszaru Definiowanie zmiennej, którą chcesz ukryć i określ dla regionu, w którym można zdefiniować ją ponownie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c90fc-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="c90fc-112">Region zmiennej</span><span class="sxs-lookup"><span data-stu-id="c90fc-112">Variable's region</span></span>|<span data-ttu-id="c90fc-113">Podregion dopuszczalny dla ponownym zdefiniowaniem go</span><span class="sxs-lookup"><span data-stu-id="c90fc-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="c90fc-114">Moduł</span><span class="sxs-lookup"><span data-stu-id="c90fc-114">Module</span></span>|<span data-ttu-id="c90fc-115">Klasa modułu</span><span class="sxs-lookup"><span data-stu-id="c90fc-115">A class within the module</span></span>|  
    |<span data-ttu-id="c90fc-116">Class</span><span class="sxs-lookup"><span data-stu-id="c90fc-116">Class</span></span>|<span data-ttu-id="c90fc-117">Podklasa klasy</span><span class="sxs-lookup"><span data-stu-id="c90fc-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="c90fc-118">Procedury w ramach klasy</span><span class="sxs-lookup"><span data-stu-id="c90fc-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="c90fc-119">Nie można zmienić procedury zmiennej w bloku, w ramach tej procedury, na przykład w `If`... `End If` konstrukcji lub `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="c90fc-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="c90fc-120">Jeśli jeszcze nie istnieje, należy utworzyć regionu.</span><span class="sxs-lookup"><span data-stu-id="c90fc-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="c90fc-121">W obrębie regionu, zapisać [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarowanie zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="c90fc-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="c90fc-122">Gdy kodu wewnątrz regionu odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="c90fc-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="c90fc-123">Poniższy przykład przedstawia cieniowania przez zakres, a także omija przesłanianie odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c90fc-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="c90fc-124">Powyższy przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w procedurze `show`).</span><span class="sxs-lookup"><span data-stu-id="c90fc-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="c90fc-125">Zmienna lokalna `num` zasłania zmiennej poziom modułu `num` w `show`, więc zmiennej lokalnej jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="c90fc-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="c90fc-126">Jednak nie ma żadnych zmiennej lokalnej na tle `num` w `useModuleLevelNum` procedury.</span><span class="sxs-lookup"><span data-stu-id="c90fc-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="c90fc-127">W związku z tym `useModuleLevelNum` ustawia wartość zmiennej modułu poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="c90fc-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="c90fc-128">`MsgBox` Wywołać wewnątrz `show` pomija przesłaniania mechanizm przez kwalifikowanie `num` z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="c90fc-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="c90fc-129">W związku z tym Wyświetla zmiennej poziom modułu zamiast zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c90fc-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="c90fc-130">Aby ukryć zmiennej przez przesłanianie go poprzez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="c90fc-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="c90fc-131">Upewnij się, że zmiennej, którą chcesz ukryć jest zadeklarowana w klasie i na poziomie klasy (poza dowolnej procedury).</span><span class="sxs-lookup"><span data-stu-id="c90fc-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="c90fc-132">W przeciwnym razie nie można go cienia przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="c90fc-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="c90fc-133">Zdefiniuj klasę pochodzącą od klasy zmiennej, jeśli już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c90fc-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="c90fc-134">W klasie pochodnej zapisu `Dim` instrukcji deklarowanie zmiennej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c90fc-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="c90fc-135">Obejmują [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c90fc-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="c90fc-136">Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator usuwa odwołanie do zmiennej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c90fc-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="c90fc-137">Poniższy przykład przedstawia cieniowania przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="c90fc-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="c90fc-138">Powoduje to dodanie dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i jedną omija cieniowania.</span><span class="sxs-lookup"><span data-stu-id="c90fc-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="c90fc-139">Powyższy przykład deklaruje zmienną `shadowString` w klasie podstawowej i przesłania go w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c90fc-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="c90fc-140">Procedura `showStrings` w klasie pochodnej Wyświetla wersję przesłaniania ciągu gdy nazwa `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="c90fc-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="c90fc-141">Następnie wyświetla zasłonięty wersji podczas `shadowString` jest kwalifikowana z `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c90fc-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c90fc-142">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c90fc-142">Robust Programming</span></span>  
 <span data-ttu-id="c90fc-143">Przesłanianie wprowadza więcej niż jedną wersję zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c90fc-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="c90fc-144">Gdy instrukcję kodu odwołuje się do nazwy zmiennej, wersji, do którego kompilator usuwa odwołanie zależy od czynników, takich jak lokalizacja instrukcji kodu oraz występowania ciągu kwalifikujących.</span><span class="sxs-lookup"><span data-stu-id="c90fc-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="c90fc-145">Może to zwiększyć ryzyko wystąpienia odwołujących się do wersji niezamierzone zmiennej zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="c90fc-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="c90fc-146">Można zmniejszyć ryzyko przez pełni kwalifikowanie wszystkie odwołania do zmiennej zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="c90fc-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90fc-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c90fc-147">See Also</span></span>  
 [<span data-ttu-id="c90fc-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="c90fc-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="c90fc-149">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c90fc-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="c90fc-150">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="c90fc-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="c90fc-151">Instrukcje: ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="c90fc-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="c90fc-152">Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="c90fc-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="c90fc-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="c90fc-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="c90fc-154">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="c90fc-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="c90fc-155">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="c90fc-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
