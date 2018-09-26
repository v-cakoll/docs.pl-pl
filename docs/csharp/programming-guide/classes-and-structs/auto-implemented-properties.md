---
title: Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 0d32dfd626cb8484e935dd0e8608c2e29d3ecbde
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108471"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="19e1e-102">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="19e1e-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="19e1e-103">W języku C# 3.0 i nowszych wersjach automatycznie implementowane właściwości należy deklaracja właściwości bardziej zwięzły widok żądanie nie dodatkowej logiki w metodach dostępu właściwości.</span><span class="sxs-lookup"><span data-stu-id="19e1e-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="19e1e-104">Umożliwiają one również kod klienta do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="19e1e-104">They also enable client code to create objects.</span></span> <span data-ttu-id="19e1e-105">Kiedy Deklarujesz właściwości, jak pokazano w poniższym przykładzie, kompilator utworzy polem zapasowym prywatne i anonimowy, który jest możliwy tylko za pośrednictwem właściwości `get` i `set` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="19e1e-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19e1e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="19e1e-106">Example</span></span>  
 <span data-ttu-id="19e1e-107">Poniższy przykład pokazuje prosty klasy, która ma kilka właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="19e1e-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="19e1e-108">W języku C# 6 lub nowszej można zainicjować właściwości zaimplementowane automatycznie, podobnie jak pola:</span><span class="sxs-lookup"><span data-stu-id="19e1e-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="19e1e-109">Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="19e1e-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="19e1e-110">Kod klienta można zmienić wartości w obiektach, po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="19e1e-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="19e1e-111">W klasach złożonych, które zawierają istotne zachowanie (metod) oraz danych często jest konieczne właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="19e1e-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="19e1e-112">Jednak dla małych klas lub struktur, które po prostu hermetyzacji zestaw wartości (dane) i ma niewielkiego lub żadnego zachowań, albo należy obiekty niezmienne przez zadeklarowanie metody dostępu set jako [prywatnej](../../../csharp/language-reference/keywords/private.md) (niezmienne konsumentom) lub przez deklarowanie tylko akcesor pobierania (niezmienne wszędzie z wyjątkiem konstruktora).</span><span class="sxs-lookup"><span data-stu-id="19e1e-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="19e1e-113">Aby uzyskać więcej informacji, zobacz [porady: Implementowanie klasy Lightweight przy użyciu implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="19e1e-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="19e1e-114">Atrybuty są dozwolone na automatycznie implementowane właściwości, ale oczywiście nie w polach zapasowy, ponieważ te nie są dostępne z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="19e1e-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="19e1e-115">Jeśli musisz użyć atrybutu pola zapasowego właściwości, wystarczy utworzyć regularne właściwości.</span><span class="sxs-lookup"><span data-stu-id="19e1e-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e1e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19e1e-116">See Also</span></span>

- [<span data-ttu-id="19e1e-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="19e1e-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="19e1e-118">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="19e1e-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
