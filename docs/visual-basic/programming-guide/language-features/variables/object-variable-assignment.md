---
title: Przypisanie zmiennej obiektu
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351829"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="16a6f-102">Przypisanie zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16a6f-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="16a6f-103">Możesz użyć normalnej instrukcji przypisania, aby przypisać obiekt do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="16a6f-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="16a6f-104">Można przypisać wyrażenie obiektu lub słowo kluczowe [Nothing](../../../../visual-basic/language-reference/nothing.md) , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="16a6f-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="16a6f-105">`Nothing` oznacza, że żaden obiekt nie jest obecnie przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="16a6f-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="16a6f-106">Inicjowanie</span><span class="sxs-lookup"><span data-stu-id="16a6f-106">Initialization</span></span>

<span data-ttu-id="16a6f-107">Gdy kod zacznie działać, zmienne obiektu są inicjowane w celu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="16a6f-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="16a6f-108">Te, których deklaracje obejmują inicjalizację, są ponownie inicjowane do wartości określonych podczas wykonywania instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="16a6f-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="16a6f-109">Można uwzględnić inicjalizację w deklaracji za pomocą słowa kluczowego [New](../../../../visual-basic/language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="16a6f-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="16a6f-110">Następujące instrukcje deklaracji deklarują zmienne obiektów `testUri` i `ver` i przypisują do nich określone obiekty.</span><span class="sxs-lookup"><span data-stu-id="16a6f-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="16a6f-111">Każdy z nich używa jednego z przeciążonych konstruktorów odpowiedniej klasy w celu zainicjowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="16a6f-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="16a6f-112">Usunięcia powiązania zastrzeżonego</span><span class="sxs-lookup"><span data-stu-id="16a6f-112">Disassociation</span></span>

<span data-ttu-id="16a6f-113">Ustawienie zmiennej obiektu na `Nothing` przerywa skojarzenie zmiennej z dowolnym określonym obiektem.</span><span class="sxs-lookup"><span data-stu-id="16a6f-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="16a6f-114">Zapobiega to przypadkowemu zmianie obiektu przez zmianę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="16a6f-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="16a6f-115">Pozwala również sprawdzić, czy zmienna obiektu wskazuje prawidłowy obiekt, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="16a6f-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="16a6f-116">Jeśli obiekt, do którego odwołuje się zmienna, znajduje się w innej aplikacji, ten test nie może określić, czy aplikacja została zakończona, czy po prostu unieważnia obiekt.</span><span class="sxs-lookup"><span data-stu-id="16a6f-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="16a6f-117">Zmienna obiektu o wartości `Nothing` jest również nazywana *odwołaniem o wartości null*.</span><span class="sxs-lookup"><span data-stu-id="16a6f-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="16a6f-118">Bieżące wystąpienie</span><span class="sxs-lookup"><span data-stu-id="16a6f-118">Current Instance</span></span>

<span data-ttu-id="16a6f-119">*Bieżące wystąpienie* obiektu to ten, w którym kod jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="16a6f-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="16a6f-120">Ponieważ cały kod jest wykonywany wewnątrz procedury, bieżące wystąpienie jest tym, w którym procedura została wywołana.</span><span class="sxs-lookup"><span data-stu-id="16a6f-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="16a6f-121">Słowo kluczowe `Me` działa jako zmienna obiektu odwołująca się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="16a6f-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="16a6f-122">Jeśli procedura nie jest [udostępniona](../../../../visual-basic/language-reference/modifiers/shared.md), może użyć słowa kluczowego `Me`, aby uzyskać wskaźnik do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="16a6f-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="16a6f-123">Współużytkowane procedury nie mogą być skojarzone z określonym wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="16a6f-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="16a6f-124">Używanie `Me` jest szczególnie przydatne do przekazywania bieżącego wystąpienia do procedury w innym module.</span><span class="sxs-lookup"><span data-stu-id="16a6f-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="16a6f-125">Załóżmy na przykład, że masz pewną liczbę dokumentów XML i chcesz dodać do nich część tekstu standardowego.</span><span class="sxs-lookup"><span data-stu-id="16a6f-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="16a6f-126">Poniższy przykład definiuje procedurę, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="16a6f-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="16a6f-127">Każdy obiekt dokumentu XML może następnie wywołać procedurę i przekazać jej bieżące wystąpienie jako argument.</span><span class="sxs-lookup"><span data-stu-id="16a6f-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="16a6f-128">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="16a6f-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="16a6f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16a6f-129">See also</span></span>

- [<span data-ttu-id="16a6f-130">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="16a6f-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="16a6f-131">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="16a6f-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="16a6f-132">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="16a6f-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="16a6f-133">Instrukcje: deklarowanie zmiennej obiektu i przypisywanie do niej obiektu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16a6f-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="16a6f-134">Instrukcje: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="16a6f-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="16a6f-135">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="16a6f-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
