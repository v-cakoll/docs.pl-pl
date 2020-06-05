---
title: 'Porady: dostęp do zmiennej ukrytej przez klasę pochodną'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392860"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="934f9-102">Porady: dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="934f9-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="934f9-103">Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle rozwiązuje odwołanie do najbliższej dostępnej wersji, czyli dostępnej wersji, którą można wykonać z tyłu od klasy dostępu.</span><span class="sxs-lookup"><span data-stu-id="934f9-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="934f9-104">Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.</span><span class="sxs-lookup"><span data-stu-id="934f9-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="934f9-105">Jeśli zmienna klasy pochodnej zasłania zmienną w klasie bazowej, ukrywa wersję klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="934f9-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="934f9-106">Można jednak uzyskać dostęp do zmiennej klasy bazowej, kwalifikując ją za pomocą `MyBase` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="934f9-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="934f9-107">Aby uzyskać dostęp do zmiennej klasy bazowej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="934f9-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="934f9-108">W instrukcji wyrażenia lub przypisania poprzedź nazwę zmiennej `MyBase` słowem kluczowym i kropką ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="934f9-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="934f9-109">Kompilator rozpoznaje odwołanie do wersji klasy bazowej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="934f9-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="934f9-110">Poniższy przykład ilustruje przesłanianie przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="934f9-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="934f9-111">Tworzy dwa odwołania, które uzyskują dostęp do zmiennej przesłaniania i jeden, który pomija przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="934f9-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="934f9-112">Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i zasłania ją w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="934f9-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="934f9-113">Procedura `showStrings` w klasie pochodnej wyświetla wersję przesłaniania ciągu, gdy nazwa `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="934f9-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="934f9-114">Następnie wyświetla wersję w tle, gdy `shadowString` jest kwalifikowana za pomocą `MyBase` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="934f9-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="934f9-115">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="934f9-115">Robust Programming</span></span>

<span data-ttu-id="934f9-116">Aby zmniejszyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej w tle, można w pełni zakwalifikować wszystkie odwołania do zmiennej cieniowej.</span><span class="sxs-lookup"><span data-stu-id="934f9-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="934f9-117">Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="934f9-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="934f9-118">Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego.</span><span class="sxs-lookup"><span data-stu-id="934f9-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="934f9-119">Może to zwiększyć ryzyko odwołania się do niewłaściwej wersji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="934f9-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="934f9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="934f9-120">See also</span></span>

- [<span data-ttu-id="934f9-121">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="934f9-121">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="934f9-122">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="934f9-122">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="934f9-123">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="934f9-123">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="934f9-124">Instrukcje: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika</span><span class="sxs-lookup"><span data-stu-id="934f9-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="934f9-125">Instrukcje: ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="934f9-125">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="934f9-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="934f9-126">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="934f9-127">Przesłonięcia</span><span class="sxs-lookup"><span data-stu-id="934f9-127">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="934f9-128">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="934f9-128">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="934f9-129">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="934f9-129">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
