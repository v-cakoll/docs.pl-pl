---
title: Zmienne struktur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: a86a60def9ac1b8140194ecb6f5e784c62a0e101
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630970"
---
# <a name="structure-variables-visual-basic"></a>Zmienne struktur (Visual Basic)

Po utworzeniu struktury można zadeklarować zmienne poziomu procedury i na poziomie modułu jako ten typ. Można na przykład utworzyć strukturę, która rejestruje informacje o systemie komputerowym. Poniższy przykład ilustruje to.

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

Można teraz zadeklarować zmienne tego typu. Ilustruje to poniższą deklarację.

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> W klasach i modułach struktury zadeklarowane przy użyciu [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) są domyślne dla dostępu publicznego. Jeśli zamierzasz mieć prywatną strukturę, upewnij się, że deklarujesz ją przy użyciu [prywatnego](../../../../visual-basic/language-reference/modifiers/private.md) słowa kluczowego.

## <a name="access-to-structure-values"></a>Dostęp do wartości struktury

Aby przypisać i pobrać wartości z elementów zmiennej struktury, należy użyć tej samej składni, która jest używana do ustawiania i pobierania właściwości obiektu. Należy umieścić operator dostępu do składowej`.`() między nazwą zmiennej struktury i nazwą elementu. Poniższy przykład uzyskuje dostęp do elementów zmiennych zadeklarowanych wcześniej jako typ `systemInfo`.

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>Przypisywanie zmiennych struktury

Można również przypisać jedną zmienną do innej, jeśli oba są tego samego typu struktury. Spowoduje to skopiowanie wszystkich elementów jednej struktury do odpowiednich elementów w drugim. Ilustruje to poniższą deklarację.

```vb
yourSystem = mySystem
```

Jeśli element struktury jest typem referencyjnym, takim jak `String`, `Object`, lub tablicą, wskaźnik do danych jest kopiowany. W poprzednim przykładzie, jeśli `systemInfo` zawierała zmienną obiektu, poprzedni przykład skopiował wskaźnik z `mySystem` do `yourSystem`, a zmiana danych obiektu za pomocą jednej struktury będzie obowiązywać, gdy zostanie uzyskany dostęp za pomocą innej struktury.

## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
