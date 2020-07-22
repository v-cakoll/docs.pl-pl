---
title: Właściwości interfejsu — Przewodnik programowania w języku C#
description: Właściwości mogą być deklarowane w interfejsie w języku C#. Ten przykład deklaruje metodę dostępu do właściwości interfejsu.
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864972"
---
# <a name="interface-properties-c-programming-guide"></a>Właściwości interfejsu (Przewodnik programowania w języku C#)

Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md). Poniższy przykład deklaruje metodę dostępu do właściwości interfejsu:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Właściwości interfejsu zazwyczaj nie mają treści. Metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu lub tylko do zapisu. W przeciwieństwie do klas i struktur, deklarując metody dostępu bez treści nie deklaruje właściwości, która jest [implementowana](auto-implemented-properties.md). Począwszy od języka C# 8,0, interfejs może definiować domyślną implementację elementów członkowskich, w tym właściwości. Definiowanie domyślnej implementacji właściwości w interfejsie jest rzadkie, ponieważ interfejsy nie mogą definiować pól danych wystąpienia.

## <a name="example"></a>Przykład

W tym przykładzie interfejs `IEmployee` ma właściwość do odczytu i zapisu `Name` oraz właściwość tylko do odczytu `Counter` . Klasa `Employee` implementuje `IEmployee` interfejs i używa tych dwóch właściwości. Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.

Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski. Na przykład:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

W powyższym przykładzie przedstawiono [jawną implementację interfejsu](../interfaces/explicit-interface-implementation.md). Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` oba interfejsy mają `Name` Właściwość, wymagana jest Jawna implementacja elementu członkowskiego interfejsu. Oznacza to, że następująca deklaracja właściwości:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

implementuje `Name` Właściwość w `IEmployee` interfejsie, podczas gdy następująca deklaracja:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

implementuje `Name` Właściwość w `ICitizen` interfejsie.

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Używanie właściwości](./using-properties.md)
- [Porównanie właściwości i indeksatorów](../indexers/comparison-between-properties-and-indexers.md)
- [Indexers (Indeksatory)](../indexers/index.md)
- [Interfejsy](../interfaces/index.md)
