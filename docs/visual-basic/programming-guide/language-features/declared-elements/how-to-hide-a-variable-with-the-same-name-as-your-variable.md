---
title: 'Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika'
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
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357235"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="50506-102">Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50506-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="50506-103">Można ukryć zmienną przez jej *obserwowanie* , czyli przez ponowne zdefiniowanie jej przy użyciu zmiennej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="50506-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="50506-104">Można zaobserwować zmienną, która ma być ukryta na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="50506-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="50506-105">**Przesłanianie przez zakres.**</span><span class="sxs-lookup"><span data-stu-id="50506-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="50506-106">Można obsłużyć ten zakres przez Zadeklaruj go wewnątrz podregionu regionu zawierającego zmienną, którą chcesz ukryć.</span><span class="sxs-lookup"><span data-stu-id="50506-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="50506-107">**Przesłanianie przez dziedziczenie.**</span><span class="sxs-lookup"><span data-stu-id="50506-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="50506-108">Jeśli zmienna, która ma być ukryta, jest zdefiniowana na poziomie klasy, można ją utworzyć w tle przez dziedziczenie, ponownie deklarując ją za pomocą słowa kluczowego [Shadows](../../../language-reference/modifiers/shadows.md) w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="50506-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="50506-109">Dwa sposoby ukrywania zmiennej</span><span class="sxs-lookup"><span data-stu-id="50506-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="50506-110">Aby ukryć zmienną przez Zacień jej w zakresie</span><span class="sxs-lookup"><span data-stu-id="50506-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="50506-111">Określ region definiujący zmienną, która ma być ukryta, i określ podregion, w którym ma zostać zmieniona jego zmiana.</span><span class="sxs-lookup"><span data-stu-id="50506-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="50506-112">Region zmiennej</span><span class="sxs-lookup"><span data-stu-id="50506-112">Variable's region</span></span>|<span data-ttu-id="50506-113">Dozwolony podregion na potrzeby jego ponownego definiowania</span><span class="sxs-lookup"><span data-stu-id="50506-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="50506-114">Moduł</span><span class="sxs-lookup"><span data-stu-id="50506-114">Module</span></span>|<span data-ttu-id="50506-115">Klasa w module</span><span class="sxs-lookup"><span data-stu-id="50506-115">A class within the module</span></span>|
    |<span data-ttu-id="50506-116">Klasa</span><span class="sxs-lookup"><span data-stu-id="50506-116">Class</span></span>|<span data-ttu-id="50506-117">Podklasa w klasie</span><span class="sxs-lookup"><span data-stu-id="50506-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="50506-118">Procedura w klasie</span><span class="sxs-lookup"><span data-stu-id="50506-118">A procedure within the class</span></span>|

    <span data-ttu-id="50506-119">Nie można ponownie zdefiniować zmiennej procedury w bloku w ramach tej procedury, na przykład w `If` pętli... `End If` konstrukcja lub `For` pętla.</span><span class="sxs-lookup"><span data-stu-id="50506-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="50506-120">Utwórz podregion, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="50506-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="50506-121">W obszarze podregionu Napisz [instrukcję Dim](../../../language-reference/statements/dim-statement.md) deklarującą zmienną cieniowania.</span><span class="sxs-lookup"><span data-stu-id="50506-121">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="50506-122">Gdy kod wewnątrz podregionu odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="50506-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="50506-123">Poniższy przykład ilustruje przesłanianie przez zakres, a także odwołanie, które pomija przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="50506-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="50506-124">Powyższy przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w procedurze `show` ).</span><span class="sxs-lookup"><span data-stu-id="50506-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="50506-125">Zmienna lokalna `num` zasłania zmienną na poziomie modułu `num` w `show` , więc zmienna lokalna jest ustawiona na 2.</span><span class="sxs-lookup"><span data-stu-id="50506-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="50506-126">Nie istnieje jednak żadna zmienna lokalna do przesłania `num` w `useModuleLevelNum` procedurze.</span><span class="sxs-lookup"><span data-stu-id="50506-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="50506-127">W związku z tym `useModuleLevelNum` ustawia wartość zmiennej poziomu modułu na 1.</span><span class="sxs-lookup"><span data-stu-id="50506-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="50506-128">`MsgBox`Wywołanie wewnątrz `show` pomija mechanizm przesłaniania przez zakwalifikowanie `num` się do nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="50506-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="50506-129">W związku z tym wyświetla zmienną na poziomie modułu zamiast zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="50506-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="50506-130">Aby ukryć zmienną przez przesłonięcie jej przez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="50506-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="50506-131">Upewnij się, że zmienna, która ma być ukryta, jest zadeklarowana w klasie i na poziomie klasy (poza jakąkolwiek procedurą).</span><span class="sxs-lookup"><span data-stu-id="50506-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="50506-132">W przeciwnym razie nie można zasłaniać go przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="50506-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="50506-133">Zdefiniuj klasę pochodną klasy, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="50506-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="50506-134">W klasie pochodnej Napisz `Dim` instrukcję deklarującą zmienną.</span><span class="sxs-lookup"><span data-stu-id="50506-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="50506-135">Uwzględnij słowo kluczowe [Shadows](../../../language-reference/modifiers/shadows.md) w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="50506-135">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="50506-136">Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="50506-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="50506-137">Poniższy przykład ilustruje przesłanianie przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="50506-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="50506-138">Tworzy dwa odwołania, które uzyskują dostęp do zmiennej przesłaniania i jeden, który pomija przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="50506-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="50506-139">Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i zasłania ją w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="50506-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="50506-140">Procedura `showStrings` w klasie pochodnej wyświetla wersję przesłaniania ciągu, gdy nazwa `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="50506-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="50506-141">Następnie wyświetla wersję w tle, gdy `shadowString` jest kwalifikowana za pomocą `MyBase` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="50506-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="50506-142">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="50506-142">Robust Programming</span></span>

<span data-ttu-id="50506-143">Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="50506-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="50506-144">Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego.</span><span class="sxs-lookup"><span data-stu-id="50506-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="50506-145">Może to zwiększyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej cieniowej.</span><span class="sxs-lookup"><span data-stu-id="50506-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="50506-146">To ryzyko można obniżyć, w pełni kwalifikując wszystkie odwołania do zmiennej w tle.</span><span class="sxs-lookup"><span data-stu-id="50506-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="50506-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50506-147">See also</span></span>

- [<span data-ttu-id="50506-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="50506-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="50506-149">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50506-149">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="50506-150">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="50506-150">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="50506-151">Instrukcje: ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="50506-151">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="50506-152">Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="50506-152">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="50506-153">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="50506-153">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="50506-154">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="50506-154">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="50506-155">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="50506-155">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
