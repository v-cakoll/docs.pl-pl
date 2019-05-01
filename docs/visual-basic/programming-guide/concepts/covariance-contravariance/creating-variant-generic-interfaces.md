---
title: Tworzenie interfejsów typu Variant (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 45454f12cf49994f3d476a9ee27f72442266db65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787299"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="1b2fa-102">Tworzenie interfejsów typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b2fa-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="1b2fa-103">Możesz deklarować parametry typu ogólnego w interfejsach jako kowariantny lub kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="1b2fa-104">*Kowariancja* umożliwia metod interfejsu do mają bardziej pochodne typy zwracane niż określone przez parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="1b2fa-105">*Kontrawariancja* umożliwia metod interfejsu mieć typy argumentów, które są mniej pochodnego niż określona przez parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="1b2fa-106">Ogólny interfejs, który ma kowariantne i kontrawariantne parametry typu ogólnego jest nazywany *wariant*.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="1b2fa-107">.NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="1b2fa-108">Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="1b2fa-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="1b2fa-109">Deklarujący interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="1b2fa-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="1b2fa-110">Można zadeklarować interfejsów ogólnych typu variant, za pomocą `in` i `out` słowa kluczowe dla parametrów typu genetycznego.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b2fa-111">`ByRef` w języku Visual Basic nie może być typ variant.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="1b2fa-112">Typy wartości nie obsługują także wariancji.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-112">Value types also do not support variance.</span></span>

<span data-ttu-id="1b2fa-113">Można zadeklarować parametru typu generycznego kowariantne przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="1b2fa-114">Kowariantnego typu musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="1b2fa-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="1b2fa-115">Typ jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="1b2fa-116">Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako kowariantny.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    <span data-ttu-id="1b2fa-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-117">There is one exception to this rule.</span></span> <span data-ttu-id="1b2fa-118">Jeśli Delegat ogólny kontrawariantny, jako parametru metody, można użyć typu co parametr typu ogólnego, dla delegata.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="1b2fa-119">Jest to zilustrowane przez typ `R` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="1b2fa-120">Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (Visual Basic) Func i](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1b2fa-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- <span data-ttu-id="1b2fa-121">Typ nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="1b2fa-122">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-122">This is illustrated in the following code.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

<span data-ttu-id="1b2fa-123">Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="1b2fa-124">Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typu zwracanego metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="1b2fa-125">Można także kontrawariantnego typu dla ograniczenia ogólne.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="1b2fa-126">Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantnego i na użytek ograniczenie generyczne jednej z jego metod.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

<span data-ttu-id="1b2fa-127">Istnieje również możliwość obsługuje zarówno kowariancji i kontrawariancji w ten sam interfejs, ale dla parametrów innego typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

<span data-ttu-id="1b2fa-128">W języku Visual Basic nie można zadeklarować zdarzenia w interfejsów typu variant, bez określania typu delegata.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="1b2fa-129">Ponadto wariantu interfejsu nie mogą zagnieżdżać klas, wyliczeń lub struktur, ale mogą być zagnieżdżone interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="1b2fa-130">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-130">This is illustrated in the following code.</span></span>

```vb
Interface ICovariant(Of Out R)
    ' The following statement generates a compiler error.
    ' Event SampleEvent()
    ' The following statement specifies the delegate type and
    ' does not generate an error.
    Event AnotherEvent As EventHandler

    ' The following statements generate compiler errors,
    ' because a variant interface cannot have
    ' nested enums, classes, or structures.

    'Enum SampleEnum : test : End Enum
    'Class SampleClass : End Class
    'Structure SampleStructure : Dim value As Integer : End Structure

    ' Variant interfaces can have nested interfaces.
    Interface INested : End Interface
End Interface
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="1b2fa-131">Implementowanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="1b2fa-131">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="1b2fa-132">Możesz zaimplementować interfejsów ogólnych typu variant klas przy użyciu składni, która jest używana niezmienna interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="1b2fa-133">Poniższy przykład kodu pokazuje sposób implementacji kowariantne interfejsu w klasie ogólnej.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```vb
Interface ICovariant(Of Out R)
    Function GetSomething() As R
End Interface

Class SampleImplementation(Of R)
    Implements ICovariant(Of R)
    Public Function GetSomething() As R _
    Implements ICovariant(Of R).GetSomething
        ' Some code.
    End Function
End Class
```

<span data-ttu-id="1b2fa-134">Klasy, które implementują interfejsów typu variant są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="1b2fa-135">Rozważmy na przykład, poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-135">For example, consider the following code.</span></span>

```vb
 The interface is covariant.
Dim ibutton As ICovariant(Of Button) =
    New SampleImplementation(Of Button)
Dim iobj As ICovariant(Of Object) = ibutton

' The class is invariant.
Dim button As SampleImplementation(Of Button) =
    New SampleImplementation(Of Button)
' The following statement generates a compiler error
' because classes are invariant.
' Dim obj As SampleImplementation(Of Object) = button
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="1b2fa-136">Rozszerzanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="1b2fa-136">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="1b2fa-137">Podczas rozszerzania typu variant interfejs ogólny, trzeba użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="1b2fa-138">Kompilator nie są rozpoznawane przez odchylenie od interfejsu, który jest rozszerzany.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="1b2fa-139">Na przykład należy wziąć pod uwagę następujące interfejsy.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-139">For example, consider the following interfaces.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T)
End Interface

Interface IExtCovariant(Of Out T)
    Inherits ICovariant(Of T)
End Interface
```

<span data-ttu-id="1b2fa-140">W `Invariant(Of T)` interfejsu, parametr typu ogólnego `T` jest niezmienny, natomiast w `IExtCovariant (Of Out T)`parametr typu jest kowariantny, mimo że oba interfejsy rozszerzyć ten sam interfejs.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="1b2fa-141">Ta sama zasada dotyczy kontrawariantne parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-141">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="1b2fa-142">Można utworzyć interfejsu, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny interfejs, w której jest kontrawariantny w rozszerzanie interfejsu parametr typu ogólnego i `T` jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="1b2fa-143">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-143">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

<span data-ttu-id="1b2fa-144">Jednak jeśli parametr typu ogólnego `T` jest kowariantny zadeklarowana w ramach jednego interfejsu, nie można zadeklarować je kontrawariantnego w interfejsie rozszerzanie lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="1b2fa-145">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-145">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="1b2fa-146">Unikanie niejednoznaczności</span><span class="sxs-lookup"><span data-stu-id="1b2fa-146">Avoiding Ambiguity</span></span>

<span data-ttu-id="1b2fa-147">Podczas implementowania interfejsów ogólnych typu variant wariancji czasami może prowadzić do niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="1b2fa-148">Należy ich unikać.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-148">This should be avoided.</span></span>

<span data-ttu-id="1b2fa-149">Na przykład w przypadku zastosowania jawnie tego samego typu variant ogólny interfejs z parametrami typu rodzajowego różnych w jednej klasie, można utworzyć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="1b2fa-150">Kompilator generuje błąd w takiej sytuacji, ale nie zostanie określony, zostanie wybrany co do implementacji interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="1b2fa-151">Może to prowadzić do subtelnych błędów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="1b2fa-152">Rozważmy następujący przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-152">Consider the following code example.</span></span>

> [!NOTE]
> <span data-ttu-id="1b2fa-153">Za pomocą `Option Strict Off`, Visual Basic generuje ostrzeżenia kompilatora, gdy jest implementacją interfejsu niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="1b2fa-154">Za pomocą `Option Strict On`, Visual Basic generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>

```vb
' Simple class hierarchy.
Class Animal
End Class

Class Cat
    Inherits Animal
End Class

Class Dog
    Inherits Animal
End Class

' This class introduces ambiguity
' because IEnumerable(Of Out T) is covariant.
Class Pets
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)

    Public Function GetEnumerator() As IEnumerator(Of Cat) _
        Implements IEnumerable(Of Cat).GetEnumerator
        Console.WriteLine("Cat")
        ' Some code.
    End Function

    Public Function GetEnumerator1() As IEnumerator(Of Dog) _
        Implements IEnumerable(Of Dog).GetEnumerator
        Console.WriteLine("Dog")
        ' Some code.
    End Function

    Public Function GetEnumerator2() As IEnumerator _
        Implements IEnumerable.GetEnumerator
        ' Some code.
    End Function
End Class

Sub Main()
    Dim pets As IEnumerable(Of Animal) = New Pets()
    pets.GetEnumerator()
End Sub
```

<span data-ttu-id="1b2fa-155">W tym przykładzie jest nieokreślona sposób, w jaki `pets.GetEnumerator` metoda wybiera między `Cat` i `Dog`.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="1b2fa-156">Może to spowodować problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b2fa-156">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b2fa-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b2fa-157">See also</span></span>

- [<span data-ttu-id="1b2fa-158">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b2fa-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="1b2fa-159">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b2fa-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
