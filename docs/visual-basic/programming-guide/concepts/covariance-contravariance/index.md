---
title: Kowariancja i Kontrawariancja (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 241b8f5864b6e9b3e1caddde25d032a24e4d0bb7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850455"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="79c39-102">Kowariancja i Kontrawariancja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="79c39-103">Kowariancja i kontrawariancja w języku Visual Basic, Włącz niejawna konwersja odwołania dla typów tablicy, typy delegatów i argumenty typu generycznego.</span><span class="sxs-lookup"><span data-stu-id="79c39-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="79c39-104">Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.</span><span class="sxs-lookup"><span data-stu-id="79c39-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="79c39-105">Poniższy kod ilustruje różnicę między zgodności przypisania, kowariancji i kontrawariancji.</span><span class="sxs-lookup"><span data-stu-id="79c39-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="79c39-106">Kowariancja dla tablic umożliwia niejawną konwersję tablicę typu bardziej pochodnego do tablicy typu mniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="79c39-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="79c39-107">Jednak ta operacja nie jest typem bezpiecznym, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="79c39-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="79c39-108">Kowariancja i kontrawariancja obsługę grupy metod umożliwia podpisów metod dopasowania z typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="79c39-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="79c39-109">Dzięki temu można przypisać do delegatów nie tylko tych metod, które pasują do sygnatur, ale także metody, które zwracają czy pochodne więcej typów (korelacja) lub że akceptujesz parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="79c39-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="79c39-110">Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="79c39-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="79c39-111">Poniższy przykład kodu pokazuje obsługę kowariancji i kontrawariancji dla grupy metod.</span><span class="sxs-lookup"><span data-stu-id="79c39-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="79c39-112">W programie .NET Framework 4 lub nowszym Visual Basic obsługuje Kowariancja i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu genetycznego.</span><span class="sxs-lookup"><span data-stu-id="79c39-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="79c39-113">Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="79c39-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="79c39-114">Poniższy przykład kodu pokazuje niejawna konwersja odwołania dla interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="79c39-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="79c39-115">Ogólny interfejs lub delegat jest nazywany *wariant* jeśli jego parametrów ogólnych są deklarowane jako kowariantny lub kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="79c39-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="79c39-116">Visual Basic umożliwia tworzenie interfejsów typu variant i delegatów.</span><span class="sxs-lookup"><span data-stu-id="79c39-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="79c39-117">Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="79c39-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="79c39-118">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="79c39-118">Related Topics</span></span>  
  
|<span data-ttu-id="79c39-119">Tytuł</span><span class="sxs-lookup"><span data-stu-id="79c39-119">Title</span></span>|<span data-ttu-id="79c39-120">Opis</span><span class="sxs-lookup"><span data-stu-id="79c39-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="79c39-121">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="79c39-122">W tym artykule omówiono Kowariancja i kontrawariancja w interfejsach ogólnych i zawiera listę interfejsów ogólnych typu variant w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79c39-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="79c39-123">Tworzenie interfejsów typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="79c39-124">Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.</span><span class="sxs-lookup"><span data-stu-id="79c39-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="79c39-125">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="79c39-126">Pokazuje, jak obsługiwać kowariancji i kontrawariancji w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy mogą pomóc ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="79c39-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="79c39-127">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="79c39-128">Omówiono kowariancji i kontrawariancji w delegatach ogólnych i nieogólnych i lista wariantów ogólnych delegatów w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79c39-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="79c39-129">Korzystanie z wariancji w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="79c39-130">Pokazuje, jak korzystać z pomocy technicznej kowariancji i kontrawariancji w delegatach nieogólnego do pasowania podpisy metod typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="79c39-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="79c39-131">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79c39-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="79c39-132">Pokazuje, jak obsługiwać kowariancji i kontrawariancji w `Func` i `Action` delegatów mogą pomóc ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="79c39-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
