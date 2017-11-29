---
title: Kowariancja i Kontrawariancja (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc6eb2c4371f69588fd235a0bd3e872b42eb028f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="fa6d8-102">Kowariancja i Kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="fa6d8-103">Kowariancja i kontrawariancja w języku C#, Włącz niejawnej konwersji odwołania dla tablic, typów delegowanych i argumentów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="fa6d8-104">Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="fa6d8-105">Poniższy kod przedstawia różnicę między zgodności przypisania, Kowariancja i kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.   
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.   
object obj = str;  
  
// Covariance.   
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument   
// is assigned to an object instantiated with a less derived type argument.   
// Assignment compatibility is preserved.   
IEnumerable<object> objects = strings;  
  
// Contravariance.             
// Assume that the following method is in the class:   
// static void SetObject(object o) { }   
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument   
// is assigned to an object instantiated with a more derived type argument.   
// Assignment compatibility is reversed.   
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="fa6d8-106">Kowariancja dla tablic umożliwia niejawna konwersja tablicy typu bardziej pochodnego do tablicy typu mniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="fa6d8-107">Jednak ta operacja nie jest typem bezpieczne, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="fa6d8-108">Kowariancja i kontrawariancja obsługę grupy metod umożliwia dopasowywanie podpisy metod typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="fa6d8-109">Ta umożliwia można przypisać do delegatów nie tylko tych metod, które pasują do podpisów, ale również metody, które zwracają się, że więcej pochodnych typów (kowariancja) lub że akceptujesz parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="fa6d8-110">Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d8-110">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="fa6d8-111">Poniższy przykład kodu pokazuje Kowariancja i kontrawariancja obsługę dla grupy metod.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="fa6d8-112">W programie .NET Framework 4 lub nowszej C# obsługuje Kowariancja i kontrawariancja w interfejsach i delegatów i umożliwia niejawnej konwersji wartości parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="fa6d8-113">Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d8-113">For more information, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="fa6d8-114">Poniższy przykład kodu pokazuje niejawnej konwersji odwołania dla ogólnych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="fa6d8-115">Ogólny interfejs lub delegat jest nazywany *variant* jeśli jego parametrów ogólnych są deklarowane jako kowariantnego lub kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="fa6d8-116">C# umożliwia tworzenie własnych interfejsów typu variant i delegatów.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="fa6d8-117">Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d8-117">For more information, see [Creating Variant Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="fa6d8-118">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="fa6d8-118">Related Topics</span></span>  
  
|<span data-ttu-id="fa6d8-119">Tytuł</span><span class="sxs-lookup"><span data-stu-id="fa6d8-119">Title</span></span>|<span data-ttu-id="fa6d8-120">Opis</span><span class="sxs-lookup"><span data-stu-id="fa6d8-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fa6d8-121">Wariancje w interfejsach (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-121">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="fa6d8-122">Zawiera omówienie Kowariancja i kontrawariancja w interfejsach, a także listę interfejsów ogólnych typu variant w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="fa6d8-123">Tworzenie interfejsów ogólnych typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-123">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="fa6d8-124">Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="fa6d8-125">Korzystanie z wariancji w interfejsach dla kolekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="fa6d8-126">Pokazuje, jak obsługują Kowariancja i kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy ułatwia ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="fa6d8-127">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-127">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="fa6d8-128">Zawiera omówienie Kowariancja i kontrawariancja w delegatach ogólne i inny niż ogólny, a także listę variant delegatów w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="fa6d8-129">Korzystanie z wariancji w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-129">Using Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="fa6d8-130">Pokazano, jak korzystać z obsługi Kowariancja i kontrawariancja w delegatach nieogólnego odpowiadać podpisy metod typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="fa6d8-131">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)</span><span class="sxs-lookup"><span data-stu-id="fa6d8-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="fa6d8-132">Pokazuje, jak obsługują Kowariancja i kontrawariancja w `Func` i `Action` delegatów ułatwia ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="fa6d8-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
