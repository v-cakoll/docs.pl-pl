---
title: Deklaracja zmiennej obiektu (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 9e57d49965537a45bc62b9078079389efcfb2e2c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598746"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="c56f8-102">Deklaracja zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c56f8-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="c56f8-103">Instrukcji deklaracji normalne umożliwiają deklarowanie zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="c56f8-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="c56f8-104">Dla typu danych, należy określić albo `Object` (czyli [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)) lub dokładniej klasy, z którego ma zostać utworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="c56f8-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="c56f8-105">Deklarowanie zmiennej jako `Object` jest taka sama jak deklarowania go jako <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c56f8-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c56f8-106">Kiedy Deklarujesz zmienną za pomocą konkretnego obiektu klasy, można uzyskać dostęp do, wszystkie metody i właściwości udostępniane przez tę klasę i klasy, z których dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="c56f8-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="c56f8-107">Przy deklarowaniu zmiennej <xref:System.Object>, może uzyskać dostęp tylko członkowie <xref:System.Object> klasy, o ile nie wyłączysz `Option Strict Off` umożliwia późnego wiązania.</span><span class="sxs-lookup"><span data-stu-id="c56f8-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c56f8-108">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="c56f8-108">Declaration Syntax</span></span>  
 <span data-ttu-id="c56f8-109">Aby zadeklarować zmienną obiektu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="c56f8-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="c56f8-110">Można również określić [publicznych](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), lub [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c56f8-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="c56f8-111">Następujące deklaracje przykład są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="c56f8-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="c56f8-112">Późne wiązanie i wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="c56f8-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="c56f8-113">Czasami określonej klasy jest nieznany, dopóki kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="c56f8-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="c56f8-114">W takim przypadku należy zadeklarować zmienną obiektu za pomocą `Object` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="c56f8-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="c56f8-115">Spowoduje to utworzenie ogólne odwołanie do dowolnego typu obiektu i określonej klasy są przypisywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c56f8-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="c56f8-116">Jest to nazywane *późnym wiązaniu*.</span><span class="sxs-lookup"><span data-stu-id="c56f8-116">This is called *late binding*.</span></span> <span data-ttu-id="c56f8-117">Późne wiązanie wymaga dodatkowego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c56f8-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="c56f8-118">Ogranicza kod do metody i właściwości klas, które ostatnio zostały przypisane do niego.</span><span class="sxs-lookup"><span data-stu-id="c56f8-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="c56f8-119">Może to spowodować błędy czasu wykonywania, jeśli kod próbuje dostęp do elementów członkowskich innej klasy.</span><span class="sxs-lookup"><span data-stu-id="c56f8-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="c56f8-120">Gdy znasz konkretną klasę w czasie kompilacji, należy zadeklarować zmienną obiektu tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c56f8-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="c56f8-121">Jest to nazywane *wczesne powiązania*.</span><span class="sxs-lookup"><span data-stu-id="c56f8-121">This is called *early binding*.</span></span> <span data-ttu-id="c56f8-122">Wczesne powiązania zapewnia lepszą wydajność i gwarantuje dostęp kod do metody i właściwości określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="c56f8-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="c56f8-123">W poprzedniej deklaracji przykład, gdy zmienna `objA` używa tylko obiekty klasy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, należy określić `As System.Windows.Forms.Label` w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c56f8-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="c56f8-124">Korzyści wynikające z wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="c56f8-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="c56f8-125">Deklarowanie zmiennej obiektu jako określoną klasę zapewnia kilka korzyści:</span><span class="sxs-lookup"><span data-stu-id="c56f8-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="c56f8-126">Kontrola typów automatyczne</span><span class="sxs-lookup"><span data-stu-id="c56f8-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="c56f8-127">Zapewniony dostęp do wszystkich elementów członkowskich określonej klasy</span><span class="sxs-lookup"><span data-stu-id="c56f8-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="c56f8-128">Obsługa Microsoft IntelliSense w edytorze kodu</span><span class="sxs-lookup"><span data-stu-id="c56f8-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="c56f8-129">Lepszej czytelności kodu</span><span class="sxs-lookup"><span data-stu-id="c56f8-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="c56f8-130">Mniej błędów w kodzie</span><span class="sxs-lookup"><span data-stu-id="c56f8-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="c56f8-131">Błędy wyłapywane w czas kompilacji, a nie czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="c56f8-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="c56f8-132">Szybsze wykonywanie kodu</span><span class="sxs-lookup"><span data-stu-id="c56f8-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="c56f8-133">Dostęp do obiektu zmiennych składowych</span><span class="sxs-lookup"><span data-stu-id="c56f8-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="c56f8-134">Gdy `Option Strict` włączeniu `On`, zmienna obiektu dostęp do metod i właściwości klasy, z którym trzeba je zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="c56f8-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="c56f8-135">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="c56f8-135">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="c56f8-136">W tym przykładzie `p` można używać tylko członków <xref:System.Object> klasy, które nie obejmują `Left` właściwości.</span><span class="sxs-lookup"><span data-stu-id="c56f8-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="c56f8-137">Z drugiej strony `q` został zadeklarowany jako typ <xref:System.Windows.Forms.Label>, dzięki czemu można użyć wszystkich metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c56f8-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="c56f8-138">Elastyczność zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="c56f8-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="c56f8-139">Podczas pracy z obiektami w hierarchii dziedziczenia, masz do wyboru klasy do deklarowania zmiennych obiektu.</span><span class="sxs-lookup"><span data-stu-id="c56f8-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="c56f8-140">Dokonując wyboru, muszą równoważyć elastyczność przypisanie obiektu względem dostępu do składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="c56f8-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="c56f8-141">Na przykład, rozważmy Hierarchia dziedziczenia, który prowadzi do <xref:System.Windows.Forms.Form?displayProperty=nameWithType> klasy:</span><span class="sxs-lookup"><span data-stu-id="c56f8-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="c56f8-142">Załóżmy, że aplikacja definiuje klasę formularza o nazwie `specialForm`, który dziedziczy z klasy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="c56f8-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="c56f8-143">Można zadeklarować zmienną obiektu, który odwołuje się specjalnie do `specialForm`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c56f8-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="c56f8-144">Deklaracji w poprzednim przykładzie ogranicza zmiennej `nextForm` do obiektów klasy `specialForm`, ale on również sprawia, że wszystkie metody i właściwości `specialForm` dostępne dla `nextForm`, jak również jak wszystkie elementy członkowskie wszystkie klasy, z którego `specialForm` dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="c56f8-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="c56f8-145">Możesz wprowadzić zmienną obiektu bardziej ogólnych, deklarując jej typu <xref:System.Windows.Forms.Form>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c56f8-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="c56f8-146">Deklaracja w powyższym przykładzie można przypisać dowolnej formie w aplikacji, aby `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="c56f8-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="c56f8-147">Jednak mimo że `anyForm` mogą uzyskiwać dostęp do wszystkich członków klasy <xref:System.Windows.Forms.Form>, nie może używać dowolnych dodatkowe metody lub właściwości, zdefiniowaną dla określonych formularzy, takich jak `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="c56f8-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="c56f8-148">Wszystkie elementy członkowskie klasy bazowej są dostępne dla klasy pochodnej, ale dodatkowe elementy członkowskie klasy pochodnej jest niedostępny do klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c56f8-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56f8-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c56f8-149">See also</span></span>

- [<span data-ttu-id="c56f8-150">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="c56f8-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="c56f8-151">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="c56f8-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="c56f8-152">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="c56f8-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="c56f8-153">Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c56f8-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="c56f8-154">Instrukcje: Dostęp do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="c56f8-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="c56f8-155">New, operator</span><span class="sxs-lookup"><span data-stu-id="c56f8-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="c56f8-156">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c56f8-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c56f8-157">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="c56f8-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
