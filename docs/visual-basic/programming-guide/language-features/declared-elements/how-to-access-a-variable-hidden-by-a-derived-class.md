---
title: 'Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61829663"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="309c5-102">Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="309c5-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="309c5-103">Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle jest rozpoznawany jako odwołanie do najbliższej wersji dostępna, oznacza to, dostępnej wersji najmniejszą liczbą derivational kroki z poprzednimi wersjami z dostępu do klasy.</span><span class="sxs-lookup"><span data-stu-id="309c5-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="309c5-104">Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.</span><span class="sxs-lookup"><span data-stu-id="309c5-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="309c5-105">Jeśli zmienna w klasie pochodnej cieni zmiennej w klasie bazowej, ukrywa wersją klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="309c5-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="309c5-106">Jednak możesz mają dostęp do klasy bazowej zmiennej kwalifikując ją za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="309c5-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="309c5-107">Dostęp do zmiennej w klasie bazowej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="309c5-107">To access a base class variable hidden by a derived class</span></span>  
  
- <span data-ttu-id="309c5-108">W wyrażeniu lub instrukcji przypisania, nazwę zmiennej należy poprzedzić `MyBase` — słowo kluczowe i okres (`.`).</span><span class="sxs-lookup"><span data-stu-id="309c5-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="309c5-109">Kompilator rozpoznaje odwołanie do zmiennej wersją klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="309c5-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="309c5-110">W poniższym przykładzie pokazano cieniowania przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="309c5-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="309c5-111">Dzięki temu dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i taki, który pomija cieniowania.</span><span class="sxs-lookup"><span data-stu-id="309c5-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="309c5-112">Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i przesłania go w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="309c5-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="309c5-113">Procedura `showStrings` w klasie pochodnej Wyświetla przesłaniania wersję ciągu podczas nazwę `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="309c5-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="309c5-114">Następnie wyświetla tekst z cieniem wersji podczas `shadowString` jest kwalifikowany za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="309c5-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="309c5-115">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="309c5-115">Robust Programming</span></span>  
 <span data-ttu-id="309c5-116">Aby zmniejszyć ryzyko odnoszące się do niezamierzonych wersję zasłonięte zmiennej, można pełnej kwalifikacji wszystkie odwołania do zmiennej zasłonięte.</span><span class="sxs-lookup"><span data-stu-id="309c5-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="309c5-117">Przesłanianie wprowadza więcej niż jedna wersja zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="309c5-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="309c5-118">Instrukcja kodu odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołania zależy od czynników, takich jak lokalizacja instrukcja kodu i występowania ciągu kwalifikującym się.</span><span class="sxs-lookup"><span data-stu-id="309c5-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="309c5-119">Może to zwiększyć ryzyko odnoszące się do niewłaściwej wersji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="309c5-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309c5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="309c5-120">See also</span></span>

- [<span data-ttu-id="309c5-121">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="309c5-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="309c5-122">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="309c5-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="309c5-123">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="309c5-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="309c5-124">Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika</span><span class="sxs-lookup"><span data-stu-id="309c5-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="309c5-125">Instrukcje: Ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="309c5-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="309c5-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="309c5-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="309c5-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="309c5-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="309c5-128">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="309c5-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="309c5-129">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="309c5-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
