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
# <a name="delegates"></a>Delegaty

***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i typem zwracanym. Delegaci umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazywane jako parametry. Delegatów są podobne do pojęcia wskaźników funkcji znaleźć w niektórych innych językach. W przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowe i bezpieczne dla typu.

Poniższy przykład deklaruje i używa typu `Function`pełnomocnika o nazwie .

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Wystąpienie typu `Function` delegata może odwoływać się `double` do dowolnej `double` metody, która przyjmuje argument i zwraca wartość. Metoda `Apply` stosuje daną funkcję do elementów `double[]`, zwracając `double[]` a z wynikami. W `Main` metodzie `Apply` służy do stosowania trzech `double[]`różnych funkcji do .

Pełnomocnik może odwoływać się do metody `Square` `Math.Sin` statycznej (takiej jak lub w `m.Multiply` poprzednim przykładzie) lub metody wystąpienia (na przykład w poprzednim przykładzie). Delegat, który odwołuje się do metody wystąpienia odwołuje się również do określonego obiektu, a gdy `this` metoda wystąpienia jest wywoływana za pośrednictwem delegata, ten obiekt staje się w wywołaniu.

Delegatów można również utworzyć przy użyciu funkcji anonimowych, które są "wbudowanych metod", które są tworzone po zadeklarowaniu. Funkcje anonimowe mogą zobaczyć zmienne lokalne otaczających metod. Poniższy przykład nie tworzy klasy:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Delegat nie zna lub dba o klasę metody, do której się odwołuje; wszystko, co ma znaczenie jest to, że metoda odwołuje się ma te same parametry i typ zwracania jako delegata.

>[!div class="step-by-step"]
>[Poprzedni](interfaces.md)
>[następny](attributes.md)
