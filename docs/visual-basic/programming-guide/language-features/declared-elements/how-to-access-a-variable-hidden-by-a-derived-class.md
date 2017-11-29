---
title: "Porady: dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="9fe8a-102">Porady: dostęp do zmiennej ukrytej przez klasę pochodną (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fe8a-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="9fe8a-103">Gdy kod w klasie pochodnej uzyskuje dostęp do zmiennej, kompilator zwykle usuwa odwołania do najbliższej wersji dostępny, oznacza to, że dostępna wersja najmniejszej derivational kroki z poprzednimi wersjami z uzyskiwaniem dostępu do klasy.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="9fe8a-104">Jeśli zmienna jest zdefiniowana w klasie pochodnej, kod zwykle uzyskuje dostęp do tej definicji.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="9fe8a-105">Jeśli zmienna klasy pochodnej cieni zmienna w klasie podstawowej, ukrywa wersja klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="9fe8a-106">Jednak mają dostęp do zmiennej klasy podstawowej przez kwalifikującego się za pomocą `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="9fe8a-107">Dostęp do zmiennej klasy podstawowej ukryty przez klasę pochodną</span><span class="sxs-lookup"><span data-stu-id="9fe8a-107">To access a base class variable hidden by a derived class</span></span>  
  
-   <span data-ttu-id="9fe8a-108">Wyrażenia lub instrukcji przypisania, poprzedź nazwę zmiennej o `MyBase` — słowo kluczowe i kropkę (`.`).</span><span class="sxs-lookup"><span data-stu-id="9fe8a-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="9fe8a-109">Kompilator usuwa odwołanie do klasy podstawowej wersji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="9fe8a-110">Poniższy przykład przedstawia cieniowania przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="9fe8a-111">Powoduje to dodanie dwa odwołania, który uzyskuje dostęp do zmiennej przesłaniania i jedną omija cieniowania.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="9fe8a-112">Powyższy przykład deklaruje zmienną `shadowString` w klasie podstawowej i przesłania go w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="9fe8a-113">Procedura `showStrings` w klasie pochodnej Wyświetla wersję przesłaniania ciągu gdy nazwa `shadowString` nie jest kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="9fe8a-114">Następnie wyświetla zasłonięty wersji podczas `shadowString` jest kwalifikowana z `MyBase` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9fe8a-115">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9fe8a-115">Robust Programming</span></span>  
 <span data-ttu-id="9fe8a-116">Aby zmniejszyć ryzyko odwołujących się do wersji niezamierzone zasłonięty zmiennej, mogą pełnej kwalifikacji wszystkie odwołania do zmiennej zasłonięty.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="9fe8a-117">Przesłanianie wprowadza więcej niż jedną wersję zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="9fe8a-118">Gdy instrukcję kodu odwołuje się do nazwy zmiennej, wersji, do którego kompilator usuwa odwołanie zależy od czynników, takich jak lokalizacja instrukcji kodu oraz występowania ciągu kwalifikujących.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="9fe8a-119">Może to zwiększyć ryzyko wystąpienia odwołujących się do niewłaściwej wersji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9fe8a-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe8a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fe8a-120">See Also</span></span>  
 [<span data-ttu-id="9fe8a-121">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="9fe8a-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="9fe8a-122">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fe8a-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="9fe8a-123">Różnice pomiędzy przesłanianiem i zastępowaniem</span><span class="sxs-lookup"><span data-stu-id="9fe8a-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="9fe8a-124">Porady: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika</span><span class="sxs-lookup"><span data-stu-id="9fe8a-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="9fe8a-125">Porady: ukrywanie dziedziczonej zmiennej</span><span class="sxs-lookup"><span data-stu-id="9fe8a-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="9fe8a-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="9fe8a-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="9fe8a-127">Zastąpienia</span><span class="sxs-lookup"><span data-stu-id="9fe8a-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="9fe8a-128">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="9fe8a-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="9fe8a-129">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="9fe8a-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
