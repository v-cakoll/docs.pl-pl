---
title: Deklaracja zmiennej obiektu
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
ms.openlocfilehash: b6de52cf738a56a42c82978b54cef31574ab0bcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410364"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="fce86-102">Deklaracja zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fce86-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="fce86-103">Użyj normalnej instrukcji deklaracji, aby zadeklarować zmienną obiektu.</span><span class="sxs-lookup"><span data-stu-id="fce86-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="fce86-104">Dla typu danych należy określić wartość `Object` (czyli [Typ danych obiektu](../../../language-reference/data-types/object-data-type.md)) lub bardziej konkretną klasę, z której ma zostać utworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="fce86-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="fce86-105">Deklarowanie zmiennej jako `Object` takiej samej jak deklarowanie jej jako <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fce86-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="fce86-106">Po zadeklarowaniu zmiennej z konkretną klasą obiektów, może ona uzyskać dostęp do wszystkich metod i właściwości uwidocznionych przez tę klasę oraz klas, z których ta dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="fce86-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="fce86-107">Jeśli zmienna jest zadeklarowana przy użyciu <xref:System.Object> , może uzyskać dostęp tylko do elementów członkowskich <xref:System.Object> klasy, chyba że `Option Strict Off` zezwolisz na późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="fce86-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="fce86-108">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="fce86-108">Declaration Syntax</span></span>  
 <span data-ttu-id="fce86-109">Aby zadeklarować zmienną obiektu, użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="fce86-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="fce86-110">Można również określić [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend` , [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md)lub [static](../../../language-reference/modifiers/static.md) w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="fce86-110">You can also specify [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md), or [Static](../../../language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="fce86-111">Następujące przykładowe deklaracje są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="fce86-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="fce86-112">Późne powiązania i wczesne powiązania</span><span class="sxs-lookup"><span data-stu-id="fce86-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="fce86-113">Czasami określona Klasa jest nieznana do momentu uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="fce86-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="fce86-114">W takim przypadku należy zadeklarować zmienną obiektu z `Object` typem danych.</span><span class="sxs-lookup"><span data-stu-id="fce86-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="fce86-115">Spowoduje to utworzenie ogólnego odwołania do dowolnego typu obiektu, a określona Klasa jest przypisana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fce86-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="fce86-116">Jest to tzw. *późne wiązanie*.</span><span class="sxs-lookup"><span data-stu-id="fce86-116">This is called *late binding*.</span></span> <span data-ttu-id="fce86-117">Późne wiązanie wymaga dodatkowego czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="fce86-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="fce86-118">Ponadto ogranicza kod do metod i właściwości klasy, do której ostatnio przypisano.</span><span class="sxs-lookup"><span data-stu-id="fce86-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="fce86-119">Może to spowodować błędy w czasie wykonywania, jeśli kod próbuje uzyskać dostęp do elementów członkowskich innej klasy.</span><span class="sxs-lookup"><span data-stu-id="fce86-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="fce86-120">Znając określoną klasę w czasie kompilacji, należy zadeklarować zmienną obiektu jako tej klasy.</span><span class="sxs-lookup"><span data-stu-id="fce86-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="fce86-121">Nazywa się to *wczesnym wiązaniem*.</span><span class="sxs-lookup"><span data-stu-id="fce86-121">This is called *early binding*.</span></span> <span data-ttu-id="fce86-122">Wczesne powiązanie zwiększa wydajność i gwarantuje dostęp kodu do wszystkich metod i właściwości konkretnej klasy.</span><span class="sxs-lookup"><span data-stu-id="fce86-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="fce86-123">W poprzednich przykładowych deklaracjach, jeśli zmienna `objA` używa tylko obiektów klasy <xref:System.Windows.Forms.Label?displayProperty=nameWithType> , należy określić `As System.Windows.Forms.Label` w swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="fce86-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="fce86-124">Zalety wczesnego wiązania</span><span class="sxs-lookup"><span data-stu-id="fce86-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="fce86-125">Deklarowanie zmiennej obiektu jako określonej klasy daje kilka korzyści:</span><span class="sxs-lookup"><span data-stu-id="fce86-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="fce86-126">Automatyczne sprawdzanie typu</span><span class="sxs-lookup"><span data-stu-id="fce86-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="fce86-127">Gwarantowany dostęp do wszystkich elementów członkowskich określonej klasy</span><span class="sxs-lookup"><span data-stu-id="fce86-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="fce86-128">Obsługa technologii IntelliSense firmy Microsoft w edytorze kodu</span><span class="sxs-lookup"><span data-stu-id="fce86-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="fce86-129">Ulepszona czytelność kodu</span><span class="sxs-lookup"><span data-stu-id="fce86-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="fce86-130">Mniejsza liczba błędów w kodzie</span><span class="sxs-lookup"><span data-stu-id="fce86-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="fce86-131">Błędy przechwycone w czasie kompilacji, a nie w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="fce86-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="fce86-132">Szybsze wykonywanie kodu</span><span class="sxs-lookup"><span data-stu-id="fce86-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="fce86-133">Dostęp do elementów członkowskich zmiennych obiektu</span><span class="sxs-lookup"><span data-stu-id="fce86-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="fce86-134">Gdy `Option Strict` jest włączona `On` , zmienna obiektu może uzyskać dostęp tylko do metod i właściwości klasy, z którą ją deklarujesz.</span><span class="sxs-lookup"><span data-stu-id="fce86-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="fce86-135">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="fce86-135">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="fce86-136">W tym przykładzie `p` można używać tylko elementów członkowskich <xref:System.Object> samej klasy, które nie zawierają `Left` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fce86-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="fce86-137">Z drugiej strony, `q` został zadeklarowany jako typu <xref:System.Windows.Forms.Label> , dlatego może używać wszystkich metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fce86-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="fce86-138">Elastyczność zmiennych obiektów</span><span class="sxs-lookup"><span data-stu-id="fce86-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="fce86-139">Podczas pracy z obiektami w hierarchii dziedziczenia można wybrać klasę, która ma być używana do deklarowania zmiennych obiektu.</span><span class="sxs-lookup"><span data-stu-id="fce86-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="fce86-140">W przypadku wybrania tego wyboru należy zrównoważyć elastyczność przypisywania obiektów w celu uzyskania dostępu do elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="fce86-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="fce86-141">Rozważmy na przykład hierarchię dziedziczenia prowadzącą do <xref:System.Windows.Forms.Form?displayProperty=nameWithType> klasy:</span><span class="sxs-lookup"><span data-stu-id="fce86-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="fce86-142">Załóżmy, że aplikacja definiuje klasę formularza o nazwie `specialForm` , która dziedziczy z klasy <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="fce86-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="fce86-143">Można zadeklarować zmienną obiektu, która odwołuje się w `specialForm` odniesieniu do, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fce86-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="fce86-144">Deklaracja w poprzednim przykładzie ogranicza zmienną `nextForm` do obiektów klasy `specialForm` , ale również udostępnia wszystkie metody i właściwości `specialForm` dostępne dla, a także `nextForm` wszystkie elementy członkowskie wszystkich klas, z których `specialForm` dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="fce86-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="fce86-145">Można sprawić, aby zmienna obiektu była bardziej ogólna przez zadeklarowanie jej jako typu <xref:System.Windows.Forms.Form> , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fce86-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="fce86-146">Deklaracja w poprzednim przykładzie umożliwia przypisanie dowolnej formy w aplikacji do programu `anyForm` .</span><span class="sxs-lookup"><span data-stu-id="fce86-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="fce86-147">Jednak chociaż `anyForm` mogą uzyskać dostęp do wszystkich elementów członkowskich klasy <xref:System.Windows.Forms.Form> , nie może używać żadnej z dodatkowych metod lub właściwości zdefiniowanych dla konkretnych formularzy, takich jak `specialForm` .</span><span class="sxs-lookup"><span data-stu-id="fce86-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="fce86-148">Wszystkie elementy członkowskie klasy bazowej są dostępne dla klas pochodnych, ale dodatkowe elementy członkowskie klasy pochodnej są niedostępne dla klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="fce86-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce86-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fce86-149">See also</span></span>

- [<span data-ttu-id="fce86-150">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="fce86-150">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="fce86-151">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="fce86-151">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="fce86-152">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="fce86-152">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="fce86-153">Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fce86-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="fce86-154">Porady: dostęp do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="fce86-154">How to: Access Members of an Object</span></span>](how-to-access-members-of-an-object.md)
- [<span data-ttu-id="fce86-155">Operator new</span><span class="sxs-lookup"><span data-stu-id="fce86-155">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="fce86-156">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="fce86-156">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="fce86-157">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="fce86-157">Local Type Inference</span></span>](local-type-inference.md)
