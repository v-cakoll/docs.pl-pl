---
title: Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 756e235dacc3fcb2bf741d1d426e8dfcb53bf19b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313803"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="b0174-102">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b0174-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="b0174-103">W języku C# 3.0 lub nowszej automatycznie implementowane właściwości należy deklaracja właściwości bardziej zwięzły gdy wymagany jest nie dodatkową logikę w akcesorach właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0174-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="b0174-104">Umożliwiają one również kod klienta do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="b0174-104">They also enable client code to create objects.</span></span> <span data-ttu-id="b0174-105">Jak pokazano w poniższym przykładzie w deklaracji właściwości, kompilator tworzy polem zapasowym prywatne i anonimowy, który jest możliwy tylko za pośrednictwem właściwości `get` i `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="b0174-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0174-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0174-106">Example</span></span>  
 <span data-ttu-id="b0174-107">W poniższym przykładzie przedstawiono prosty klasy, która ma niektórych właściwości zaimplementowane automatycznie:</span><span class="sxs-lookup"><span data-stu-id="b0174-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="b0174-108">W języku C# 6 i nowsze można zainicjować właściwości zaimplementowane automatycznie, podobnie jak pola:</span><span class="sxs-lookup"><span data-stu-id="b0174-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="b0174-109">Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="b0174-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="b0174-110">Kod klienta można zmienić wartości w obiektach, po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="b0174-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="b0174-111">W złożonych klasy, które zawierają istotne zachowanie (metody) oraz dane jest często konieczne właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="b0174-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="b0174-112">Jednak dla małych klasy lub struktury, po prostu Hermetyzowanie zbiór wartości (dane) i mieć żadnych zachowań, albo należy obiekty niezmienne przez zadeklarowanie metody dostępu set jako [prywatnej](../../../csharp/language-reference/keywords/private.md) (niezmienne konsumentom) lub przez deklarowanie akcesora get (niezmienne wszędzie, z wyjątkiem konstruktora).</span><span class="sxs-lookup"><span data-stu-id="b0174-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="b0174-113">Aby uzyskać więcej informacji, zobacz [porady: Implementowanie klasy Lightweight przy użyciu właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b0174-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="b0174-114">Atrybuty są dozwolone na właściwości zaimplementowane automatycznie, ale oczywiście nie na pola zapasowy, ponieważ te nie są dostępne z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="b0174-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="b0174-115">Jeśli atrybut musi być używany dla pola zapasowy właściwości, wystarczy utworzyć regularne właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0174-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0174-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0174-116">See Also</span></span>  
 [<span data-ttu-id="b0174-117">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b0174-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="b0174-118">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="b0174-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
