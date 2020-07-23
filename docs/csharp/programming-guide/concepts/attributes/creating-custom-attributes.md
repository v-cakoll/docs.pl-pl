---
title: Tworzenie atrybutów niestandardowych (C#)
description: Dowiedz się, jak tworzyć atrybuty niestandardowe w języku C# przez zdefiniowanie klasy atrybutu, która dziedziczy z klasy Attribute.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 7d6f98620388af8715652dcbcfe78366952b853d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925088"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="f9c20-103">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="f9c20-103">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="f9c20-104">Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute> , co sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="f9c20-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="f9c20-105">Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ.</span><span class="sxs-lookup"><span data-stu-id="f9c20-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="f9c20-106">Można zdefiniować `Author` klasę niestandardowego atrybutu:</span><span class="sxs-lookup"><span data-stu-id="f9c20-106">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="f9c20-107">Nazwa klasy `AuthorAttribute` to nazwa atrybutu, `Author` a także `Attribute` sufiks.</span><span class="sxs-lookup"><span data-stu-id="f9c20-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="f9c20-108">Jest ona pochodną `System.Attribute` , więc jest klasą atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f9c20-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="f9c20-109">Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f9c20-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="f9c20-110">W tym przykładzie `name` jest parametrem pozycyjnym.</span><span class="sxs-lookup"><span data-stu-id="f9c20-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="f9c20-111">Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="f9c20-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="f9c20-112">W tym przypadku `version` jest jedynym nazwanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="f9c20-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="f9c20-113">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby atrybut był `Author` prawidłowy tylko dla klasy i `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f9c20-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="f9c20-114">Tego nowego atrybutu można użyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9c20-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="f9c20-115">`AttributeUsage`ma nazwany parametr, `AllowMultiple` za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f9c20-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="f9c20-116">W poniższym przykładzie kodu tworzony jest atrybut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="f9c20-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="f9c20-117">W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="f9c20-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9c20-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9c20-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="f9c20-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f9c20-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="f9c20-120">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f9c20-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="f9c20-121">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="f9c20-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="f9c20-122">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="f9c20-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="f9c20-123">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="f9c20-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="f9c20-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="f9c20-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
