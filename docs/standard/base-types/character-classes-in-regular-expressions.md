---
title: Klasy znaków w wyrażeniach regularnych programu .NET
description: Dowiedz się, jak używać klas znaków do reprezentowania zestawu znaków w wyrażeniach regularnych programu .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
ms.custom: seodec18
ms.openlocfilehash: dbfa61077cbfdd7da104dc12f304a4096b3c032d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120610"
---
# <a name="character-classes-in-regular-expressions"></a>Klasy znaków w wyrażeniach regularnych

Klasa znaków definiuje zestaw znaków, z którego każdy jeden znak może wystąpić w ciągu wejściowym, aby dopasowanie zakończyło się sukcesem. Język wyrażeń regularnych w programie .NET obsługuje następujące klasy znaków:  
  
- Grupy znaków pozytywnych. Znak w ciągu wejściowym musi odpowiadać jednemu ze znaków z określonego zestawu znaków. Aby uzyskać więcej informacji, zobacz [Grupa znaków pozytywnych](#PositiveGroup).  
  
- Grupy znaków negatywnych. Znak w ciągu wejściowym nie może odpowiadać żadnemu ze znaków z określonego zestawu znaków. Aby uzyskać więcej informacji, zobacz [Grupa znaków negatywnych](#NegativeGroup).  
  
- Dowolny znak. Znak `.` (kropka lub kropka) w wyrażeniu regularnym jest symbolem wieloznacznym, który pasuje do dowolnego znaku z wyjątkiem `\n`. Aby uzyskać więcej informacji, zobacz [dowolny znak](#AnyCharacter).  
  
- Ogólna kategoria Unicode lub blok nazwany. Aby dopasowanie zakończyło się sukcesem, znak w ciągu wejściowym musi być elementem członkowskim określonej kategorii Unicode lub musi należeć do ciągłego zakresu znaków Unicode. Aby uzyskać więcej informacji, zobacz [Kategoria Unicode lub blok Unicode](#CategoryOrBlock).  
  
- Negatywna ogólna kategoria Unicode lub blok nazwany. Aby dopasowanie zakończyło się sukcesem, znak w ciągu wejściowym nie może być elementem członkowskim określonej kategorii Unicode, ani nie może należeć do ciągłego zakresu znaków Unicode. Aby uzyskać więcej informacji, zobacz [negatywna kategoria Unicode lub blok Unicode](#NegativeCategoryOrBlock).  
  
- Znak słowa. Znak w ciągu wejściowym może należeć do dowolnej kategorii Unicode, która jest odpowiednia dla znaków w wyrazach. Aby uzyskać więcej informacji, zobacz [znak słowa](#WordCharacter).  
  
- Znak niebędący znakiem słowa. Znak w ciągu wejściowym może należeć do dowolnej kategorii Unicode, która nie jest znakiem słowa. Aby uzyskać więcej informacji, zobacz [znak niebędący słowem](#NonWordCharacter).  
  
- Znak odstępu. Znak w ciągu wejściowym może być dowolnym znakiem separatora Unicode, a także dowolnym ze znaków kontrolnych. Aby uzyskać więcej informacji, zobacz [znak](#WhitespaceCharacter)odstępu.  
  
- Znak niebędący odstępem. Znak w ciągu wejściowym może być dowolnym znakiem, który nie jest znakiem odstępu. Aby uzyskać więcej informacji, zobacz [znak niebędący odstępem](#NonWhitespaceCharacter).  
  
- Cyfra dziesiętna. Znak w ciągu wejściowym może być dowolnym ze znaków klasyfikowanych jako cyfry dziesiętne Unicode. Aby uzyskać więcej informacji, zobacz [znak cyfr dziesiętnych](#DigitCharacter).  
  
- Cyfra niebędąca cyfrą dziesiętną. Znak w ciągu wejściowym może być dowolnym znakiem innym niż cyfra dziesiętna Unicode. Aby uzyskać więcej informacji, zobacz [znak cyfr dziesiętnych](#NonDigitCharacter).  
  
 Platforma .NET obsługuje wyrażenia odejmowania klas znaków, które umożliwiają zdefiniowanie zestawu znaków jako wyniku wykluczenia jednej klasy znaków z innej klasy znaków. Aby uzyskać więcej informacji, zobacz [odejmowanie klasy znaków](#CharacterClassSubtraction).  
  
> [!NOTE]
> Klasy znaków, które pasują do znaków według kategorii, takich jak [\w](#WordCharacter) , aby dopasować znaki wyrazu lub [\p{}](#CategoryOrBlock) w celu dopasowania do kategorii Unicode, polegają na klasie <xref:System.Globalization.CharUnicodeInfo> w celu podania informacji o kategoriach znaków.  Począwszy od .NET Framework 4.6.2, kategorie znaków są oparte na [standardzie Unicode w wersji 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). W .NET Framework 4 za pośrednictwem .NET Framework 4.6.1 są one oparte na [standardzie Unicode w wersji 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a>Grupa znaków pozytywnych: []  
 Grupa znaków pozytywnych określa listę znaków, z których każdy może wystąpić w ciągu wejściowym, aby wystąpiło dopasowanie. Ta lista znaków może być określona indywidualnie, jako zakres lub na oba te sposoby.  
  
 Składnia służąca do określenia listy indywidualnych znaków jest następująca:  

`[*character_group*]`

 gdzie *character_group* jest listą pojedynczych znaków, które mogą być wyświetlane w ciągu wejściowym, aby dopasowanie zakończyło się pomyślnie. *character_group* może składać się z dowolnej kombinacji jednego lub większej liczby znaków literału, [znaków ucieczki](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)lub klasy znaków.  
  
 Składnia służąca do określania zakresu znaków jest następująca:  
  
`[firstCharacter-lastCharacter]`  
  
 gdzie *firstCharacter* jest znakiem, który rozpoczyna zakres, a *lastCharacter* jest znakiem kończącym zakres. Zakres znaków jest ciągłą serią znaków definiowaną przez określenie pierwszego znaku w serii, łącznika (-), a następnie ostatniego znaku w serii. Dwa znaki są ciągłe, jeśli mają sąsiadujące punkty kodowe Unicode. *firstCharacter* musi być znakiem z dolnym punktem kodu, a *lastCharacter* musi być znakiem z wyższym punktem kodu.

> [!NOTE]
> Ponieważ Grupa znaków pozytywnych może zawierać zarówno zestaw znaków, jak i zakres znaków, znak łącznika (`-`) jest zawsze interpretowany jako separator zakresu, chyba że jest to pierwszy lub ostatni znak grupy.

W poniższej tabeli wymieniono niektóre typowe wzorce wyrażeń regularnych zawierających klasy znaków pozytywnych.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`[aeiou]`|Dopasowuje wszystkie samogłoski.|  
|`[\p{P}\d]`|Dopasowuje wszystkie znaki interpunkcyjne oraz znaki cyfr dziesiętnych.|  
|`[\s\p{P}]`|Dopasowuje cały biały znak i znaki interpunkcyjne.|  
  
 W poniższym przykładzie zdefiniowano grupę znaków pozytywnych, która zawiera znaki „a” i „e”, tak aby ciąg wejściowy musiał zawierać słowa „grey” lub „gray”, a następnie inne słowo, aby wystąpiło dopasowanie.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 Wyrażenie regularne `gr[ae]y\s\S+?[\s|\p{P}]` jest zdefiniowane w następujący sposób:  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`gr`|Dopasowuje znaki literału „gr”.|  
|`[ae]`|Dopasowuje znak „a” lub „e”.|  
|`y\s`|Dopasowuje znak literału „y”, po którym następuje znak odstępu.|  
|`\S+?`|Dopasowuje jeden lub więcej znaków, które nie są znakami odstępu, jednak możliwie najmniej.|  
|`[\s\p{P}]`|Dopasowuje znak odstępu lub znak interpunkcyjny.|  
  
 W poniższym przykładzie dopasowywane są wyrazy zaczynające się od wielkiej litery. Używa podwyrażenia `[A-Z]` do reprezentowania zakresu wielkich liter od A do Z.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 Wyrażenie regularne `\b[A-Z]\w*\b` jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`[A-Z]`|Dopasowuje dowolny znak wielkiej litery z zakresu od A do Z.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a>Ujemna Grupa znaków: [^]  
 Grupa znaków negatywnych określa listę znaków, z których żaden nie może wystąpić w ciągu wejściowym, aby wystąpiło dopasowanie. Ta lista znaków może być określona indywidualnie, jako zakres lub na oba te sposoby.  
  
Składnia służąca do określenia listy indywidualnych znaków jest następująca:  

`[*^character_group*]`

 gdzie *character_group* jest listą pojedynczych znaków, które nie mogą być wyświetlane w ciągu wejściowym, aby dopasowanie zakończyło się pomyślnie. *character_group* może składać się z dowolnej kombinacji jednego lub większej liczby znaków literału, [znaków ucieczki](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)lub klasy znaków.  
  
 Składnia służąca do określania zakresu znaków jest następująca:  

`[^*firstCharacter*-*lastCharacter*]`

gdzie *firstCharacter* jest znakiem, który rozpoczyna zakres, a *lastCharacter* jest znakiem kończącym zakres. Zakres znaków jest ciągłą serią znaków definiowaną przez określenie pierwszego znaku w serii, łącznika (-), a następnie ostatniego znaku w serii. Dwa znaki są ciągłe, jeśli mają sąsiadujące punkty kodowe Unicode. *firstCharacter* musi być znakiem z dolnym punktem kodu, a *lastCharacter* musi być znakiem z wyższym punktem kodu.

> [!NOTE]
> Ponieważ Grupa znaków negatywnych może zawierać zarówno zestaw znaków, jak i zakres znaków, znak łącznika (`-`) jest zawsze interpretowany jako separator zakresu, chyba że jest to pierwszy lub ostatni znak grupy.
  
 Można połączyć co najmniej dwa zakresy znaków. Na przykład, aby określić zakres cyfr dziesiętnych od "0" do "9", zakres małych liter od "a" do "f" oraz zakres wielkich liter od "A" do "F", użyj `[0-9a-fA-F]`.  
  
 Wiodący znak daszka (`^`) w grupie znaków negatywnych jest obowiązkowy i wskazuje, że Grupa znaków jest grupą znaków negatywnych zamiast grupy znaków pozytywnych.  
  
> [!IMPORTANT]
> Grupa znaków negatywnych w większym wzorcu wyrażenia regularnego nie jest asercją o zerowej szerokości. Czyli po dokonaniu oceny grupy znaków negatywnych aparat wyrażeń regularnych postępuje o jeden znak do przodu w ciągu wejściowym.  
  
 W poniższej tabeli wymieniono niektóre typowe wzorce wyrażeń regularnych zawierających grupy znaków negatywnych.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`[^aeiou]`|Dopasowuje wszystkie znaki z wyjątkiem samogłosek.|  
|`[^\p{P}\d]`|Dopasowuje wszystkie znaki z wyjątkiem znaków interpunkcyjnych oraz znaków cyfr dziesiętnych.|  
  
 W poniższym przykładzie jest dopasowywany dowolny wyraz rozpoczynający się od znaków „th”, po których nie występuje znak „o”.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 Wyrażenie regularne `\bth[^o]\w+\b` jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`th`|Dopasowuje znaki literału „th”.|  
|`[^o]`|Dopasowuje dowolny znak inny niż „o”.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy na granicy wyrazu.|  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a>Dowolny znak:.  
 Znak kropki (.) dopasowuje dowolny znak z wyjątkiem `\n` (znak nowego wiersza, \u000A), z następującymi dwoma kwalifikacjami:  
  
- Jeśli wzorzec wyrażenia regularnego jest modyfikowany przez opcję <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> lub jeśli część wzorca, która zawiera klasę `.` jest modyfikowana przez `s` opcji, `.` dopasowuje dowolny znak. Aby uzyskać więcej informacji, zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md).  
  
     Poniższy przykład ilustruje różne zachowanie klasy znaków `.` domyślnie i z opcją <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>. Wyrażenie regularne `^.+` rozpoczyna się na początku ciągu i dopasowuje każdy znak. Domyślnie dopasowanie kończy się na końcu pierwszego wiersza; wzorzec wyrażenia regularnego dopasowuje znak powrotu karetki, `\r` lub \u000D, ale nie jest zgodny z `\n`. Ponieważ opcja <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> interpretuje cały ciąg wejściowy jako pojedynczy wiersz, dopasowuje każdy znak w ciągu wejściowym, w tym `\n`.  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
> Ponieważ dopasowuje dowolny znak z wyjątkiem `\n`, Klasa znaku `.` również dopasowuje `\r` (znak powrotu karetki, \u000D).  
  
- W grupie znaków pozytywnych lub negatywnych kropka jest traktowana jako znak kropki literału, a nie jako klasa znaków. Aby uzyskać więcej informacji, zobacz [Grupa znaków pozytywnych](#PositiveGroup) i [Grupa znaków negatywnych](#NegativeGroup) wcześniej w tym temacie. Poniższy przykład przedstawia ilustrację definiując wyrażenie regularne, które zawiera znak kropki (`.`) zarówno jako klasę znaku, jak i jako element członkowski grupy znaków pozytywnych. `\b.*[.?!;:](\s|\z)` wyrażenia regularnego rozpoczyna się od granicy słowa, dopasowuje dowolny znak, dopóki nie napotka jeden z pięciu znaków interpunkcyjnych, łącznie z kropką, a następnie dopasowuje znak odstępu lub koniec ciągu.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
> Ponieważ dopasowuje dowolny znak, element języka `.` jest często używany z kwantyfikatorem z opóźnieniem, Jeśli wzorzec wyrażenia regularnego próbuje dopasować dowolny znak wielokrotnie. Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a>Kategoria Unicode lub blok Unicode: \p{}  
 W standardzie Unicode każdemu znakowi przypisuje się kategorię ogólną. Na przykład konkretny znak może być wielką literą (reprezentowana przez `Lu` kategorii), cyfrą dziesiętną (`Nd` kategorii), symbolem matematycznym (kategoria `Sm`) lub separatorem akapitu (kategoria `Zl`). Określone zestawy znaków w standardzie Unicode zajmują również określony zakres lub blok kolejnych kodów znaku. Na przykład podstawowy zestaw znaków łacińskich można znaleźć w zakresie od \u0000 do \u007F, podczas gdy zestaw znaków arabskich znajduje się w zakresie od \u0600 do \u06FF.  
  
 Konstrukcja wyrażenia regularnego  
  
 *nazwa* `\p{` `}`  
  
 Dopasowuje dowolny znak, który należy do ogólnej kategorii Unicode lub bloku nazwanego, gdzie *name* jest skrótem kategorii lub nazwą bloku nazwanego. Aby zapoznać się z listą skrótów kategorii, zobacz sekcję [obsługiwane ogólne kategorie Unicode](#SupportedUnicodeGeneralCategories) w dalszej części tego tematu. Aby uzyskać listę nazwanych bloków, zobacz sekcję [obsługiwane bloki nazwane](#SupportedNamedBlocks) w dalszej części tego tematu.  
  
 W poniższym przykładzie zastosowano `\p{`*nazwę*`}` konstrukcja, aby dopasować ją do ogólnej kategorii Unicode (w tym przypadku `Pd`, lub interpunkcji, kategorii kreski) i nazwanego bloku (`IsGreek` i `IsBasicLatin` nazwane bloki).  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 Wyrażenie regularne `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\p{IsGreek}+`|Dopasowuje jeden lub więcej znaków greckich.|  
|`(\s)?`|Dopasowuje zero lub jeden znak odstępu.|  
|`(\p{IsGreek}+(\s)?)+`|Dopasowuje wzorzec jednego lub więcej znaków greckich, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
|`\p{Pd}`|Dopasowuje znak interpunkcyjny kreskę.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\p{IsBasicLatin}+`|Dopasowuje jeden lub więcej znaków łacińskich.|  
|`(\s)?`|Dopasowuje zero lub jeden znak odstępu.|  
|`(\p{IsBasicLatin}+(\s)?)+`|Dopasowuje wzorzec jednego lub większej liczby podstawowych znaków łacińskich, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a>Ujemna kategoria Unicode lub blok Unicode: \p{}  
 W standardzie Unicode każdemu znakowi przypisuje się kategorię ogólną. Na przykład konkretny znak może być wielką literą (reprezentowana przez `Lu` kategorii), cyfrą dziesiętną (`Nd` kategorii), symbolem matematycznym (kategoria `Sm`) lub separatorem akapitu (kategoria `Zl`). Określone zestawy znaków w standardzie Unicode zajmują również określony zakres lub blok kolejnych kodów znaku. Na przykład podstawowy zestaw znaków łacińskich można znaleźć w zakresie od \u0000 do \u007F, podczas gdy zestaw znaków arabskich znajduje się w zakresie od \u0600 do \u06FF.  
  
 Konstrukcja wyrażenia regularnego  
  
 *nazwa* `\P{` `}`  
  
 Dopasowuje dowolny znak, który nie należy do ogólnej kategorii Unicode lub bloku nazwanego, gdzie *name* jest skrótem kategorii lub nazwą bloku nazwanego. Aby zapoznać się z listą skrótów kategorii, zobacz sekcję [obsługiwane ogólne kategorie Unicode](#SupportedUnicodeGeneralCategories) w dalszej części tego tematu. Aby uzyskać listę nazwanych bloków, zobacz sekcję [obsługiwane bloki nazwane](#SupportedNamedBlocks) w dalszej części tego tematu.  
  
 Poniższy przykład używa konstrukcji `\P{`*name*`}` do usuwania symboli walut (w tym przypadku `Sc`lub symbol, Kategoria waluty) z ciągów liczbowych.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Wzorzec wyrażenia regularnego `(\P{Sc})+` dopasowuje co najmniej jeden znak, który nie jest symbolem waluty; efektywnie przyłączają dowolny symbol waluty z ciągu wynikowego.  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a>Znak wyrazu: \w  
 `\w` dopasowuje dowolny znak słowa. Znak słowa jest elementem członkowskim każdej z kategorii Unicode wymienionej w poniższej tabeli.  
  
|Kategoria|Opis|  
|--------------|-----------------|  
|Ll|Litera, Małe litery|  
|Lu|Litera, Wielkie litery|  
|Lt|Litera, Duże litery na początku wyrazu|  
|Lo|Litera, Inne|  
|Lm|Litera, Modyfikator|  
|Mn|Znak, Brak odstępów|  
|Nd|Liczba, Cyfra dziesiętna|  
|Pc|Znak interpunkcyjny, Łącznik. Ta kategoria obejmuje dziesięć znaków, z których najczęściej używany jest znak LOWLINE (_), u+005F.|  
  
 Jeśli określono zachowanie zgodne ze standardem ECMAScript, `\w` jest równoznaczne z `[a-zA-Z_0-9]`. Aby uzyskać informacje na temat wyrażeń regularnych języka ECMAScript, zobacz sekcję "zachowanie zgodne z językiem ECMAScript" w [opcjach wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Ponieważ dopasowuje dowolny znak słowa, element języka `\w` jest często używany z kwantyfikatorem z opóźnieniem, Jeśli wzorzec wyrażenia regularnego próbuje dopasować dowolny znak wyrazu wielokrotnie, po którym następuje określony znak słowa. Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 W poniższym przykładzie użyto elementu języka `\w`, aby dopasować zduplikowane znaki w wyrazie. W przykładzie zdefiniowano wzorzec wyrażenia regularnego, `(\w)\1`, który może być interpretowany w następujący sposób.  
  
|Element|Opis|  
|-------------|-----------------|  
|(\w)|Dopasowuje znak słowa. Jest to pierwsza grupa przechwytywania.|  
|\ 1|Dopasowuje wartość pierwszego przechwycenia.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a>Znak niebędący słowem: \w  
 `\W` dopasowuje dowolny znak niebędący słowem. Element języka \W jest równoważny z następującą klasą znaków:  
  
`[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]`  
  
 Innymi słowy, dopasowuje dowolny znak z wyjątkiem tych w kategoriach Unicode wymienionych w poniższej tabeli.  
  
|Kategoria|Opis|  
|--------------|-----------------|  
|Ll|Litera, Małe litery|  
|Lu|Litera, Wielkie litery|  
|Lt|Litera, Duże litery na początku wyrazu|  
|Lo|Litera, Inne|  
|Lm|Litera, Modyfikator|  
|Mn|Znak, Brak odstępów|  
|Nd|Liczba, Cyfra dziesiętna|  
|Pc|Znak interpunkcyjny, Łącznik. Ta kategoria obejmuje dziesięć znaków, z których najczęściej używany jest znak LOWLINE (_), u+005F.|  
  
 Jeśli określono zachowanie zgodne ze standardem ECMAScript, `\W` jest równoznaczne z `[^a-zA-Z_0-9]`. Aby uzyskać informacje na temat wyrażeń regularnych języka ECMAScript, zobacz sekcję "zachowanie zgodne z językiem ECMAScript" w [opcjach wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Ponieważ dopasowuje dowolny znak niebędący słowem, element języka `\W` jest często używany z kwantyfikatorem z opóźnieniem, Jeśli wzorzec wyrażenia regularnego próbuje dopasować dowolny znak niebędący słowem, po którym następuje określony znak niebędący słowem. Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
 Poniższy przykład ilustruje klasę znaków `\W`.  Definiuje wzorzec wyrażenia regularnego, `\b(\w+)(\W){1,2}`, który pasuje do wyrazu, po którym następuje jeden lub dwa znaki niebędące słowami, takie jak odstępy czy interpunkcja. Wyrażenie regularne jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|\b|Rozpoczyna dopasowanie na granicy wyrazu.|  
|(\w+)|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|(\W){1,2}|Dopasowuje znak niebędący znakiem słowa jeden lub dwa razy. Jest to druga grupa przechwytywania.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 Ponieważ obiekt <xref:System.Text.RegularExpressions.Group> dla drugiej grupy przechwytywania zawiera tylko jeden przechwycony znak niebędący słowem, a przykład pobiera wszystkie przechwycone znaki niebędące słowami z obiektu <xref:System.Text.RegularExpressions.CaptureCollection>, który jest zwracany przez właściwość <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.  
  
<a name="WhitespaceCharacter"></a>   
## <a name="whitespace-character-s"></a>Znak odstępu: \s  
 `\s` dopasowuje dowolny znak odstępu. Jest to równoważne z sekwencjami ucieczki oraz kategoriami Unicode wymienionymi w poniższej tabeli.  
  
|Kategoria|Opis|  
|--------------|-----------------|  
|`\f`|Znak wysuwu strony, \u000C.|  
|`\n`|Znak nowego wiersza, \u000A.|  
|`\r`|Znaku powrotu karetki, \u000D.|  
|`\t`|Znak tabulacji, \u0009.|  
|`\v`|Znak tabulacji pionowej, \u000B.|  
|`\x85`|Wielokropek lub znak NEXT LINE (NEL) (...), \u0085.|  
|`\p{Z}`|Dopasowuje dowolny znak separatora.|  
  
 Jeśli określono zachowanie zgodne ze standardem ECMAScript, `\s` jest równoznaczne z `[ \f\n\r\t\v]`. Aby uzyskać informacje na temat wyrażeń regularnych języka ECMAScript, zobacz sekcję "zachowanie zgodne z językiem ECMAScript" w [opcjach wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Poniższy przykład ilustruje klasę znaków `\s`. Definiuje wzorzec wyrażenia regularnego, `\b\w+(e)?s(\s|$)`, który pasuje do wyrazu kończącego się na "s" lub "es", po którym następuje znak odstępu lub koniec ciągu wejściowego. Wyrażenie regularne jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|\b|Rozpoczyna dopasowanie na granicy wyrazu.|  
|\w+|Dopasowuje co najmniej jeden znak słowa.|  
|(e)?|Dopasowuje znak „e” zero lub jeden raz.|  
|s|Dopasowuje znak „s”.|  
|(\s&#124;$)|Dopasowuje znak odstępu lub koniec ciągu wejściowego.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-whitespace-character-s"></a>Znak niebędący odstępem: \s  
 `\S` dopasowuje dowolny znak niebędący odstępem. Jest on odpowiednikiem wzorca wyrażenia regularnego `[^\f\n\r\t\v\x85\p{Z}]` lub przeciwieństwem wzorca wyrażenia regularnego, który jest odpowiednikiem `\s`, który jest zgodny ze znakami odstępu. Aby uzyskać więcej informacji, zobacz znak odstępu [: \s](#WhitespaceCharacter).  
  
 Jeśli określono zachowanie zgodne ze standardem ECMAScript, `\S` jest równoznaczne z `[^ \f\n\r\t\v]`. Aby uzyskać informacje na temat wyrażeń regularnych języka ECMAScript, zobacz sekcję "zachowanie zgodne z językiem ECMAScript" w [opcjach wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Poniższy przykład ilustruje `\S` element języka. Wzorzec wyrażenia regularnego `\b(\S+)\s?` dopasowuje ciągi, które są rozdzielane znakami odstępu. Drugi element w obiekcie <xref:System.Text.RegularExpressions.GroupCollection> Match zawiera dopasowany ciąg. Wyrażenie regularne może być interpretowane tak jak pokazano w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\S+)`|Dopasowuje jeden lub więcej znaków niebędących znakami odstępu. Jest to pierwsza grupa przechwytywania.|  
|`\s?`|Dopasowuje zero lub jeden znak odstępu.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a>Znak cyfry dziesiętnej: \d  
 `\d` dopasowuje dowolną cyfrę dziesiętną. Jest to odpowiednik wzorca wyrażenia regularnego `\p{Nd}`, który zawiera standardowe cyfry dziesiętne 0-9, a także cyfry dziesiętne wielu innych zestawów znaków.  
  
 Jeśli określono zachowanie zgodne ze standardem ECMAScript, `\d` jest równoznaczne z `[0-9]`. Aby uzyskać informacje na temat wyrażeń regularnych języka ECMAScript, zobacz sekcję "zachowanie zgodne z językiem ECMAScript" w [opcjach wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
 Poniższy przykład ilustruje `\d` element języka. Sprawdza, czy ciąg wejściowy reprezentuje prawidłowy numeru telefonu w Stanach Zjednoczonych i Kanadzie. `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`\(?`|Dopasowuje zero lub jeden literał znakowy „(”.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`\)?`|Dopasowuje zero lub jeden literał znakowy „)”.|  
|`[\s-]`|Dopasowuje łącznik lub znak odstępu.|  
|`(\(?\d{3}\)?[\s-])?`|Dopasowuje opcjonalny nawias otwierający, po którym zero lub jeden raz następują trzy cyfry dziesiętne, opcjonalny nawias zamykający i znak odstępu lub łącznik. Jest to pierwsza grupa przechwytywania.|  
|`\d{3}-\d{4}`|Dopasowuje trzy cyfry dziesiętne, po których następuje łącznik i cztery następne cyfry dziesiętne.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a>Znak niebędący cyfrą: \d  
 `\D` dopasowuje dowolny znak niebędący cyfrą. Jest to odpowiednik wzorca wyrażenia regularnego `\P{Nd}`.  
  
 Jeśli określono zachowanie zgodne ze standardem ECMAScript, `\D` jest równoznaczne z `[^0-9]`. Aby uzyskać informacje na temat wyrażeń regularnych języka ECMAScript, zobacz sekcję "zachowanie zgodne z językiem ECMAScript" w [opcjach wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
 W poniższym przykładzie pokazano element języka \D. Sprawdza, czy ciąg, taki jak numer części, zawiera odpowiednią kombinację znaków dziesiętnych oraz niebędących dziesiętnymi. `^\D\d{1,5}\D*$` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`\D`|Dopasowuje znak niebędący cyfrą.|  
|`\d{1,5}`|Dopasowuje od jednej do pięciu cyfr dziesiętnych.|  
|`\D*`|Dopasowuje zero, jeden lub więcej znaków niebędących cyframi dziesiętnymi.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a>Obsługiwane kategorie ogólne Unicode  
 Standard Unicode określa ogólne kategorie wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz temat "UCD File Format" i "ogólne wartości kategorii" w [bazie danych znaków Unicode](https://www.unicode.org/reports/tr44/).  
  
|Kategoria|Opis|  
|--------------|-----------------|  
|`Lu`|Litera, Wielkie litery|  
|`Ll`|Litera, Małe litery|  
|`Lt`|Litera, Duże litery na początku wyrazu|  
|`Lm`|Litera, Modyfikator|  
|`Lo`|Litera, Inne|  
|`L`|Wszystkie znaki liter. Obejmuje to `Lu`, `Ll`, `Lt`, `Lm`i `Lo` znaków.|  
|`Mn`|Znak, Brak odstępów|  
|`Mc`|Znak, Odstępy mieszane|  
|`Me`|Znak, Dołączenie|  
|`M`|Wszystkie znaki diakrytyczne. Obejmuje to kategorie `Mn`, `Mc`i `Me`.|  
|`Nd`|Liczba, Cyfra dziesiętna|  
|`Nl`|Liczba, Litera|  
|`No`|Liczba, Inne|  
|`N`|Wszystkie liczby. Obejmuje to kategorie `Nd`, `Nl`i `No`.|  
|`Pc`|Znak interpunkcyjny, Łącznik|  
|`Pd`|Znak interpunkcyjny, Kreska|  
|`Ps`|Znak interpunkcyjny, Otwarcie|  
|`Pe`|Znak interpunkcyjny, Zamknięcie|  
|`Pi`|Znak interpunkcyjny, Cudzysłów początkowy (może zachowywać się jak Ps i Pe w zależności od użycia)|  
|`Pf`|Znak interpunkcyjny, Cudzysłów końcowy (może zachowywać się jak Ps i Pe w zależności od użycia)|  
|`Po`|Znak interpunkcyjny, Inne|  
|`P`|Wszystkie znaki interpunkcyjne. Obejmuje to `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`i `Po` kategorii.|  
|`Sm`|Symbol, Matematyczne|  
|`Sc`|Symbol, Waluta|  
|`Sk`|Symbol, Modyfikator|  
|`So`|Symbol, Inne|  
|`S`|Wszystkie symbole. Obejmuje to `Sm`, `Sc`, `Sk`i `So` kategorii.|  
|`Zs`|Separator, Spacja|  
|`Zl`|Separator, Wiersz|  
|`Zp`|Separator, Akapit|  
|`Z`|Wszystkie znaki separatora. Obejmuje to kategorie `Zs`, `Zl`i `Zp`.|  
|`Cc`|Inne, Sterowanie|  
|`Cf`|Inne, Format|  
|`Cs`|Inne, Zastępcze|  
|`Co`|Inne, Do użytku prywatnego|  
|`Cn`|Inne, Nieprzypisane (żadne znaki nie mają tej właściwości)|  
|`C`|Wszystkie znaki kontrolne. Obejmuje to `Cc`, `Cf`, `Cs`, `Co`i `Cn` kategorii.|  
  
 Możesz określić kategorię Unicode dowolnego określonego znaku, przekazując ten znak do metody <xref:System.Char.GetUnicodeCategory%2A>. W poniższym przykładzie zastosowano metodę <xref:System.Char.GetUnicodeCategory%2A>, aby określić kategorię każdego elementu w tablicy, która zawiera wybrane znaki łacińskie.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a>Obsługiwane nazwane bloki

Platforma .NET udostępnia nazwane bloki wymienione w poniższej tabeli. Zestaw obsługiwanych bloków nazwanych jest oparty na standardach Unicode 4.0 i Perl 5.6. W przypadku wyrażenia regularnego, które używa nazwanych bloków, zobacz sekcję [Kategoria Unicode lub blok Unicode: \\p{}](#unicode-category-or-unicode-block-p) .  
  
|Zakres kodów znaków|Nazwa bloku|  
|----------------------|----------------|  
|0000–007F|`IsBasicLatin`|  
|0080–00FF|`IsLatin-1Supplement`|  
|0100–017F|`IsLatinExtended-A`|  
|0180–024F|`IsLatinExtended-B`|  
|0250–02AF|`IsIPAExtensions`|  
|02B0–02FF|`IsSpacingModifierLetters`|  
|0300–036F|`IsCombiningDiacriticalMarks`|  
|0370–03FF|`IsGreek`<br /><br /> —lub—<br /><br /> `IsGreekandCoptic`|  
|0400–04FF|`IsCyrillic`|  
|0500–052F|`IsCyrillicSupplement`|  
|0530–058F|`IsArmenian`|  
|0590–05FF|`IsHebrew`|  
|0600–06FF|`IsArabic`|  
|0700–074F|`IsSyriac`|  
|0780–07BF|`IsThaana`|  
|0900–097F|`IsDevanagari`|  
|0980–09FF|`IsBengali`|  
|0A00–0A7F|`IsGurmukhi`|  
|0A80–0AFF|`IsGujarati`|  
|0B00–0B7F|`IsOriya`|  
|0B80–0BFF|`IsTamil`|  
|0C00–0C7F|`IsTelugu`|  
|0C80–0CFF|`IsKannada`|  
|0D00–0D7F|`IsMalayalam`|  
|0D80–0DFF|`IsSinhala`|  
|0E00–0E7F|`IsThai`|  
|0E80–0EFF|`IsLao`|  
|0F00–0FFF|`IsTibetan`|  
|1000–109F|`IsMyanmar`|  
|10A0–10FF|`IsGeorgian`|  
|1100–11FF|`IsHangulJamo`|  
|1200–137F|`IsEthiopic`|  
|13A0–13FF|`IsCherokee`|  
|1400–167F|`IsUnifiedCanadianAboriginalSyllabics`|  
|1680–169F|`IsOgham`|  
|16A0–16FF|`IsRunic`|  
|1700–171F|`IsTagalog`|  
|1720–173F|`IsHanunoo`|  
|1740–175F|`IsBuhid`|  
|1760–177F|`IsTagbanwa`|  
|1780–17FF|`IsKhmer`|  
|1800–18AF|`IsMongolian`|  
|1900–194F|`IsLimbu`|  
|1950–197F|`IsTaiLe`|  
|19E0–19FF|`IsKhmerSymbols`|  
|1D00–1D7F|`IsPhoneticExtensions`|  
|1E00–1EFF|`IsLatinExtendedAdditional`|  
|1F00–1FFF|`IsGreekExtended`|  
|2000–206F|`IsGeneralPunctuation`|  
|2070–209F|`IsSuperscriptsandSubscripts`|  
|20A0–20CF|`IsCurrencySymbols`|  
|20D0–20FF|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> —lub—<br /><br /> `IsCombiningMarksforSymbols`|  
|2100–214F|`IsLetterlikeSymbols`|  
|2150–218F|`IsNumberForms`|  
|2190–21FF|`IsArrows`|  
|2200–22FF|`IsMathematicalOperators`|  
|2300–23FF|`IsMiscellaneousTechnical`|  
|2400–243F|`IsControlPictures`|  
|2440–245F|`IsOpticalCharacterRecognition`|  
|2460–24FF|`IsEnclosedAlphanumerics`|  
|2500–257F|`IsBoxDrawing`|  
|2580–259F|`IsBlockElements`|  
|25A0–25FF|`IsGeometricShapes`|  
|2600–26FF|`IsMiscellaneousSymbols`|  
|2700–27BF|`IsDingbats`|  
|27C0–27EF|`IsMiscellaneousMathematicalSymbols-A`|  
|27F0–27FF|`IsSupplementalArrows-A`|  
|2800–28FF|`IsBraillePatterns`|  
|2900–297F|`IsSupplementalArrows-B`|  
|2980–29FF|`IsMiscellaneousMathematicalSymbols-B`|  
|2A00–2AFF|`IsSupplementalMathematicalOperators`|  
|2B00–2BFF|`IsMiscellaneousSymbolsandArrows`|  
|2E80–2EFF|`IsCJKRadicalsSupplement`|  
|2F00–2FDF|`IsKangxiRadicals`|  
|2FF0–2FFF|`IsIdeographicDescriptionCharacters`|  
|3000–303F|`IsCJKSymbolsandPunctuation`|  
|3040–309F|`IsHiragana`|  
|30A0–30FF|`IsKatakana`|  
|3100–312F|`IsBopomofo`|  
|3130–318F|`IsHangulCompatibilityJamo`|  
|3190–319F|`IsKanbun`|  
|31A0–31BF|`IsBopomofoExtended`|  
|31F0–31FF|`IsKatakanaPhoneticExtensions`|  
|3200–32FF|`IsEnclosedCJKLettersandMonths`|  
|3300–33FF|`IsCJKCompatibility`|  
|3400–4DBF|`IsCJKUnifiedIdeographsExtensionA`|  
|4DC0–4DFF|`IsYijingHexagramSymbols`|  
|4E00–9FFF|`IsCJKUnifiedIdeographs`|  
|A000–A48F|`IsYiSyllables`|  
|A490–A4CF|`IsYiRadicals`|  
|AC00–D7AF|`IsHangulSyllables`|  
|D800–DB7F|`IsHighSurrogates`|  
|DB80–DBFF|`IsHighPrivateUseSurrogates`|  
|DC00–DFFF|`IsLowSurrogates`|  
|E000–F8FF|`IsPrivateUse` lub `IsPrivateUseArea`|  
|F900–FAFF|`IsCJKCompatibilityIdeographs`|  
|FB00–FB4F|`IsAlphabeticPresentationForms`|  
|FB50–FDFF|`IsArabicPresentationForms-A`|  
|FE00–FE0F|`IsVariationSelectors`|  
|FE20–FE2F|`IsCombiningHalfMarks`|  
|FE30–FE4F|`IsCJKCompatibilityForms`|  
|FE50–FE6F|`IsSmallFormVariants`|  
|FE70–FEFF|`IsArabicPresentationForms-B`|  
|FF00–FFEF|`IsHalfwidthandFullwidthForms`|  
|FFF0–FFFF|`IsSpecials`|  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-base_group---excluded_group"></a>Odejmowanie klasy znaków: [Base_group-[Excluded_group]]  
 Klasy znaków definiuje zestaw znaków. Wynikiem odejmowania klas znaków jest zestaw znaków będący wynikiem wykluczenia znaków jednej klasy znaków z innej klasy znaków.  
  
 Wyrażenie odejmowania klas znaków ma następującą formę:  
  
 `[` *base_group* `-[` *Excluded_group* `]]`  
  
 Nawiasy kwadratowe (`[]`) i łącznik (`-`) są obowiązkowe. *Base_group* jest [grupą znaków pozytywnych](#PositiveGroup) lub [grupą znaków negatywnych](#NegativeGroup). Składnik *Excluded_group* jest kolejną dodatnią lub ujemną grupą znaków lub innym wyrażeniem odejmowania klasy znaków (to oznacza, że można zagnieżdżać wyrażenia odejmowania klas znaków).  
  
 Na przykład załóżmy że grupa podstawowa składa się z zakresu znaków od „a” do „z”. Aby zdefiniować zestaw znaków, który składa się z grupy podstawowej z wyjątkiem znaku "m", użyj `[a-z-[m]]`. Aby zdefiniować zestaw znaków, który składa się z grupy podstawowej z wyjątkiem zestawu znaków "d", "j" i "p", użyj `[a-z-[djp]]`. Aby zdefiniować zestaw znaków, który składa się z grupy podstawowej z wyjątkiem zakresu znaków od "m" do "p", użyj `[a-z-[m-p]]`.  
  
 Rozważ wyrażenie odejmowania klasy znaków zagnieżdżonych, `[a-z-[d-w-[m-o]]]`. To wyrażenie jest wykonywane począwszy od najbardziej wewnętrznego zakresu znaków na zewnątrz. Najpierw zakres znaków od „m” do „o” jest odejmowany od zakresu znaków od „d” do „w”, wynikiem czego jest zestaw znaków od „d” do „l” oraz od „p” do „w”. Ten zestaw jest następnie odejmowany od zakresu znaków od "a" do "z", który daje zestaw znaków `[abcmnoxyz]`.  
  
 Można odejmować dowolne klasy znaków. Aby zdefiniować zestaw znaków, który składa się ze wszystkich znaków Unicode od \u0000 do \uFFFF, z wyjątkiem białych znaków (`\s`), znaków w ogólnej kategorii (`\p{P}`), znaki w `IsGreek` nazwanym bloku (`\p{IsGreek}`) i znak kontrolny następnej linii Unicode (\x85), użyj `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.  
  
 W wyrażeniach odejmowania klas znaków należy używać klas znaków umożliwiających zwrócenie przydatnych wyników. Należy unikać wyrażeń, które zwracają puste zestawy znaków, które nie mogą nic dopasować, oraz wyrażeń, które są równoważne oryginalnej grupie podstawowej. Na przykład, pusty zestaw jest wynikiem wyrażenia `[\p{IsBasicLatin}-[\x00-\x7F]]`, co odejmuje wszystkie znaki w zakresie znaków `IsBasicLatin` z ogólnej kategorii `IsBasicLatin`. Analogicznie, oryginalna Grupa podstawowa jest wynikiem wyrażenia `[a-z-[0-9]]`.  Dzieje się tak, ponieważ grupa podstawowa, czyli zakres znaków od „a” do „z”, nie zawiera żadnych znaków z grupy wykluczanej, która jest zakresem cyfr dziesiętnych od „0” do „9”.  
  
 Poniższy przykład definiuje wyrażenie regularne `^[0-9-[2468]]+$`, które dopasowuje zero i nieparzystą cyfr w ciągu wejściowym.  Wyrażenie regularne jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|^|Dopasowywanie rozpoczyna się początku ciągu wejściowego.|  
|`[0-9-[2468]]+`|Dopasowuje jedno lub więcej wystąpień dowolnego znaku z zakresu od 0 do 9 z wyjątkiem 2, 4, 6 i 8. Innymi słowy, dopasowuje co najmniej jedno wystąpienie zera lub cyfry nieparzystej.|  
|$|Dopasowywanie kończy się na końcu ciągu wejściowego.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Char.GetUnicodeCategory%2A>
- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)
