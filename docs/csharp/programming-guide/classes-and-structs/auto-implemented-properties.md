---
title: Właściwości zaimplementowane przez implementację — Przewodnik programowania w języku C#
description: Dla właściwości automatycznie zaimplementowane w języku C#, zgodność tworzy prywatne, anonimowe pole umożliwiające dostęp tylko za pomocą metody dostępu get i set właściwości.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: f58f9a23f26bde7e80d834528d94e38af1231e7b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474478"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="86f2e-103">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="86f2e-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="86f2e-104">W języku C# 3,0 i nowszych właściwości, które są implementowane przez implementację właściwości, są bardziej zwięzłe, gdy w metodzie dostępu do właściwości nie jest wymagana żadna dodatkowa logika.</span><span class="sxs-lookup"><span data-stu-id="86f2e-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="86f2e-105">Umożliwiają również tworzenie obiektów przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="86f2e-105">They also enable client code to create objects.</span></span> <span data-ttu-id="86f2e-106">W przypadku deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe pole zapasowe, do którego można uzyskać dostęp tylko za pomocą właściwości `get` i `set` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="86f2e-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="86f2e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="86f2e-107">Example</span></span>

<span data-ttu-id="86f2e-108">W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="86f2e-108">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="86f2e-109">Nie można zadeklarować właściwości, które są implementowane w interfejsach.</span><span class="sxs-lookup"><span data-stu-id="86f2e-109">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="86f2e-110">Wstępnie zaimplementowane właściwości deklarują pole kopii zapasowej wystąpienia prywatnego, a interfejsy nie mogą deklarować pól wystąpień.</span><span class="sxs-lookup"><span data-stu-id="86f2e-110">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="86f2e-111">Deklarowanie właściwości w interfejsie bez definiowania treści deklaruje właściwość z dostępem, które muszą być zaimplementowane przez każdy typ, który implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="86f2e-111">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="86f2e-112">W języku C# 6 i nowszych można inicjować właściwości, które zostały zaimplementowane w podobny sposób do pól:</span><span class="sxs-lookup"><span data-stu-id="86f2e-112">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="86f2e-113">Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="86f2e-113">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="86f2e-114">Kod klienta może zmienić wartości w obiektach po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="86f2e-114">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="86f2e-115">W przypadku złożonych klas, które zawierają znaczące zachowanie (metody), jak również dane, często konieczne jest posiadanie właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="86f2e-115">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="86f2e-116">Jednakże w przypadku małych klas i struktur, które po prostu hermetyzują zestaw wartości (danych) i mają niewielkie lub nie zachowania, należy sprawić, aby obiekty były niezmienne poprzez zadeklarowanie metody dostępu do zestawu jako [prywatne](../../language-reference/keywords/private.md) (niezmiennych dla konsumentów) lub przez zadeklarowanie tylko metody dostępu get (niezmiennej wszędzie poza konstruktorem).</span><span class="sxs-lookup"><span data-stu-id="86f2e-116">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="86f2e-117">Aby uzyskać więcej informacji, zobacz [jak zaimplementować klasę uproszczoną z właściwościami, które są implementowane](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="86f2e-117">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86f2e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86f2e-118">See also</span></span>

- [<span data-ttu-id="86f2e-119">Właściwości</span><span class="sxs-lookup"><span data-stu-id="86f2e-119">Properties</span></span>](./properties.md)
- [<span data-ttu-id="86f2e-120">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="86f2e-120">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
