---
title: 'Instrukcje: Ukrywanie dziedziczonej zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: ee147ecd00b88b538ace32844c42ac9c5022b2ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794696"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="dcc59-102">Instrukcje: Ukrywanie dziedziczonej zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcc59-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="dcc59-103">Klasa pochodna dziedziczy wszystkie definicje klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="dcc59-104">Jeśli chcesz zdefiniować zmienną przy użyciu tej samej nazwie jako element klasy podstawowej, można ukryć, lub *w tle*, ten element klasy bazowej podczas definiowania zmiennej w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="dcc59-105">Jeśli to zrobisz, kod w klasie pochodnej uzyskuje dostęp do zmiennej, chyba że jawnie pomija mechanizm przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="dcc59-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="dcc59-106">Jest kolejnym powodem, że możesz chcieć ukrywanie dziedziczonej zmiennej do ochrony przed poprawki klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="dcc59-107">Klasy bazowej może zostać poddane zmianę, która modyfikuje element, do którego są dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="dcc59-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="dcc59-108">W takim przypadku `Shadows` modyfikator wymusza odwołania z klasy pochodnej jest rozpoznawana do zmiennej, zamiast elementu klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="dcc59-109">Aby ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="dcc59-109">To hide an inherited variable</span></span>  
  
1. <span data-ttu-id="dcc59-110">Upewnij się, że zmiennej, którą chcesz ukryć zadeklarowano na poziomie klasy (poza dowolnej procedury).</span><span class="sxs-lookup"><span data-stu-id="dcc59-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="dcc59-111">W przeciwnym razie nie trzeba je ukryć.</span><span class="sxs-lookup"><span data-stu-id="dcc59-111">Otherwise you do not need to hide it.</span></span>  
  
2. <span data-ttu-id="dcc59-112">Wewnątrz klasy pochodnej, należy napisać [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarowanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="dcc59-113">Użyj takiej samej nazwie, jak w przypadku dziedziczonej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-113">Use the same name as that of the inherited variable.</span></span>  
  
3. <span data-ttu-id="dcc59-114">Obejmują [cieni](../../../../visual-basic/language-reference/modifiers/shadows.md) — słowo kluczowe w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="dcc59-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="dcc59-115">Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="dcc59-116">Poniższy przykład ilustruje przesłanianie dziedziczonej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
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
  
     <span data-ttu-id="dcc59-117">Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i przesłania go w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="dcc59-118">Procedura `showStrings` w klasie pochodnej Wyświetla przesłaniania wersję ciągu podczas nazwę `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="dcc59-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="dcc59-119">Następnie wyświetla tekst z cieniem wersji podczas `shadowString` jest kwalifikowany za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="dcc59-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dcc59-120">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="dcc59-120">Robust Programming</span></span>  
 <span data-ttu-id="dcc59-121">Przesłanianie wprowadza więcej niż jedna wersja zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="dcc59-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="dcc59-122">Instrukcja kodu odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołania zależy od czynników, takich jak lokalizacja instrukcja kodu i występowania ciągu kwalifikującym się.</span><span class="sxs-lookup"><span data-stu-id="dcc59-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="dcc59-123">Może to zwiększyć ryzyko odnoszące się do niezamierzonych wersję zasłonięte zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dcc59-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="dcc59-124">Możesz obniżyć ryzyko kwalifikując pełni wszystkie odwołania do zmiennej zasłonięte.</span><span class="sxs-lookup"><span data-stu-id="dcc59-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc59-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcc59-125">See also</span></span>

- [<span data-ttu-id="dcc59-126">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="dcc59-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="dcc59-127">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dcc59-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="dcc59-128">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="dcc59-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="dcc59-129">Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika</span><span class="sxs-lookup"><span data-stu-id="dcc59-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="dcc59-130">Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="dcc59-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="dcc59-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="dcc59-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="dcc59-132">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="dcc59-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="dcc59-133">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="dcc59-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
