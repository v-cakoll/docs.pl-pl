---
title: Właściwości implementowane automatycznie — przewodnik programowania C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170328"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="88927-102">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="88927-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="88927-103">W języku C# 3.0 i nowszych właściwości auto-implemented dokonać deklaracji właściwości bardziej zwięzłe, gdy nie dodatkowe logiki jest wymagane w akcesorów właściwości.</span><span class="sxs-lookup"><span data-stu-id="88927-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="88927-104">Umożliwiają one również kod klienta do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="88927-104">They also enable client code to create objects.</span></span> <span data-ttu-id="88927-105">Podczas deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe `get` `set` pole zapasowe, które jest dostępne tylko za pośrednictwem właściwości i akcesorów.</span><span class="sxs-lookup"><span data-stu-id="88927-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="88927-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="88927-106">Example</span></span>

<span data-ttu-id="88927-107">W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości implementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="88927-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="88927-108">Nie można zadeklarować właściwości zaimplementowane automatycznie w interfejsach.</span><span class="sxs-lookup"><span data-stu-id="88927-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="88927-109">Właściwości implementowane automatycznie deklarują pole zapasowe wystąpienia prywatnego, a interfejsy mogą nie deklarować pól wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="88927-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="88927-110">Deklarowanie właściwości w interfejsie bez definiowania treści deklaruje właściwość z akcesorami, które muszą być implementowane przez każdy typ, który implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="88927-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="88927-111">W języku C# 6 i nowszych można zainicjować właściwości implementowane automatycznie podobnie do pól:</span><span class="sxs-lookup"><span data-stu-id="88927-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="88927-112">Klasa, która jest pokazana w poprzednim przykładzie jest zmienna.</span><span class="sxs-lookup"><span data-stu-id="88927-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="88927-113">Kod klienta można zmienić wartości w obiektach po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="88927-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="88927-114">W złożonych klas, które zawierają znaczące zachowanie (metody), a także dane, często jest konieczne, aby mieć właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="88927-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="88927-115">Jednak dla małych klas lub struktur, które po prostu hermetyzują zestaw wartości (dane) i mają niewiele lub nie ma zachowań, należy albo zrobić obiekty niezmienne, deklarując set akcesor jako [prywatny](../../language-reference/keywords/private.md) (niezmienne dla konsumentów) lub deklarując tylko get akcesor (niezmienne wszędzie z wyjątkiem konstruktora).</span><span class="sxs-lookup"><span data-stu-id="88927-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="88927-116">Aby uzyskać więcej informacji, zobacz [Jak zaimplementować klasę lekką z właściwościami implementowanymi automatycznie](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="88927-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88927-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88927-117">See also</span></span>

- [<span data-ttu-id="88927-118">Właściwości</span><span class="sxs-lookup"><span data-stu-id="88927-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="88927-119">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="88927-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
