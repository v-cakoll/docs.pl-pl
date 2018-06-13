---
title: C# delegatów — samouczek języka C#
description: Dowiedz się, późne powiązania z delegatów C#
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 1dcd078b275d951b049b0c5bb6e084a4083d042d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360573"
---
# <a name="delegates"></a><span data-ttu-id="dbc91-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="dbc91-103">Delegates</span></span>

<span data-ttu-id="dbc91-104">A ***typ delegata*** reprezentuje odwołania do metody z określonego parametru listę i typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="dbc91-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="dbc91-105">Obiekty delegowane umożliwiają traktować jako jednostek, które można przypisywać do zmiennych i przekazywane jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="dbc91-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="dbc91-106">Obiekty delegowane są podobne do koncepcji znaleziono w przypadku niektórych języków innych wskaźników funkcji, ale w przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowo i bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="dbc91-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="dbc91-107">W poniższym przykładzie deklaruje i używa typu delegata o nazwie `Function`.</span><span class="sxs-lookup"><span data-stu-id="dbc91-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="dbc91-108">Wystąpienie `Function` typ delegowany może odwoływać się wszystkie metody pobierającej `double` argument i zwraca `double` wartość.</span><span class="sxs-lookup"><span data-stu-id="dbc91-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="dbc91-109">`Apply` Metoda dotyczy elementów daną funkcję `double[]`, zwracająca `double[]` z wynikami.</span><span class="sxs-lookup"><span data-stu-id="dbc91-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="dbc91-110">W `Main` metody `Apply` służy do stosowania trzy różne funkcje do `double[]`.</span><span class="sxs-lookup"><span data-stu-id="dbc91-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="dbc91-111">Delegat może odwoływać się statycznej metody (takie jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metodą wystąpienia (takich jak `m.Multiply` w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="dbc91-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="dbc91-112">Delegata, który odwołuje się do metody wystąpienia odwołuje się również do określonego obiektu, a po wywołaniu metody wystąpienia za pośrednictwem pełnomocnika, staje się ten obiekt `this` w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="dbc91-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="dbc91-113">Obiekty delegowane można również tworzyć przy użyciu anonimowego funkcji, które są "wbudowanego metody", które są tworzone na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="dbc91-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="dbc91-114">Funkcje anonimowe można wyświetlić zmienne lokalne otaczającego metod.</span><span class="sxs-lookup"><span data-stu-id="dbc91-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="dbc91-115">W związku z tym w powyższym przykładzie mnożnik mogą być zapisywane łatwiej bez użycia klasy mnożnik:</span><span class="sxs-lookup"><span data-stu-id="dbc91-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="dbc91-116">Właściwość interesujące i przydatne delegata jest że nie wiadomo lub interesujących klasy, metody, która odwołuje się do; wszystkie punkty, które ma znaczenie się, że metoda przywoływanego ma takie same parametry oraz zwracany typ jako pełnomocnik.</span><span class="sxs-lookup"><span data-stu-id="dbc91-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="dbc91-117">[Poprzednie](enums.md)
[dalej](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="dbc91-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
