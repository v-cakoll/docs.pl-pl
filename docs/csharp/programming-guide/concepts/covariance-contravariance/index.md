---
title: Kowariancja i kontrawariancja (C#)
description: Dowiedz się więcej o kowariancji i kontrawariancja oraz o tym, jak wpływają na zgodność z przydziałami. Zobacz przykładowy kod, który pokazuje różnice między nimi.
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 65c75029c27b6c9a5ddc96f01622b520e8698f55
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105692"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="1c55c-104">Kowariancja i kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-104">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="1c55c-105">W języku C#, Kowariancja i kontrawariancja umożliwiają włączenie niejawnej konwersji odwołań dla typów tablic, typów delegatów i argumentów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1c55c-105">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="1c55c-106">Kowariancja zachowuje zgodność przypisania i kontrawariancja ją odwraca.</span><span class="sxs-lookup"><span data-stu-id="1c55c-106">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="1c55c-107">Poniższy kod ilustruje różnicę między zgodnością przypisania, kowariancją i kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="1c55c-107">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="1c55c-108">Kowariancja dla tablic umożliwia niejawną konwersję tablicy o bardziej pochodny typ do tablicy mniej pochodnego typu.</span><span class="sxs-lookup"><span data-stu-id="1c55c-108">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="1c55c-109">Ale ta operacja nie jest bezpieczna, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1c55c-109">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="1c55c-110">Obsługa kowariancji i kontrawariancja dla grup metod umożliwia dopasowywanie sygnatur metod przy użyciu typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="1c55c-110">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="1c55c-111">Dzięki temu można przypisywać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="1c55c-111">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="1c55c-112">Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (c#)](./variance-in-delegates.md) i [Korzystanie z wariancji w delegatach (c#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1c55c-112">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="1c55c-113">Poniższy przykład kodu pokazuje kowariancję i obsługę kontrawariancja dla grup metod.</span><span class="sxs-lookup"><span data-stu-id="1c55c-113">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="1c55c-114">W .NET Framework 4 i nowszych wersjach język C# obsługuje kowariancję i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1c55c-114">In .NET Framework 4 and later versions, C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="1c55c-115">Aby uzyskać więcej informacji, zobacz [Wariancja w interfejsach ogólnych (c#)](./variance-in-generic-interfaces.md) i [Wariancja w delegatach (c#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1c55c-115">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="1c55c-116">Poniższy przykład kodu przedstawia niejawną konwersję odwołań dla interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="1c55c-116">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="1c55c-117">Ogólny interfejs lub delegat jest nazywany *wariantem* , jeśli jego parametry ogólne są zadeklarowane jako współvariant lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="1c55c-117">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="1c55c-118">Język C# umożliwia tworzenie własnych interfejsów i delegatów wariantów.</span><span class="sxs-lookup"><span data-stu-id="1c55c-118">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="1c55c-119">Aby uzyskać więcej informacji, zobacz [Tworzenie wariantów ogólnych interfejsów (c#)](./creating-variant-generic-interfaces.md) i [Wariancja w delegatach (c#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1c55c-119">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="1c55c-120">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="1c55c-120">Related Topics</span></span>  
  
|<span data-ttu-id="1c55c-121">Tytuł</span><span class="sxs-lookup"><span data-stu-id="1c55c-121">Title</span></span>|<span data-ttu-id="1c55c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1c55c-122">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1c55c-123">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-123">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="1c55c-124">Omawia kowariancję i kontrawariancja w interfejsach ogólnych i zawiera listę podstawowych interfejsów w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c55c-124">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="1c55c-125">Tworzenie interfejsów ogólnych typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-125">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="1c55c-126">Pokazuje, jak utworzyć niestandardowe interfejsy wariantów.</span><span class="sxs-lookup"><span data-stu-id="1c55c-126">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="1c55c-127">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-127">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="1c55c-128">Pokazuje, jak Kowariancja i obsługa kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601> interfejsie i mogą ułatwić ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="1c55c-128">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="1c55c-129">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-129">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="1c55c-130">Omawia kowariancję i kontrawariancja w obiektach ogólnych i nieogólnych oraz zawiera listę delegatów ogólnych typu Variant w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c55c-130">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="1c55c-131">Korzystanie z wariancji w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-131">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="1c55c-132">Pokazuje, w jaki sposób używać kowariancji i obsługi kontrawariancja w delegatach innych niż ogólne do dopasowywania sygnatur metod z typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="1c55c-132">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="1c55c-133">Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)</span><span class="sxs-lookup"><span data-stu-id="1c55c-133">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="1c55c-134">Pokazuje, jak Kowariancja i obsługa kontrawariancja w `Func` `Action` delegatach i mogą ułatwić ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="1c55c-134">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
