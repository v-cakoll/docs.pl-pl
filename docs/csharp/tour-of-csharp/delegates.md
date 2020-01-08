---
title: C#Delegaty — Przewodnik po C# języku
description: Uzyskaj późne powiązania C# z delegatami
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 317d3ee6fb1350824fa9b3b4d0e3e851780ce4d4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346869"
---
# <a name="delegates"></a>Delegaty

***Typ delegata*** reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach, ale w przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.

Poniższy przykład deklaruje i używa typu delegata o nazwie `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Wystąpienie typu delegata `Function` może odwoływać się do dowolnej metody, która przyjmuje argument `double` i zwraca wartość `double`. Metoda `Apply` stosuje daną funkcję do elementów `double[]`, zwracając `double[]` z wynikami. W metodzie `Main` `Apply` służy do zastosowania trzech różnych funkcji do `double[]`.

Delegat może odwoływać się do metody statycznej (takiej jak `Square` lub `Math.Sin` w poprzednim przykładzie) lub metody wystąpienia (takiej jak `m.Multiply` w poprzednim przykładzie). Delegat odwołujący się do metody instancji odwołuje się również do określonego obiektu i gdy wywoływana jest metoda wystąpienia za pomocą delegata, obiekt ten zostanie `this` w wywołaniu.

Delegatów można także tworzyć za pomocą funkcji anonimowych, które są "metodami wbudowanymi", które są tworzone na bieżąco. Funkcje anonimowe mogą zobaczyć zmienne lokalne otaczających metod. W ten sposób przykład mnożnika można napisać łatwiej, bez użycia klasy mnożnika:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Interesująca i przydatna właściwość delegata polega na tym, że nie wie ani nie posługuje się klasą metody, do której się odwołuje; wszystkie te kwestie polegają na tym, że metoda przywoływana ma te same parametry i zwracany typ jako delegat.

>[!div class="step-by-step"]
>[Poprzedni](interfaces.md)
>[Następny](attributes.md)
