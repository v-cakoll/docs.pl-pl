---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81e7440279a2d7dfa801394ee0e9af6181da3c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attributeusage-c"></a><span data-ttu-id="3f3a4-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="3f3a4-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="3f3a4-103">Określa sposób użycia klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="3f3a4-104">`AttributeUsage`jest atrybut, który może odnosić się do definicji atrybutu niestandardowego do kontrolowania, jak można zastosować nowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="3f3a4-105">Po zastosowaniu jawnie, domyślne ustawienia następującą postać:</span><span class="sxs-lookup"><span data-stu-id="3f3a4-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="3f3a4-106">W tym przykładzie `NewAttribute` klasa może być stosowane do dowolnej jednostki kodu atrybutu można, ale mogą być stosowane tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="3f3a4-107">Zostało ono odziedziczone przez klas pochodnych po zastosowaniu do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="3f3a4-108">`AllowMultiple` i `Inherited` argumenty są opcjonalne, dlatego ten kod działa tak samo:</span><span class="sxs-lookup"><span data-stu-id="3f3a4-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="3f3a4-109">Pierwszy `AttributeUsage` argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="3f3a4-110">Wiele typów docelowy może odnosić się wraz z operatora OR w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3f3a4-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="3f3a4-111">Jeśli `AllowMultiple` argument ma wartość `true`, następnie wynikowy atrybut można stosować więcej niż raz do jednej jednostki, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="3f3a4-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 <span data-ttu-id="3f3a4-112">W takim przypadku `MultiUseAttr` może odnosić się wielokrotnie ponieważ `AllowMultiple` ma ustawioną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="3f3a4-113">Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="3f3a4-114">Jeśli `Inherited` ma ustawioną wartość `false`, a następnie ten atrybut nie jest dziedziczone przez klasy, które są pochodnymi klasy, która ma atrybut.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="3f3a4-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3f3a4-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="3f3a4-116">W takim przypadku `Attr1` nie ma zastosowania do `DClass` za pośrednictwem dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f3a4-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f3a4-117">Remarks</span></span>  
 <span data-ttu-id="3f3a4-118">`AttributeUsage` Jest atrybutem jednorazowy — nie można zastosować w więcej niż raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="3f3a4-119">`AttributeUsage`alias jest <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="3f3a4-120">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="3f3a4-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f3a4-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f3a4-121">Example</span></span>  
 <span data-ttu-id="3f3a4-122">Poniższy przykład ilustruje efekt `Inherited` i `AllowMultiple` argumenty `AttributeUsage` atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="3f3a4-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a><span data-ttu-id="3f3a4-123">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3f3a4-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f3a4-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f3a4-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="3f3a4-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3f3a4-125">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3f3a4-126">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f3a4-126">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="3f3a4-127">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="3f3a4-127">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="3f3a4-128">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f3a4-128">Attributes</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="3f3a4-129">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="3f3a4-129">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="3f3a4-130">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="3f3a4-130">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
