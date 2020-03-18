---
title: Delegatów języka C# — przewodnik po języku Języka C#
description: Dowiedz się późne wiązanie z delegatów Języka C#
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159172"
---
# <a name="delegates"></a><span data-ttu-id="ea68e-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="ea68e-103">Delegates</span></span>

<span data-ttu-id="ea68e-104">***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i typem zwracanym.</span><span class="sxs-lookup"><span data-stu-id="ea68e-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="ea68e-105">Delegaci umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazywane jako parametry.</span><span class="sxs-lookup"><span data-stu-id="ea68e-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="ea68e-106">Delegatów są podobne do pojęcia wskaźników funkcji znaleźć w niektórych innych językach.</span><span class="sxs-lookup"><span data-stu-id="ea68e-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="ea68e-107">W przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowe i bezpieczne dla typu.</span><span class="sxs-lookup"><span data-stu-id="ea68e-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="ea68e-108">Poniższy przykład deklaruje i używa typu `Function`pełnomocnika o nazwie .</span><span class="sxs-lookup"><span data-stu-id="ea68e-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="ea68e-109">Wystąpienie typu `Function` delegata może odwoływać się `double` do dowolnej `double` metody, która przyjmuje argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="ea68e-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="ea68e-110">Metoda `Apply` stosuje daną funkcję do elementów `double[]`, zwracając `double[]` a z wynikami.</span><span class="sxs-lookup"><span data-stu-id="ea68e-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="ea68e-111">W `Main` metodzie `Apply` służy do stosowania trzech `double[]`różnych funkcji do .</span><span class="sxs-lookup"><span data-stu-id="ea68e-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="ea68e-112">Pełnomocnik może odwoływać się do metody `Square` `Math.Sin` statycznej (takiej jak lub w `m.Multiply` poprzednim przykładzie) lub metody wystąpienia (na przykład w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="ea68e-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="ea68e-113">Delegat, który odwołuje się do metody wystąpienia odwołuje się również do określonego obiektu, a gdy `this` metoda wystąpienia jest wywoływana za pośrednictwem delegata, ten obiekt staje się w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="ea68e-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="ea68e-114">Delegatów można również utworzyć przy użyciu funkcji anonimowych, które są "wbudowanych metod", które są tworzone po zadeklarowaniu.</span><span class="sxs-lookup"><span data-stu-id="ea68e-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="ea68e-115">Funkcje anonimowe mogą zobaczyć zmienne lokalne otaczających metod.</span><span class="sxs-lookup"><span data-stu-id="ea68e-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="ea68e-116">Poniższy przykład nie tworzy klasy:</span><span class="sxs-lookup"><span data-stu-id="ea68e-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="ea68e-117">Delegat nie zna lub dba o klasę metody, do której się odwołuje; wszystko, co ma znaczenie jest to, że metoda odwołuje się ma te same parametry i typ zwracania jako delegata.</span><span class="sxs-lookup"><span data-stu-id="ea68e-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ea68e-118">[Poprzedni](interfaces.md)
>[następny](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="ea68e-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
