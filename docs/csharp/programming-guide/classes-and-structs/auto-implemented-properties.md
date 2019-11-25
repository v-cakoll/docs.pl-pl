---
title: Zaimplementowane właściwości — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 92d20ec305fcbc824a929459ff69a29c22b2ff34
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971276"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="b352a-102">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b352a-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="b352a-103">W C# 3,0 i nowszych właściwości, które są implementowane przez funkcję właściwości, są bardziej zwięzłe, gdy w metodzie dostępu do właściwości nie jest wymagana żadna dodatkowa logika.</span><span class="sxs-lookup"><span data-stu-id="b352a-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="b352a-104">Umożliwiają również tworzenie obiektów przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="b352a-104">They also enable client code to create objects.</span></span> <span data-ttu-id="b352a-105">W przypadku deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe pole zapasowe, do którego można uzyskać dostęp tylko za pomocą `get` i `set` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="b352a-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b352a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b352a-106">Example</span></span>  
 <span data-ttu-id="b352a-107">W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="b352a-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 <span data-ttu-id="b352a-108">W C# 6 i nowszych można inicjować właściwości zaimplementowane w sposób podobny do pól:</span><span class="sxs-lookup"><span data-stu-id="b352a-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="b352a-109">Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="b352a-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="b352a-110">Kod klienta może zmienić wartości w obiektach po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="b352a-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="b352a-111">W przypadku złożonych klas, które zawierają znaczące zachowanie (metody), jak również dane, często konieczne jest posiadanie właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="b352a-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="b352a-112">Jednakże w przypadku małych klas i struktur, które po prostu hermetyzują zestaw wartości (danych) i mają niewielkie lub bez zachowań, należy sprawić, aby obiekty były niezmienne poprzez zadeklarowanie metody dostępu do zestawu jako [prywatne](../../language-reference/keywords/private.md) (niezmiennych dla konsumentów) lub przez zadeklarowanie tylko Get Metoda dostępu (niezmiennej wszędzie poza konstruktorem).</span><span class="sxs-lookup"><span data-stu-id="b352a-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="b352a-113">Aby uzyskać więcej informacji, zobacz [jak zaimplementować klasę uproszczoną z właściwościami, które są implementowane](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b352a-113">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b352a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b352a-114">See also</span></span>

- [<span data-ttu-id="b352a-115">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b352a-115">Properties</span></span>](./properties.md)
- [<span data-ttu-id="b352a-116">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="b352a-116">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
