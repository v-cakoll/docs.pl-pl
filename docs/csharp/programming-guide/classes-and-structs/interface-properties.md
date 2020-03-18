---
title: Właściwości interfejsu — przewodnik programowania C#
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626623"
---
# <a name="interface-properties-c-programming-guide"></a>Właściwości interfejsu (Przewodnik programowania w języku C#)

Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md). W poniższym przykładzie deklaruje akcesor właściwości interfejsu:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Właściwości interfejsu zazwyczaj nie mają treści. Akcesory wskazują, czy właściwość jest do odczytu i zapisu, tylko do odczytu lub tylko do zapisu. W przeciwieństwie do klas i struktur, deklarowanie akcesorów bez treści nie deklaruje [właściwości autoimplemented](auto-implemented-properties.md). Począwszy od języka C# 8.0, interfejs może zdefiniować implementację domyślną dla elementów członkowskich, w tym właściwości. Definiowanie domyślnej implementacji właściwości w interfejsie jest rzadkie, ponieważ interfejsy mogą nie definiować pól danych wystąpienia.

## <a name="example"></a>Przykład

W tym przykładzie `IEmployee` interfejs ma właściwość odczytu i zapisu `Name`, `Counter`i właściwości tylko do odczytu , . Klasa `Employee` implementuje `IEmployee` interfejs i używa tych dwóch właściwości. Program odczytuje nazwę nowego pracownika i bieżącą liczbę pracowników i wyświetla nazwisko pracownika i obliczony numer pracownika.

Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym element członkowski jest zadeklarowany. Przykład:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

W poprzednim przykładzie przedstawiono [implementację interfejsu jawnego](../interfaces/explicit-interface-implementation.md). Na przykład jeśli `Employee` klasa implementuje `ICitizen` dwa `IEmployee` interfejsy i `Name` oba interfejsy mają właściwość, implementacja elementu członkowskiego interfejsu jawnego będzie konieczne. Oznacza to, że następujące oświadczenie majątkowe:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

implementuje `Name` właściwość na `IEmployee` interfejsie, podczas gdy następująca deklaracja:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

implementuje `Name` właściwość na `ICitizen` interfejsie.

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

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Właściwości](./properties.md)
- [Używanie właściwości](./using-properties.md)
- [Porównanie właściwości i indeksatorów](../indexers/comparison-between-properties-and-indexers.md)
- [Indexers](../indexers/index.md) (Indeksatory)
- [Interfejsy](../interfaces/index.md)
