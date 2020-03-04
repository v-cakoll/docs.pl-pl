---
title: C#Delegaty — Przewodnik po C# języku
description: Uzyskaj późne powiązania C# z delegatami
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159172"
---
# <a name="delegates"></a><span data-ttu-id="a3807-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="a3807-103">Delegates</span></span>

<span data-ttu-id="a3807-104">***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem.</span><span class="sxs-lookup"><span data-stu-id="a3807-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="a3807-105">Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry.</span><span class="sxs-lookup"><span data-stu-id="a3807-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="a3807-106">Delegaty są podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach.</span><span class="sxs-lookup"><span data-stu-id="a3807-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="a3807-107">W przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.</span><span class="sxs-lookup"><span data-stu-id="a3807-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="a3807-108">Poniższy przykład deklaruje i używa typu delegata o nazwie `Function`.</span><span class="sxs-lookup"><span data-stu-id="a3807-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="a3807-109">Wystąpienie typu delegata `Function` może odwoływać się do dowolnej metody, która przyjmuje argument `double` i zwraca wartość `double`.</span><span class="sxs-lookup"><span data-stu-id="a3807-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="a3807-110">Metoda `Apply` stosuje daną funkcję do elementów `double[]`, zwracając `double[]` z wynikami.</span><span class="sxs-lookup"><span data-stu-id="a3807-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="a3807-111">W metodzie `Main` `Apply` służy do zastosowania trzech różnych funkcji do `double[]`.</span><span class="sxs-lookup"><span data-stu-id="a3807-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="a3807-112">Delegat może odwoływać się do metody statycznej (takiej jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metody wystąpienia (takiej jak `m.Multiply` w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="a3807-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="a3807-113">Delegat odwołujący się do metody instancji odwołuje się również do określonego obiektu i gdy wywoływana jest metoda wystąpienia za pomocą delegata, obiekt ten zostanie `this` w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a3807-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="a3807-114">Delegatów można także tworzyć za pomocą funkcji anonimowych, które są "metodami wbudowanymi", które są tworzone podczas deklarowania.</span><span class="sxs-lookup"><span data-stu-id="a3807-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="a3807-115">Funkcje anonimowe mogą zobaczyć zmienne lokalne otaczających metod.</span><span class="sxs-lookup"><span data-stu-id="a3807-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="a3807-116">Poniższy przykład nie tworzy klasy:</span><span class="sxs-lookup"><span data-stu-id="a3807-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="a3807-117">Delegat nie wie ani nie posługuje się klasą metody, do której się odwołuje; wszystkie te kwestie polegają na tym, że metoda przywoływana ma te same parametry i zwracany typ jako delegat.</span><span class="sxs-lookup"><span data-stu-id="a3807-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a3807-118">[Poprzednie](interfaces.md)
>[dalej](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="a3807-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
