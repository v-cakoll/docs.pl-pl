---
title: 'Porady: ukrywanie dziedziczonej zmiennej'
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
ms.openlocfilehash: c20c36b26c90c82da4e8836799f499498ccc40e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345356"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="e79ae-102">Porady: ukrywanie dziedziczonej zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e79ae-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="e79ae-103">Klasa pochodna dziedziczy wszystkie definicje swojej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="e79ae-104">Jeśli chcesz zdefiniować zmienną przy użyciu takiej samej nazwy, jak element klasy bazowej, można ukryć lub *zaobserwować*ten element klasy bazowej podczas definiowania zmiennej w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="e79ae-105">W takim przypadku kod w klasie pochodnej uzyskuje dostęp do zmiennej, chyba że jawnie pomija mechanizm przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="e79ae-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="e79ae-106">Kolejną przyczyną może być ukrycie dziedziczonej zmiennej jest ochrona przed poprawką klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="e79ae-107">Klasa bazowa może ulec zmianie, która zmienia element, który jest dziedziczony.</span><span class="sxs-lookup"><span data-stu-id="e79ae-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="e79ae-108">W takim przypadku modyfikator `Shadows` wymusza odwołania z klasy pochodnej, aby można było je rozpoznać do zmiennej, a nie do elementu klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="e79ae-109">Aby ukryć dziedziczoną zmienną</span><span class="sxs-lookup"><span data-stu-id="e79ae-109">To hide an inherited variable</span></span>

1. <span data-ttu-id="e79ae-110">Upewnij się, że zmienna, która ma być ukryta, jest zadeklarowana na poziomie klasy (poza jakąkolwiek procedurą).</span><span class="sxs-lookup"><span data-stu-id="e79ae-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="e79ae-111">W przeciwnym razie nie trzeba go ukrywać.</span><span class="sxs-lookup"><span data-stu-id="e79ae-111">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="e79ae-112">Wewnątrz klasy pochodnej Napisz [instrukcję Dim](../../../language-reference/statements/dim-statement.md) deklarującą zmienną.</span><span class="sxs-lookup"><span data-stu-id="e79ae-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="e79ae-113">Użyj takiej samej nazwy, jak w przypadku zmiennej dziedziczonej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-113">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="e79ae-114">Uwzględnij słowo kluczowe [Shadows](../../../language-reference/modifiers/shadows.md) w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e79ae-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="e79ae-115">Gdy kod w klasie pochodnej odwołuje się do nazwy zmiennej, kompilator rozpoznaje odwołanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="e79ae-116">Poniższy przykład ilustruje cieniowanie zmiennej dziedziczonej:</span><span class="sxs-lookup"><span data-stu-id="e79ae-116">The following example illustrates shadowing of an inherited variable:</span></span>
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="e79ae-117">Poprzedni przykład deklaruje zmienną `shadowString` w klasie bazowej i zasłania ją w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="e79ae-118">Procedura `ShowStrings` w klasie pochodnej wyświetla wersję przesłaniania ciągu, gdy nazwa `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="e79ae-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="e79ae-119">Następnie wyświetla wersję w tle, gdy `shadowString` jest kwalifikowana za pomocą słowa kluczowego `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="e79ae-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e79ae-120">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e79ae-120">Robust programming</span></span>

<span data-ttu-id="e79ae-121">Przesłanianie zawiera więcej niż jedną wersję zmiennej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="e79ae-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="e79ae-122">Gdy instrukcja Code odwołuje się do nazwy zmiennej, wersja, do której kompilator rozpoznaje odwołanie, zależy od czynników, takich jak lokalizacja instrukcji Code i obecność ciągu uprawniającego.</span><span class="sxs-lookup"><span data-stu-id="e79ae-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="e79ae-123">Może to zwiększyć ryzyko związane z odwołującymi się do niezamierzonej wersji zmiennej cieniowej.</span><span class="sxs-lookup"><span data-stu-id="e79ae-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="e79ae-124">To ryzyko można obniżyć, w pełni kwalifikując wszystkie odwołania do zmiennej w tle.</span><span class="sxs-lookup"><span data-stu-id="e79ae-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="e79ae-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e79ae-125">See also</span></span>

- [<span data-ttu-id="e79ae-126">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="e79ae-126">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="e79ae-127">Obserwowanie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e79ae-127">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="e79ae-128">Różnice między przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="e79ae-128">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="e79ae-129">Instrukcje: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika</span><span class="sxs-lookup"><span data-stu-id="e79ae-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="e79ae-130">Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="e79ae-130">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="e79ae-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="e79ae-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="e79ae-132">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="e79ae-132">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="e79ae-133">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="e79ae-133">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
