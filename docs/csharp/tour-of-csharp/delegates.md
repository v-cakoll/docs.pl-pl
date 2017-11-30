---
title: "C# delegatów — samouczek języka C#"
description: "Dowiedz się, późne powiązania z delegatów C#"
keywords: ".NET, csharp, delegat, lambda, późne wiązanie"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="949ee-104">Delegaty</span><span class="sxs-lookup"><span data-stu-id="949ee-104">Delegates</span></span>

<span data-ttu-id="949ee-105">A ***typ delegata*** reprezentuje odwołania do metody z określonego parametru listę i typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="949ee-105">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="949ee-106">Obiekty delegowane umożliwiają traktować jako jednostek, które można przypisywać do zmiennych i przekazywane jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="949ee-106">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="949ee-107">Obiekty delegowane są podobne do koncepcji znaleziono w przypadku niektórych języków innych wskaźników funkcji, ale w przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowo i bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="949ee-107">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="949ee-108">W poniższym przykładzie deklaruje i używa typu delegata o nazwie `Function`.</span><span class="sxs-lookup"><span data-stu-id="949ee-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="949ee-109">Wystąpienie `Function` typ delegowany może odwoływać się wszystkie metody pobierającej `double` argument i zwraca `double` wartość.</span><span class="sxs-lookup"><span data-stu-id="949ee-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="949ee-110">`Apply` Metoda dotyczy elementów daną funkcję `double[]`, zwracająca `double[]` z wynikami.</span><span class="sxs-lookup"><span data-stu-id="949ee-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="949ee-111">W `Main` metody `Apply` służy do stosowania trzy różne funkcje do `double[]`.</span><span class="sxs-lookup"><span data-stu-id="949ee-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="949ee-112">Delegat może odwoływać się statycznej metody (takie jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metodą wystąpienia (takich jak `m.Multiply` w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="949ee-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="949ee-113">Delegata, który odwołuje się do metody wystąpienia odwołuje się również do określonego obiektu, a po wywołaniu metody wystąpienia za pośrednictwem pełnomocnika, staje się ten obiekt `this` w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="949ee-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="949ee-114">Obiekty delegowane można również tworzyć przy użyciu anonimowego funkcji, które są "wbudowanego metody", które są tworzone na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="949ee-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="949ee-115">Funkcje anonimowe można wyświetlić zmienne lokalne otaczającego metod.</span><span class="sxs-lookup"><span data-stu-id="949ee-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="949ee-116">W związku z tym w powyższym przykładzie mnożnik mogą być zapisywane łatwiej bez użycia klasy mnożnik:</span><span class="sxs-lookup"><span data-stu-id="949ee-116">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="949ee-117">Właściwość interesujące i przydatne delegata jest że nie wiadomo lub interesujących klasy, metody, która odwołuje się do; wszystkie punkty, które ma znaczenie się, że metoda przywoływanego ma takie same parametry oraz zwracany typ jako pełnomocnik.</span><span class="sxs-lookup"><span data-stu-id="949ee-117">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="949ee-118">[Poprzednie](enums.md)
[dalej](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="949ee-118">[Previous](enums.md)
[Next](attributes.md)</span></span>
