---
title: Indeksatory w interfejsach C# — Przewodnik programowania
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627841"
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

W powyższym przykładzie można użyć jawnej implementacji elementu członkowskiego interfejsu przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu. Na przykład

```csharp
string IIndexInterface.this[int index]
{
}
```

Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora. Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy, `ICitizen` i `IEmployee`, a oba interfejsy mają ten sam podpis indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu. Oznacza to, że następująca deklaracja indeksatora:

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

implementuje indeksator w interfejsie `ICitizen`.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Indexers](./index.md) (Indeksatory)
- [Właściwości](../classes-and-structs/properties.md)
- [Interfejsy](../interfaces/index.md)
