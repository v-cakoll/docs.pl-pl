---
title: Kowariancja i Kontrawariancja (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1df3b01573ae1a9dc5c106efa5e387927c57c55f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="a6f58-102">Kowariancja i Kontrawariancja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="a6f58-103">Kowariancja i kontrawariancja w języku Visual Basic, Włącz niejawnej konwersji odwołania dla tablic, typów delegowanych i argumentów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a6f58-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="a6f58-104">Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.</span><span class="sxs-lookup"><span data-stu-id="a6f58-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="a6f58-105">Poniższy kod przedstawia różnicę między zgodności przypisania, Kowariancja i kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="a6f58-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="a6f58-106">Kowariancja dla tablic umożliwia niejawna konwersja tablicy typu bardziej pochodnego do tablicy typu mniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="a6f58-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="a6f58-107">Jednak ta operacja nie jest typem bezpieczne, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a6f58-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="a6f58-108">Kowariancja i kontrawariancja obsługę grupy metod umożliwia dopasowywanie podpisy metod typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="a6f58-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="a6f58-109">Ta umożliwia można przypisać do delegatów nie tylko tych metod, które pasują do podpisów, ale również metody, które zwracają się, że więcej pochodnych typów (kowariancja) lub że akceptujesz parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="a6f58-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="a6f58-110">Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a6f58-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="a6f58-111">Poniższy przykład kodu pokazuje Kowariancja i kontrawariancja obsługę dla grupy metod.</span><span class="sxs-lookup"><span data-stu-id="a6f58-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="a6f58-112">W .NET Framework 4 lub nowszym Visual Basic obsługuje Kowariancja i kontrawariancja w interfejsach i delegatów i umożliwiają niejawnej konwersji wartości parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a6f58-112">In .NET Framework 4 or later Visual Basic support covariance and contravariance in generic interfaces and delegates and allow for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="a6f58-113">Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a6f58-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="a6f58-114">Poniższy przykład kodu pokazuje niejawnej konwersji odwołania dla ogólnych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="a6f58-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="a6f58-115">Ogólny interfejs lub delegat jest nazywany *variant* jeśli jego parametrów ogólnych są deklarowane jako kowariantnego lub kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="a6f58-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="a6f58-116">Visual Basic umożliwia tworzenie własnych interfejsów typu variant i delegatów.</span><span class="sxs-lookup"><span data-stu-id="a6f58-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="a6f58-117">Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="a6f58-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="a6f58-118">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="a6f58-118">Related Topics</span></span>  
  
|<span data-ttu-id="a6f58-119">Tytuł</span><span class="sxs-lookup"><span data-stu-id="a6f58-119">Title</span></span>|<span data-ttu-id="a6f58-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a6f58-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a6f58-121">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="a6f58-122">Zawiera omówienie Kowariancja i kontrawariancja w interfejsach, a także listę interfejsów ogólnych typu variant w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6f58-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="a6f58-123">Tworzenie interfejsów ogólnych typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="a6f58-124">Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.</span><span class="sxs-lookup"><span data-stu-id="a6f58-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="a6f58-125">Korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="a6f58-126">Pokazuje, jak obsługują Kowariancja i kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy ułatwia ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="a6f58-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="a6f58-127">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="a6f58-128">Zawiera omówienie Kowariancja i kontrawariancja w delegatach ogólne i inny niż ogólny, a także listę variant delegatów w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6f58-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="a6f58-129">Korzystanie z wariancji w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="a6f58-130">Pokazano, jak korzystać z obsługi Kowariancja i kontrawariancja w delegatach nieogólnego odpowiadać podpisy metod typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="a6f58-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="a6f58-131">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6f58-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="a6f58-132">Pokazuje, jak obsługują Kowariancja i kontrawariancja w `Func` i `Action` delegatów ułatwia ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="a6f58-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
