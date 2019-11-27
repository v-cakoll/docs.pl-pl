---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351279"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Określa, że zmienna lub właściwość może być odczytana, ale nie zapisywana.

## <a name="remarks"></a>Uwagi

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** `ReadOnly` można używać tylko na poziomie modułu. Oznacza to, że kontekst deklaracji dla elementu `ReadOnly` musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.

- **Połączone modyfikatory.** Nie można określić `ReadOnly` razem z `Static` w tej samej deklaracji.

- **Przypisywanie wartości.** Kod zużywający Właściwość `ReadOnly` nie może ustawić jej wartości. Jednak kod, który ma dostęp do magazynu bazowego, może przypisywać lub zmieniać wartość w dowolnym momencie.

     Można przypisać wartość do zmiennej `ReadOnly` tylko w swojej deklaracji lub w konstruktorze klasy lub struktury, w której jest zdefiniowana.

## <a name="when-to-use-a-readonly-variable"></a>Kiedy używać zmiennej tylko do odczytu

Istnieją sytuacje, w których nie można użyć [instrukcji const](../../../visual-basic/language-reference/statements/const-statement.md) do zadeklarowania i przypisania wartości stałej. Na przykład instrukcja `Const` może nie akceptować typu danych, który chcesz przypisać, lub nie można obliczyć wartości w czasie kompilacji przy użyciu wyrażenia stałej. Wartość w czasie kompilacji może nie być jeszcze znana. W takich przypadkach można użyć zmiennej `ReadOnly` do przechowywania wartości stałej.

> [!IMPORTANT]
> Jeśli typ danych zmiennej jest typem referencyjnym, takim jak tablica lub wystąpienie klasy, jego elementy członkowskie można zmienić, nawet jeśli sama zmienna jest `ReadOnly`. Ilustruje to poniższy przykład.

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

Po zainicjowaniu tablica wskazywana przez `characterArray()` zawiera wartości "x", "y" i "z". Ponieważ zmienna `characterArray` jest `ReadOnly`, nie można zmienić jej wartości, gdy zostanie ona zainicjowana; oznacza to, że nie można przypisać do niej nowej tablicy. Można jednak zmienić wartości co najmniej jednego elementu członkowskiego tablicy. Po wywołaniu procedury `ChangeArrayElement`tablica wskazywana przez `characterArray()` zawiera "x", "M" i "z".

Należy zauważyć, że jest to podobne do deklarowania parametru procedury jako [ByVal](byval.md), co uniemożliwia procedury zmiany argumentu wywołującego, ale pozwala na zmianę jego elementów członkowskich.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano Właściwość `ReadOnly` dla daty zatrudnienia pracownika. Klasa przechowuje wartość właściwości wewnętrznie jako zmienną `Private`, a tylko kod wewnątrz klasy może zmienić tę wartość. Jednak właściwość jest `Public`, a każdy kod, który może uzyskać dostęp do klasy, może odczytać właściwość.

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

Modyfikator `ReadOnly` może być używany w tych kontekstach:

- [Dim, instrukcja](../statements/dim-statement.md)
- [Property, instrukcja](../statements/property-statement.md)

## <a name="see-also"></a>Zobacz także

- [WriteOnly](writeonly.md)
- [Słowa kluczowe](../keywords/index.md)
