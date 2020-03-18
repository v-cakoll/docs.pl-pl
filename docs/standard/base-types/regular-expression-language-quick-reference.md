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
ms.openlocfilehash: 8acf0886215c2d31f949e38401c4705ac9e2aef5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124315"
---
# <a name="regular-expression-language---quick-reference"></a>Język wyrażeń regularnych — podręczny wykaz

Wyrażenie regularne to wzorzec, który aparat wyrażeń regularnych próbuje dopasować w tekście wejściowym. Wzorzec składa się z co najmniej jednego literału znakowego, operatora lub konstrukcji. Aby zapoznać się z krótkim wprowadzeniem, zobacz [wyrażenia regularne .NET](regular-expressions.md).

Każda sekcja w tym skróconym odwołaniu zawiera listę określonej kategorii znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.

Udostępniliśmy również te informacje w dwóch formatach, które można pobrać i wydrukować w celu łatwego odniesienia:

- [Pobieranie w formacie Programu Word (docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Pobierz w formacie PDF (pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Znaki unikowe

Znak ukośnika\\odwrotnego ( ) w wyrażeniu regularnym wskazuje, że znak, który następuje po nim, jest znakiem specjalnym (jak pokazano w poniższej tabeli) lub powinien być interpretowany dosłownie. Aby uzyskać więcej informacji, zobacz [Ucieczki znaków](character-escapes-in-regular-expressions.md).

|Znak poprzedzony znakiem ucieczki|Opis|Wzorce|Dopasowania|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Dopasowuje znak sygnału dźwiękowego, \u0007.|`\a`|`"\u0007"` w elemencie `"Error!" + '\u0007'`|
|`\b`|W klasie znaków dopasowuje znak backspace, \u0008.|`[\b]{3,}`|`"\b\b\b\b"` w elemencie `"\b\b\b\b"`|
|`\t`|Dopasowuje znak tabulatora, \u0009.|`(\w+)\t`|`"item1\t"`, `"item2\t"` w`"item1\titem2\t"`|
|`\r`|Dopasowuje znak powrotu karetki, \u000D (`\r` nie jest odpowiednikiem znaku `\n`nowego wiersza, .)|`\r\n(\w+)`|`"\r\nThese"` w elemencie `"\r\nThese are\ntwo lines."`|
|`\v`|Dopasowuje tabulator pionowy, \u000B.|`[\v]{2,}`|`"\v\v\v"` w elemencie `"\v\v\v"`|
|`\f`|Dopasowuje znak wysuwu strony, \u000C.|`[\f]{2,}`|`"\f\f\f"` w elemencie `"\f\f\f"`|
|`\n`|Dopasowuje znak nowego wiersza, \u000A.|`\r\n(\w+)`|`"\r\nThese"` w elemencie `"\r\nThese are\ntwo lines."`|
|`\e`|Dopasowuje znak escape, \u001B.|`\e`|`"\x001B"` w elemencie `"\x001B"`|
|`\`*nnn (nnn)*|Używa reprezentacji ósemkowej, aby określić znak *(nnn* składa się z dwóch lub trzech cyfr).|`\w\040\w`|`"a b"`, `"c d"` w`"a bc d"`|
|`\x`*nn*|Używa reprezentacji szesnastkowej, aby określić znak *(nn* składa się z dokładnie dwóch cyfr).|`\w\x20\w`|`"a b"`, `"c d"` w`"a bc d"`|
|`\c` *X*<br /><br /> `\c`*x*|Dopasowuje znak kontrolny ASCII określony przez *X* lub *x*, gdzie *X* lub *x* jest literą znaku kontrolnego.|`\cC`|`"\x0003"`w `"\x0003"` (Ctrl-C)|
|`\u`*nnnn (nnnn)*|Dopasowuje znak Unicode przy użyciu reprezentacji szesnastkowej (dokładnie cztery cyfry, reprezentowane przez *nnnn*).|`\w\u0020\w`|`"a b"`, `"c d"` w`"a bc d"`|
|`\`|Kiedy następuje po nim znak, który nie jest rozpoznawany jako znak ucieczki w tej lub innej tabeli zawartej w tym temacie, dopasowuje ten znak. Na przykład `\*` jest taka `\x2A`sama `\.` jak , `\x2E`i jest taka sama jak . Dzięki temu aparat wyrażeń regularnych do rozróżniania \* elementów języka (takich jak lub `\*` `\?`?) i literały znaków (reprezentowane przez lub ).|`\d+[\+-x\*]\d+`|`"2+2"` i `"3*9"` w elemencie `"(2+2) * 3*9"`|

## <a name="character-classes"></a>Klasy znaku

Klasa znaków dopasowuje dowolny zestaw znaków. Klasy znaków obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Klasy znaków](character-classes-in-regular-expressions.md).

|Klasa znaków|Opis|Wzorce|Dopasowania|
|---------------------|-----------------|-------------|-------------|
|`[`*character_group*`]`|Pasuje do dowolnego pojedynczego znaku w *character_group*. Domyślnie w dopasowaniu jest uwzględniana wielkość liter.|`[ae]`|`"a"` w elemencie `"gray"`<br /><br /> `"a"`, `"e"` w`"lane"`|
|`[^`*character_group*`]`|Negacja: Dopasowuje dowolny pojedynczy znak, który nie znajduje się w *character_group*. Domyślnie znaki w *character_group* są uwzględniane wielkości liter.|`[^aei]`|`"r"`, `"g"` `"n"` w`"reign"`|
|`[`*pierwszy* `-` *ostatni*`]`|Zakres znaków: dopasowuje dowolny pojedynczy znak w zakresie od *pierwszego* do *ostatniego*.|`[A-Z]`|`"A"`, `"B"` w`"AB123"`|
|`.`|Symbol wieloznaczny: Dopasowuje każdy pojedynczy znak, oprócz znaku \n.<br /><br /> Aby dopasować znak okresu literału (. lub `\u002E`), należy poprzedzić`\.`go znakiem ucieczki ( ).|`a.e`|`"ave"` w elemencie `"nave"`<br /><br /> `"ate"` w elemencie `"water"`|
|`\p{`*nazwa*`}`|Dopasowuje dowolny pojedynczy znak w kategorii ogólnej Unicode lub nazwany blok określony przez *nazwę*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"`, `"L"` w`"City Lights"`<br /><br /> `"Д"`, `"Ж"` w`"ДЖem"`|
|`\P{`*nazwa*`}`|Dopasowuje dowolny pojedynczy znak, który nie znajduje się w kategorii ogólnej Unicode lub nazwanym bloku określonym przez *nazwę*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"` `"y"` w`"City"`<br /><br /> `"e"`, `"m"` w`"ДЖem"`|
|`\w`|Dopasowuje dowolny znak słowa.|`\w`|`"I"`, `"D"` `"A"`, `"1"` `"3"` w`"ID A1.3"`|
|`\W`|Dopasowuje dowolny znak niebędący znakiem słowa.|`\W`|`" "`, `"."` w`"ID A1.3"`|
|`\s`|Dopasowuje dowolny znak odstępu.|`\w\s`|`"D "` w elemencie `"ID A1.3"`|
|`\S`|Dopasowuje dowolny znak niebędący znakiem odstępu.|`\s\S`|`" _"` w elemencie `"int __ctr"`|
|`\d`|Dopasowuje dowolną cyfrę dziesiętną.|`\d`|`"4"` w elemencie `"4 = IV"`|
|`\D`|Dopasowuje dowolny znak inny niż cyfra dziesiętna.|`\D`|`" "`, `"="` `" "`, `"I"` `"V"` w`"4 = IV"`|

## <a name="anchors"></a>Kotwice

Kotwice (niepodzielne asercje o zerowej szerokości) powodują, że sukces lub niepowodzenie dopasowywania jest zależne od bieżącej pozycji w ciągu, ale nie powodują, że aparat przechodzi do dalszej części ciągu lub używa znaków. Metaznaki wymienione w poniższej tabeli są kotwicami. Aby uzyskać więcej informacji, zobacz [Kotwice](anchors-in-regular-expressions.md).

|Asercja|Opis|Wzorce|Dopasowania|
|---------------|-----------------|-------------|-------------|
|`^`|Domyślnie dopasowanie musi rozpoczynać się na początku ciągu; w trybie wielowierszowym musi zaczynać się od początku linii.|`^\d{3}`|`"901"` w elemencie `"901-333-"`|
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu `\n` lub wcześniej na końcu ciągu; w trybie wielowierszowym musi nastąpić przed końcem linii lub wcześniej `\n` na końcu linii.|`-\d{3}$`|`"-333"` w elemencie `"-901-333"`|
|`\A`|Dopasowanie musi wystąpić na początku ciągu.|`\A\d{3}`|`"901"` w elemencie `"901-333-"`|
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu `\n` lub wcześniej na końcu ciągu.|`-\d{3}\Z`|`"-333"` w elemencie `"-901-333"`|
|`\z`|Dopasowanie musi wystąpić na końcu ciągu.|`-\d{3}\z`|`"-333"` w elemencie `"-901-333"`|
|`\G`|Dopasowanie musi wystąpić w punkcie, w którym kończy się poprzednie dopasowanie.|`\G\(\d\)`|`"(1)"`, `"(3)"` `"(5)"` w`"(1)(3)(5)[7](9)"`|
|`\b`|Dopasowanie musi występować na granicy `\w` między znakiem (alfanumerycznym) i `\W` (niealfalicznym).|`\b\w+\s\w+\b`|`"them theme"`, `"them them"` w`"them theme them them"`|
|`\B`|Dopasowanie nie może wystąpić `\b` na granicy.|`\Bend\w*\b`|`"ends"`, `"ender"` w`"end sends endure lender"`|

## <a name="grouping-constructs"></a>Konstrukty grupujące

Konstrukcje grupujące wyznaczają podwyrażenia wyrażeń regularnych i często przechwytywane podciągi ciągu wejściowego. Konstrukcje grupowania obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).

|Konstrukcja grupująca|Opis|Wzorce|Dopasowania|
|------------------------|-----------------|-------------|-------------|
|`(`*wyrażenie podrzędne*`)`|Przechwytuje dopasowane podwyrażenia i przypisuje mu liczbę porządkową (liczone od zera).|`(\w)\1`|`"ee"` w elemencie `"deep"`|
|`(?<`*wyrażenie* `>` *podrzędne* nazwy`)`|Przechwytuje dopasowane podwyrażenie do nazwanej grupy.|`(?<double>\w)\k<double>`|`"ee"` w elemencie `"deep"`|
|`(?<`*name1* `-` *name2* `>` *wyrażenie podrzędne*`)`|Określa definicję grupy równoważącej. Aby uzyskać więcej informacji, zobacz sekcję "Definicja grupy bilansującej" w [sekcji Grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"((1-3)*(3-1))"` w elemencie `"3+2^((1-3)*(3-1))"`|
|`(?:`*wyrażenie podrzędne*`)`|Definiuje nieprzechwytywaną grupę.|`Write(?:Line)?`|`"WriteLine"` w elemencie `"Console.WriteLine()"`<br /><br /> `"Write"` w elemencie `"Console.Write(value)"`|
|`(?imnsx-imnsx:`*wyrażenie podrzędne*`)`|Stosuje lub wyłącza określone opcje w *wyrażeniu podrzędnym*. Aby uzyskać więcej informacji, zobacz [Opcje wyrażeń regularnych](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"`, `"A12XL"` w`"A12xl A12XL a12xl"`|
|`(?=`*wyrażenie podrzędne*`)`|Pozytywna asercja wyprzedzająca o zerowej szerokości.|`\w+(?=\.)`|`"is"`, `"ran"`oraz `"out"` w`"He is. The dog ran. The sun is out."`|
|`(?!`*wyrażenie podrzędne*`)`|Negatywna asercja wyprzedzająca o zerowej szerokości.|`\b(?!un)\w+\b`|`"sure"`, `"used"` w`"unsure sure unity used"`|
|`(?<=`*wyrażenie podrzędne*`)`|Pozytywna asercja wsteczna o zerowej szerokości.|`(?<=19)\d{2}\b`|`"99"`, `"50"` `"05"` w`"1851 1999 1950 1905 2003"`|
|`(?<!`*wyrażenie podrzędne*`)`|Negatywna asercja wsteczna o zerowej szerokości.|`(?<!19)\d{2}\b`|`"51"`, `"03"` w`"1851 1999 1950 1905 2003"`|
|`(?>`*wyrażenie podrzędne*`)`|Grupa atomowa.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"`oraz `"5AB"` w`"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Kwantyfikatory

Kwantyfikator określa, ile wystąpień poprzedniego elementu (którym może być znak, grupa lub klasa znaków) musi znajdować się w ciągu wejściowym, aby wystąpiło dopasowanie. Kwantyfikatory obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](quantifiers-in-regular-expressions.md).

|Kwantyfikator|Opis|Wzorce|Dopasowania|
|----------------|-----------------|-------------|-------------|
|`*`|Dopasowuje poprzedni element zero lub większą liczbę razy.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Dopasowuje poprzedni element co najmniej raz.|`"be+"`|`"bee"`w `"been"` `"be"` , w , w`"bent"`|
|`?`|Dopasowuje poprzedni element zero lub jeden raz.|`"rai?n"`|`"ran"`, `"rain"`|
|`{`*n*`}`|Dopasowuje poprzedni element dokładnie *n* razy.|`",\d{3}"`|`",043"`w `"1,043.6"` `",876"`, `",543"`, `",210"` oraz w`"9,876,543,210"`|
|`{`*n*`,}`|Dopasowuje poprzedni element co najmniej *n* razy.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}`|Dopasowuje poprzedni element co najmniej *n* razy, ale nie więcej niż *m* razy.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"19302"` w elemencie `"193024"`|
|`*?`|Dopasowuje poprzedni element zero lub większą liczbę razy (przy czym ta liczba jest jak najmniejsza).|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Dopasowuje poprzedni element raz lub większą liczbę razy (przy czym ta liczba jest jak najmniejsza).|`"be+?"`|`"be"`w `"been"` `"be"` , w , w`"bent"`|
|`??`|Dopasowuje poprzedni element zero lub jeden raz (przy czym liczba dopasowań jest jak najmniejsza).|`"rai??n"`|`"ran"`, `"rain"`|
|`{`*n*`}?`|Dopasowuje poprzedni element dokładnie *n* razy.|`",\d{3}?"`|`",043"`w `"1,043.6"` `",876"`, `",543"`, `",210"` oraz w`"9,876,543,210"`|
|`{`*n*`,}?`|Dopasowuje poprzedni element co najmniej *n* razy, ale jak kilka razy.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}?`|Dopasowuje poprzedni element między *czasami n* i *m,* ale jak kilka razy.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"`, `"024"` w`"193024"`|

## <a name="backreference-constructs"></a>Konstrukty grupowania wstecznego

Dopasowywanie wsteczne umożliwia kolejne identyfikacje uprzednio dopasowanego podwyrażenia w tym samym wyrażeniu regularnym. W poniższej tabeli wymieniono konstrukcje backreference obsługiwane przez wyrażenia regularne w .NET. Aby uzyskać więcej informacji, zobacz [Backreference Konstrukcje](backreference-constructs-in-regular-expressions.md).

|Konstrukcja dopasowywania wstecznego|Opis|Wzorce|Dopasowania|
|-----------------------------|-----------------|-------------|-------------|
|`\` *numer*|Dopasowanie wsteczne. Dopasowuje wartość numerowanego podwyrażenia.|`(\w)\1`|`"ee"` w elemencie `"seek"`|
|`\k<`*nazwa*`>`|Nazwane dopasowanie wsteczne. Dopasowuje wartość nazwanego wyrażenia.|`(?<char>\w)\k<char>`|`"ee"` w elemencie `"seek"`|

## <a name="alternation-constructs"></a>Konstrukty naprzemienne

Konstrukcje zmiany modyfikują wyrażenie regularne, aby umożliwić dopasowanie typu albo/albo. Te konstrukcje obejmują elementy języka wyszczególnione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Konstrukcje naprzemienne](alternation-constructs-in-regular-expressions.md).

|Konstrukcje zmiany|Opis|Wzorce|Dopasowania|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Dopasowuje dowolny element oddzielony znakiem pionowego paska (<code>&#124;</code>)|<code>th(e&#124;is&#124;at)</code>|`"the"`, `"this"` w`"this is the day."`|
|`(?(`*wyrażenie* `)` *tak* <code>&#124;</code> *nie*`)`|Dopasowuje *tak,* jeśli wzorzec wyrażenia regularnego wyznaczony przez *wyrażenie* pasuje; w przeciwnym razie pasuje do opcjonalnej *żadnej* części. *wyrażenie* jest interpretowane jako twierdzenie o zerowej szerokości.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"`, `"910"` w`"A10 C103 910"`|
|`(?(`*nazwa* `)` *tak nie* <code>&#124;</code> *no*`)`|Dopasowuje *tak,* jeśli *nazwa*, nazwana lub numerowana grupa przechwytywania, ma dopasowanie; w przeciwnym razie jest zgodna z opcjonalnym *numerem .*|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "`, `"\"Yiska playing.jpg\""` w`"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Zastępstwa

Podstawienia są elementami języka wyrażeń regularnych, które są obsługiwane we wzorcach zamieniania. Aby uzyskać więcej informacji, zobacz [Podstawienia](substitutions-in-regular-expressions.md). Metaznaki wymienione w poniższej tabeli są niepodzielnymi asercjami o zerowej szerokości.

|Znak|Opis|Wzorce|Wzorzec zamieniania|Ciąg wejściowy|Ciąg wynikowy|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|`$` *numer*|Zastępuje podciąg dopasowany według *numeru*grupy .|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|`${`*nazwa*`}`|Podciąg zastępuje podciąg dopasowany do nazwanej *nazwy*grupy .|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Podstawia literał „$”.|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Podstawia kopię całego dopasowania.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Podstawia cały tekst ciągu wejściowego przed dopasowaniem.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Podstawia cały tekst ciągu wejściowego po dopasowaniu.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Podstawia ostatnią przechwyconą grupę.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Podstawia cały ciąg wejściowy.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Opcje wyrażeń regularnych

Można określić opcje sterujące sposobem, w jaki aparat wyrażeń regularnych interpretuje wzorzec wyrażenia regularnego. Wiele z tych opcji można określić w wierszu (we wzorcu <xref:System.Text.RegularExpressions.RegexOptions> wyrażenia regularnego) lub jako jedną lub więcej stałych. W tym krótkim opisie wymieniono tylko opcje określane w tekście. Aby uzyskać więcej informacji <xref:System.Text.RegularExpressions.RegexOptions> na temat wbudowanych i opcji, zobacz artykuł [Opcje wyrażenia regularnego](regular-expression-options.md).

Opcję określaną w tekście można określić na dwa sposoby:

- Za pomocą [różnych konstrukcji](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, gdzie znak minus (-) przed opcją lub zestaw opcji wyłącza te opcje. Na przykład `(?i-mn)` włącza dopasowanie bez`i`uwzględniania wielkości liter (`m`) powoduje wyłączenie trybu wielowierszowego ( ) i wyłączenie nienazwanych przechwytów grup (`n`) . Ta opcja jest stosowana do wzorca wyrażenia regularnego od czasu zdefiniowania opcji i działa do końca wzorca lub punktu, w którym inna konstrukcja odwróci działanie opcji.
- Za pomocą [grupy konstrukcji](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*podwyrażenie*`)`, który definiuje opcje tylko dla określonej grupy.

Aparat wyrażeń regularnych .NET obsługuje następujące opcje wbudowanych:

|Opcja|Opis|Wzorce|Dopasowania|
|------------|-----------------|-------------|-------------|
|`i`|Używa dopasowywania bez uwzględniania wielkości liter.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"`, `"aaaAuto"` w`"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Używa trybu wielowierszowego. `^`i `$` dopasować początek i koniec wiersza, zamiast początku i końca ciągu.|Na przykład zobacz sekcję "Tryb wielowierszowy" w [sekcji Opcje wyrażenia regularnego](regular-expression-options.md).||
|`n`|Nie przechwytuje nienazwanych grup.|Na przykład zobacz sekcję "Jawne przechwytywanie tylko" w [sekcji Opcje wyrażenia regularnego](regular-expression-options.md).||
|`s`|Używa trybu jednowierszowego.|Na przykład zobacz sekcję "Tryb jednowierszowy" w [sekcji Opcje wyrażenia regularnego](regular-expression-options.md).||
|`x`|Ignoruje niepoprzedzony znakiem ucieczki znak odstępu we wzorcu wyrażenia regularnego.|`\b(?x) \d+ \s \w+`|`"1 aardvark"`, `"2 cats"` w`"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Różne konstruktory

Konstrukcje inne służą do modyfikowania wzorca wyrażenia regularnego lub dostarczania informacji na jego temat. W poniższej tabeli wymieniono różne konstrukcje obsługiwane przez program .NET. Aby uzyskać więcej informacji, zobacz [Różne konstrukcje](miscellaneous-constructs-in-regular-expressions.md).

|Konstrukcja|Definicja|Przykład|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Ustawia lub wyłącza opcje, takie jak niewrażliwość wielkości liter w środku szyku. Aby uzyskać więcej informacji, zobacz [Opcje wyrażeń regularnych](regular-expression-options.md).|`\bA(?i)b\w+\b`mecze `"ABA"` `"Able"` , w`"ABA Able Act"`|
|`(?#`*komentarz*`)`|Komentarz w tekście. Komentarz kończy się przy pierwszym nawiasie zamykającym.|`\bA(?#Matches words starting with A)\w+\b`|
|`#`[do końca linii]|Komentarz trybu X. Komentarz zaczyna się od `#` nieuciekł i trwa do końca linii.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Zobacz też

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Wyrażenia regularne](regular-expressions.md)
- [Klasy wyrażeń regularnych](the-regular-expression-object-model.md)
- [Przykłady wyrażeń regularnych](regular-expression-examples.md)
- [Wyrażenia regularne — podręczny numer eksploatacja (pobieranie w formacie Worda)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Wyrażenia regularne — podręczna dokumentacja (pobieranie w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
