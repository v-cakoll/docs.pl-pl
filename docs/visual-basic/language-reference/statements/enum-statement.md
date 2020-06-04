---
title: Enum, instrukcja
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
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404735"
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

  Opcjonalny. Lista atrybutów, które są stosowane do tego wyliczenia. Należy ująć [listę atrybutów](attribute-list.md) w nawiasy kątowe (" `<` " i " `>` ").

  Ten <xref:System.FlagsAttribute> atrybut wskazuje, że wartość wystąpienia wyliczenia może zawierać wiele elementów członkowskich wyliczenia i że każdy element członkowski reprezentuje pole bitowe w wartości wyliczenia.

- `accessmodifier`

  Opcjonalny. Określa kod, który może uzyskać dostęp do tego wyliczenia. Może być jedną z następujących czynności:

  - [Społeczeństwo](../modifiers/public.md)

  - [Chronione](../modifiers/protected.md)

  - [Osoby](../modifiers/friend.md)

  - [Użytek](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Prywatne chronione](../modifiers/private-protected.md)

- `Shadows`

  Opcjonalny. Określa, że to Wyliczenie ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej. Można określić tylko [cienie](../modifiers/shadows.md) na samym wyliczeniu, a nie na żadnym z jej elementów członkowskich.

- `enumerationname`

  Wymagany. Nazwa wyliczenia. Aby uzyskać informacje o prawidłowych nazwach, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Opcjonalny. Typ danych wyliczenia i wszystkie jego elementy członkowskie.

- `memberlist`

  Wymagany. Lista stałych elementów członkowskich, które są zadeklarowane w tej instrukcji. W poszczególnych wierszach kodu źródłowego są wyświetlane wiele elementów członkowskich.

  Każda `member` z nich ma następującą składnię i części:`[<attribute list>] member name [ = initializer ]`

  |Część|Opis|
  |---|---|
  |`membername`|Wymagany. Nazwa tego elementu członkowskiego.|
  |`initializer`|Opcjonalny. Wyrażenie, które jest oceniane w czasie kompilacji i przypisane do tego elementu członkowskiego.|

- `End` `Enum`

  Kończy `Enum` blok.

## <a name="remarks"></a>Uwagi

Jeśli masz zestaw niezmienionych wartości, które są ze sobą logicznie powiązane, możesz zdefiniować je razem w wyliczeniu. Zapewnia to zrozumiałe nazwy dla wyliczenia i jego członków, które są łatwiejsze do zapamiętania niż ich wartości. Następnie można używać elementów członkowskich wyliczenia w wielu miejscach w kodzie.

Zalety korzystania z wyliczeń obejmują następujące elementy:

- Zmniejsza liczbę błędów spowodowanych przez transpozycję lub błędne wpisanie numerów.

- Ułatwia zmianę wartości w przyszłości.

- Sprawia, że kod jest łatwiejszy do odczytania, co oznacza, że błędy będą wprowadzane.

- Zapewnia zgodność dalej. W przypadku korzystania z wyliczeń kod jest mniej prawdopodobnie niepowodzeniem, jeśli w przyszłości ktoś zmieni wartości odpowiadające nazwom członków.

Wyliczenie ma nazwę, podstawowy typ danych i zestaw elementów członkowskich. Każdy element członkowski reprezentuje stałą.

Wyliczenie zadeklarowane na poziomie klasy, struktury, modułu lub interfejsu, poza żadną procedurą, jest *wyliczeniem elementu członkowskiego*. Jest członkiem klasy, struktury, modułu lub interfejsu, który go deklaruje.

Do wyliczania elementów członkowskich można uzyskiwać dostęp z dowolnego miejsca w swojej klasie, strukturze, module lub interfejsie. Kod poza klasą, strukturą lub modułem musi kwalifikować nazwę wyliczenia elementu członkowskiego o nazwie tej klasy, struktury lub modułu. Można uniknąć konieczności używania w pełni kwalifikowanych nazw przez dodanie instrukcji [Imports](imports-statement-net-namespace-and-type.md) do pliku źródłowego.

Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasą, strukturą, modułem lub interfejsem, jest członkiem przestrzeni nazw, w której występuje.

*Kontekst deklaracji* wyliczenia musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Atrybuty można zastosować do wyliczenia jako całości, ale nie do elementów członkowskich. Atrybut tworzy informacje w metadanych zestawu.

## <a name="data-type"></a>Typ danych

`Enum`Instrukcja może deklarować typ danych wyliczenia. Każdy element członkowski Pobiera typ danych wyliczenia. Można określić,,,,,, `Byte` `Integer` `Long` `SByte` `Short` `UInteger` `ULong` lub `UShort` .

Jeśli nie określisz `datatype` dla wyliczenia, każdy element członkowski Pobiera typ danych `initializer` . Jeśli określisz oba elementy `datatype` i `initializer` , typ danych `initializer` musi być konwertowany na `datatype` . Jeśli ani `datatype` nie `initializer` jest obecny, typ danych jest wartością domyślną `Integer` .

## <a name="initializing-members"></a>Inicjowanie członków

`Enum`Instrukcja może inicjować zawartość wybranych elementów członkowskich w `memberlist` . Używasz, `initializer` Aby podać wyrażenie, które ma zostać przypisane do elementu członkowskiego.

Jeśli nie określisz `initializer` dla elementu członkowskiego, Visual Basic Inicjuje to zero (jeśli jest to pierwsze `member` w `memberlist` ) lub wartość większą o jeden niż ta, która jest bezpośrednio Poprzednia `member` .

Wyrażenie podane w każdym z nich `initializer` może być dowolną kombinacją literałów, innych stałych, które są już zdefiniowane, oraz składowych wyliczenia, które są już zdefiniowane, włącznie z poprzednią składową tego wyliczenia. Do łączenia takich elementów można używać operatorów arytmetycznych i logicznych.

W programie nie można używać zmiennych ani funkcji `initializer` . Można jednak użyć słów kluczowych konwersji, takich jak `CByte` i `CShort` . Można również użyć `AscW` , jeśli wywołasz ją z stałą `String` lub `Char` argumentem, ponieważ może być oceniane w czasie kompilacji.

Wyliczenia nie mogą mieć wartości zmiennoprzecinkowych. Jeśli element członkowski ma przypisaną wartość zmiennoprzecinkową i `Option Strict` jest ustawiony na on, wystąpi błąd kompilatora. Jeśli `Option Strict` jest wyłączona, wartość jest automatycznie konwertowana na `Enum` Typ.

Jeśli wartość elementu członkowskiego przekracza dozwolony zakres dla bazowego typu danych lub jeśli zainicjujesz dowolny element członkowski do wartości maksymalnej dozwolonej przez typ danych, kompilator zgłosi błąd.

## <a name="modifiers"></a>Modyfikatory

Wyliczenia klasy, struktury, modułu i elementu członkowskiego interfejsu są domyślne dla dostępu publicznego. Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Wyliczenie elementu członkowskiego przestrzeni nazw domyślnie ma dostęp do znajomych. Poziom dostępu można dostosować do publicznego, ale nie do prywatnego lub chronionego. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Wszyscy członkowie wyliczenia mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu. Jeśli jednak Wyliczenie ma bardziej ograniczony poziom dostępu, pierwszeństwo ma określony poziom dostępu do wyliczenia.

Domyślnie wszystkie wyliczenia są typami i ich pola są stałymi. W związku z tym `Shared` `Static` `ReadOnly` słowa kluczowe, i nie mogą być używane podczas deklarowania wyliczenia lub jego elementów członkowskich.

## <a name="assigning-multiple-values"></a>Przypisywanie wielu wartości

Wyliczenia zazwyczaj reprezentują wzajemnie wykluczające się wartości. Dołączając <xref:System.FlagsAttribute> atrybut w `Enum` deklaracji, można zamiast tego przypisać wiele wartości do wystąpienia wyliczenia. Ten <xref:System.FlagsAttribute> atrybut określa, że Wyliczenie ma być traktowane jako pole bitowe, czyli zestaw flag. Są one nazywane wyliczaniem *bitowym* .

W przypadku deklarowania wyliczenia przy użyciu <xref:System.FlagsAttribute> atrybutu zalecamy użycie uprawnień 2, czyli 1, 2, 4, 8, 16 itd., dla wartości. Zalecamy również, aby wartość "none" była nazwą elementu członkowskiego, którego wartością jest 0. Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum> .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `Enum` instrukcji. Należy zauważyć, że element członkowski jest określany jako `EggSizeEnum.Medium` , a nie jako `Medium` .

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Przykład

Metoda w poniższym przykładzie znajduje się poza `Egg` klasą. W związku z tym, `EggSizeEnum` jest w pełni kwalifikowana jako `Egg.EggSizeEnum` .

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Przykład

Poniższy przykład używa `Enum` instrukcji w celu zdefiniowania powiązanego zestawu nazwanych stałych wartości. W takim przypadku wartości są kolorami, które można wybrać do projektowania formularzy wprowadzania danych dla bazy danych.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje wartości, które zawierają zarówno liczbę dodatnią, jak i ujemną.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Przykład

W poniższym przykładzie `As` klauzula służy do określenia `datatype` wyliczenia.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać wyliczenia bitowego. Do wystąpienia wyliczenia bitowego można przypisać wiele wartości. `Enum`Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że Wyliczenie może być traktowane jako zestaw flag.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje iterację przez wyliczenie. Używa metody, <xref:System.Enum.GetNames%2A> Aby pobrać tablicę nazw elementów członkowskich z wyliczenia i <xref:System.Enum.GetValues%2A> pobrać tablicę wartości elementów członkowskich.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const, instrukcja](const-statement.md)
- [Dim, instrukcja](dim-statement.md)
- [Konwersje jawne i niejawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Stałe i wyliczenia](../constants-and-enumerations.md)
