---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389557"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="7787d-102">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="7787d-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="7787d-103">Można utworzyć własne atrybuty niestandardowe, definiując klasę atrybutu, klasę, <xref:System.Attribute>która wywodzi się bezpośrednio lub pośrednio z , co sprawia, że identyfikowanie definicji atrybutów w metadanych jest szybkie i łatwe.</span><span class="sxs-lookup"><span data-stu-id="7787d-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="7787d-104">Załóżmy, że chcesz oznaczyć typy z nazwą programisty, który napisał typ.</span><span class="sxs-lookup"><span data-stu-id="7787d-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="7787d-105">Można zdefiniować `Author` klasę atrybutów niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="7787d-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="7787d-106">Nazwa klasy jest nazwą atrybutu `Author`, .</span><span class="sxs-lookup"><span data-stu-id="7787d-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="7787d-107">Jest pochodną `System.Attribute`, więc jest to klasa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="7787d-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="7787d-108">Parametry konstruktora są parametry pozycyjne atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="7787d-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="7787d-109">W tym `name` przykładzie jest parametrem pozycyjnym.</span><span class="sxs-lookup"><span data-stu-id="7787d-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="7787d-110">Wszystkie publiczne pola odczytu i zapisu lub właściwości są nazywane parametrami.</span><span class="sxs-lookup"><span data-stu-id="7787d-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="7787d-111">W takim `version` przypadku jest jedynym nazwanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="7787d-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="7787d-112">Zanotuj `AttributeUsage` użycie atrybutu, `Author` aby atrybut był `struct` prawidłowy tylko dla klasy i deklaracji.</span><span class="sxs-lookup"><span data-stu-id="7787d-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="7787d-113">Możesz użyć tego nowego atrybutu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7787d-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="7787d-114">`AttributeUsage`ma nazwany parametr, `AllowMultiple`za pomocą którego można wykonać atrybut niestandardowy jednorazowego użytku lub wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="7787d-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="7787d-115">W poniższym przykładzie kodu tworzony jest atrybut wielofunkcyjny.</span><span class="sxs-lookup"><span data-stu-id="7787d-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="7787d-116">W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="7787d-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7787d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7787d-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="7787d-118">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="7787d-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="7787d-119">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7787d-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="7787d-120">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="7787d-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="7787d-121">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="7787d-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="7787d-122">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="7787d-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="7787d-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="7787d-123">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
