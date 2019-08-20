---
title: Kowariancja i kontrawariancja (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 1d5a1de1825e585512f694a0cd72cee9b37cda36
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595275"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="4c27b-102">Kowariancja i kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="4c27b-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="4c27b-103">W C#, Kowariancja i kontrawariancja Włącz niejawną konwersję odwołań dla typów tablic, typów delegatów i argumentów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4c27b-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="4c27b-104">Kowariancja zachowuje zgodność przypisania i kontrawariancja ją odwraca.</span><span class="sxs-lookup"><span data-stu-id="4c27b-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="4c27b-105">Poniższy kod ilustruje różnicę między zgodnością przypisania, kowariancją i kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="4c27b-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="4c27b-106">Kowariancja dla tablic umożliwia niejawną konwersję tablicy o bardziej pochodny typ do tablicy mniej pochodnego typu.</span><span class="sxs-lookup"><span data-stu-id="4c27b-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="4c27b-107">Ale ta operacja nie jest bezpieczna, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4c27b-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="4c27b-108">Obsługa kowariancji i kontrawariancja dla grup metod umożliwia dopasowywanie sygnatur metod przy użyciu typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="4c27b-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="4c27b-109">Dzięki temu można przypisywać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4c27b-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="4c27b-110">Aby uzyskać więcej informacji, zobacz [Wariancja wC#delegatach ()](./variance-in-delegates.md) i [Używanie wariancji w delegatach (C#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c27b-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="4c27b-111">Poniższy przykład kodu pokazuje kowariancję i obsługę kontrawariancja dla grup metod.</span><span class="sxs-lookup"><span data-stu-id="4c27b-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="4c27b-112">W .NET Framework 4 lub nowszej C# obsługuje kowariancję i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4c27b-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="4c27b-113">Aby uzyskać więcej informacji, zobacz [Wariancja w interfejsachC#ogólnych ()](./variance-in-generic-interfaces.md) i Wariancja [w delegatach (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c27b-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="4c27b-114">Poniższy przykład kodu przedstawia niejawną konwersję odwołań dla interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="4c27b-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="4c27b-115">Ogólny interfejs lub delegat jest nazywany *wariantem* , jeśli jego parametry ogólne są zadeklarowane jako współvariant lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="4c27b-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="4c27b-116">C#umożliwia tworzenie własnych interfejsów i delegatów wariantów.</span><span class="sxs-lookup"><span data-stu-id="4c27b-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="4c27b-117">Aby uzyskać więcej informacji, zobacz [Tworzenie wariantów ogólnych interfejsówC#()](./creating-variant-generic-interfaces.md) i [Wariancja wC#delegatach ()](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c27b-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="4c27b-118">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="4c27b-118">Related Topics</span></span>  
  
|<span data-ttu-id="4c27b-119">Tytuł</span><span class="sxs-lookup"><span data-stu-id="4c27b-119">Title</span></span>|<span data-ttu-id="4c27b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="4c27b-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4c27b-121">Wariancja w interfejsachC#ogólnych ()</span><span class="sxs-lookup"><span data-stu-id="4c27b-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="4c27b-122">Omawia kowariancję i kontrawariancja w interfejsach ogólnych i zawiera listę podstawowych interfejsów w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c27b-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="4c27b-123">Tworzenie interfejsów ogólnych typu VariantC#()</span><span class="sxs-lookup"><span data-stu-id="4c27b-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="4c27b-124">Pokazuje, jak utworzyć niestandardowe interfejsy wariantów.</span><span class="sxs-lookup"><span data-stu-id="4c27b-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="4c27b-125">Korzystanie z wariancji w interfejsach dlaC#kolekcji ogólnych ()</span><span class="sxs-lookup"><span data-stu-id="4c27b-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="4c27b-126">Pokazuje, jak Kowariancja i obsługa kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> interfejsie i <xref:System.IComparable%601> mogą ułatwić ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="4c27b-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="4c27b-127">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="4c27b-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="4c27b-128">Omawia kowariancję i kontrawariancja w obiektach ogólnych i nieogólnych oraz zawiera listę delegatów ogólnych typu Variant w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c27b-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="4c27b-129">Korzystanie z wariancji wC#delegatach ()</span><span class="sxs-lookup"><span data-stu-id="4c27b-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="4c27b-130">Pokazuje, w jaki sposób używać kowariancji i obsługi kontrawariancja w delegatach innych niż ogólne do dopasowywania sygnatur metod z typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="4c27b-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="4c27b-131">Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()</span><span class="sxs-lookup"><span data-stu-id="4c27b-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="4c27b-132">Pokazuje, jak Kowariancja i obsługa kontrawariancja w `Func` delegatach i `Action` mogą ułatwić ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="4c27b-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
