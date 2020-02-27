---
title: Implementacja interfejsu jawnego C# — Przewodnik programowania
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628153"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)

Jeśli [Klasa](../../language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski o tym samym podpisie, a następnie wdrożenie tego elementu członkowskiego w klasie spowoduje, że oba interfejsy używają tego elementu członkowskiego jako ich implementacji. W poniższym przykładzie wszystkie wywołania do `Paint` wywołują tę samą metodę. Ten pierwszy przykład definiuje typy:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Poniższy przykład wywołuje metody:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Gdy dwa elementy członkowskie interfejsu nie wykonują tej samej funkcji, prowadzi do niepoprawnej implementacji jednego lub obu interfejsów. Istnieje możliwość jawnej implementacji elementu członkowskiego interfejsu — tworzenie składowej klasy, która jest wywoływana tylko przez interfejs i jest specyficzna dla tego interfejsu. Nazwij element członkowski klasy przy użyciu nazwy interfejsu i kropki. Na przykład:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

`IControl.Paint` elementu członkowskiego klasy jest dostępna tylko za pomocą interfejsu `IControl`, a `ISurface.Paint` jest dostępny tylko za pomocą `ISurface`. Obie implementacje metod są oddzielne i nie są dostępne bezpośrednio w klasie. Na przykład:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Jawna implementacja służy również do rozwiązywania przypadków, gdy dwa interfejsy deklarują różne elementy członkowskie o tej samej nazwie, takie jak właściwość i metoda. Aby zaimplementować oba interfejsy, Klasa musi używać jawnej implementacji dla właściwości `P`lub metody `P`lub obu, aby uniknąć błędu kompilatora. Na przykład:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Jeśli klasa dziedziczy implementację metody z interfejsu, ta metoda jest dostępna tylko za pośrednictwem typu interfejsu. Dziedziczony element członkowski nie jest wyświetlany jako część interfejsu publicznego. Poniższy przykład definiuje domyślną implementację metody interfejsu:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Poniższy przykład wywołuje domyślną implementację:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Każda klasa implementująca interfejs `IControl` może przesłonić domyślną metodę `Paint`, jako metodę publiczną lub jako jawną implementację interfejsu.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
