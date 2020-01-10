---
title: Właściwości interfejsu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: ff892a35f4be6600c00bc0c72c2f789ef6eb4408
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705538"
---
# <a name="interface-properties-c-programming-guide"></a>Właściwości interfejsu (Przewodnik programowania w języku C#)

Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md). Oto przykład metody dostępu do właściwości interfejsu:

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

Metoda dostępu do właściwości interfejsu nie ma treści. W tym celu metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.

## <a name="example"></a>Przykład

W tym przykładzie interfejs `IEmployee` ma właściwość do odczytu i zapisu, `Name`i właściwość tylko do odczytu, `Counter`. Klasa `Employee` implementuje interfejs `IEmployee` i używa tych dwóch właściwości. Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.

Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski. Na przykład:

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

Ta nazwa jest nazywana [jawnym implementacją interfejsu](../interfaces/explicit-interface-implementation.md). Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i oba interfejsy mają właściwość `Name`, wymagana jest Jawna implementacja elementów członkowskich interfejsu. Oznacza to, że następująca deklaracja właściwości:

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

implementuje Właściwość `Name` w interfejsie `IEmployee`, podczas gdy następująca deklaracja:

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

implementuje Właściwość `Name` w interfejsie `ICitizen`.

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

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
- [Indeksatory](../indexers/index.md)
- [Interfejsy](../interfaces/index.md)
