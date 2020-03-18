---
title: Kowariancja i kontrawariancja (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169873"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="3b8a8-102">Kowariancja i kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="3b8a8-103">W języku C#, kowariancja i kontrawariancja umożliwiają niejawną konwersję referencyjną dla typów tablic, typów delegowanych i argumentów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="3b8a8-104">Kowariancja zachowuje zgodność przypisania i contravariance odwraca go.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="3b8a8-105">Poniższy kod pokazuje różnicę między zgodnością przypisania, kowariancją i kontrawarancją.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="3b8a8-106">Kowariancja dla tablic umożliwia niejawną konwersję tablicy typu bardziej pochodnego do tablicy typu mniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="3b8a8-107">Ale ta operacja nie jest typu bezpieczne, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="3b8a8-108">Obsługa kowariancji i kontrawaracji dla grup metod umożliwia dopasowywanie podpisów metod z typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="3b8a8-109">Dzięki temu można przypisać do delegatów nie tylko metody, które mają pasujące podpisy, ale także metody, które zwracają więcej typów pochodnych (kowariancja) lub które akceptują parametry, które mają mniej pochodnych typów (contravariance) niż określone przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="3b8a8-110">Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (C#)](./variance-in-delegates.md) i [Użycie wariancji w delegatach (C#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3b8a8-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="3b8a8-111">Poniższy przykład kodu pokazuje obsługę kowariancji i przeciwwariancji dla grup metod.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="3b8a8-112">W .NET Framework 4 lub nowszych C# obsługuje kowariancji i kontrawariancji w ogólnych interfejsów i delegatów i umożliwia niejawną konwersję parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="3b8a8-113">Aby uzyskać więcej informacji, zobacz [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md) i [Odchylenie w delegatach (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3b8a8-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="3b8a8-114">Poniższy przykład kodu pokazuje niejawną konwersję referencyjną dla interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="3b8a8-115">Ogólny interfejs lub delegat jest nazywany *wariantem,* jeśli jego parametry ogólne są zadeklarowane jako kowariantne lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="3b8a8-116">C# umożliwia tworzenie własnych interfejsów warianti i delegatów.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="3b8a8-117">Aby uzyskać więcej informacji, zobacz [Tworzenie wariantowych interfejsów ogólnych (C#)](./creating-variant-generic-interfaces.md) i [Odchylenie w delegatach (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3b8a8-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="3b8a8-118">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="3b8a8-118">Related Topics</span></span>  
  
|<span data-ttu-id="3b8a8-119">Tytuł</span><span class="sxs-lookup"><span data-stu-id="3b8a8-119">Title</span></span>|<span data-ttu-id="3b8a8-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3b8a8-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3b8a8-121">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="3b8a8-122">W tym artykule omówiono kowariancję i kontrawariancji w interfejsach ogólnych i zawiera listę wariantowych interfejsów ogólnych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="3b8a8-123">Tworzenie wariantowych interfejsów ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="3b8a8-124">Pokazuje, jak tworzyć niestandardowe interfejsy wariantowe.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="3b8a8-125">Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="3b8a8-126">Pokazuje, jak obsługa kowariancji i contravariance w <xref:System.Collections.Generic.IEnumerable%601> interfejsach i <xref:System.IComparable%601> może pomóc w ponownym użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="3b8a8-127">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="3b8a8-128">W tym artykule omówiono kowariancję i kontrawariancji w delegatów ogólnych i nieogólnych i zawiera listę wariantu delegatów ogólnych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="3b8a8-129">Używanie wariancji w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="3b8a8-130">Pokazuje, jak używać obsługi kowariancji i kontrawaracji w delegatach nieogólnych w celu dopasowania podpisów metod do typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="3b8a8-131">Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)</span><span class="sxs-lookup"><span data-stu-id="3b8a8-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="3b8a8-132">Pokazuje, jak obsługa kowariancji i contravariance w `Func` delegatów i `Action` może pomóc w ponownym użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="3b8a8-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
