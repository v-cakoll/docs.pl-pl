---
title: Tworzenie interfejsów typu Variant
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 74362b9d9effab028bebb9e9ecf72ac0111366d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347071"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="b9d72-102">Tworzenie interfejsów ogólnych typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9d72-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="b9d72-103">Parametry typu ogólnego można zadeklarować w interfejsach jako współvariant lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="b9d72-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="b9d72-104">*Kowariancja* umożliwia metodom interfejsu posiadanie bardziej pochodnych typów zwracanych niż te zdefiniowane przez parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b9d72-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="b9d72-105">*Kontrawariancja* umożliwia metodom interfejsu posiadanie typów argumentów, które są mniej pochodne niż określone przez parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="b9d72-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="b9d72-106">Ogólny interfejs, który ma parametry typu generycznego lub kontrawariantne, nazywa się *wariantem*.</span><span class="sxs-lookup"><span data-stu-id="b9d72-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="b9d72-107">.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b9d72-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="b9d72-108">Aby uzyskać listę interfejsów wariantów w .NET Framework, zobacz [Wariancja w interfejsach ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="b9d72-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="b9d72-109">Deklarowanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b9d72-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="b9d72-110">Można zadeklarować interfejsy ogólne dla wariantów przy użyciu słów kluczowych `in` i `out` dla parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b9d72-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9d72-111">parametry `ByRef` w Visual Basic nie mogą być wariantem.</span><span class="sxs-lookup"><span data-stu-id="b9d72-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="b9d72-112">Typy wartości nie obsługują również wariancji.</span><span class="sxs-lookup"><span data-stu-id="b9d72-112">Value types also do not support variance.</span></span>

<span data-ttu-id="b9d72-113">Za pomocą słowa kluczowego `out` można zadeklarować element współvariant parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b9d72-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="b9d72-114">Typ współwariantu musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="b9d72-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="b9d72-115">Typ jest używany tylko jako typ zwracany metod interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="b9d72-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="b9d72-116">Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako współvariant.</span><span class="sxs-lookup"><span data-stu-id="b9d72-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    <span data-ttu-id="b9d72-117">Istnieje jeden wyjątek dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="b9d72-117">There is one exception to this rule.</span></span> <span data-ttu-id="b9d72-118">Jeśli masz delegata generycznego kontrawariantne jako parametr metody, możesz użyć typu jako parametru typu ogólnego dla delegata.</span><span class="sxs-lookup"><span data-stu-id="b9d72-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="b9d72-119">Jest to zilustrowane przez typ `R` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9d72-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="b9d72-120">Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b9d72-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- <span data-ttu-id="b9d72-121">Typ nie jest używany jako ograniczenie ogólne metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="b9d72-122">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b9d72-122">This is illustrated in the following code.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

<span data-ttu-id="b9d72-123">Parametry typu ogólnego kontrawariantne można zadeklarować za pomocą słowa kluczowego `in`.</span><span class="sxs-lookup"><span data-stu-id="b9d72-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="b9d72-124">Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="b9d72-125">Typ kontrawariantne może być również używany dla ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b9d72-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="b9d72-126">Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantne i używania ograniczenia ogólnego dla jednej z jej metod.</span><span class="sxs-lookup"><span data-stu-id="b9d72-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

<span data-ttu-id="b9d72-127">Istnieje również możliwość obsługi zarówno kowariancji, jak i kontrawariancja w tym samym interfejsie, ale dla różnych parametrów typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

<span data-ttu-id="b9d72-128">W Visual Basic nie można zadeklarować zdarzeń w interfejsach Variant bez określania typu delegata.</span><span class="sxs-lookup"><span data-stu-id="b9d72-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="b9d72-129">Ponadto interfejs wariantu nie może mieć klas zagnieżdżonych, wyliczeniowych ani struktur, ale może mieć zagnieżdżone interfejsy.</span><span class="sxs-lookup"><span data-stu-id="b9d72-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="b9d72-130">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b9d72-130">This is illustrated in the following code.</span></span>

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

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="b9d72-131">Implementowanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b9d72-131">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="b9d72-132">W klasach można zaimplementować interfejsy ogólne o zmiennej, korzystając z tej samej składni, która jest używana dla interfejsów niezmienna.</span><span class="sxs-lookup"><span data-stu-id="b9d72-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="b9d72-133">Poniższy przykład kodu pokazuje, jak zaimplementować interfejs współvariant w klasie generycznej.</span><span class="sxs-lookup"><span data-stu-id="b9d72-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="b9d72-134">Klasy implementujące interfejsy Variant są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="b9d72-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="b9d72-135">Rozważmy na przykład poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="b9d72-135">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="b9d72-136">Rozszerzanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b9d72-136">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="b9d72-137">Podczas rozszerzającej uniwersalnego interfejsu wariantu należy użyć słów kluczowych `in` i `out`, aby jawnie określić, czy interfejs pochodny obsługuje wariancję.</span><span class="sxs-lookup"><span data-stu-id="b9d72-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="b9d72-138">Kompilator nie wywnioskuje wariancji z rozszerzanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="b9d72-139">Rozważmy na przykład następujące interfejsy.</span><span class="sxs-lookup"><span data-stu-id="b9d72-139">For example, consider the following interfaces.</span></span>

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

<span data-ttu-id="b9d72-140">W interfejsie `Invariant(Of T)` parametr typu generycznego `T` jest niezmienny, podczas gdy w `IExtCovariant (Of Out T)`parametr typu jest współvariant, chociaż oba interfejsy rozszerzającą ten sam interfejs.</span><span class="sxs-lookup"><span data-stu-id="b9d72-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="b9d72-141">Ta sama reguła jest stosowana do parametrów typu ogólnego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="b9d72-141">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="b9d72-142">Można utworzyć interfejs, który rozszerza interfejs, w którym parametr typu generycznego `T` jest współvariant i interfejsem, gdzie jest kontrawariantne, jeśli w rozszerzanym interfejsie parametr typu generycznego `T` jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="b9d72-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="b9d72-143">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-143">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

<span data-ttu-id="b9d72-144">Jeśli jednak parametr typu generycznego `T` jest zadeklarowany jako współwariant w jednym interfejsie, nie można zadeklarować go kontrawariantne w interfejsie rozszerzającym lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="b9d72-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="b9d72-145">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-145">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="b9d72-146">Unikanie niejednoznaczności</span><span class="sxs-lookup"><span data-stu-id="b9d72-146">Avoiding Ambiguity</span></span>

<span data-ttu-id="b9d72-147">Podczas implementowania interfejsów ogólnych typu Variant WARIANCJA może czasami prowadzić do niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="b9d72-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="b9d72-148">Należy to uniknąć.</span><span class="sxs-lookup"><span data-stu-id="b9d72-148">This should be avoided.</span></span>

<span data-ttu-id="b9d72-149">Na przykład w przypadku jawnego zaimplementowania tego samego uniwersalnego interfejsu wariantu z różnymi parametrami typu ogólnego w jednej klasie można utworzyć niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="b9d72-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="b9d72-150">Kompilator nie generuje błędu w tym przypadku, ale nie jest określony, która implementacja interfejsu zostanie wybrana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9d72-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="b9d72-151">Może to prowadzić do delikatnych usterek w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b9d72-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="b9d72-152">Rozważmy następujący przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-152">Consider the following code example.</span></span>

> [!NOTE]
> <span data-ttu-id="b9d72-153">W przypadku `Option Strict Off`Visual Basic generuje ostrzeżenie kompilatora, gdy istnieje niejednoznaczna implementacja interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b9d72-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="b9d72-154">W przypadku `Option Strict On`Visual Basic generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b9d72-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>

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

<span data-ttu-id="b9d72-155">W tym przykładzie nie określono, jak Metoda `pets.GetEnumerator` wybiera między `Cat` i `Dog`.</span><span class="sxs-lookup"><span data-stu-id="b9d72-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="b9d72-156">Może to spowodować problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b9d72-156">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9d72-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9d72-157">See also</span></span>

- [<span data-ttu-id="b9d72-158">Wariancja w interfejsach ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9d72-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="b9d72-159">Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9d72-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
