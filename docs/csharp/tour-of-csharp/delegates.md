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
# <a name="delegates"></a>Delegaty

***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach. W przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.

Poniższy przykład deklaruje i używa typu delegata o nazwie `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Wystąpienie typu delegata `Function` może odwoływać się do dowolnej metody, która przyjmuje argument `double` i zwraca wartość `double`. Metoda `Apply` stosuje daną funkcję do elementów `double[]`, zwracając `double[]` z wynikami. W metodzie `Main` `Apply` służy do zastosowania trzech różnych funkcji do `double[]`.

Delegat może odwoływać się do metody statycznej (takiej jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metody wystąpienia (takiej jak `m.Multiply` w poprzednim przykładzie). Delegat odwołujący się do metody instancji odwołuje się również do określonego obiektu i gdy wywoływana jest metoda wystąpienia za pomocą delegata, obiekt ten zostanie `this` w wywołaniu.

Delegatów można także tworzyć za pomocą funkcji anonimowych, które są "metodami wbudowanymi", które są tworzone podczas deklarowania. Funkcje anonimowe mogą zobaczyć zmienne lokalne otaczających metod. Poniższy przykład nie tworzy klasy:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Delegat nie wie ani nie posługuje się klasą metody, do której się odwołuje; wszystkie te kwestie polegają na tym, że metoda przywoływana ma te same parametry i zwracany typ jako delegat.

>[!div class="step-by-step"]
>[Poprzednie](interfaces.md)
>[dalej](attributes.md)
