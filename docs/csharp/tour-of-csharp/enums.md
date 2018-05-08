---
title: C# wyliczenia — samouczek języka C#
description: Dowiedz się więcej o wyliczenia, odrębny o nazwie stałe języka C#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 7fe2626381cb90e55842e3be17dd450eb73d5a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enums"></a>Wyliczenia

***Typu wyliczeniowego*** jest typem unikatowych wartości przy użyciu zestawu stałe nazwane. Typy wyliczeniowe należy zdefiniować, kiedy należy zdefiniować typu, który może mieć zestaw wartości dyskretnych. Używają jednego z typów całkowitych wartości jako ich powiązany magazyn. Udostępniają one semantycznego znaczenie wartości dyskretnych.

W poniższym przykładzie deklaruje i używa `enum` typu o nazwie `Color` z trzech wartości stałej, `Red`, `Green`, i `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Każdy `enum` typ ma odpowiedni typ całkowity o nazwie ***typ podstawowy*** z `enum` typu. `enum` Typu, który nie deklaruje jawnie typ podstawowy ma typ podstawowy elementu `int`. `enum` Typu formatu przechowywania i zakresu możliwych wartości są określane przez jego typem podstawowym. Zbiór wartości, które `enum` typu może zająć na nie jest ograniczona przez jego `enum` elementów członkowskich. W szczególności typ wartości podstawowych `enum` mogą być rzutowane na `enum` typu i jest prawidłową wartością różne tego `enum` typu.

Poniższy przykład deklaruje `enum` typu o nazwie `Alignment` z typem podstawowym typu `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Jak pokazano w poprzednim przykładzie `enum` deklaracji elementu członkowskiego mogą zawierać wyrażenie stałe, która określa wartość elementu członkowskiego. Wartość stała dla każdego `enum` element członkowski musi być w zakresie typ podstawowy elementu `enum`. Podczas `enum` deklaracji elementu członkowskiego nie jawnie określona wartość, element członkowski znajduje się wartość zero (jeśli pierwszego elementu członkowskiego w `enum` typu) lub wartość postaci tekstu poprzedniego `enum` elementu członkowskiego plus jeden.

`Enum` wartości mogą być przekonwertowane na całkowite wartości i na odwrót przy użyciu typu rzutowania. Na przykład:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

Wartość domyślna dowolnej `enum` typ jest integralną wartość zero przekonwertować `enum` typu. W przypadkach, gdy zmienne są inicjowane automatycznie wartość domyślna to wartość zmiennych `enum` typów. Aby wartość domyślną `enum` typu były łatwo dostępne, literał `0` niejawnie konwertuje wszelkie `enum` typu. W związku z tym następujące jest dozwolone.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
[Poprzednie](interfaces.md)
[dalej](delegates.md)
