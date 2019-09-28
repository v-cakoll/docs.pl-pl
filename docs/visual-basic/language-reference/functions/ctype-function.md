---
title: CType — Funkcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592098"
---
# <a name="ctype-function-visual-basic"></a>CType — Funkcja (Visual Basic)

Zwraca wynik jawnej konwersji wyrażenia do określonego typu danych, obiektu, struktury, klasy lub interfejsu.

## <a name="syntax"></a>Składnia

```vb
CType(expression, typename)
```

## <a name="parts"></a>Części

`expression` dowolne prawidłowe wyrażenie. Jeśli wartość `expression` znajduje się poza zakresem dozwolonym przez `typename`, Visual Basic zgłasza wyjątek.

`typename` dowolne wyrażenie, które jest dozwolone w klauzuli `As` w instrukcji `Dim`, czyli nazwę dowolnego typu danych, obiektu, struktury, klasy lub interfejsu.

## <a name="remarks"></a>Uwagi

> [!TIP]
> Aby przeprowadzić konwersję typu, można również użyć następujących funkcji:
>
> - Funkcje konwersji typów, takie jak `CByte`, `CDbl` i `CInt`, które wykonują konwersję do określonego typu danych. Aby uzyskać więcej informacji, zobacz [funkcje konwersji typów](../../../visual-basic/language-reference/functions/type-conversion-functions.md).
> - [Operator DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [operator TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md). Operatory te wymagają, aby jeden typ dziedziczył z lub zaimplementował inny typ. Mogą one zapewnić nieco lepszą wydajność niż `CType` podczas konwersji do i z typu danych `Object`.

`CType` jest kompilowane w tekście, co oznacza, że kod konwersji jest częścią kodu, który szacuje wyrażenie. W niektórych przypadkach kod działa szybciej, ponieważ żadne procedury nie są wywoływane w celu przeprowadzenia konwersji.

Jeśli konwersja nie jest zdefiniowana z `expression` do `typename` (na przykład z `Integer` do `Date`), Visual Basic wyświetla komunikat o błędzie kompilacji.

Jeśli konwersja nie powiedzie się w czasie wykonywania, zostanie zgłoszony odpowiedni wyjątek. W przypadku niepowodzenia konwersji wąskiej, <xref:System.OverflowException> jest najbardziej typowym wynikiem. Jeśli konwersja jest niezdefiniowana, zostanie zgłoszony <xref:System.InvalidCastException>. Na przykład może się tak zdarzyć, jeśli `expression` jest typu `Object`, a jego typ czasu wykonywania nie ma konwersji na `typename`.

Jeśli typem danych `expression` lub `typename` jest zdefiniowana Klasa lub struktura, można zdefiniować `CType` w tej klasie lub strukturze jako operator konwersji. Dzięki temu `CType` działa jako *przeciążony operator*. W takim przypadku można kontrolować zachowanie konwersji do i z klasy lub struktury, łącznie z wyjątkami, które mogą być zgłaszane.

## <a name="overloading"></a>Przeciążenie

Operator `CType` może być również przeciążony na klasie lub strukturze zdefiniowanej poza kodem. Jeśli kod jest konwertowany na lub z takiej klasy lub struktury, upewnij się, że rozumiesz zachowanie operatora `CType`. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Konwertowanie obiektów dynamicznych

Konwersje typów obiektów dynamicznych są wykonywane przez zdefiniowane przez użytkownika Konwersje dynamiczne, które używają metod <xref:System.Dynamic.DynamicObject.TryConvert%2A> lub <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>. Jeśli pracujesz z obiektami dynamicznymi, użyj metody <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>, aby przekonwertować obiekt dynamiczny.

## <a name="example"></a>Przykład

W poniższym przykładzie zastosowano funkcję `CType`, aby przekonwertować wyrażenie na typ danych `Single`.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Aby uzyskać więcej przykładów, zobacz [konwersje niejawne i jawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Funkcje konwersji](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrukcje: Definiowanie operatora konwersji @ no__t-0
- [Konwersja typu w .NET Framework](../../../standard/base-types/type-conversion.md)
