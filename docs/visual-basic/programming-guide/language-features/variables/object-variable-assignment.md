---
title: Przypisanie zmiennej obiektu (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb6b53bebddc1c9cf1b9088e96ded36a5e1c5242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="42da4-102">Przypisanie zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42da4-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="42da4-103">Instrukcja przydział normalny umożliwia przydzielanie obiektu do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="42da4-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="42da4-104">Można przypisać wyrażenia obiektu lub [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, jak w poniższym przykładzie przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="42da4-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="42da4-105">`Nothing`oznacza, że nie ma żadnego obiektu aktualnie przypisane do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42da4-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="42da4-106">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="42da4-106">Initialization</span></span>  
 <span data-ttu-id="42da4-107">Po kodzie rozpoczyna, zmienne są inicjowane do obiektu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="42da4-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="42da4-108">Te, których deklaracje zawierają inicjowania są ponownie inicjowane do wartości, które można określić podczas wykonywania instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="42da4-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="42da4-109">Inicjowanie można uwzględnić w deklaracji z za pomocą [New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="42da4-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="42da4-110">Poniższe instrukcje deklaracji Zadeklaruj zmienne obiektu `testUri` i `ver` i przypisz konkretne obiekty do nich.</span><span class="sxs-lookup"><span data-stu-id="42da4-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="42da4-111">W każdej jedną przeciążone konstruktory odpowiedniej klasy używane do inicjalizacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="42da4-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="42da4-112">Ukończona</span><span class="sxs-lookup"><span data-stu-id="42da4-112">Disassociation</span></span>  
 <span data-ttu-id="42da4-113">Ustawienie zmiennej obiektu `Nothing` zaprzestaje skojarzenie zmiennej z dowolnego określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="42da4-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="42da4-114">Zapobiega to przypadkowym zmianom, zmieniając zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="42da4-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="42da4-115">Można też sprawdzić, czy zmienna obiektu wskazuje prawidłowy obiekt, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42da4-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="42da4-116">W przypadku obiektu, do którego odnosi się zmienna użytkownika w innej aplikacji, ten test nie może określić, czy tę aplikację ma zakończone lub po prostu unieważnienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="42da4-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="42da4-117">Zmienna obiektu o wartości `Nothing` jest również nazywany *odwołanie o wartości null*.</span><span class="sxs-lookup"><span data-stu-id="42da4-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="42da4-118">Bieżące wystąpienie</span><span class="sxs-lookup"><span data-stu-id="42da4-118">Current Instance</span></span>  
 <span data-ttu-id="42da4-119">*Bieżącego wystąpienia* obiektu jest ten, w którym kod jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="42da4-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="42da4-120">Ponieważ cały kod jest wykonywana wewnątrz procedury, bieżące wystąpienie jest w którym została wywołana procedura.</span><span class="sxs-lookup"><span data-stu-id="42da4-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="42da4-121">`Me` — Słowo kluczowe działa jako zmienna obiektu odwołanie do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="42da4-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="42da4-122">Jeśli nie jest procedurą [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), może użyć `Me` — słowo kluczowe uzyskać wskaźnik do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="42da4-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="42da4-123">Procedury udostępnionego nie może być skojarzony z określonym wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="42da4-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="42da4-124">Przy użyciu `Me` jest szczególnie przydatne podczas przekazywania do procedury w innym module bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="42da4-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="42da4-125">Na przykład załóżmy, że liczba dokumentów XML i chcesz dodać tekst standardowy do wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="42da4-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="42da4-126">W poniższym przykładzie zdefiniowano procedury w tym celu.</span><span class="sxs-lookup"><span data-stu-id="42da4-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="42da4-127">Każdego obiektu dokumentu XML można następnie wywołania tej procedury i przekaż jej bieżące wystąpienie jako argument.</span><span class="sxs-lookup"><span data-stu-id="42da4-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="42da4-128">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="42da4-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="42da4-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42da4-129">See Also</span></span>  
 [<span data-ttu-id="42da4-130">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="42da4-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="42da4-131">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="42da4-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="42da4-132">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="42da4-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="42da4-133">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42da4-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="42da4-134">Porady: umieszczanie zmienna obiektu nie odwołuje się do dowolnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="42da4-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [<span data-ttu-id="42da4-135">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="42da4-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
