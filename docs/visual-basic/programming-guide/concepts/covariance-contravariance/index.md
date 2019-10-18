---
title: Kowariancja i kontrawariancja (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 8315a272aca891820f7349d854a16375abdae900
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524257"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="03673-102">Kowariancja i kontrawariancja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-102">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="03673-103">W Visual Basic, Kowariancja i kontrawariancja umożliwiają włączenie niejawnej konwersji odwołań dla typów tablic, typów delegatów i argumentów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="03673-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="03673-104">Kowariancja zachowuje zgodność przypisania i kontrawariancja ją odwraca.</span><span class="sxs-lookup"><span data-stu-id="03673-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="03673-105">Poniższy kod ilustruje różnicę między zgodnością przypisania, kowariancją i kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="03673-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="03673-106">Kowariancja dla tablic umożliwia niejawną konwersję tablicy o bardziej pochodny typ do tablicy mniej pochodnego typu.</span><span class="sxs-lookup"><span data-stu-id="03673-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="03673-107">Ale ta operacja nie jest bezpieczna, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="03673-107">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="03673-108">Obsługa kowariancji i kontrawariancja dla grup metod umożliwia dopasowywanie sygnatur metod przy użyciu typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="03673-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="03673-109">Dzięki temu można przypisywać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="03673-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="03673-110">Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Korzystanie z wariancji w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="03673-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>

<span data-ttu-id="03673-111">Poniższy przykład kodu pokazuje kowariancję i obsługę kontrawariancja dla grup metod.</span><span class="sxs-lookup"><span data-stu-id="03673-111">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="03673-112">W .NET Framework 4 lub nowszych Visual Basic obsługuje kowariancję i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="03673-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="03673-113">Aby uzyskać więcej informacji, zobacz [Wariancja w interfejsach ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [Wariancja w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="03673-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>

<span data-ttu-id="03673-114">Poniższy przykład kodu przedstawia niejawną konwersję odwołań dla interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="03673-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="03673-115">Ogólny interfejs lub delegat jest nazywany *wariantem* , jeśli jego parametry ogólne są zadeklarowane jako współvariant lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="03673-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="03673-116">Visual Basic umożliwia tworzenie własnych interfejsów i delegatów wariantów.</span><span class="sxs-lookup"><span data-stu-id="03673-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="03673-117">Aby uzyskać więcej informacji, zobacz [Tworzenie wariantów ogólnych interfejsów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [Wariancja w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="03673-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="03673-118">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="03673-118">Related Topics</span></span>

|<span data-ttu-id="03673-119">Tytuł</span><span class="sxs-lookup"><span data-stu-id="03673-119">Title</span></span>|<span data-ttu-id="03673-120">Opis</span><span class="sxs-lookup"><span data-stu-id="03673-120">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="03673-121">Wariancja w interfejsach ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="03673-122">Omawia kowariancję i kontrawariancja w interfejsach ogólnych i zawiera listę podstawowych interfejsów w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03673-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="03673-123">Tworzenie interfejsów ogólnych typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="03673-124">Pokazuje, jak utworzyć niestandardowe interfejsy wariantów.</span><span class="sxs-lookup"><span data-stu-id="03673-124">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="03673-125">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="03673-126">Pokazuje, jak Kowariancja i obsługa kontrawariancja w interfejsach <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> mogą ułatwić ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="03673-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="03673-127">Wariancja w delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="03673-128">Omawia kowariancję i kontrawariancja w obiektach ogólnych i nieogólnych oraz zawiera listę delegatów ogólnych typu Variant w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03673-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="03673-129">Korzystanie z wariancji w delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="03673-130">Pokazuje, w jaki sposób używać kowariancji i obsługi kontrawariancja w delegatach innych niż ogólne do dopasowywania sygnatur metod z typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="03673-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="03673-131">Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03673-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="03673-132">Pokazuje, jak Kowariancja i obsługa kontrawariancja w delegatach `Func` i `Action` mogą ułatwić ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="03673-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
