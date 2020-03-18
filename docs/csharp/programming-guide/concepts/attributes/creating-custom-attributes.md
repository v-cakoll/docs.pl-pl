---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595406"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="a5a88-102">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="a5a88-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="a5a88-103">Można utworzyć własne atrybuty niestandardowe, definiując klasę atrybutów, klasę, <xref:System.Attribute>która wywodzi się bezpośrednio lub pośrednio z , co sprawia, że identyfikowanie definicji atrybutów w metadanych jest szybkie i łatwe.</span><span class="sxs-lookup"><span data-stu-id="a5a88-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="a5a88-104">Załóżmy, że chcesz oznaczyć typy z nazwą programisty, który napisał typ.</span><span class="sxs-lookup"><span data-stu-id="a5a88-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="a5a88-105">Można zdefiniować klasę `Author` atrybutu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="a5a88-105">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="a5a88-106">Nazwa klasy jest nazwą atrybutu `Author`.</span><span class="sxs-lookup"><span data-stu-id="a5a88-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="a5a88-107">Pochodzi z `System.Attribute`, więc jest to klasa atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a5a88-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="a5a88-108">Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a5a88-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="a5a88-109">W tym `name` przykładzie jest parametrem pozycyjnym.</span><span class="sxs-lookup"><span data-stu-id="a5a88-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="a5a88-110">Wszystkie publiczne pola odczytu i zapisu są nazywane parametrami.</span><span class="sxs-lookup"><span data-stu-id="a5a88-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="a5a88-111">W tym `version` przypadku jest jedynym nazwanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="a5a88-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="a5a88-112">Należy zwrócić uwagę `AttributeUsage` na użycie `Author` atrybutu, aby `struct` atrybut był prawidłowy tylko w klasie i deklaracjach.</span><span class="sxs-lookup"><span data-stu-id="a5a88-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="a5a88-113">Możesz użyć tego nowego atrybutu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a5a88-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="a5a88-114">`AttributeUsage`ma nazwany parametr, `AllowMultiple`, z którym można dokonać atrybutu niestandardowego jednorazowego użytku lub wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="a5a88-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="a5a88-115">W poniższym przykładzie kodu tworzony jest atrybut wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="a5a88-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="a5a88-116">W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="a5a88-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5a88-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a88-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="a5a88-118">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="a5a88-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a5a88-119">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a5a88-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="a5a88-120">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="a5a88-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a5a88-121">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="a5a88-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="a5a88-122">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="a5a88-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="a5a88-123">Użycie atrybutu (C#)</span><span class="sxs-lookup"><span data-stu-id="a5a88-123">AttributeUsage (C#)</span></span>](./attributeusage.md)
