---
title: 'Instrukcje: Utrzymywanie więcej niż jednej wartości w zmiennej'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393899"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Porady: utrzymywanie więcej niż jednej wartości w zmiennej (Visual Basic)

Zmienna zawiera więcej niż jedną wartość, jeśli deklaruje ją jako *złożony typ danych*.

[Złożone typy danych](composite-data-types.md) obejmują struktury, tablice i klasy. Zmienna złożonego typu danych może zawierać kombinację podstawowych typów danych i innych typów złożonych. Struktury i klasy mogą przechowywać kod oraz dane.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Aby przechowywać więcej niż jedną wartość w zmiennej

1. Określ typ danych złożonych, który ma być używany dla zmiennej.

2. Jeśli złożony typ danych nie jest jeszcze zdefiniowany, zdefiniuj go tak, aby zmienna mogła z niego korzystać.

    - Zdefiniuj strukturę przy użyciu [instrukcji struktury](../../../language-reference/statements/structure-statement.md).

    - Zdefiniuj tablicę z [instrukcją Dim](../../../language-reference/statements/dim-statement.md).

    - Zdefiniuj klasę z [instrukcją klasy](../../../language-reference/statements/class-statement.md).

3. Zadeklaruj zmienną za pomocą `Dim` instrukcji.

4. Postępuj według nazwy zmiennej z `As` klauzulą.

5. Użyj `As` słowa kluczowego z nazwą odpowiedniego złożonego typu danych.

## <a name="see-also"></a>Zobacz też

- [Typy danych](../../../language-reference/data-types/index.md)
- [Znaki typu](type-characters.md)
- [Złożone typy danych](composite-data-types.md)
- [Struktury](structures.md)
- [Tablice](../arrays/index.md)
- [Obiekty i klasy](../objects-and-classes/index.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
