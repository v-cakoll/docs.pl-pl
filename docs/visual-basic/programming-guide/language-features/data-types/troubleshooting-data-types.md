---
title: Rozwiązywanie problemów związanych z typami
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 63b2513e420320742bf7e25314743f08404f46a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350512"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Rozwiązywanie problemów związanych z typami danych (Visual Basic)

Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas wykonywania operacji na wewnętrznych typach danych.

## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Wyrażenia zmiennoprzecinkowe nie są porównywane jako równe

Podczas pracy z liczbami zmiennoprzecinkowymi ([pojedynczym typem danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) i [podwójnym typem danych](../../../../visual-basic/language-reference/data-types/double-data-type.md)) należy pamiętać, że są one przechowywane jako ułamki binarne. Oznacza to, że nie mogą przechowywać dokładnej reprezentacji żadnej ilości, która nie jest częścią binarną (w postaci k/(2 ^ n), gdzie k i n są liczbami całkowitymi). Na przykład 0,5 (= 1/2) i 0,3125 (= 5/16) mogą być przechowywane jako dokładne wartości, natomiast 0,2 (= 1/5) i 0,3 (= 3/10) mogą być tylko przybliżami.

Z powodu tej niedokładności nie można polegać na dokładnych wynikach podczas wykonywania operacji na wartościach zmiennoprzecinkowych. W szczególności dwie wartości, które są teoretycznie równe, mogą mieć nieco inne reprezentacje.

| Aby porównać ilości zmiennoprzecinkowe |
|---|
|1. Oblicz wartość bezwzględną różnicy przy użyciu metody <xref:System.Math.Abs%2A> klasy <xref:System.Math> w przestrzeni nazw <xref:System>.<br />2. Ustal akceptowalną maksymalną różnicę, tak aby można było rozważyć, że te dwie ilości będą równe w praktyce, jeśli ich różnica nie jest większa.<br />3. Porównaj wartość bezwzględną różnicy z akceptowalną różnicą.|

Poniższy przykład ilustruje nieprawidłowe i prawidłowe porównanie dwóch wartości `Double`.

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

W poprzednim przykładzie zastosowano metodę <xref:System.Double.ToString%2A>ową struktury <xref:System.Double>, aby można było określić lepszą precyzję niż użycie słowa kluczowego `CStr`. Wartość domyślna to 15 cyfr, ale format "G17" rozszerza go do 17 cyfr.

## <a name="mod-operator-does-not-return-accurate-result"></a>Operator mod nie zwraca dokładnego wyniku

Ze względu na niedokładność magazynu zmiennoprzecinkowego [operator mod](../../../../visual-basic/language-reference/operators/mod-operator.md) może zwrócić nieoczekiwany wynik, gdy co najmniej jeden operand jest zmiennoprzecinkowy.

[Typ danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nie używa reprezentacji zmiennoprzecinkowej. Wiele liczb, które są niedokładne w `Single` i `Double` są dokładne w `Decimal` (na przykład 0,2 i 0,3). Chociaż arytmetyka jest wolniejsza w `Decimal` niż zmiennoprzecinkowa, może być cenny spadek wydajności, aby osiągnąć lepszą precyzję.

|Aby znaleźć liczbę całkowitą reszty liczb zmiennoprzecinkowych|
|---|
|1. Zadeklaruj zmienne jako `Decimal`.<br />2. Użyj znaku literału typu `D`, aby wymusić literały `Decimal`, w przypadku gdy ich wartości są za duże dla typu danych `Long`.|

Poniższy przykład ilustruje potencjalną niedokładność argumentów operacji zmiennoprzecinkowych.

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

W poprzednim przykładzie zastosowano metodę <xref:System.Double.ToString%2A>ową struktury <xref:System.Double>, aby można było określić lepszą precyzję niż użycie słowa kluczowego `CStr`. Wartość domyślna to 15 cyfr, ale format "G17" rozszerza go do 17 cyfr.

Ponieważ `zeroPointTwo` jest `Double`, jego wartość dla 0,2 to nieskończonie powtarzające się ułamek binarny z przechowywaną wartością 0.20000000000000001. Dzielenie 2,0 przez tę ilość daje 9.9999999999999995 z pozostałą częścią 0.19999999999999991.

W wyrażeniu dla `decimalRemainder`znak typu literału `D` wymusza, aby oba operandy `Decimal`, a 0,2 ma precyzyjną reprezentację. W związku z tym operator `Mod` zwraca oczekiwaną resztę 0,0.

Należy pamiętać, że nie jest wystarczające, aby zadeklarować `decimalRemainder` jako `Decimal`. Należy również wymusić `Decimal`literałów lub używać `Double` domyślnie, a `decimalRemainder` otrzymuje tę samą niedokładną wartość, co `doubleRemainder`.

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ Boolean nie jest dokładnie konwertowany na typ liczbowy

Wartości [typu danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) nie są przechowywane jako liczby, a przechowywane wartości nie są równoważne z liczbami. W celu zapewnienia zgodności z wcześniejszymi wersjami Visual Basic zawiera słowa kluczowe konwersji ([CType](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`itd.) w celu konwersji między `Boolean` i typami liczbowymi. Jednak inne języki czasami wykonują te konwersje inaczej, tak jak metody .NET Framework.

Nigdy nie należy pisać kodu, który opiera się na odpowiednich wartościach liczbowych dla `True` i `False`. Jeśli to możliwe, należy ograniczyć użycie zmiennych `Boolean` do wartości logicznych, dla których zostały zaprojektowane. Jeśli trzeba mieszać `Boolean` i wartości liczbowe, należy zapoznać się z wybraną metodą konwersji.

### <a name="conversion-in-visual-basic"></a>Konwersja w Visual Basic

Po użyciu słów kluczowych konwersji `CType` lub `CBool` do przekonwertowania liczbowych typów danych na `Boolean`, wartość 0 staje się `False`, a wszystkie inne wartości stają się `True`. Podczas konwertowania wartości `Boolean` na typy liczbowe przy użyciu słów kluczowych konwersji `False` przyjmuje wartość 0, a `True` zmieni się-1.

### <a name="conversion-in-the-framework"></a>Konwersja w strukturze

Metoda <xref:System.Convert.ToInt32%2A> klasy <xref:System.Convert> w przestrzeni nazw <xref:System> konwertuje `True` do + 1.

Jeśli konieczne jest przekonwertowanie wartości `Boolean` na typ danych liczbowych, należy zachować ostrożność, która metoda konwersji jest używana.

## <a name="character-literal-generates-compiler-error"></a>Literał znakowy generuje błąd kompilatora

W przypadku braku znaków typu, Visual Basic przyjmuje domyślne typy danych dla literałów. Domyślny typ literału znakowego, ujęty w cudzysłów (`" "`) — jest `String`.

Typ danych `String` nie jest rozszerzany na [Typ danych char](../../../../visual-basic/language-reference/data-types/char-data-type.md). Oznacza to, że jeśli chcesz przypisać literał do zmiennej `Char`, musisz wykonać konwersję zwężaną lub wymusić literał dla typu `Char`.

|Aby utworzyć literał char do przypisania do zmiennej lub stałej|
|---|
|1. Zadeklaruj zmienną lub stałą jako `Char`.<br />2. ujmij wartość znaku w cudzysłów (`" "`).<br />3. Postępuj zgodnie ze znakiem zamykającym podwójnego cudzysłowu z typem literału `C`, aby wymusić `Char`literału. Jest to konieczne, jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`i jest pożądany w każdym przypadku.|

Poniższy przykład ilustruje nieudane i pomyślne przypisania literału do zmiennej `Char`.

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

Jest to zawsze ryzykowne przy użyciu wąskich konwersji, ponieważ mogą one kończyć się niepowodzeniem w czasie wykonywania. Na przykład konwersja z `String` na `Char` może zakończyć się niepowodzeniem, jeśli wartość `String` zawiera więcej niż jeden znak. W związku z tym lepszym rozwiązaniem jest użycie znaku typu `C`.

## <a name="string-conversion-fails-at-run-time"></a>Konwersja ciągu kończy się niepowodzeniem w czasie wykonywania

[Typ danych ciągu](../../../../visual-basic/language-reference/data-types/string-data-type.md) uczestniczy w bardzo nielicznych konwersjach rozszerzających. `String` rozszerza tylko do siebie i `Object`, a tylko `Char` i `Char()` (`Char` Array) rozszerzać do `String`. Wynika to z faktu, że `String` zmienne i stałe mogą zawierać wartości, które nie mogą zawierać innych typów danych.

Gdy przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, kompilator nie zezwala na wszystkie niejawne konwersje zawężające. Dotyczy to również `String`. Kod może nadal używać słów kluczowych konwersji, takich jak `CStr` i [Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md), które kierują .NET Framework do próby konwersji.

> [!NOTE]
> Zawężanie — błąd konwersji jest pomijany dla konwersji z elementów w kolekcji `For Each…Next` do zmiennej kontroli pętli. Aby uzyskać więcej informacji i przykładów, zobacz sekcję "Konwersje wąskie" w sekcji [for each... Next — instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).

### <a name="narrowing-conversion-protection"></a>Zawężanie ochrony konwersji

Wadą konwersji zawężania jest to, że mogą one kończyć się niepowodzeniem w czasie wykonywania. Na przykład jeśli zmienna `String` zawiera coś innego niż "true" lub "false", nie można jej przekonwertować na `Boolean`. Jeśli zawiera znaki interpunkcyjne, konwersja na dowolny typ liczbowy kończy się niepowodzeniem. Chyba że wiadomo, że zmienna `String` zawsze przechowuje wartości, które typ docelowy może zaakceptować, nie należy próbować konwersji.

Jeśli konieczne jest przekonwertowanie z `String` na inny typ danych, najbezpieczniejsza procedura polega na zawieszeniu próby konwersji w [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Pozwala to na poradzenie sobie z błędem czasu wykonywania.

### <a name="character-arrays"></a>Tablice znaków

Pojedyncze `Char` i tablica `Char` elementów rozszerzają się do `String`. Jednak `String` nie rozszerza `Char()`. Aby przekonwertować wartość `String` na tablicę `Char`, można użyć metody <xref:System.String.ToCharArray%2A> klasy <xref:System.String?displayProperty=nameWithType>.

### <a name="meaningless-values"></a>Bez znaczenia wartości

Ogólnie rzecz biorąc, wartości `String` nie mają znaczenia w przypadku innych typów danych, a konwersja jest wysoce sztuczna i niebezpieczna. Jeśli to możliwe, należy ograniczyć użycie zmiennych `String` do sekwencji znaków, dla których zostały zaprojektowane. Nigdy nie należy pisać kodu, który opiera się na równoważnych wartościach w innych typach.

## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
