---
title: Implementacja interfejsu jawnego — przewodnik programowania języka C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167676"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)

Jeśli [klasa](../../language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski z tym samym podpisem, a następnie implementacji tego elementu członkowskiego w klasie spowoduje, że oba interfejsy do użycia tego elementu członkowskiego jako ich implementacji. W poniższym przykładzie wszystkie `Paint` wywołania tej samej metody. Ten pierwszy przykład definiuje typy:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Poniższy przykład wywołuje metody:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Gdy dwa elementy członkowskie interfejsu nie wykonują tej samej funkcji, prowadzi do niepoprawnej implementacji jednego lub obu interfejsów. Istnieje możliwość zaimplementowania elementu członkowskiego interfejsu jawnie — tworzenie elementu członkowskiego klasy, który jest wywoływany tylko za pośrednictwem interfejsu i jest specyficzne dla tego interfejsu. Nazwij element członkowski klasy nazwą interfejsu i kropką. Przykład:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Element `IControl.Paint` członkowski klasy `IControl` jest dostępny `ISurface.Paint` tylko za `ISurface`pośrednictwem interfejsu i jest dostępny tylko za pośrednictwem . Obie implementacje metody są oddzielne i nie są dostępne bezpośrednio w klasie. Przykład:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Implementacja jawna jest również używany do rozwiązywania przypadków, w których dwa interfejsy każdy deklarują różne elementy członkowskie o tej samej nazwie, takich jak właściwość i metoda. Aby zaimplementować oba interfejsy, klasa musi używać `P`jawnej `P`implementacji dla właściwości lub metody lub obu, aby uniknąć błędu kompilatora. Przykład:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Począwszy od [języka C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), można zdefiniować implementację dla elementów członkowskich zadeklarowanych w interfejsie. Jeśli klasa dziedziczy implementacji metody z interfejsu, ta metoda jest dostępna tylko za pośrednictwem odwołania typu interfejsu. Dziedziczony element członkowski nie jest wyświetlany jako część interfejsu publicznego. Poniższy przykład definiuje domyślną implementację dla metody interfejsu:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Poniższy przykład wywołuje domyślną implementację:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Każda klasa, która `IControl` implementuje interfejs `Paint` można zastąpić metodę domyślną, jako metodę publiczną lub jako implementacja interfejsu jawnego.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
