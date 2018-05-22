---
title: C# atrybutów — samouczek języka C#
description: Dowiedz się więcej o deklaratywne programowania w języku C# przy użyciu atrybutów
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 671023f268ae78d63db8868ef6046b8f13880659
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
---
# <a name="attributes"></a>Atrybuty

Typy elementów członkowskich i inne jednostki w programie C# obsługuje modyfikatory, które kontrolować niektóre aspekty ich zachowanie. Na przykład dostępność metody jest kontrolowany przy użyciu `public`, `protected`, `internal`, i `private` modyfikatorów. C# uogólnia tę możliwość w taki sposób, że typy zdefiniowane przez użytkownika informacji, deklaratywne może być dołączony do programu jednostek i pobierane w czasie wykonywania. Programy Określ dodatkowe informacje deklaratywne przez definiowanie i użycie ***atrybutów***.

Poniższy przykład deklaruje `HelpAttribute` atrybut, który można umieścić na jednostkach program zapewnienie linki do dokumentacji skojarzone.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Wszystkie klasy atrybutu pochodzi od <xref:System.Attribute> pochodzącymi z biblioteki standardowej klasy podstawowej. Atrybuty można zastosować, zapewniając ich nazw, wraz z żadnych argumentów w nawiasach kwadratowych bezpośrednio przed deklaracją skojarzone. Jeśli nazwa atrybutu kończy się `Attribute`, gdy odwołuje się do atrybutu można pominąć części nazwy. Na przykład `HelpAttribute` można używać w następujący sposób.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

W tym przykładzie dołącza `HelpAttribute` do `Widget` klasy. Dodaje innego `HelpAttribute` do `Display` metody w klasie. Konstruktory publiczne klasy atrybutu kontrolować informacje, które należy podać, gdy atrybut jest dołączony do jednostki programu. Dodatkowe informacje może być udostępniane przez publicznego właściwości odczytu / zapisu z klasy atrybutów odwołania (np. odwołanie do `Topic` właściwości wcześniej).

Określonego atrybutu zleconą przez odbicie konstruktora dla klasy atrybutów jest wywoływana z informacji dostępnych w źródle programu, a wynikowy wystąpienie atrybutu jest zwracane. Jeśli dodatkowe informacje były udostępniane za pośrednictwem właściwości, te właściwości są ustawione na wartości danego przed zwróceniem wystąpienie atrybutu.

>[!div class="step-by-step"]
[Poprzednie](delegates.md)
