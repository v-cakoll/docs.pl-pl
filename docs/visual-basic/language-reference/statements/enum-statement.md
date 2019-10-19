---
title: Enum — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: be1780b00b4d58964e1de5ec199cb80dc0f9dba5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583409"
---
# <a name="enum-statement-visual-basic"></a>Enum — Instrukcja (Visual Basic)

Deklaruje Wyliczenie i definiuje wartości jego elementów członkowskich.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>Części

- `attributelist`

  Opcjonalny. Lista atrybutów, które są stosowane do tego wyliczenia. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ostre ("`<`" i "`>`").

  Atrybut <xref:System.FlagsAttribute> wskazuje, że wartość wystąpienia wyliczenia może zawierać wiele elementów członkowskich wyliczenia i że każdy element członkowski reprezentuje pole bitowe w wartości wyliczenia.

- `accessmodifier`

  Opcjonalny. Określa kod, który może uzyskać dostęp do tego wyliczenia. Może być jedną z następujących czynności:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  Opcjonalny. Określa, że to Wyliczenie ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej. Można określić tylko [cienie](../../../visual-basic/language-reference/modifiers/shadows.md) na samym wyliczeniu, a nie na żadnym z jej elementów członkowskich.

- `enumerationname`

  Wymagany. Nazwa wyliczenia. Aby uzyskać informacje o prawidłowych nazwach, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Opcjonalny. Typ danych wyliczenia i wszystkie jego elementy członkowskie.

- `memberlist`

  Wymagany. Lista stałych elementów członkowskich, które są zadeklarowane w tej instrukcji. W poszczególnych wierszach kodu źródłowego są wyświetlane wiele elementów członkowskich.

  Każda `member` ma następującą składnię i części: `[<attribute list>] member name [ = initializer ]`

  |Części|Opis|
  |---|---|
  |`membername`|Wymagany. Nazwa tego elementu członkowskiego.|
  |`initializer`|Opcjonalny. Wyrażenie, które jest oceniane w czasie kompilacji i przypisane do tego elementu członkowskiego.|

- `End``Enum`

  Kończy blok `Enum`.

## <a name="remarks"></a>Uwagi

Jeśli masz zestaw niezmienionych wartości, które są ze sobą logicznie powiązane, możesz zdefiniować je razem w wyliczeniu. Zapewnia to zrozumiałe nazwy dla wyliczenia i jego członków, które są łatwiejsze do zapamiętania niż ich wartości. Następnie można używać elementów członkowskich wyliczenia w wielu miejscach w kodzie.

Zalety korzystania z wyliczeń obejmują następujące elementy:

- Zmniejsza liczbę błędów spowodowanych przez transpozycję lub błędne wpisanie numerów.

- Ułatwia zmianę wartości w przyszłości.

- Sprawia, że kod jest łatwiejszy do odczytania, co oznacza, że błędy będą wprowadzane.

- Zapewnia zgodność dalej. W przypadku korzystania z wyliczeń kod jest mniej prawdopodobnie niepowodzeniem, jeśli w przyszłości ktoś zmieni wartości odpowiadające nazwom członków.

Wyliczenie ma nazwę, podstawowy typ danych i zestaw elementów członkowskich. Każdy element członkowski reprezentuje stałą.

Wyliczenie zadeklarowane na poziomie klasy, struktury, modułu lub interfejsu, poza żadną procedurą, jest *wyliczeniem elementu członkowskiego*. Jest członkiem klasy, struktury, modułu lub interfejsu, który go deklaruje.

Do wyliczania elementów członkowskich można uzyskiwać dostęp z dowolnego miejsca w swojej klasie, strukturze, module lub interfejsie. Kod poza klasą, strukturą lub modułem musi kwalifikować nazwę wyliczenia elementu członkowskiego o nazwie tej klasy, struktury lub modułu. Można uniknąć konieczności używania w pełni kwalifikowanych nazw przez dodanie instrukcji [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do pliku źródłowego.

Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasą, strukturą, modułem lub interfejsem, jest członkiem przestrzeni nazw, w której występuje.

*Kontekst deklaracji* wyliczenia musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Atrybuty można zastosować do wyliczenia jako całości, ale nie do elementów członkowskich. Atrybut tworzy informacje w metadanych zestawu.

## <a name="data-type"></a>Typ danych

Instrukcja `Enum` może deklarować typ danych wyliczenia. Każdy element członkowski Pobiera typ danych wyliczenia. Można określić `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong` lub `UShort`.

Jeśli nie określisz `datatype` do wyliczenia, każdy element członkowski Pobiera typ danych `initializer`. W przypadku określenia obydwu wartości `datatype` i `initializer` typ danych `initializer` musi być konwertowany na `datatype`. Jeśli nie `datatype` ani `initializer` nie istnieje, typ danych jest wartością domyślną `Integer`.

## <a name="initializing-members"></a>Inicjowanie członków

Instrukcja `Enum` może inicjować zawartość wybranych elementów członkowskich w `memberlist`. Użyj `initializer`, aby podać wyrażenie, które ma zostać przypisane do elementu członkowskiego.

Jeśli nie określisz `initializer` dla elementu członkowskiego, Visual Basic Inicjuje to zero (jeśli jest to pierwszy `member` w `memberlist`) lub wartość większą o jeden niż bezpośrednio przed `member`.

Wyrażenie podane w każdej `initializer` może być dowolną kombinacją literałów, innych stałych, które są już zdefiniowane, oraz składowych wyliczenia, które są już zdefiniowane, włącznie z poprzednią składową tego wyliczenia. Do łączenia takich elementów można używać operatorów arytmetycznych i logicznych.

Nie można używać zmiennych ani funkcji w `initializer`. Można jednak użyć słów kluczowych konwersji, takich jak `CByte` i `CShort`. Można również użyć `AscW`, jeśli wywołasz ją ze stałą `String` lub `Char`, ponieważ można ją ocenić w czasie kompilacji.

Wyliczenia nie mogą mieć wartości zmiennoprzecinkowych. Jeśli element członkowski ma przypisaną wartość zmiennoprzecinkową i `Option Strict` jest ustawiona na on, wystąpi błąd kompilatora. Jeśli `Option Strict` jest wyłączone, wartość zostanie automatycznie przekonwertowana na typ `Enum`.

Jeśli wartość elementu członkowskiego przekracza dozwolony zakres dla bazowego typu danych lub jeśli zainicjujesz dowolny element członkowski do wartości maksymalnej dozwolonej przez typ danych, kompilator zgłosi błąd.

## <a name="modifiers"></a>Modyfikatory

Wyliczenia klasy, struktury, modułu i elementu członkowskiego interfejsu są domyślne dla dostępu publicznego. Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Wyliczenie elementu członkowskiego przestrzeni nazw domyślnie ma dostęp do znajomych. Poziom dostępu można dostosować do publicznego, ale nie do prywatnego lub chronionego. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Wszyscy członkowie wyliczenia mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu. Jeśli jednak Wyliczenie ma bardziej ograniczony poziom dostępu, pierwszeństwo ma określony poziom dostępu do wyliczenia.

Domyślnie wszystkie wyliczenia są typami i ich pola są stałymi. W związku z tym słowa kluczowe `Shared`, `Static` i `ReadOnly` nie mogą być używane podczas deklarowania wyliczenia lub jego elementów członkowskich.

## <a name="assigning-multiple-values"></a>Przypisywanie wielu wartości

Wyliczenia zazwyczaj reprezentują wzajemnie wykluczające się wartości. Uwzględniając atrybut <xref:System.FlagsAttribute> w deklaracji `Enum`, można zamiast tego przypisać wiele wartości do wystąpienia wyliczenia. Atrybut <xref:System.FlagsAttribute> określa, że Wyliczenie ma być traktowane jako pole bitowe, czyli zestaw flag. Są one nazywane wyliczaniem *bitowym* .

W przypadku deklarowania wyliczenia przy użyciu atrybutu <xref:System.FlagsAttribute> zalecamy użycie uprawnień 2, czyli 1, 2, 4, 8, 16 itd., dla wartości. Zalecamy również, aby wartość "none" była nazwą elementu członkowskiego, którego wartością jest 0. Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać instrukcji `Enum`. Należy zauważyć, że element członkowski jest określany jako `EggSizeEnum.Medium`, a nie jako `Medium`.

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Przykład

Metoda w poniższym przykładzie znajduje się poza klasą `Egg`. W związku z tym `EggSizeEnum` jest w pełni kwalifikowana jako `Egg.EggSizeEnum`.

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Przykład

Poniższy przykład używa instrukcji `Enum` w celu zdefiniowania powiązanego zestawu nazwanych stałych wartości. W takim przypadku wartości są kolorami, które można wybrać do projektowania formularzy wprowadzania danych dla bazy danych.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje wartości, które zawierają zarówno liczbę dodatnią, jak i ujemną.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Przykład

W poniższym przykładzie klauzula `As` jest używana do określenia `datatype` wyliczenia.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać wyliczenia bitowego. Do wystąpienia wyliczenia bitowego można przypisać wiele wartości. Deklaracja `Enum` zawiera atrybut <xref:System.FlagsAttribute>, który wskazuje, że Wyliczenie może być traktowane jako zestaw flag.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje iterację przez wyliczenie. Używa metody <xref:System.Enum.GetNames%2A>, aby pobrać tablicę nazw elementów członkowskich z wyliczenia, i <xref:System.Enum.GetValues%2A>, aby pobrać tablicę wartości elementów członkowskich.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Stałe i wyliczenia](../../../visual-basic/language-reference/constants-and-enumerations.md)
