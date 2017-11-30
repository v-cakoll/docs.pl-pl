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
# <a name="delegates"></a>Delegaty

A ***typ delegata*** reprezentuje odwołania do metody z określonego parametru listę i typ zwracany. Obiekty delegowane umożliwiają traktować jako jednostek, które można przypisywać do zmiennych i przekazywane jako parametry metody. Obiekty delegowane są podobne do koncepcji znaleziono w przypadku niektórych języków innych wskaźników funkcji, ale w przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowo i bezpieczne.

W poniższym przykładzie deklaruje i używa typu delegata o nazwie `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Wystąpienie `Function` typ delegowany może odwoływać się wszystkie metody pobierającej `double` argument i zwraca `double` wartość. `Apply` Metoda dotyczy elementów daną funkcję `double[]`, zwracająca `double[]` z wynikami. W `Main` metody `Apply` służy do stosowania trzy różne funkcje do `double[]`.

Delegat może odwoływać się statycznej metody (takie jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metodą wystąpienia (takich jak `m.Multiply` w poprzednim przykładzie). Delegata, który odwołuje się do metody wystąpienia odwołuje się również do określonego obiektu, a po wywołaniu metody wystąpienia za pośrednictwem pełnomocnika, staje się ten obiekt `this` w wywołaniu.

Obiekty delegowane można również tworzyć przy użyciu anonimowego funkcji, które są "wbudowanego metody", które są tworzone na bieżąco. Funkcje anonimowe można wyświetlić zmienne lokalne otaczającego metod. W związku z tym w powyższym przykładzie mnożnik mogą być zapisywane łatwiej bez użycia klasy mnożnik:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Właściwość interesujące i przydatne delegata jest że nie wiadomo lub interesujących klasy, metody, która odwołuje się do; wszystkie punkty, które ma znaczenie się, że metoda przywoływanego ma takie same parametry oraz zwracany typ jako pełnomocnik.

>[!div class="step-by-step"]
[Poprzednie](enums.md)
[dalej](attributes.md)
