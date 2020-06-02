---
title: Indeksatory w interfejsach — Przewodnik programowania w języku C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 9ce6e4f0e0533c2880c6241f44409435248a336a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287483"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indeksatory w interfejsach (Przewodnik programowania w języku C#)

Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md). Metody dostępu indeksatorów interfejsów różnią się od metod dostępu indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:

- Metody dostępu interfejsów nie używają modyfikatorów.
- Metoda dostępu do interfejsu zazwyczaj nie ma treści.

Celem metody dostępu jest wskazanie, czy indeksator jest tylko do odczytu i zapisu, tylko do odczytu lub tylko do zapisu. Możesz podać implementację indeksatora zdefiniowanego w interfejsie, ale jest to rzadkie. Indeksatory zwykle definiują interfejs API do uzyskiwania dostępu do pól danych, a pola danych nie mogą być zdefiniowane w interfejsie.

Oto przykład metody dostępu indeksatora interfejsu:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Podpis indeksatora musi różnić się od sygnatur wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zaimplementować indeksatory interfejsów.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

W powyższym przykładzie można użyć jawnej implementacji elementu członkowskiego interfejsu przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu. Na przykład:

```csharp
string IIndexInterface.this[int index]
{
}
```

Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora. Na przykład jeśli `Employee` Klasa implementuje dwa interfejsy, a `ICitizen` `IEmployee` oba interfejsy mają tę samą sygnaturę indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu. Oznacza to, że następująca deklaracja indeksatora:

```csharp
string IEmployee.this[int index]
{
}
```

implementuje indeksator w `IEmployee` interfejsie, podczas gdy następująca deklaracja:

```csharp
string ICitizen.this[int index]
{
}
```

implementuje indeksator w `ICitizen` interfejsie.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Indeksatory](./index.md)
- [Właściwości](../classes-and-structs/properties.md)
- [Interfejsy](../interfaces/index.md)
