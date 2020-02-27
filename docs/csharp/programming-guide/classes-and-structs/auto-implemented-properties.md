---
title: Zaimplementowane właściwości — C# Przewodnik programowania
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 989266bfc2de9bd5ce2948f09a2b9f19dd2c782e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628296"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="dde57-102">Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="dde57-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="dde57-103">W C# 3,0 i nowszych właściwości, które są implementowane przez funkcję właściwości, są bardziej zwięzłe, gdy w metodzie dostępu do właściwości nie jest wymagana żadna dodatkowa logika.</span><span class="sxs-lookup"><span data-stu-id="dde57-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="dde57-104">Umożliwiają również tworzenie obiektów przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="dde57-104">They also enable client code to create objects.</span></span> <span data-ttu-id="dde57-105">W przypadku deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe pole zapasowe, do którego można uzyskać dostęp tylko za pomocą `get` i `set` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="dde57-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="dde57-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="dde57-106">Example</span></span>

<span data-ttu-id="dde57-107">W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="dde57-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="dde57-108">Nie można zadeklarować właściwości, które są implementowane w interfejsach.</span><span class="sxs-lookup"><span data-stu-id="dde57-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="dde57-109">Wstępnie zaimplementowane właściwości deklarują pole kopii zapasowej wystąpienia prywatnego, a interfejsy nie mogą deklarować pól wystąpień.</span><span class="sxs-lookup"><span data-stu-id="dde57-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="dde57-110">Deklarowanie właściwości w interfejsie bez definiowania treści deklaruje właściwość z dostępem, które muszą być zaimplementowane przez każdy typ, który implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="dde57-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="dde57-111">W C# 6 i nowszych można inicjować właściwości zaimplementowane w sposób podobny do pól:</span><span class="sxs-lookup"><span data-stu-id="dde57-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
 
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
 
<span data-ttu-id="dde57-112">Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="dde57-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="dde57-113">Kod klienta może zmienić wartości w obiektach po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="dde57-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="dde57-114">W przypadku złożonych klas, które zawierają znaczące zachowanie (metody), jak również dane, często konieczne jest posiadanie właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="dde57-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="dde57-115">Jednakże w przypadku małych klas i struktur, które po prostu hermetyzują zestaw wartości (danych) i mają niewielkie lub nie zachowania, należy sprawić, aby obiekty były niezmienne poprzez zadeklarowanie metody dostępu do zestawu jako [prywatne](../../language-reference/keywords/private.md) (niezmiennych dla konsumentów) lub przez zadeklarowanie tylko metody dostępu get (niezmiennej wszędzie poza konstruktorem).</span><span class="sxs-lookup"><span data-stu-id="dde57-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="dde57-116">Aby uzyskać więcej informacji, zobacz [jak zaimplementować klasę uproszczoną z właściwościami, które są implementowane](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="dde57-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dde57-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dde57-117">See also</span></span>

- [<span data-ttu-id="dde57-118">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dde57-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="dde57-119">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="dde57-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
