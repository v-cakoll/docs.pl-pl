---
title: C# atrybuty — Przewodnik po przykładzie w języku C#
description: Dowiedz się więcej o deklaratywne programowania w języku C# przy użyciu atrybutów
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 671023f268ae78d63db8868ef6046b8f13880659
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "34312238"
---
# <a name="attributes"></a>Atrybuty

Typy, członków i inne jednostki w programie C# obsługuje modyfikatory, które kontrolują niektóre aspekty swojego zachowania. Na przykład dostępność metody jest kontrolowany przy użyciu `public`, `protected`, `internal`, i `private` modyfikatorów. C# uogólnia tej możliwości w taki sposób, że typy zdefiniowane przez użytkownika deklaratywne informacji może być dołączony do programu jednostek i pobierane w czasie wykonywania. Programy Określ dodatkowe informacje deklaratywne przez definiowanie i korzystanie z ***atrybuty***.

Poniższy przykład deklaruje `HelpAttribute` atrybut, który można umieścić na program jednostki zawierają łącza do ich dokumentacji skojarzone.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Wszystkie klasy atrybutu pochodzić od <xref:System.Attribute> dostarczone przez standardową bibliotekę klasy bazowej. Atrybuty mogą być stosowane, zapewniając ich nazw, wraz z żadnych argumentów, w nawiasach kwadratowych tuż przed skojarzone deklaracji. Jeśli nazwa atrybutu, który kończy się na `Attribute`, gdy odwołuje się do atrybutu można pominąć tę część nazwy. Na przykład `HelpAttribute` może służyć w następujący sposób.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

W tym przykładzie dołącza `HelpAttribute` do `Widget` klasy. Dodaje, kolejny `HelpAttribute` do `Display` metody w klasie. Konstruktory publiczne klasy atrybutu kontrolować informacje, które należy podać, gdy atrybut jest dołączany do jednostki programu. Można podać dodatkowe informacje, odwołując się do właściwości publiczne odczytu / zapisu atrybutu klasy (np. odwołanie do `Topic` właściwość wcześniej).

Metadane zdefiniowane przez atrybuty może odczytywać i modyfikować w czasie wykonywania przy użyciu odbicia. Zleconą określonego atrybutu przy użyciu tej metody, Konstruktor dla klasy atrybutu jest wywoływana z informacji podanych w źródle programu, a wynikowy wystąpienie atrybutu jest zwracana. Dodatkowe informacje były udostępniane za pośrednictwem właściwości, te właściwości są ustawione na wartości podanej w przed zwróceniem wystąpienie atrybutu.

Poniższy przykład kodu pokazuje, jak uzyskać `HelpAttribute` wystąpień skojarzonej `Widget` klasy i jego `Display` metody.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
[Poprzednie](delegates.md)
