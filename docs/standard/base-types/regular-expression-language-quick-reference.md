---
title: Język wyrażeń regularnych — podręczny wykaz
ms.date: 03/30/2017
ms.technology: dotnet-standard
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8a2cb64d4dcfba1580d714c7dffae7e91ef01fb
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040986"
---
# <a name="regular-expression-language---quick-reference"></a>Język wyrażeń regularnych — podręczny wykaz

Wyrażenie regularne to wzorzec, który aparat wyrażeń regularnych próbuje dopasować w tekście wejściowym. Wzorzec składa się z co najmniej jednego literału znakowego, operatora lub konstrukcji. Aby zapoznać się z krótkim wprowadzeniem, zobacz [wyrażenia regularne programu .NET](regular-expressions.md).

Każda sekcja w tym przewodniku szybkim zawiera listę znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.

Podano również te informacje w dwóch formatach, które można pobrać i wydrukować w celu łatwego odwoływania się:

- [Pobierz w formacie programu Word (docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Pobierz w formacie PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Znaki unikowe

Znak ukośnika odwrotnego (\\) w wyrażeniu regularnym wskazuje, że znak, który następuje po nim jest znakiem specjalnym (jak pokazano w poniższej tabeli) lub powinien być interpretowany dosłownie. Aby uzyskać więcej informacji, zobacz [znak ucieczki](character-escapes-in-regular-expressions.md).

|Znak poprzedzony znakiem ucieczki|Opis|Wzorzec|Dopasowania|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Dopasowuje znak sygnału dźwiękowego, \u0007.|`\a`|`"\u0007"` w `"Error!" + '\u0007'`|
|`\b`|W klasie znaków dopasowuje znak backspace, \u0008.|`[\b]{3,}`|`"\b\b\b\b"` w `"\b\b\b\b"`|
|`\t`|Dopasowuje znak tabulatora, \u0009.|`(\w+)\t`|`"item1\t"`, `"item2\t"` w `"item1\titem2\t"`|
|`\r`|Dopasowuje znak powrotu karetki, \u000D (`\r` nie jest odpowiednikiem znaku nowego wiersza, `\n`).|`\r\n(\w+)`|`"\r\nThese"` w `"\r\nThese are\ntwo lines."`|
|`\v`|Dopasowuje tabulator pionowy, \u000B.|`[\v]{2,}`|`"\v\v\v"` w `"\v\v\v"`|
|`\f`|Dopasowuje znak wysuwu strony, \u000C.|`[\f]{2,}`|`"\f\f\f"` w `"\f\f\f"`|
|`\n`|Dopasowuje znak nowego wiersza, \u000A.|`\r\n(\w+)`|`"\r\nThese"` w `"\r\nThese are\ntwo lines."`|
|`\e`|Dopasowuje znak escape, \u001B.|`\e`|`"\x001B"` w `"\x001B"`|
|`\` *nnn*|Używa reprezentacji ósemkowej do określenia znaku (*nnn* składa się z dwóch lub trzech cyfr).|`\w\040\w`|`"a b"`, `"c d"` w `"a bc d"`|
|`\x` *NN*|Używa reprezentacji szesnastkowej w celu określenia znaku (*NN* składa się z dokładnie dwóch cyfr).|`\w\x20\w`|`"a b"`, `"c d"` w `"a bc d"`|
|`\c` *X*<br /><br /> `\c` *x*|Dopasowuje znak kontrolny ASCII, który jest określony przez *x* lub *x*, gdzie *x* lub *x* jest literą znaku kontrolnego.|`\cC`|`"\x0003"` w `"\x0003"` (Ctrl-C)|
|`\u` *nnnn*|Dopasowuje znak Unicode przy użyciu reprezentacji szesnastkowej (dokładnie cztery cyfry, reprezentowane przez *nnnn*).|`\w\u0020\w`|`"a b"`, `"c d"` w `"a bc d"`|
|`\`|Kiedy następuje po nim znak, który nie jest rozpoznawany jako znak ucieczki w tej lub innej tabeli zawartej w tym temacie, dopasowuje ten znak. Na przykład `\*` jest taka sama jak `\x2A`, a `\.` jest taka sama jak `\x2E`. Dzięki temu aparat wyrażeń regularnych może odróżnić elementy języka (takie jak \* lub?) i literały znakowe (reprezentowane przez `\*` lub `\?`).|`\d+[\+-x\*]\d+`|`"2+2"` i `"3*9"` w `"(2+2) * 3*9"`|

## <a name="character-classes"></a>Klasy znaku

Klasa znaków dopasowuje dowolny zestaw znaków. Klasy znaków obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [klasy znaków](character-classes-in-regular-expressions.md).

|Klasa znaków|Opis|Wzorzec|Dopasowania|
|---------------------|-----------------|-------------|-------------|
|`[` *character_group* `]`|Dopasowuje dowolny pojedynczy znak w *character_group*. Domyślnie w dopasowaniu jest uwzględniana wielkość liter.|`[ae]`|`"a"` w `"gray"`<br /><br /> `"a"`, `"e"` w `"lane"`|
|`[^` *character_group* `]`|Negacja: dopasowuje dowolny pojedynczy znak, który nie znajduje się w *character_group*. Domyślnie znaki w *character_group* uwzględniają wielkość liter.|`[^aei]`|`"r"`, `"g"`, `"n"` w `"reign"`|
|`[` *pierwsze* `-` *ostatnim* `]`|Zakres znaków: dopasowuje dowolny pojedynczy znak z zakresu od *pierwszego* do *ostatniego*.|`[A-Z]`|`"A"`, `"B"` w `"AB123"`|
|`.`|Symbol wieloznaczny: Dopasowuje każdy pojedynczy znak, oprócz znaku \n.<br /><br /> Aby dopasować znak kropki literału (. lub `\u002E`), musisz poprzedzać znak ucieczki (`\.`).|`a.e`|`"ave"` w `"nave"`<br /><br /> `"ate"` w `"water"`|
|*nazwa* `\p{` `}`|Dopasowuje dowolny pojedynczy znak z ogólnej kategorii Unicode lub nazwanego bloku określonego przez *nazwę*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"`, `"L"` w `"City Lights"`<br /><br /> `"Д"`, `"Ж"` w `"ДЖem"`|
|*nazwa* `\P{` `}`|Dopasowuje dowolny pojedynczy znak, który nie należy do ogólnej kategorii Unicode lub bloku o nazwie określonej przez *nazwę*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"`, `"y"` w `"City"`<br /><br /> `"e"`, `"m"` w `"ДЖem"`|
|`\w`|Dopasowuje dowolny znak słowa.|`\w`|`"I"`, `"D"`, `"A"`, `"1"`, `"3"` w `"ID A1.3"`|
|`\W`|Dopasowuje dowolny znak niebędący znakiem słowa.|`\W`|`" "`, `"."` w `"ID A1.3"`|
|`\s`|Dopasowuje dowolny znak odstępu.|`\w\s`|`"D "` w `"ID A1.3"`|
|`\S`|Dopasowuje dowolny znak niebędący znakiem odstępu.|`\s\S`|`" _"` w `"int __ctr"`|
|`\d`|Dopasowuje dowolną cyfrę dziesiętną.|`\d`|`"4"` w `"4 = IV"`|
|`\D`|Dopasowuje dowolny znak inny niż cyfra dziesiętna.|`\D`|`" "`, `"="`, `" "`, `"I"`, `"V"` w `"4 = IV"`|

## <a name="anchors"></a>Kotwice

Kotwice (niepodzielne asercje o zerowej szerokości) powodują, że sukces lub niepowodzenie dopasowywania jest zależne od bieżącej pozycji w ciągu, ale nie powodują, że aparat przechodzi do dalszej części ciągu lub używa znaków. Metaznaki wymienione w poniższej tabeli są kotwicami. Aby uzyskać więcej informacji, zobacz [kotwice](anchors-in-regular-expressions.md).

|Asercja|Opis|Wzorzec|Dopasowania|
|---------------|-----------------|-------------|-------------|
|`^`|Domyślnie dopasowanie musi rozpoczynać się na początku ciągu znaków. w trybie wielowierszowym, musi rozpoczynać się na początku wiersza.|`^\d{3}`|`"901"` w `"901-333-"`|
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu; w trybie wielowierszowym musi następować przed końcem wiersza lub przed `\n` na końcu wiersza.|`-\d{3}$`|`"-333"` w `"-901-333"`|
|`\A`|Dopasowanie musi wystąpić na początku ciągu.|`\A\d{3}`|`"901"` w `"901-333-"`|
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu.|`-\d{3}\Z`|`"-333"` w `"-901-333"`|
|`\z`|Dopasowanie musi wystąpić na końcu ciągu.|`-\d{3}\z`|`"-333"` w `"-901-333"`|
|`\G`|Dopasowanie musi wystąpić w punkcie, w którym kończy się poprzednie dopasowanie.|`\G\(\d\)`|`"(1)"`, `"(3)"`, `"(5)"` w `"(1)(3)(5)[7](9)"`|
|`\b`|Dopasowanie musi wystąpić na granicy między `\w` (alfanumeryczne) i `\W` (niealfanumeryczne).|`\b\w+\s\w+\b`|`"them theme"`, `"them them"` w `"them theme them them"`|
|`\B`|Dopasowanie nie może wystąpić na granicy `\b`.|`\Bend\w*\b`|`"ends"`, `"ender"` w `"end sends endure lender"`|

## <a name="grouping-constructs"></a>Konstrukty grupujące

Konstrukcje grupujące wyznaczają podwyrażenia wyrażeń regularnych i często przechwytywane podciągi ciągu wejściowego. Konstrukcje grupowania obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).

|Konstrukcja grupująca|Opis|Wzorzec|Dopasowania|
|------------------------|-----------------|-------------|-------------|
|`(` *Podwyrażenie* `)`|Przechwytuje dopasowane podwyrażenia i przypisuje mu liczbę porządkową (liczone od zera).|`(\w)\1`|`"ee"` w `"deep"`|
|*nazwa* `(?<` `>` *podwyrażeniem* `)`|Przechwytuje dopasowane podwyrażenie do nazwanej grupy.|`(?<double>\w)\k<double>`|`"ee"` w `"deep"`|
|`(?<` *name1* `-` *NAME2* `>` *podwyrażenia* `)`|Określa definicję grupy równoważącej. Aby uzyskać więcej informacji, zobacz sekcję "Definicja grupy równoważenia" w temacie [grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"((1-3)*(3-1))"` w `"3+2^((1-3)*(3-1))"`|
|`(?:` *Podwyrażenie* `)`|Definiuje nieprzechwytywaną grupę.|`Write(?:Line)?`|`"WriteLine"` w `"Console.WriteLine()"`<br /><br /> `"Write"` w `"Console.Write(value)"`|
|`(?imnsx-imnsx:` *Podwyrażenie* `)`|Stosuje lub wyłącza określone opcje w ramach *podwyrażenia*. Aby uzyskać więcej informacji, zobacz [Opcje wyrażenia regularnego](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"`, `"A12XL"` w `"A12xl A12XL a12xl"`|
|`(?=` *Podwyrażenie* `)`|Pozytywna asercja wyprzedzająca o zerowej szerokości.|`\w+(?=\.)`|`"is"`, `"ran"`i `"out"` w `"He is. The dog ran. The sun is out."`|
|`(?!` *Podwyrażenie* `)`|Negatywna asercja wyprzedzająca o zerowej szerokości.|`\b(?!un)\w+\b`|`"sure"`, `"used"` w `"unsure sure unity used"`|
|`(?<=` *Podwyrażenie* `)`|Pozytywna asercja wsteczna o zerowej szerokości.|`(?<=19)\d{2}\b`|`"99"`, `"50"`, `"05"` w `"1851 1999 1950 1905 2003"`|
|`(?<!` *Podwyrażenie* `)`|Negatywna asercja wsteczna o zerowej szerokości.|`(?<!19)\d{2}\b`|`"51"`, `"03"` w `"1851 1999 1950 1905 2003"`|
|`(?>` *Podwyrażenie* `)`|Podwyrażenia bez wycofywania („zachłanne”)|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"`i `"5AB"` w `"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Kwantyfikatory

Kwantyfikator określa, ile wystąpień poprzedniego elementu (którym może być znak, grupa lub klasa znaków) musi znajdować się w ciągu wejściowym, aby wystąpiło dopasowanie. Kwantyfikatory obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](quantifiers-in-regular-expressions.md).

|Kwantyfikator|Opis|Wzorzec|Dopasowania|
|----------------|-----------------|-------------|-------------|
|`*`|Dopasowuje poprzedni element zero lub większą liczbę razy.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Dopasowuje poprzedni element co najmniej raz.|`"be+"`|`"bee"` w `"been"`, `"be"` w `"bent"`|
|`?`|Dopasowuje poprzedni element zero lub jeden raz.|`"rai?n"`|`"ran"`, `"rain"`|
|`{` *n* `}`|Dopasowuje poprzedni element dokładnie *n* razy.|`",\d{3}"`|`",043"` `"1,043.6"`, `",876"`, `",543"`i `",210"` w `"9,876,543,210"`|
|`{` *n* `,}`|Dopasowuje poprzedni element co najmniej *n* razy.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{` *n* `,` *m* `}`|Dopasowuje poprzedni element co najmniej *n* razy, ale nie więcej niż *m* razy.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"19302"` w `"193024"`|
|`*?`|Dopasowuje poprzedni element zero lub większą liczbę razy (przy czym ta liczba jest jak najmniejsza).|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Dopasowuje poprzedni element raz lub większą liczbę razy (przy czym ta liczba jest jak najmniejsza).|`"be+?"`|`"be"` w `"been"`, `"be"` w `"bent"`|
|`??`|Dopasowuje poprzedni element zero lub jeden raz (przy czym liczba dopasowań jest jak najmniejsza).|`"rai??n"`|`"ran"`, `"rain"`|
|`{` *n* `}?`|Dopasowuje poprzedzający element dokładnie *n* razy.|`",\d{3}?"`|`",043"` `"1,043.6"`, `",876"`, `",543"`i `",210"` w `"9,876,543,210"`|
|`{` *n* `,}?`|Dopasowuje poprzedni element co najmniej *n* razy, ale tyle razy, ile to możliwe.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{` *n* `,` *m* `}?`|Dopasowuje poprzedni element między *n* i *m* razy, ale tyle razy, ile to możliwe.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"`, `"024"` w `"193024"`|

## <a name="backreference-constructs"></a>Konstrukty grupowania wstecznego

Dopasowywanie wsteczne umożliwia kolejne identyfikacje uprzednio dopasowanego podwyrażenia w tym samym wyrażeniu regularnym. W poniższej tabeli wymieniono konstrukcje odwołań wstecznych obsługiwane przez wyrażenia regularne w programie .NET. Aby uzyskać więcej informacji, zobacz [konstrukcje odwołań wstecznych](backreference-constructs-in-regular-expressions.md).

|Konstrukcja dopasowywania wstecznego|Opis|Wzorzec|Dopasowania|
|-----------------------------|-----------------|-------------|-------------|
|*numer* `\`|Dopasowanie wsteczne. Dopasowuje wartość numerowanego podwyrażenia.|`(\w)\1`|`"ee"` w `"seek"`|
|*nazwa* `\k<` `>`|Nazwane dopasowanie wsteczne. Dopasowuje wartość nazwanego wyrażenia.|`(?<char>\w)\k<char>`|`"ee"` w `"seek"`|

## <a name="alternation-constructs"></a>Konstrukty naprzemienne

Konstrukcje zmiany modyfikują wyrażenie regularne, aby umożliwić dopasowanie typu albo/albo. Te konstrukcje obejmują elementy języka wyszczególnione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [konstrukcje warunkowe](alternation-constructs-in-regular-expressions.md).

|Konstrukcje zmiany|Opis|Wzorzec|Dopasowania|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Dopasowuje dowolny jeden element oddzielony znakiem kreski pionowej (<code>&#124;</code>).|<code>th(e&#124;is&#124;at)</code>|`"the"`, `"this"` w `"this is the day."`|
|*wyrażenie* `(?(` `)` *tak* <code>&#124;</code> *nie* `)`|Dopasowuje *wartość Yes (tak* ), Jeśli wzorzec wyrażenia regularnego wyznaczono przez *wyrażenie* pasuje; w przeciwnym razie dopasowuje *opcjonalną* część. *wyrażenie* jest interpretowane jako potwierdzenie o zerowej szerokości.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"`, `"910"` w `"A10 C103 910"`|
|*nazwa* `(?(` `)` *tak* <code>&#124;</code> *nie* `)`|Dopasowuje *wartość tak* , jeśli *Nazwa*, nazwana lub numerowana grupa przechwytywania, ma dopasowanie; w przeciwnym razie dopasowuje opcjonalny *Nr*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "`, `"\"Yiska playing.jpg\""` w `"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Zastępstwa

Podstawienia są elementami języka wyrażeń regularnych, które są obsługiwane we wzorcach zamieniania. Aby uzyskać więcej informacji, zobacz [podstawianie](substitutions-in-regular-expressions.md). Metaznaki wymienione w poniższej tabeli są niepodzielnymi asercjami o zerowej szerokości.

|Znak|Opis|Wzorzec|Wzorzec zamieniania|Ciąg wejściowy|Ciąg wynikowy|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|*numer* `$`|Zastępuje podciąg dopasowany przez *numer*grupy.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|*nazwa* `${` `}`|Podstawia podciąg dopasowany przez *nazwę grupy nazwanej*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Podstawia literał „$”.|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Podstawia kopię całego dopasowania.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Podstawia cały tekst ciągu wejściowego przed dopasowaniem.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Podstawia cały tekst ciągu wejściowego po dopasowaniu.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Podstawia ostatnią przechwyconą grupę.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Podstawia cały ciąg wejściowy.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Opcje wyrażeń regularnych

Można określić opcje sterujące sposobem, w jaki aparat wyrażeń regularnych interpretuje wzorzec wyrażenia regularnego. Wiele z tych opcji można określić jako wbudowane (we wzorcu wyrażenia regularnego) lub jako jeden lub więcej <xref:System.Text.RegularExpressions.RegexOptions> stałych. W tym krótkim opisie wymieniono tylko opcje określane w tekście. Aby uzyskać więcej informacji na temat opcji wbudowanych i <xref:System.Text.RegularExpressions.RegexOptions>, zobacz temat [Opcje wyrażenia regularnego](regular-expression-options.md)artykułu.

Opcję określaną w tekście można określić na dwa sposoby:

- Użycie [konstrukcji różnej](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, gdzie znak minus (-) przed opcją lub zestawem opcji powoduje wyłączenie tych opcji. Na przykład `(?i-mn)` włącza dopasowanie bez uwzględniania wielkości liter (`i`) włączone, wyłącza tryb wielowierszowy (`m`) i wyłącza nienazwane przechwycenia grupy (`n`). Ta opcja jest stosowana do wzorca wyrażenia regularnego od czasu zdefiniowania opcji i działa do końca wzorca lub punktu, w którym inna konstrukcja odwróci działanie opcji.
- Przy użyciu [konstrukcji grupowania](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:``)`*podwyrażenia* , które definiuje opcje tylko dla określonej grupy.

Aparat wyrażeń regularnych programu .NET obsługuje następujące opcje wbudowane:

|Opcja|Opis|Wzorzec|Dopasowania|
|------------|-----------------|-------------|-------------|
|`i`|Używa dopasowywania bez uwzględniania wielkości liter.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"`, `"aaaAuto"` w `"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Używa trybu wielowierszowego. `^` i `$` pasują do początku i końca wiersza, zamiast początku i końca ciągu.|Aby zapoznać się z przykładem, zobacz sekcję "tryb wielowierszowy" w [opcjach wyrażeń regularnych](regular-expression-options.md).||
|`n`|Nie przechwytuje nienazwanych grup.|Aby zapoznać się z przykładem, zobacz sekcję "tylko jawne przechwycenia" w [opcjach wyrażeń regularnych](regular-expression-options.md).||
|`s`|Używa trybu jednowierszowego.|Aby zapoznać się z przykładem, zobacz sekcję "tryb jednowierszowy" w [opcjach wyrażeń regularnych](regular-expression-options.md).||
|`x`|Ignoruje niepoprzedzony znakiem ucieczki znak odstępu we wzorcu wyrażenia regularnego.|`\b(?x) \d+ \s \w+`|`"1 aardvark"`, `"2 cats"` w `"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Różne konstruktory

Konstrukcje inne służą do modyfikowania wzorca wyrażenia regularnego lub dostarczania informacji na jego temat. W poniższej tabeli wymieniono różne konstrukcje obsługiwane przez platformę .NET. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](miscellaneous-constructs-in-regular-expressions.md).

|Konstrukcja|Definicja|Przykład|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Ustawia lub wyłącza opcje, takie jak wyróżnianie wielkości liter w środku wzorca. Aby uzyskać więcej informacji, zobacz [Opcje wyrażenia regularnego](regular-expression-options.md).|`\bA(?i)b\w+\b` dopasowuje `"ABA"`, `"Able"` w `"ABA Able Act"`|
|`(?#` `)` *komentarzy*|Komentarz w tekście. Komentarz kończy się przy pierwszym nawiasie zamykającym.|`\bA(?#Matches words starting with A)\w+\b`|
|`#` [do końca wiersza]|Komentarz trybu X. Komentarz zaczyna się niezmienionym `#` i kontynuuje na końcu wiersza.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Zobacz także

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Wyrażenia regularne](regular-expressions.md)
- [Klasy wyrażeń regularnych](the-regular-expression-object-model.md)
- [Przykłady wyrażeń regularnych](regular-expression-examples.md)
- [Wyrażenia regularne — krótkie odwołanie (pobieranie w formacie programu Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Wyrażenia regularne — krótkie odwołanie (pobieranie w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
