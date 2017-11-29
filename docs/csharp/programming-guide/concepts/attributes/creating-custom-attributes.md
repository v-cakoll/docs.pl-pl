---
title: "Tworzenie atrybutów niestandardowych (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 38bdedb352cc79f7a4cc3d08eb6138e7d994514b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="55c71-102">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="55c71-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="55c71-103">Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która jest pochodną bezpośrednio lub pośrednio <xref:System.Attribute>, która sprawia, że identyfikacji definicje atrybutów w metadanych szybkie i łatwe.</span><span class="sxs-lookup"><span data-stu-id="55c71-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="55c71-104">Załóżmy, że chcesz typów tagu o nazwie programisty autorze typu.</span><span class="sxs-lookup"><span data-stu-id="55c71-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="55c71-105">Możesz zdefiniować niestandardowy `Author` klasy atrybutu:</span><span class="sxs-lookup"><span data-stu-id="55c71-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="55c71-106">Nazwa klasy jest nazwa atrybutu `Author`.</span><span class="sxs-lookup"><span data-stu-id="55c71-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="55c71-107">Jest pochodną `System.Attribute`, co klasa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="55c71-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="55c71-108">Konstruktor parametry są parametry pozycyjne atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="55c71-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="55c71-109">W tym przykładzie `name` jest parametrów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="55c71-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="55c71-110">Parametry są nazwane właściwości lub pola publiczne odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="55c71-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="55c71-111">W takim przypadku `version` tylko nosi nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="55c71-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="55c71-112">Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby `Author` atrybut jest prawidłowy tylko w klasie i `struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="55c71-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="55c71-113">Ten nowy atrybut można użyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="55c71-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="55c71-114">`AttributeUsage`Nazwany parametr `AllowMultiple`, z której można utworzyć atrybutu niestandardowego, jednorazowych lub multiuse.</span><span class="sxs-lookup"><span data-stu-id="55c71-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="55c71-115">W poniższym przykładzie jest tworzony multiuse atrybutu.</span><span class="sxs-lookup"><span data-stu-id="55c71-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="55c71-116">W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="55c71-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="55c71-117">Jeśli atrybut klasy zawiera właściwości, tej właściwości musi być do odczytu / zapisu.</span><span class="sxs-lookup"><span data-stu-id="55c71-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c71-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55c71-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="55c71-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="55c71-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="55c71-120">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="55c71-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="55c71-121">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="55c71-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="55c71-122">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="55c71-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="55c71-123">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="55c71-123">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="55c71-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="55c71-124">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
