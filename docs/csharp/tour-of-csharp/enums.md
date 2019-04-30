---
title: C#Typy wyliczeniowe — Przewodnik po przykładzie C# języka
description: Dowiedz się więcej na temat typów wyliczeń, odrębny o nazwie stałych wC#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706354"
---
# <a name="enums"></a>Wyliczenia

***Typu wyliczeniowego*** jest typem wartości odrębnych z szeregu nazwanych stałych. Należy zdefiniować typy wyliczeniowe, gdy trzeba zdefiniować typ, który może mieć zestaw wartości dyskretnych. Używają jednego z typów całkowitych wartości jako swojego podstawowego magazynu. Zapewniają one znaczenia semantycznego dyskretnych wartości.

Poniższy przykład deklaruje i wykorzystuje `enum` typu o nazwie `Color` z trzech wartości stałych, `Red`, `Green`, i `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Każdy `enum` typ ma odpowiedni typ całkowity, o nazwie ***typ bazowy*** z `enum` typu. `enum` Typ, który jawnie deklaruj typu podstawowego jest podstawowym typem `int`. `enum` Typu formatu przechowywania i zakres możliwych wartości są określane przez jej typ podstawowy. Zbiór wartości, które `enum` typu można wykonać na nie jest ograniczone przez jego `enum` elementów członkowskich. W szczególności wszelkich wartości elementu bazowego typu `enum` mogą być rzutowane na `enum` typu i jest prawidłową wartością distinct tego `enum` typu.

Poniższy przykład deklaruje `enum` typu o nazwie `Alignment` z podstawowym typem `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Jak pokazano w poprzednim przykładzie `enum` deklaracji składowej może zawierać wyrażenie stałe, które określa wartość elementu członkowskiego. Stała wartość dla każdego `enum` elementu członkowskiego musi należeć do zakresu podstawowym typem `enum`. Podczas `enum` deklaracji składowej bez określenia wartości, element członkowski jest podana wartość zero (jeśli jest pierwszym elementem w `enum` typu) lub wartość poprzedniego formie tekstu `enum` elementu członkowskiego, plus jeden.

`Enum` wartości mogą być przekonwertowane do całkowitej wartości i odwrotnie przy użyciu typu rzutowania. Na przykład:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

Wartość domyślna dowolnej `enum` typ jest wartością typu całkowitego konwertowane na wartość zero `enum` typu. W przypadkach, gdy zmienne są automatycznie inicjowane na wartość domyślną, jest to wartość do zmiennych `enum` typów. Aby wartość domyślną `enum` typ były łatwo dostępne, literał `0` niejawnie konwertuje do dowolnego `enum` typu. W związku z tym że jest dozwolone.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> [Poprzednie](interfaces.md)
> [dalej](delegates.md)
