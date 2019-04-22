---
title: Przypisanie zmiennej obiektu (Visual Basic)
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
ms.openlocfilehash: dff1b9bb9e87f827663786cac3f33531db41b2c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840279"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="84582-102">Przypisanie zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84582-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="84582-103">Instrukcja przypisania normalne umożliwia przydzielanie obiektu do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="84582-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="84582-104">Możesz przypisać wyrażenie obiektu lub [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="84582-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="84582-105">`Nothing` oznacza, że nie ma obiektu aktualnie przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="84582-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="84582-106">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="84582-106">Initialization</span></span>  
 <span data-ttu-id="84582-107">Po kodzie rozpoczyna się uruchomiony, zmienne są inicjowane na obiekt `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="84582-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="84582-108">Te, których deklaracje zawierają inicjowania są ponownie inicjowane na wartości, które określisz, gdy wykonywane są instrukcje deklaracji.</span><span class="sxs-lookup"><span data-stu-id="84582-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="84582-109">Inicjowanie można uwzględnić w swojej deklaracji, za pomocą [New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="84582-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="84582-110">Poniższe instrukcje deklaracji deklarują zmienne obiektów `testUri` i `ver` i przypisywać im konkretnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="84582-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="84582-111">Każdy używa jednego z przeciążenia konstruktorów z odpowiedniej klasy do inicjalizacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="84582-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="84582-112">Usuwanie skojarzeń</span><span class="sxs-lookup"><span data-stu-id="84582-112">Disassociation</span></span>  
 <span data-ttu-id="84582-113">Ustawienie zmiennej obiektu `Nothing` zaprzestaje skojarzenia zmiennej z dowolnego określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="84582-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="84582-114">Zapobiega to przypadkowym zmianom obiektu przez zmianę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="84582-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="84582-115">Umożliwia on również sprawdzić, czy zmienna obiektu wskazuje prawidłowego obiektu, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="84582-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="84582-116">Jeśli obiekt, który Twoja zmienna odwołuje się do innej aplikacji, ten test nie może określić, czy tę aplikację ma zakończone lub po prostu unieważnione obiektu.</span><span class="sxs-lookup"><span data-stu-id="84582-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="84582-117">Zmienna obiektu z wartością `Nothing` jest również nazywany *null odwołanie*.</span><span class="sxs-lookup"><span data-stu-id="84582-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="84582-118">Bieżące wystąpienie</span><span class="sxs-lookup"><span data-stu-id="84582-118">Current Instance</span></span>  
 <span data-ttu-id="84582-119">*Bieżącego wystąpienia* obiektu jest ten, w którym aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="84582-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="84582-120">Ponieważ cały kod jest wykonywany wewnątrz procedury, bieżące wystąpienie jest w której wywołano procedury.</span><span class="sxs-lookup"><span data-stu-id="84582-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="84582-121">`Me` — Słowo kluczowe działa jako zmienną obiektu odwołanie do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="84582-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="84582-122">Jeśli nie jest procedurą [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), można użyć `Me` — słowo kluczowe, aby uzyskać wskaźnik do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="84582-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="84582-123">Udostępnione procedury można skojarzyć z określonego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="84582-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="84582-124">Za pomocą `Me` jest szczególnie przydatne w przypadku przekazywania bieżącego wystąpienia do procedury w innym module.</span><span class="sxs-lookup"><span data-stu-id="84582-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="84582-125">Na przykład załóżmy, że masz wiele dokumentów XML i chcesz dodać standardowy tekst do wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="84582-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="84582-126">W poniższym przykładzie zdefiniowano procedury, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="84582-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="84582-127">Każdy obiekt dokumentu XML może następnie wywołania tej procedury i przekaż jej bieżące wystąpienie jako argument.</span><span class="sxs-lookup"><span data-stu-id="84582-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="84582-128">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="84582-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="84582-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84582-129">See also</span></span>

- [<span data-ttu-id="84582-130">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="84582-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="84582-131">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="84582-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="84582-132">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="84582-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="84582-133">Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84582-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="84582-134">Instrukcje: Sprawianie Aby zmienna obiektu nie odwoływała się do dowolnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="84582-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="84582-135">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="84582-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
