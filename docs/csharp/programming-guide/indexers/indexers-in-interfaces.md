---
title: Indeksatory w interfejsach — przewodnik programowania C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627841"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indeksatory w interfejsach (Przewodnik programowania w języku C#)

Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md). Akcesory indeksatorów interfejsu różnią się od akcesorów indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:

- Akcesory interfejsu nie używają modyfikatorów.
- Akcesor interfejsu zazwyczaj nie ma treści.

Celem akcesora jest wskazanie, czy indeksator jest zapisu do odczytu, tylko do odczytu lub tylko do zapisu. Można podać implementację dla indeksatora zdefiniowane w interfejsie, ale jest to rzadkie. Indeksatory zazwyczaj definiują interfejs API, aby uzyskać dostęp do pól danych, a pola danych nie mogą być zdefiniowane w interfejsie.

Poniżej przedstawiono przykład akcesora indeksatora interfejsu:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Podpis indeksatora musi różnić się od podpisów wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak zaimplementować indeksatory interfejsu.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

W poprzednim przykładzie można użyć implementacji elementu członkowskiego interfejsu jawnego przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu. Na przykład:

```csharp
string IIndexInterface.this[int index]
{
}
```

Jednak w pełni kwalifikowana nazwa jest potrzebna tylko w celu uniknięcia niejednoznaczności, gdy klasa implementuje więcej niż jeden interfejs z tym samym podpisem indeksatora. Na przykład jeśli `Employee` klasa implementuje dwa `ICitizen` `IEmployee`interfejsy i , i oba interfejsy mają ten sam podpis indeksatora, implementacja elementu członkowskiego interfejsu jawnego jest konieczne. Oznacza to, że następująca deklaracja indeksatora:

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

implementuje indeksatora `ICitizen` w interfejsie.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Indexers](./index.md) (Indeksatory)
- [Właściwości](../classes-and-structs/properties.md)
- [Interfejsy](../interfaces/index.md)
