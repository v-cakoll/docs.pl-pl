---
title: Deklaracja zmiennej obiektu (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cdca188d778e9884f918d97eba492a29c64af826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="8133a-102">Deklaracja zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8133a-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="8133a-103">Instrukcja deklaracji normalne umożliwia deklarowanie zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="8133a-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="8133a-104">Dla typu danych, należy określić albo `Object` (to znaczy [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)) lub więcej określonej klasy, z którego ma być utworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="8133a-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="8133a-105">Deklarowanie zmiennej jako `Object` jest taka sama jak deklarowanie go jako <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8133a-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8133a-106">Deklaracja zmiennej z konkretnego obiektu klasy dostępne wszystkie metody i właściwości udostępniane przez tę klasę i klasy, z których dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="8133a-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="8133a-107">Deklarowanie zmiennej o <xref:System.Object>, może uzyskać dostęp tylko do elementów członkowskich z <xref:System.Object> klasy, chyba że włączenie `Option Strict Off` umożliwia późne powiązania.</span><span class="sxs-lookup"><span data-stu-id="8133a-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="8133a-108">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="8133a-108">Declaration Syntax</span></span>  
 <span data-ttu-id="8133a-109">Deklarowanie zmiennej obiektu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="8133a-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="8133a-110">Można również określić [publicznego](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), lub [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8133a-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="8133a-111">Następujące deklaracje przykładzie są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="8133a-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="8133a-112">Późne wiązanie i wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="8133a-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="8133a-113">Czasami określonej klasy jest nieznany, dopóki działania kodu.</span><span class="sxs-lookup"><span data-stu-id="8133a-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="8133a-114">W takim przypadku należy zadeklarować zmienną obiektu o `Object` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="8133a-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="8133a-115">Spowoduje to utworzenie ogólne odwołanie do dowolnego typu obiektu i określonej klasy jest przypisana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8133a-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="8133a-116">Ta metoda jest wywoływana *późne wiązanie*.</span><span class="sxs-lookup"><span data-stu-id="8133a-116">This is called *late binding*.</span></span> <span data-ttu-id="8133a-117">Późne wiązanie wymaga dodatkowego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8133a-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="8133a-118">Ogranicza kod do metody i właściwości klas, które ostatnio zostały przypisane do niego.</span><span class="sxs-lookup"><span data-stu-id="8133a-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="8133a-119">Może to powodować błędy środowiska wykonawczego, jeśli kod spróbuje dostęp do elementów członkowskich innej klasy.</span><span class="sxs-lookup"><span data-stu-id="8133a-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="8133a-120">Gdy znasz określonej klasy w czasie kompilacji, powinny deklarować zmienna obiektu, należy dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="8133a-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="8133a-121">Ta metoda jest wywoływana *wczesne wiązanie*.</span><span class="sxs-lookup"><span data-stu-id="8133a-121">This is called *early binding*.</span></span> <span data-ttu-id="8133a-122">Wczesne powiązania poprawia wydajność i zapewnia dostęp kod do metody i właściwości określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="8133a-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="8133a-123">W poprzednich deklaracjach przykład, gdy zmienna `objA` używa tylko obiektów klasy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, należy określić `As System.Windows.Forms.Label` w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8133a-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="8133a-124">Zalety wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="8133a-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="8133a-125">Deklarowanie zmiennej obiektu jako określonej klasy zapewnia kilka korzyści:</span><span class="sxs-lookup"><span data-stu-id="8133a-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
-   <span data-ttu-id="8133a-126">Sprawdzanie typu automatyczne</span><span class="sxs-lookup"><span data-stu-id="8133a-126">Automatic type checking</span></span>  
  
-   <span data-ttu-id="8133a-127">Zapewniony dostęp do wszystkich członków określonej klasy</span><span class="sxs-lookup"><span data-stu-id="8133a-127">Guaranteed access to all members of the specific class</span></span>  
  
-   <span data-ttu-id="8133a-128">Obsługa Microsoft IntelliSense w edytorze kodu</span><span class="sxs-lookup"><span data-stu-id="8133a-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
-   <span data-ttu-id="8133a-129">Ulepszona czytelność kodu</span><span class="sxs-lookup"><span data-stu-id="8133a-129">Improved readability of your code</span></span>  
  
-   <span data-ttu-id="8133a-130">Mniejszą liczbę błędów w kodzie</span><span class="sxs-lookup"><span data-stu-id="8133a-130">Fewer errors in your code</span></span>  
  
-   <span data-ttu-id="8133a-131">Błędy przechwycono na czas kompilacji, a nie czas wykonywania</span><span class="sxs-lookup"><span data-stu-id="8133a-131">Errors caught at compile time rather than run time</span></span>  
  
-   <span data-ttu-id="8133a-132">Szybsze wykonywanie kodu</span><span class="sxs-lookup"><span data-stu-id="8133a-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="8133a-133">Dostęp do członków zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="8133a-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="8133a-134">Gdy `Option Strict` włączono `On`, zmienna obiektu można uzyskać dostęp tylko metody i właściwości klasy, z którym należy zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="8133a-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="8133a-135">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="8133a-135">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="8133a-136">W tym przykładzie `p` można używać tylko członkowie <xref:System.Object> klasy, które nie obejmują `Left` właściwości.</span><span class="sxs-lookup"><span data-stu-id="8133a-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="8133a-137">Z drugiej strony `q` został zadeklarowany jako typ <xref:System.Windows.Forms.Label>, dlatego można używać metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8133a-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="8133a-138">Elastyczność zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="8133a-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="8133a-139">Podczas pracy z obiektów w hierarchii dziedziczenia, masz do wyboru klasy, które do użycia na potrzeby deklarowania zmiennych obiektu.</span><span class="sxs-lookup"><span data-stu-id="8133a-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="8133a-140">Do zgłoszenia tego wyboru, należy uwzględnić elastyczność przypisanie obiektu przed dostępem do członków klasy.</span><span class="sxs-lookup"><span data-stu-id="8133a-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="8133a-141">Rozważmy na przykład hierarchii dziedziczenia, który prowadzi do <xref:System.Windows.Forms.Form?displayProperty=nameWithType> klasy:</span><span class="sxs-lookup"><span data-stu-id="8133a-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="8133a-142">Załóżmy, że aplikacja definiuje klasy formularza o nazwie `specialForm`, który dziedziczy z klasy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="8133a-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="8133a-143">Można zadeklarować zmiennej obiektu, który odwołuje się specjalnie do `specialForm`, jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8133a-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="8133a-144">Deklaracja w poprzednim przykładzie ogranicza zmiennej `nextForm` do obiektów klasy `specialForm`, ale również zapewnia wszystkie metody i właściwości `specialForm` dostępne dla `nextForm`, jak również ze wszystkimi członkami wszystkie klasy, z którego `specialForm` dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="8133a-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="8133a-145">Zmienna obiektu bardziej ogólne ułatwia ona typu <xref:System.Windows.Forms.Form>, jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8133a-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="8133a-146">Deklaracja w poprzednim przykładzie można przypisać wszystkie formularza w aplikacji `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="8133a-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="8133a-147">Jednak mimo że `anyForm` mogą uzyskiwać dostęp do wszystkich elementów członkowskich klasy <xref:System.Windows.Forms.Form>, nie może używać dodatkowych metod i właściwości zdefiniowane dla określonych formularzy, takie jak `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="8133a-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="8133a-148">Wszystkie elementy członkowskie klasy podstawowej są dostępne dla klasy pochodnej, ale dodatkowe elementy członkowskie klasy pochodnej są niedostępne dla klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="8133a-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8133a-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8133a-149">See Also</span></span>  
 [<span data-ttu-id="8133a-150">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="8133a-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="8133a-151">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="8133a-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="8133a-152">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="8133a-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="8133a-153">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8133a-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="8133a-154">Porady: dostęp do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="8133a-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [<span data-ttu-id="8133a-155">New — Operator</span><span class="sxs-lookup"><span data-stu-id="8133a-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="8133a-156">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8133a-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="8133a-157">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="8133a-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
