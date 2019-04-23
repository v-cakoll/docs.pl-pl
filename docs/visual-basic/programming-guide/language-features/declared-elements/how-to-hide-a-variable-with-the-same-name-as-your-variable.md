---
title: 'Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)'
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
ms.openlocfilehash: 744c7aed50690d5591d1e8248e121cb66ef39108
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296189"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="15607-102">Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15607-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="15607-103">Można ukryć zmiennej przez *przesłanianie* go, oznacza to poprzez zmianę definicji go ze zmienną o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="15607-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="15607-104">Można w tle zmienną, którą chcesz ukryć na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="15607-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="15607-105">**Cieniowania przez zakres.**</span><span class="sxs-lookup"><span data-stu-id="15607-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="15607-106">Można go cienia przez zakres przez redeclaring go wewnątrz Podobszar regionu zawierającego zmienną, którą chcesz ukryć.</span><span class="sxs-lookup"><span data-stu-id="15607-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="15607-107">**Przesłanianie poprzez dziedziczenie.**</span><span class="sxs-lookup"><span data-stu-id="15607-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="15607-108">Jeśli nie zdefiniowano zmiennej, którą chcesz ukryć na poziomie klasy, można cień go poprzez dziedziczenie przez redeclaring ją za pomocą [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="15607-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="15607-109">Ukrywanie zmiennej na dwa sposoby</span><span class="sxs-lookup"><span data-stu-id="15607-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="15607-110">Aby ukryć zmiennej przez przesłanianie go przy użyciu zakresu</span><span class="sxs-lookup"><span data-stu-id="15607-110">To hide a variable by shadowing it through scope</span></span>  
  
1. <span data-ttu-id="15607-111">Określić region Definiowanie zmiennej, którą chcesz ukryć i określ Podobszar, w której ma zostać przedefiniować go za pomocą zmiennej.</span><span class="sxs-lookup"><span data-stu-id="15607-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="15607-112">Region zmiennej</span><span class="sxs-lookup"><span data-stu-id="15607-112">Variable's region</span></span>|<span data-ttu-id="15607-113">Dozwolone Podobszar dla ponownego definiowania go</span><span class="sxs-lookup"><span data-stu-id="15607-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="15607-114">Moduł</span><span class="sxs-lookup"><span data-stu-id="15607-114">Module</span></span>|<span data-ttu-id="15607-115">Klasa modułu</span><span class="sxs-lookup"><span data-stu-id="15607-115">A class within the module</span></span>|  
    |<span data-ttu-id="15607-116">Class</span><span class="sxs-lookup"><span data-stu-id="15607-116">Class</span></span>|<span data-ttu-id="15607-117">Podklasa klasy</span><span class="sxs-lookup"><span data-stu-id="15607-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="15607-118">Procedury w klasie</span><span class="sxs-lookup"><span data-stu-id="15607-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="15607-119">Nie można przedefiniować procedury zmiennej w bloku, w ramach tej procedury, na przykład w `If`... `End If` konstrukcji lub `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="15607-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2. <span data-ttu-id="15607-120">Utwórz regionu, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="15607-120">Create the subregion if it does not already exist.</span></span>  
  
3. <span data-ttu-id="15607-121">W regionie zapisu [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zadeklarowanie zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="15607-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="15607-122">Gdy kod wewnątrz regionu odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="15607-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="15607-123">W poniższym przykładzie pokazano cieniowania przez zakres, a także odwołania omija cieniowania.</span><span class="sxs-lookup"><span data-stu-id="15607-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="15607-124">Poprzedni przykład deklaruje zmienną `num` zarówno na poziomie modułu, jak i na poziomie procedury (w ramach procedury `show`).</span><span class="sxs-lookup"><span data-stu-id="15607-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="15607-125">Zmienna lokalna `num` zasłania zmiennej poziom modułu `num` w ramach `show`, więc zmiennej lokalnej jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="15607-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="15607-126">Jednak nie ma żadnych zmienną lokalną, aby w tle `num` w `useModuleLevelNum` procedury.</span><span class="sxs-lookup"><span data-stu-id="15607-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="15607-127">W związku z tym `useModuleLevelNum` ustawia wartość zmiennej modułu poziomu 1.</span><span class="sxs-lookup"><span data-stu-id="15607-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="15607-128">`MsgBox` Wywołać wewnątrz `show` pomija przesłaniania mechanizm kwalifikując `num` z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="15607-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="15607-129">W związku z tym Wyświetla zmiennej na poziomie modułu, zamiast zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="15607-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="15607-130">Aby ukryć zmiennej przez przesłanianie go poprzez dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="15607-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1. <span data-ttu-id="15607-131">Upewnij się, że zmiennej, którą chcesz ukryć jest zadeklarowana w klasie i na poziomie klasy (poza dowolnej procedury).</span><span class="sxs-lookup"><span data-stu-id="15607-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="15607-132">W przeciwnym razie nie można go cienia poprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="15607-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2. <span data-ttu-id="15607-133">Zdefiniuj klasę pochodną klasy zmiennej, jeśli już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="15607-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3. <span data-ttu-id="15607-134">W klasie pochodnej zapisu `Dim` instrukcji deklarowania zmiennej.</span><span class="sxs-lookup"><span data-stu-id="15607-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="15607-135">Obejmują [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="15607-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="15607-136">Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="15607-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="15607-137">W poniższym przykładzie pokazano cieniowania przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="15607-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="15607-138">Dzięki temu dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i taki, który pomija cieniowania.</span><span class="sxs-lookup"><span data-stu-id="15607-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="15607-139">Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i przesłania go w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="15607-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="15607-140">Procedura `showStrings` w klasie pochodnej Wyświetla przesłaniania wersję ciągu podczas nazwę `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="15607-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="15607-141">Następnie wyświetla tekst z cieniem wersji podczas `shadowString` jest kwalifikowany za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="15607-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="15607-142">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="15607-142">Robust Programming</span></span>  
 <span data-ttu-id="15607-143">Przesłanianie wprowadza więcej niż jedna wersja zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="15607-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="15607-144">Instrukcja kodu odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołania zależy od czynników, takich jak lokalizacja instrukcja kodu i występowania ciągu kwalifikującym się.</span><span class="sxs-lookup"><span data-stu-id="15607-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="15607-145">Może to zwiększyć ryzyko odnoszące się do niezamierzonych wersję zasłonięte zmiennej.</span><span class="sxs-lookup"><span data-stu-id="15607-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="15607-146">Możesz obniżyć ryzyko kwalifikując pełni wszystkie odwołania do zmiennej zasłonięte.</span><span class="sxs-lookup"><span data-stu-id="15607-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15607-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15607-147">See also</span></span>

- [<span data-ttu-id="15607-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="15607-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="15607-149">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15607-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="15607-150">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="15607-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="15607-151">Instrukcje: Ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="15607-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="15607-152">Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="15607-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="15607-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="15607-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="15607-154">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="15607-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="15607-155">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="15607-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
