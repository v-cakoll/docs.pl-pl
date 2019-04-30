---
title: Tworzenie atrybutów niestandardowych (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 0277a88b7e5beda511f6490261a7009adcfed4ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668708"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="88805-102">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="88805-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="88805-103">Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która pochodzi bezpośrednio lub pośrednio z <xref:System.Attribute>, co sprawia, że identyfikowanie definicji atrybutów w metadanych jest łatwe i szybkie.</span><span class="sxs-lookup"><span data-stu-id="88805-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="88805-104">Załóżmy, że chcesz typy tag o nazwie programisty, który napisał typu.</span><span class="sxs-lookup"><span data-stu-id="88805-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="88805-105">Można zdefiniować niestandardowy `Author` klasy atrybutu:</span><span class="sxs-lookup"><span data-stu-id="88805-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="88805-106">Nazwa klasy jest nazwą atrybutu `Author`.</span><span class="sxs-lookup"><span data-stu-id="88805-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="88805-107">Jest pochodną `System.Attribute`, więc jest klasą atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="88805-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="88805-108">Parametry Konstruktora są parametry pozycyjne atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="88805-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="88805-109">W tym przykładzie `name` jest parametr pozycyjne.</span><span class="sxs-lookup"><span data-stu-id="88805-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="88805-110">Właściwości lub pola publiczne odczytu / zapisu czy nazwanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="88805-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="88805-111">W tym przypadku `version` tylko nosi nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="88805-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="88805-112">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby wprowadzić `Author` atrybut jest prawidłowy tylko w klasie i `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="88805-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="88805-113">Można użyć tego nowego atrybutu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="88805-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="88805-114">`AttributeUsage` został nazwany parametr `AllowMultiple`, dzięki którym możesz ustawić atrybutu niestandardowego jednorazowych lub multiuse —.</span><span class="sxs-lookup"><span data-stu-id="88805-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="88805-115">W poniższym przykładzie kodu multiuse — atrybut jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="88805-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="88805-116">W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="88805-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="88805-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88805-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="88805-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88805-118">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="88805-119">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="88805-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="88805-120">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="88805-120">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="88805-121">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="88805-121">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="88805-122">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="88805-122">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="88805-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="88805-123">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
