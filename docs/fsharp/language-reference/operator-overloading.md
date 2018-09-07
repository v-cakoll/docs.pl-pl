---
title: Przeładowanie operatora (F#)
description: 'Dowiedz się, jak przeciążania operatorów arytmetycznych w klasie lub typie rekordu oraz na poziomie globalnym w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087302"
---
# <a name="operator-overloading"></a>Przeciążanie operatora

W tym temacie opisano sposób przeciążania operatorów arytmetycznych w klasie lub typie rekordu oraz na poziomie globalnym.

## <a name="syntax"></a>Składnia

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *symbol operatora* jest jednym z `+`, `-`, `*`, `/`, `=`i tak dalej. *Listy parametrów* Określa argumenty operacji w kolejności, pojawiają się na typowej składni danego operatora. *Treści metody* konstruuje wartość wynikową.

Przeciążenia operatorów muszą być statyczne. Przeciążenia operatorów jednoargumentowych, takich jak `+` i `-`, należy użyć tyldy (`~`) w *symbol operatora* do wskazania, że operator jest jednoargumentowy a nie operatora binarnego, jak pokazano w poniższej deklaracji.

```fsharp
static member (~-) (v : Vector)
```

Kod poniżej ilustruje klasę wektorową, która ma tylko dwa operatory: jeden dla jednoargumentowego znaku minusa, a drugi dla mnożenia przez wartość skalarną. W przykładzie są wymagane dwa przeciążenia mnożenia skalarnego, ponieważ operator musi działać niezależnie od kolejności występowania wartości wektorowej i skalarnej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Tworzenie nowych operatorów

Można przeciążać wszystkie operatory standardowe, ale także tworzyć nowe operatory z sekwencji określonych znaków. Dozwolone znaki to `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, i `~`. Znak `~` odgrywa specjalną rolę (oznacza operator jednoargumentowy) i nie jest częścią sekwencji znaków operatora. Nie wszystkie operatory mogą być jednoargumentowe.

W zależności od konkretnej sekwencji użytych znaków operator będzie miał określone pierwszeństwo i łączność. Łączność może być typu od lewej do prawej lub od prawej do lewej. Jest wykorzystywana zawsze wtedy, gdy operatory o tym samym poziomie pierwszeństwa występują w sekwencji bez nawiasów.

Znak operatora `.` nie wpływa na pierwszeństwo, dlatego na przykład w celu zdefiniowania własnej wersji mnożenia, która ma takie samo pierwszeństwo i łączność jak zwykłe mnożenie, można utworzyć operatora `.*` albo podobnego.

Tylko operatory `?` i `?<-` może się rozpoczynać `?`.

Tabelę ilustrująca pierwszeństwo wszystkich operatorów w języku F # można znaleźć w [Operator odwołanie do symbolu i](symbol-and-operator-reference/index.md).

## <a name="overloaded-operator-names"></a>Nazwy przeciążonych operatorów

Gdy kompilator języka F# kompiluje wyrażenie operatora, tworzy dla tego operatora metodę o wygenerowanej przez siebie nazwie. Ta nazwa metody jest wyświetlana w składni języka Microsoft Intermediate Language (MSIL), w odbiciu oraz w narzędziu IntelliSense. Zazwyczaj nie trzeba używać tych nazw w kodzie języka F#.

W tabeli poniżej pokazano standardowe operatory oraz odpowiadające im wygenerowane nazwy.

|Operator|Wygenerowana nazwa|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

Jako operatorów można również używać innych, niewymienionych tutaj kombinacji znaków operatorów. Ich nazwy mogą powstawać z połączenia nazw poszczególnych znaków podanych w tabeli poniżej. Na przykład +! staje się `op_PlusBang`.

|Znak operatora|Nazwa|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Operatory przedrostkowe i wrostkowe

*Prefiks* operatory powinny należy umieszczać przed argumentami operacji, podobnie jak funkcje. *Wrostkowe* operatory powinny być umieszczona między dwoma argumentami operacji.

Jako operatorów przedrostkowych można używać tylko niektórych operatorów. Niektóre operatory są zawsze operatorami przedrostkowymi, inne mogą być wrostkowe lub przedrostkowe, a pozostałe są zawsze operatorami wrostkowymi. Operatory, które zaczynają się znakiem `!` (z wyjątkiem `!=`), oraz operator `~` lub powtarzające się sekwencje operatora `~`, są zawsze operatorami przedrostkowymi. Operatory `+`, `-`, `+.`, `-.`, `&`, `&&`, `%` i `%%` mogą być przedrostkowe lub wrostkowe. Przedrostkowe wersje tych operatorów można odróżnić od wersji wrostkowych przez dodanie znaku `~` na początku operatora przedrostkowego podczas jego definiowania. Znak `~` nie jest wykorzystywany podczas używania operatora, a tylko podczas jego definiowania.

## <a name="example"></a>Przykład

Poniższy kod ilustruje zastosowania przeciążenia operatora w celu zaimplementowania typu ułamkowego. Ułamek jest reprezentowany przez licznik i mianownik. Funkcja `hcf` służy do określenia największego wspólnego dzielnika, który pozwala zmniejszyć ułamek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Dane wyjściowe:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Operatory na poziomie globalnym

Operatory można również definiować na poziomie globalnym. Poniższy kod definiuje operator `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

Danymi wyjściowymi powyższego kodu jest wartość `12`.

W ten sposób można zmieniać definicje zwykłych operatorów arytmetycznych, ponieważ reguły określania zakresów w języku F# narzucają pierwszeństwo nowo definiowanych operatorów przed operatorami wbudowanymi.

W połączeniu z operatorami globalnymi często używa się słowa kluczowego `inline`, ponieważ operatory te są przeważnie małymi funkcjami, które najlepiej integrować w kodzie wywołującym. Wbudowanie funkcji operatorów umożliwia im także współpracę z parametrami typów rozpoznawanymi statycznie i dzięki temu generowanie statycznie rozpoznawanego kodu ogólnego. Aby uzyskać więcej informacji, zobacz [funkcji śródwierszowych](functions/inline-functions.md) i [statycznie rozwiązywanych parametrach typu](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](members/index.md)
