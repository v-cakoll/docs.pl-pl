---
title: 'Instrukcje: Deklarowanie struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 7fc4aed4d405729b64a2f7ba772cdd794df40f2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825100"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="7dec3-102">Instrukcje: Deklarowanie struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dec3-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="7dec3-103">Rozpocznij deklaracji struktury z [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md), i kończy z `End Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7dec3-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="7dec3-104">Między te dwie instrukcje należy zadeklarować co najmniej jeden *elementu*.</span><span class="sxs-lookup"><span data-stu-id="7dec3-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="7dec3-105">Elementy mogą być dowolnego typu danych, ale co najmniej jedna musi być zmienną nieudostępnionych lub nieudostępnionych, niestandardowych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7dec3-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="7dec3-106">Nie można zainicjować elementy struktury w deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="7dec3-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="7dec3-107">Kiedy Deklarujesz zmienną typu struktury, należy przypisać wartości do elementów, uzyskując dostęp do nich za pośrednictwem zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7dec3-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="7dec3-108">Omówienie różnic między strukturami i klasami, zobacz [struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7dec3-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="7dec3-109">Dla celów demonstracyjnych Rozważmy sytuację, w miejscu do śledzenia nazwa, numer wewnętrzny i wynagrodzenia pracownika.</span><span class="sxs-lookup"><span data-stu-id="7dec3-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="7dec3-110">Struktura umożliwia to zrobić w pojedynczej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7dec3-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="7dec3-111">Aby zadeklarować strukturę</span><span class="sxs-lookup"><span data-stu-id="7dec3-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="7dec3-112">Utwórz początkowy i końcowy instrukcji w strukturze.</span><span class="sxs-lookup"><span data-stu-id="7dec3-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="7dec3-113">Można określić poziom dostępu przy użyciu struktury [publicznych](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe lub można pozwolić, aby go Domyślnie `Public`.</span><span class="sxs-lookup"><span data-stu-id="7dec3-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="7dec3-114">Dodawanie elementów do treści struktury.</span><span class="sxs-lookup"><span data-stu-id="7dec3-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="7dec3-115">Struktura musi mieć co najmniej jeden element.</span><span class="sxs-lookup"><span data-stu-id="7dec3-115">A structure must have at least one element.</span></span> <span data-ttu-id="7dec3-116">Musisz zadeklarować każdego elementu i określić poziom dostępu dla niego.</span><span class="sxs-lookup"><span data-stu-id="7dec3-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="7dec3-117">Jeśli używasz [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez żadnych słów kluczowych, domyślnie dostępność `Public`.</span><span class="sxs-lookup"><span data-stu-id="7dec3-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="7dec3-118">`salary` Pole w powyższym przykładzie jest `Private`, co oznacza, że jest niedostępny poza struktury, nawet z zawierający klasy.</span><span class="sxs-lookup"><span data-stu-id="7dec3-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="7dec3-119">Jednak `giveRaise` procedura jest `Public`, dzięki czemu mogą być wywoływane z poza struktury.</span><span class="sxs-lookup"><span data-stu-id="7dec3-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="7dec3-120">Podobnie, można podnieść `salaryReviewTime` zdarzenie z poza struktury.</span><span class="sxs-lookup"><span data-stu-id="7dec3-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="7dec3-121">Oprócz zmiennych `Sub` procedur i zdarzeń, można również zdefiniować stałych, `Function` procedur i właściwości w strukturze.</span><span class="sxs-lookup"><span data-stu-id="7dec3-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="7dec3-122">Możesz wyznaczyć co najwyżej jedną właściwość jako *właściwość domyślna*, o ile trwa co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="7dec3-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="7dec3-123">Można obsługiwać zdarzenia z [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="7dec3-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="7dec3-124">Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="7dec3-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dec3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dec3-125">See also</span></span>

- [<span data-ttu-id="7dec3-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7dec3-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="7dec3-127">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="7dec3-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="7dec3-128">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="7dec3-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="7dec3-129">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="7dec3-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="7dec3-130">Struktury</span><span class="sxs-lookup"><span data-stu-id="7dec3-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7dec3-131">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="7dec3-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="7dec3-132">Zmienne struktur</span><span class="sxs-lookup"><span data-stu-id="7dec3-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="7dec3-133">Struktury oraz inne elementy programowania</span><span class="sxs-lookup"><span data-stu-id="7dec3-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="7dec3-134">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="7dec3-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="7dec3-135">User-Defined, typ danych</span><span class="sxs-lookup"><span data-stu-id="7dec3-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
