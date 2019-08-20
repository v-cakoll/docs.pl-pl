---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595406"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="35070-102">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="35070-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="35070-103">Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z, co <xref:System.Attribute>sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="35070-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="35070-104">Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ.</span><span class="sxs-lookup"><span data-stu-id="35070-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="35070-105">Można zdefiniować klasę niestandardowego `Author` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="35070-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="35070-106">Nazwa klasy jest nazwą atrybutu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="35070-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="35070-107">Jest ona pochodną `System.Attribute`, więc jest klasą atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="35070-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="35070-108">Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="35070-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="35070-109">W tym przykładzie `name` jest parametrem pozycyjnym.</span><span class="sxs-lookup"><span data-stu-id="35070-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="35070-110">Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="35070-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="35070-111">W tym przypadku `version` jest jedynym nazwanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="35070-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="35070-112">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby `Author` atrybut był prawidłowy tylko dla klasy i `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="35070-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="35070-113">Tego nowego atrybutu można użyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="35070-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="35070-114">`AttributeUsage`ma nazwany parametr `AllowMultiple`, za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="35070-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="35070-115">W poniższym przykładzie kodu tworzony jest atrybut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="35070-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="35070-116">W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="35070-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="35070-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35070-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="35070-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="35070-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="35070-119">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="35070-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="35070-120">OdbicieC#()</span><span class="sxs-lookup"><span data-stu-id="35070-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="35070-121">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="35070-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="35070-122">Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()</span><span class="sxs-lookup"><span data-stu-id="35070-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="35070-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="35070-123">AttributeUsage (C#)</span></span>](./attributeusage.md)
