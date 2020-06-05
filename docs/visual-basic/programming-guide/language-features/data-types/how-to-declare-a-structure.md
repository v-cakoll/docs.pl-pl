---
title: 'Instrukcje: Deklarowanie struktury'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a6b70d0973e92db90e35e61b7fed2279c5b0bac3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393977"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="3324f-102">Porady: deklarowanie struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3324f-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="3324f-103">Należy rozpocząć deklarację struktury za pomocą [instrukcji Structure](../../../language-reference/statements/structure-statement.md)i zakończyć ją za pomocą `End Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3324f-103">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="3324f-104">Między tymi dwiema instrukcjami należy zadeklarować co najmniej jeden *element*.</span><span class="sxs-lookup"><span data-stu-id="3324f-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="3324f-105">Elementy mogą być dowolnego typu danych, ale co najmniej jeden musi być zmienną nieudostępnioną lub niestandardowym zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="3324f-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="3324f-106">Nie można zainicjować któregokolwiek z elementów struktury w deklaracji struktury.</span><span class="sxs-lookup"><span data-stu-id="3324f-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="3324f-107">Podczas deklarowania zmiennej jako typu struktury, należy przypisać wartości do elementów, uzyskując dostęp do nich za pomocą zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3324f-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="3324f-108">Aby zapoznać się z omówieniem różnic między strukturami i klasami, zobacz [struktury i klasy](structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="3324f-108">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="3324f-109">W celach demonstracyjnych Rozważmy sytuację, w której chcesz śledzić nazwisko pracownika, numer telefonu i wynagrodzenie.</span><span class="sxs-lookup"><span data-stu-id="3324f-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="3324f-110">Struktura pozwala wykonać tę czynność w jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3324f-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="3324f-111">Aby zadeklarować strukturę</span><span class="sxs-lookup"><span data-stu-id="3324f-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="3324f-112">Utwórz instrukcje początkowe i końcowe dla struktury.</span><span class="sxs-lookup"><span data-stu-id="3324f-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="3324f-113">Możesz określić poziom dostępu struktury za pomocą [publicznego](../../../language-reference/modifiers/public.md), [chronionego](../../../language-reference/modifiers/protected.md), [przyjaznego](../../../language-reference/modifiers/friend.md)lub [prywatnego](../../../language-reference/modifiers/private.md) słowa kluczowego lub można zezwolić na ustawienie domyślne `Public` .</span><span class="sxs-lookup"><span data-stu-id="3324f-113">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="3324f-114">Dodaj elementy do treści struktury.</span><span class="sxs-lookup"><span data-stu-id="3324f-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="3324f-115">Struktura musi mieć co najmniej jeden element.</span><span class="sxs-lookup"><span data-stu-id="3324f-115">A structure must have at least one element.</span></span> <span data-ttu-id="3324f-116">Należy zadeklarować każdy element i określić dla niego poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="3324f-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="3324f-117">Jeśli używasz [instrukcji Dim](../../../language-reference/statements/dim-statement.md) bez żadnych słów kluczowych, dostępność domyślna to `Public` .</span><span class="sxs-lookup"><span data-stu-id="3324f-117">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
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
  
     <span data-ttu-id="3324f-118">`salary`Pole w powyższym przykładzie jest `Private` , co oznacza, że jest niedostępne poza strukturą, nawet z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="3324f-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="3324f-119">Jednak `giveRaise` procedura jest `Public` , dlatego można ją wywołać spoza struktury.</span><span class="sxs-lookup"><span data-stu-id="3324f-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="3324f-120">Analogicznie, można zgłosić `salaryReviewTime` zdarzenie spoza struktury.</span><span class="sxs-lookup"><span data-stu-id="3324f-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="3324f-121">Oprócz zmiennych, `Sub` procedur i zdarzeń można także definiować stałe, `Function` procedury i właściwości w strukturze.</span><span class="sxs-lookup"><span data-stu-id="3324f-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="3324f-122">Można wyznaczyć najwyżej jedną właściwość jako *Właściwość domyślną*, pod warunkiem, że przyjmuje co najmniej jeden argument.</span><span class="sxs-lookup"><span data-stu-id="3324f-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="3324f-123">Można obsłużyć zdarzenie z [wspólną](../../../language-reference/modifiers/shared.md) `Sub` procedurą.</span><span class="sxs-lookup"><span data-stu-id="3324f-123">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="3324f-124">Aby uzyskać więcej informacji, zobacz [jak: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="3324f-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3324f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3324f-125">See also</span></span>

- [<span data-ttu-id="3324f-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="3324f-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="3324f-127">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="3324f-127">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="3324f-128">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="3324f-128">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="3324f-129">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="3324f-129">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="3324f-130">Struktury</span><span class="sxs-lookup"><span data-stu-id="3324f-130">Structures</span></span>](structures.md)
- [<span data-ttu-id="3324f-131">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="3324f-131">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="3324f-132">Zmienne struktur</span><span class="sxs-lookup"><span data-stu-id="3324f-132">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="3324f-133">Struktury oraz inne elementy programowania</span><span class="sxs-lookup"><span data-stu-id="3324f-133">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="3324f-134">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="3324f-134">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="3324f-135">User-Defined Data Type</span><span class="sxs-lookup"><span data-stu-id="3324f-135">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
