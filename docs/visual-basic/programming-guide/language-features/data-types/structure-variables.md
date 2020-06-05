---
title: Zmienne struktur
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393588"
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
> W klasach i modułach struktury zadeklarowane przy użyciu [instrukcji Dim](../../../language-reference/statements/dim-statement.md) są domyślne dla dostępu publicznego. Jeśli zamierzasz mieć prywatną strukturę, upewnij się, że deklarujesz ją przy użyciu [prywatnego](../../../language-reference/modifiers/private.md) słowa kluczowego.

## <a name="access-to-structure-values"></a>Dostęp do wartości struktury

Aby przypisać i pobrać wartości z elementów zmiennej struktury, należy użyć tej samej składni, która jest używana do ustawiania i pobierania właściwości obiektu. Należy umieścić operator dostępu do składowej ( `.` ) między nazwą zmiennej struktury i nazwą elementu. Poniższy przykład uzyskuje dostęp do elementów zmiennych zadeklarowanych wcześniej jako typ `systemInfo` .

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

Jeśli element struktury jest typem referencyjnym, takim jak `String` , `Object` , lub tablicą, wskaźnik do danych jest kopiowany. W poprzednim przykładzie, jeśli zawierała `systemInfo` zmienną obiektu, poprzedni przykład skopiował wskaźnik z `mySystem` do `yourSystem` , a zmiana danych obiektu za pomocą jednej struktury będzie obowiązywać w przypadku uzyskania dostępu za pośrednictwem innej struktury.

## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Typy danych podstawowych](elementary-data-types.md)
- [Złożone typy danych](composite-data-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Instrukcje: Deklarowanie struktury](how-to-declare-a-structure.md)
- [Struktury oraz inne elementy programowania](structures-and-other-programming-elements.md)
- [Struktury i klasy](structures-and-classes.md)
- [Structure — Instrukcja](../../../language-reference/statements/structure-statement.md)
