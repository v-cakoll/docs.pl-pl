---
title: Option Infer — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346500"
---
# <a name="option-infer-statement"></a>Option Infer — Instrukcja

Umożliwia użycie wnioskowania o typie lokalnym podczas deklarowania zmiennych.

## <a name="syntax"></a>Składnia

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`On`|Opcjonalna. Włącza wnioskowanie o typie lokalnym.|
|`Off`|Opcjonalna. Wyłącza wnioskowanie o typie lokalnym.|

## <a name="remarks"></a>Uwagi

Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` w górnej części pliku przed jakimkolwiek innym kodem źródłowym. Jeśli wartość ustawiona dla `Option Infer` w pliku powoduje konflikt z wartością ustawioną w środowisku IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.

Po ustawieniu `Option Infer` na `On`można zadeklarować zmienne lokalne bez jawnego wypełniania typu danych. Kompilator wnioskuje typ danych zmiennej z typu wyrażenia inicjującego.

Na poniższej ilustracji `Option Infer` jest włączona. Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowana jako liczba całkowita przez wnioskowanie o typie.

Poniższy zrzut ekranu przedstawia technologię IntelliSense, gdy jest włączona opcja wnioskowanie:

![Zrzut ekranu przedstawiający widok IntelliSense, gdy opcja wnioskowanie jest włączona.](./media/option-infer-statement/option-infer-as-integer-on.png)

Na poniższej ilustracji `Option Infer` jest wyłączone. Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowana jako `Object` przez wnioskowanie o typie. W tym przykładzie ustawienie **Option Strict** jest **wyłączone** na [stronie kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

Poniższy zrzut ekranu przedstawia funkcję IntelliSense, gdy wywnioskowanie opcji jest wyłączone:

![Zrzut ekranu przedstawiający widok IntelliSense, gdy wywnioskowanie opcji jest wyłączone.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> Gdy zmienna jest zadeklarowana jako `Object`, typ czasu wykonywania może ulec zmianie, gdy program jest uruchomiony. Visual Basic wykonuje operacje nazywane *opakowaniem* i *rozpakowywaniem* w celu konwersji między `Object` i typem wartości, co powoduje wolniejsze wykonywanie. Aby uzyskać informacje na temat pakowania i rozpakowywania, zobacz [Specyfikacja języka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).

Wnioskowanie o typie ma zastosowanie na poziomie procedury i nie ma zastosowania poza procedurą w klasie, strukturze, module lub interfejsie.

Aby uzyskać dodatkowe informacje, zobacz temat [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>Gdy nie ma instrukcji wnioskowania o opcji

Jeśli kod źródłowy nie zawiera instrukcji `Option Infer`, zostanie użyta **opcja wnioskowanie** dotyczące ustawienia na [stronie kompilowania, projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Jeśli jest używany kompilator wiersza polecenia, opcja kompilatora [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) jest używana.

#### <a name="to-set-option-infer-in-the-ide"></a>Aby ustawić wnioskowanie opcji w środowisku IDE

1. W **Eksplorator rozwiązań**wybierz projekt. W menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **kompilacja** .

3. Ustaw wartość w polu **wnioskowanie dotyczące opcji** .

Podczas tworzenia nowego projektu, **opcja wnioskowanie opcji** na karcie **Kompilowanie** ma ustawioną wartość ustawienia **wnioskowania** w oknie dialogowym **Ustawienia domyślne języka vb** . Aby uzyskać dostęp do okna dialogowego **Ustawienia domyślne VB** , w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie w **języku VB** domyślnie jest `On`.

#### <a name="to-set-option-infer-on-the-command-line"></a>Aby ustawić wnioskowanie opcji w wierszu polecenia

Dołącz opcję kompilatora [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) w poleceniu **VBC** .

## <a name="default-data-types-and-values"></a>Domyślne typy danych i wartości

W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w instrukcji `Dim`.

|Określono typ danych?|Określono inicjator?|Przykład|Wynik|
|---|---|---|---|
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (wartość domyślna), zmienna jest ustawiona na `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|
|Nie|Tak|`Dim qty = 5`|Jeśli `Option Infer` jest włączone (wartość domyślna), zmienna Pobiera typ danych inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączone i `Option Strict` jest wyłączone, zmienna Pobiera typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|
|Tak|Nie|`Dim qty As Integer`|Zmienna jest inicjowana do wartości domyślnej dla typu danych. Aby uzyskać więcej informacji, zobacz [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych inicjatora nie zostanie przekonwertowany na określony typ danych, wystąpi błąd w czasie kompilacji.|

## <a name="example"></a>Przykład

W poniższych przykładach pokazano, jak instrukcja `Option Infer` włącza wnioskowanie typu lokalnego.

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, że typ czasu wykonywania może się różnić, gdy zmienna jest identyfikowana jako `Object`.

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>Zobacz także

- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Konwersja boxing i konwersja unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
