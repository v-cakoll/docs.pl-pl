---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 3a70b738b376e52482e63f2eb9cc4d7bb62a9b35
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141621"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="6cbd7-102">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="6cbd7-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="6cbd7-103">Można utworzyć własne atrybuty niestandardowe przez zdefiniowanie klasy atrybutów, klasy, która dziedziczy bezpośrednio lub pośrednio z <xref:System.Attribute> , co sprawia, że definicje atrybutów i są łatwe w użyciu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="6cbd7-104">Załóżmy, że chcesz oznakować typy nazwą programisty, który zapisał typ.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="6cbd7-105">Można zdefiniować `Author` klasę niestandardowego atrybutu:</span><span class="sxs-lookup"><span data-stu-id="6cbd7-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="6cbd7-106">Nazwa klasy `AuthorAttribute` to nazwa atrybutu, `Author` a także `Attribute` sufiks.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-106">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="6cbd7-107">Jest ona pochodną `System.Attribute` , więc jest klasą atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="6cbd7-108">Parametry konstruktora są parametrami pozycyjnymi atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="6cbd7-109">W tym przykładzie `name` jest parametrem pozycyjnym.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="6cbd7-110">Wszystkie publiczne pola do odczytu i zapisu są nazwanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="6cbd7-111">W tym przypadku `version` jest jedynym nazwanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="6cbd7-112">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby atrybut był `Author` prawidłowy tylko dla klasy i `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="6cbd7-113">Tego nowego atrybutu można użyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6cbd7-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="6cbd7-114">`AttributeUsage`ma nazwany parametr, `AllowMultiple` za pomocą którego można wykonać pojedyncze użycie lub Multiuse atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="6cbd7-115">W poniższym przykładzie kodu tworzony jest atrybut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="6cbd7-116">W poniższym przykładzie kodu do klasy są stosowane wiele atrybutów tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="6cbd7-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cbd7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cbd7-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="6cbd7-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6cbd7-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="6cbd7-119">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6cbd7-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="6cbd7-120">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="6cbd7-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="6cbd7-121">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="6cbd7-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="6cbd7-122">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="6cbd7-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="6cbd7-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="6cbd7-123">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
