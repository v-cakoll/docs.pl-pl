---
title: C#Delegaty — Przewodnik po przykładzie C# języka
description: Dowiedz się, późne powiązania z C# delegatów
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 2744f774392ef021974535de535b063264ae9a54
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151281"
---
# <a name="delegates"></a><span data-ttu-id="825aa-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="825aa-103">Delegates</span></span>

<span data-ttu-id="825aa-104">A ***typ delegowany*** reprezentuje odwołania do metod z określonego parametru listy i typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="825aa-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="825aa-105">Delegatów można umożliwić traktować metod jako jednostki, które mogą być przypisane do zmiennych i przekazywane jako parametry.</span><span class="sxs-lookup"><span data-stu-id="825aa-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="825aa-106">Delegaty są podobne do koncepcji wskaźników funkcji, w przeciwieństwie do innych języków, ale w przeciwieństwie do wskaźników funkcji, obiekty delegowane są zorientowane obiektowo i bezpieczny typowo.</span><span class="sxs-lookup"><span data-stu-id="825aa-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="825aa-107">Poniższy przykład deklaruje i wykorzystuje typ delegata, o nazwie `Function`.</span><span class="sxs-lookup"><span data-stu-id="825aa-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="825aa-108">Wystąpienie `Function` typ delegata można odwoływać się do dowolnej metody, która przyjmuje `double` argument i zwraca `double` wartość.</span><span class="sxs-lookup"><span data-stu-id="825aa-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="825aa-109">`Apply` Metodę stosuje się daną funkcję do elementów `double[]`, zwracanie `double[]` z wynikami.</span><span class="sxs-lookup"><span data-stu-id="825aa-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="825aa-110">W `Main` metody `Apply` służy do trzech różnych funkcji w celu stosowania `double[]`.</span><span class="sxs-lookup"><span data-stu-id="825aa-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="825aa-111">Delegat może odwoływać się statycznej metody (takie jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metodą wystąpienia (takie jak `m.Multiply` w poprzednim przykładzie).</span><span class="sxs-lookup"><span data-stu-id="825aa-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="825aa-112">Delegat, który odwołuje się do metody wystąpienia odwołuje się konkretny obiekt, a gdy wywoływana jest metoda wystąpienia, za pośrednictwem delegata, staje się ten obiekt `this` w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="825aa-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="825aa-113">Delegatów można także tworzyć, używając funkcji anonimowych, które są "wbudowane metody", które są tworzone na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="825aa-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="825aa-114">Funkcje anonimowe można zobaczyć zmienne lokalne otaczającym metody.</span><span class="sxs-lookup"><span data-stu-id="825aa-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="825aa-115">Zatem w powyższym przykładzie mnożnik mogą być zapisywane łatwiej bez korzystania z klasy mnożnik:</span><span class="sxs-lookup"><span data-stu-id="825aa-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="825aa-116">Interesujące i przydatne własności delegata jest, nie wiedzieć, i nie interesuje klasy, metody, która odwołuje się do; wszystko, co dla Ciebie ważne jest, do którego istnieje odwołanie metoda ma te same parametry oraz zwracany typ jak delegat.</span><span class="sxs-lookup"><span data-stu-id="825aa-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="825aa-117">[Poprzednie](enums.md)
>[dalej](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="825aa-117">[Previous](enums.md)
[Next](attributes.md)</span></span>