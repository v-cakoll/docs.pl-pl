---
title: 'Instrukcje: Zablokuj więcej niż jedną wartość w zmiennej (Visual Basic)'
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
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054197"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Instrukcje: Zablokuj więcej niż jedną wartość w zmiennej (Visual Basic)

Zmienna zawiera więcej niż jedną wartość, jeśli deklaruje ją jako *złożony typ danych*.

[Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) obejmują struktury, tablice i klasy. Zmienna złożonego typu danych może zawierać kombinację podstawowych typów danych i innych typów złożonych. Struktury i klasy mogą przechowywać kod oraz dane.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Aby przechowywać więcej niż jedną wartość w zmiennej

1. Określ typ danych złożonych, który ma być używany dla zmiennej.

2. Jeśli złożony typ danych nie jest jeszcze zdefiniowany, zdefiniuj go tak, aby zmienna mogła z niego korzystać.

    - Zdefiniuj strukturę przy użyciu [instrukcji struktury](../../../../visual-basic/language-reference/statements/structure-statement.md).

    - Zdefiniuj tablicę z [instrukcją Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

    - Zdefiniuj klasę z [instrukcją klasy](../../../../visual-basic/language-reference/statements/class-statement.md).

3. Zadeklaruj zmienną za pomocą `Dim` instrukcji.

4. Postępuj według nazwy zmiennej z `As` klauzulą.

5. `As` Użyj słowa kluczowego z nazwą odpowiedniego złożonego typu danych.

## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
