---
title: C# Atrybuty — przewodnik po języku Języka C#
description: 'Dowiedz się więcej o programowaniu deklaratywnym przy użyciu atrybutów w języku C #'
ms.date: 02/27/2020
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: dc5b194c22fc2746ff8b0ab3e550e560a3666bbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159211"
---
# <a name="attributes"></a>Atrybuty

Typy, elementy członkowskie i inne jednostki w programie C# obsługują modyfikatory, które kontrolują niektóre aspekty ich zachowania. Na przykład dostępność metody jest kontrolowana `public`za `protected` `internal`pomocą `private` , , i modyfikatorów. C# generalizuje tę funkcję, tak aby zdefiniowane przez użytkownika typy informacji deklaratywnych można dołączyć do jednostek programu i pobrać w czasie wykonywania. Programy określają te dodatkowe informacje deklaratywne, definiując i używając ***atrybutów***.

W poniższym `HelpAttribute` przykładzie deklaruje atrybut, który można umieścić w jednostkach programu, aby zapewnić łącza do ich skojarzonej dokumentacji.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Wszystkie klasy atrybutów <xref:System.Attribute> pochodzą od klasy podstawowej dostarczonej przez bibliotekę standardową. Atrybuty mogą być stosowane przez podanie ich nazwy, wraz z dowolnymi argumentami, wewnątrz nawiasów kwadratowych tuż przed skojarzonej deklaracji. Jeśli nazwa atrybutu kończy `Attribute`się na , tej części nazwy można pominąć, gdy atrybut jest przywoływany. Na przykład `HelpAttribute` można użyć w następujący sposób.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

W tym przykładzie `HelpAttribute` dołącza `Widget` a do klasy. Dodaje inny `HelpAttribute` do `Display` metody w klasie. Konstruktory publiczne klasy atrybutu kontrolują informacje, które muszą być dostarczone, gdy atrybut jest dołączony do jednostki programu. Dodatkowe informacje można podać, odwołując się do publicznych właściwości odczytu i `Topic` zapisu klasy atrybutu (takie jak odwołanie do właściwości wcześniej).

Metadane zdefiniowane przez atrybuty mogą być odczytywane i manipulowane w czasie wykonywania przy użyciu odbicia. Gdy określony atrybut jest wymagane przy użyciu tej techniki, konstruktor dla klasy atrybutu jest wywoływana z informacji podanych w źródle programu, a wynikowy wystąpienie atrybutu jest zwracany. Jeśli dodatkowe informacje zostały dostarczone za pośrednictwem właściwości, te właściwości są ustawione na podane wartości przed wystąpieniem atrybutu jest zwracany.

Poniższy przykład owy pokazuje, jak `HelpAttribute` uzyskać wystąpienia `Widget` skojarzone `Display` z klasą i jej metodą.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Wstecz](delegates.md)
