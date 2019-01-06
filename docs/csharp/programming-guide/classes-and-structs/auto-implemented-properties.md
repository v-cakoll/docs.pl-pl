---
title: Automatycznie implementowane właściwości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef9243498f3f97e560e45c389932ff57e1e4eef7
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058519"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="c28b0-102">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c28b0-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="c28b0-103">W języku C# 3.0 i nowszych wersjach automatycznie implementowane właściwości należy deklaracja właściwości bardziej zwięzły widok żądanie nie dodatkowej logiki w metodach dostępu właściwości.</span><span class="sxs-lookup"><span data-stu-id="c28b0-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="c28b0-104">Umożliwiają one również kod klienta do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="c28b0-104">They also enable client code to create objects.</span></span> <span data-ttu-id="c28b0-105">Kiedy Deklarujesz właściwości, jak pokazano w poniższym przykładzie, kompilator utworzy polem zapasowym prywatne i anonimowy, który jest możliwy tylko za pośrednictwem właściwości `get` i `set` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="c28b0-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c28b0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c28b0-106">Example</span></span>  
 <span data-ttu-id="c28b0-107">Poniższy przykład pokazuje prosty klasy, która ma kilka właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="c28b0-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="c28b0-108">W języku C# 6 lub nowszej można zainicjować właściwości zaimplementowane automatycznie, podobnie jak pola:</span><span class="sxs-lookup"><span data-stu-id="c28b0-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="c28b0-109">Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="c28b0-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="c28b0-110">Kod klienta można zmienić wartości w obiektach, po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="c28b0-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="c28b0-111">W klasach złożonych, które zawierają istotne zachowanie (metod) oraz danych często jest konieczne właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="c28b0-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="c28b0-112">Jednak dla małych klas lub struktur, które po prostu hermetyzacji zestaw wartości (dane) i ma niewielkiego lub żadnego zachowań, albo należy obiekty niezmienne przez zadeklarowanie metody dostępu set jako [prywatnej](../../../csharp/language-reference/keywords/private.md) (niezmienne konsumentom) lub przez deklarowanie tylko akcesor pobierania (niezmienne wszędzie z wyjątkiem konstruktora).</span><span class="sxs-lookup"><span data-stu-id="c28b0-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="c28b0-113">Aby uzyskać więcej informacji, zobacz [jak: Implementowanie klasy Lightweight przy użyciu automatycznie implementowanych właściwości](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c28b0-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28b0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c28b0-114">See Also</span></span>

- [<span data-ttu-id="c28b0-115">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c28b0-115">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="c28b0-116">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="c28b0-116">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
