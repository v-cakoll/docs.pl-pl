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
ms.openlocfilehash: cedabbfff10b89f9755b14b963fd1d1a143cb0f0
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204889"
---
# <a name="regular-expression-language---quick-reference"></a>Język wyrażeń regularnych — podręczny wykaz
<a name="top"></a> Wyrażenie regularne to wzorzec, który aparat wyrażeń regularnych próbuje dopasować w tekście wejściowym. Wzorzec składa się z co najmniej jednego literału znakowego, operatora lub konstrukcji.  Aby uzyskać krótkie wprowadzenie – zobacz [wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md).  
  
 Każda sekcja w tym krótkim opisie przedstawia pewną kategorię znaków, operatorów i konstrukcji, które służą do definiowania wyrażeń regularnych:  
  
 [Sekwencje ucieczki znaków](#character_escapes)  
 [Klasy znaków](#character_classes)  
 [Kotwice](#anchors)  
 [Konstrukcje grupujące](#grouping_constructs)  
 [Kwantyfikatory](#quantifiers)  
 [Konstrukcje dopasowywania wstecznego](#backreference_constructs)  
 [Konstrukcje warunkowe](#alternation_constructs)  
 [Zastąpienia](#substitutions)  
 [Opcje wyrażeń regularnych](#options)  
 [Inne konstrukcje](#miscellaneous_constructs)  
  
 Udostępniliśmy również te informacje w dwa formaty, które można pobrać i wydrukować łatwiejszego odwoływania:  
  
 [Pobierz w formacie programu Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Pobierz w formacie PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>Znaki unikowe  
 Znak ukośnika odwrotnego (\\) w wyrażeniu regularnym wskazuje, że znak, który następuje po nim jest znakiem specjalnym (jak pokazano w poniższej tabeli) lub powinien być interpretowany literalnie. Aby uzyskać więcej informacji, zobacz [Znaki specjalne](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md).   
  
|Znak poprzedzony znakiem ucieczki|Opis|Wzorzec|Dopasowania|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|Dopasowuje znak sygnału dźwiękowego, \u0007.|`\a`|„\u0007” w ciągu „Błąd!” + '\u0007'|  
|`\b`|W klasie znaków dopasowuje znak backspace, \u0008.|`[\b]{3,}`|„\b\b\b\b” w ciągu „\b\b\b\b”|  
|`\t`|Dopasowuje znak tabulatora, \u0009.|`(\w+)\t`|„item1\t”, „item2\t” w ciągu „item1\titem2\t”|  
|`\r`|Dopasowuje znak powrotu karetki, \u000D (`\r` nie jest odpowiednikiem znaku nowego wiersza, `\n`.)|`\r\n(\w+)`|„\r\nThese” w ciągu „\r\nThese are\ntwo lines.”|  
|`\v`|Dopasowuje tabulator pionowy, \u000B.|`[\v]{2,}`|„\v\v\v” w ciągu „\v\v\v”|  
|`\f`|Dopasowuje znak wysuwu strony, \u000C.|`[\f]{2,}`|„\f\f\f” w ciągu „\f\f\f”|  
|`\n`|Dopasowuje znak nowego wiersza, \u000A.|`\r\n(\w+)`|„\r\nThese” w ciągu „\r\nThese are\ntwo lines.”|  
|`\e`|Dopasowuje znak escape, \u001B.|`\e`|„\x001B” w ciągu „\x001B”|  
|`\` *nnn*|Używa ósemkowej reprezentacji określającej znak (*nnn* składa się z dwóch lub trzech cyfr).|`\w\040\w`|"a b", "c d" w "a bc d"|  
|`\x` *nn*|Używa szesnastkowej reprezentacji określającej znak (*nn* składa się dokładnie z dwóch cyfr).|`\w\x20\w`|"a b", "c d" w "a bc d"|  
|`\c` *X*<br /><br /> `\c` *x*|Dopasowuje znak kontrolny ASCII, który jest określony przez *X* lub *x*, gdzie *X* lub *x* jest literą znaku kontrolnego.|`\cC`|„\x0003” w ciągu „\x0003” (Ctrl-C)|  
|`\u` *nnnn*|Dopasowuje znak Unicode przy użyciu reprezentacji szesnastkowej (dokładnie cztery cyfry, reprezentowane przez *nnnn*).|`\w\u0020\w`|"a b", "c d" w "a bc d"|  
|`\`|Kiedy następuje po nim znak, który nie jest rozpoznawany jako znak ucieczki w tej lub innej tabeli zawartej w tym temacie, dopasowuje ten znak. Na przykład `\*` jest taka sama jak `\x2A`, i `\.` jest taka sama jak `\x2E`. Umożliwia to aparatowi wyrażeń regularnych rozróżniać elementy języka (takie jak \* lub?) i literały znakowe (reprezentowane przez `\*` lub `\?`).|`\d+[\+-x\*]\d+`|"2 + 2" i "3\*9" w "(2+2) \* 3\*9"|  
  
 [Powrót do początku](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>Klasy znaku  
 Klasa znaków dopasowuje dowolny zestaw znaków. Klasy znaków obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [klas znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
|Klasa znaków|Opis|Wzorzec|Dopasowania|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|Dopasowuje dowolny pojedynczy znak w *character_group*. Domyślnie w dopasowaniu jest uwzględniana wielkość liter.|`[ae]`|„a” w ciągu „gray”<br /><br /> „a”, „e” w ciągu „lane”|  
|`[^` *character_group* `]`|Negacja: Dopasowuje dowolny pojedynczy znak, który nie znajduje się w *character_group*. Domyślnie, znaki w *character_group* jest rozróżniana wielkość liter.|`[^aei]`|„r”, „g”, „n” w „reign”|  
|`[` *first* `-` *last* `]`|Zakres znaków: Dopasowuje dowolny pojedynczy znak z zakresu od *pierwszy* do *ostatniego*.|`[A-Z]`|„A”, „B” w ciągu „AB123”|  
|`.`|Symbol wieloznaczny: Dopasowuje dowolny pojedynczy znak z wyjątkiem \n.<br /><br /> Aby dopasować znak literału kropki (. lub `\u002E`), należy poprzedzić znak ucieczki (`\.`).|`a.e`|„ave” w ciągu „nave”<br /><br /> „ate” w ciągu „water”|  
|`\p{` *Nazwa* `}`|Dopasowuje dowolny pojedynczy znak w ogólnej kategorii Unicode lub nazwanego bloku określonego przez *nazwa*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|„C”, „L” w ciągu „City Lights”<br /><br /> „Д”, „Ж” w ciągu „ДЖem”|  
|`\P{` *Nazwa* `}`|Dopasowuje dowolny pojedynczy znak, który nie znajduje się w ogólnej kategorii Unicode lub nazwanego bloku określonego przez *nazwa*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|„i”, „t”, „y” w ciągu „City”<br /><br /> „e”, „m” w ciągu „ДЖem”|  
|`\w`|Dopasowuje dowolny znak słowa.|`\w`|„I”, „D”, „A”, „1”, „3” w ciągu „ID A1.3”|  
|`\W`|Dopasowuje dowolny znak niebędący znakiem słowa.|`\W`|„ ”, „.” w ciągu „ID A1.3”|  
|`\s`|Dopasowuje dowolny znak odstępu.|`\w\s`|„D ” w ciągu „ID A1.3”|  
|`\S`|Dopasowuje dowolny znak niebędący znakiem odstępu.|`\s\S`|"_" w "int \__ctr"|  
|`\d`|Dopasowuje dowolną cyfrę dziesiętną.|`\d`|„4” w ciągu „4 = IV”|  
|`\D`|Dopasowuje dowolny znak inny niż cyfra dziesiętna.|`\D`|„ ”, „=”, „ ”, „I”, „V” w „4 = IV”|  
  
 [Powrót do początku](#top)  
  
## <a name="anchors"></a>Kotwice  
 Kotwice (niepodzielne asercje o zerowej szerokości) powodują, że sukces lub niepowodzenie dopasowywania jest zależne od bieżącej pozycji w ciągu, ale nie powodują, że aparat przechodzi do dalszej części ciągu lub używa znaków. Metaznaki wymienione w poniższej tabeli są kotwicami. Aby uzyskać więcej informacji, zobacz [kotwic](../../../docs/standard/base-types/anchors-in-regular-expressions.md).  
  
|Asercja|Opis|Wzorzec|Dopasowania|  
|---------------|-----------------|-------------|-------------|  
|`^`|Domyślnie dopasowanie musi rozpoczynać się od ciągu; w tryb wielowierszowy musi zaczynać się od początku wiersza.|`^\d{3}`|"901" w "901 - 333-"|  
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu; w tryb wielowierszowy musi wystąpić przed końcem wiersza lub przed `\n` na końcu wiersza.|`-\d{3}$`|"-333" w "-901-333"|  
|`\A`|Dopasowanie musi wystąpić na początku ciągu.|`\A\d{3}`|"901" w "901 - 333-"|  
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu.|`-\d{3}\Z`|"-333" w "-901-333"|  
|`\z`|Dopasowanie musi wystąpić na końcu ciągu.|`-\d{3}\z`|"-333" w "-901-333"|  
|`\G`|Dopasowanie musi wystąpić w punkcie, w którym kończy się poprzednie dopasowanie.|`\G\(\d\)`|"(1)", "(3)", "(5)" w "(1) [3] [5] [7] (9\)"|  
|`\b`|Dopasowanie musi wystąpić na granicy między `\w` (alfanumeryczny) i `\W` znaku (inny niż alfanumeryczny).|`\b\w+\s\w+\b`|„them theme”, „them them” w ciągu „them theme them them”|  
|`\B`|Dopasowanie nie musi wystąpić na `\b` granic.|`\Bend\w*\b`|„ends”, „ender” w ciągu „end sends endure lender”|  
  
 [Powrót do początku](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>Konstrukty grupujące  
 Konstrukcje grupujące wyznaczają podwyrażenia wyrażeń regularnych i często przechwytywane podciągi ciągu wejściowego. Konstrukcje grupowania obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Grouping Constructs](grouping-constructs-in-regular-expressions.md).  
  
|Konstrukcja grupująca|Opis|Wzorzec|Dopasowania|  
|------------------------|-----------------|-------------|-------------|  
|`(` *Podwyrażenie* `)`|Przechwytuje dopasowane podwyrażenia i przypisuje mu liczbę porządkową (liczone od zera).|`(\w)\1`|„ee” w ciągu „deep”|  
|`(?<` *Nazwa* `>` *Podwyrażenie* `)`|Przechwytuje dopasowane podwyrażenie do nazwanej grupy.|`(?<double>\w)\k<double>`|„ee” w ciągu „deep”|  
|`(?<` *name1* `-` *name2* `>` *subexpression* `)`|Określa definicję grupy równoważącej. Aby uzyskać więcej informacji, zobacz sekcję "Definicja grupy równoważącej" w [Grouping Constructs](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|"((1-3)\*(3-1))" w "3+2^((1-3)\*(3-1))"|  
|`(?:` *Podwyrażenie* `)`|Definiuje nieprzechwytywaną grupę.|`Write(?:Line)?`|„WriteLine” w ciągu „Console.WriteLine()”<br /><br /> „Write” w ciągu „Console.Write(value)”|  
|`(?imnsx-imnsx:` *Podwyrażenie* `)`|Stosuje lub wyłącza określone opcje w *Podwyrażenie*. Aby uzyskać więcej informacji, zobacz [Regular Expression Options](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|„A12xl”, „A12XL” w ciągu „A12xl A12XL a12xl”|  
|`(?=` *Podwyrażenie* `)`|Pozytywna asercja wyprzedzająca o zerowej szerokości.|`\w+(?=\.)`|„is”, „ran” i „out” w ciągu „He is. The dog ran. The sun is out.”|  
|`(?!` *Podwyrażenie* `)`|Negatywna asercja wyprzedzająca o zerowej szerokości.|`\b(?!un)\w+\b`|„sure”, „used” w ciągu „unsure sure unity used”|  
|`(?<=` *Podwyrażenie* `)`|Pozytywna asercja wsteczna o zerowej szerokości.|`(?<=19)\d{2}\b`|„99”, „50”, „05” w ciągu „1851 1999 1950 1905 2003”|  
|`(?<!` *Podwyrażenie* `)`|Negatywna asercja wsteczna o zerowej szerokości.|`(?<!19)\d{2}\b`|„51”, „03” w ciągu „1851 1999 1950 1905 2003”|  
|`(?>` *Podwyrażenie* `)`|Podwyrażenia bez wycofywania („zachłanne”)|`[13579](?>A+B+)`|„1ABB”, „3ABB” i „5AB” w ciągu „1ABB 3ABBC 5AB 5AC”|  
  
 [Powrót do początku](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>Kwantyfikatory  
 Kwantyfikator określa, ile wystąpień poprzedniego elementu (którym może być znak, grupa lub klasa znaków) musi znajdować się w ciągu wejściowym, aby wystąpiło dopasowanie. Kwantyfikatory obejmują elementy języka wymienione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](quantifiers-in-regular-expressions.md).  
  
|Kwantyfikator|Opis|Wzorzec|Dopasowania|  
|----------------|-----------------|-------------|-------------|  
|`*`|Dopasowuje poprzedni element zero lub większą liczbę razy.|`\d*\.\d`|„.0”, „19,9”, „219,9”|  
|`+`|Dopasowuje poprzedni element co najmniej raz.|`"be+"`|„bee” w ciągu „been”, „be” w ciągu „bent”|  
|`?`|Dopasowuje poprzedni element zero lub jeden raz.|`"rai?n"`|„ran”, „rain”|  
|`{` *n* `}`|Dopasowuje poprzedni element dokładnie *n* razy.|`",\d{3}"`|„,043” w ciągu „1,043.6”,„876”, „,543” i „,210” w ciągu „9,876,543,210"|  
|`{` *n* `,}`|Dopasowuje poprzedni element co najmniej *n* razy.|`"\d{2,}"`|„166”, „29”, „1930”|  
|`{` *n* `,` *m* `}`|Dopasowuje poprzedni element co najmniej *n* razy, ale nie więcej niż *m* razy.|`"\d{3,5}"`|„166”, „17668”<br /><br /> „19302” w ciągu „193024”|  
|`*?`|Dopasowuje poprzedni element zero lub większą liczbę razy (przy czym ta liczba jest jak najmniejsza).|`\d*?\.\d`|„.0”, „19,9”, „219,9”|  
|`+?`|Dopasowuje poprzedni element raz lub większą liczbę razy (przy czym ta liczba jest jak najmniejsza).|`"be+?"`|„be” w ciągu „been”, „be” w ciągu „bent”|  
|`??`|Dopasowuje poprzedni element zero lub jeden raz (przy czym liczba dopasowań jest jak najmniejsza).|`"rai??n"`|„ran”, „rain”|  
|`{` *n* `}?`|Dopasowuje poprzedzający element dokładnie *n* razy.|`",\d{3}?"`|„,043” w ciągu „1,043.6”,„876”, „,543” i „,210” w ciągu „9,876,543,210"|  
|`{` *n* `,}?`|Dopasowuje poprzedni element co najmniej *n* razy, ale tyle razy, ile to możliwe.|`"\d{2,}?"`|„166”, „29”, „1930”|  
|`{` *n* `,` *m* `}?`|Dopasowuje poprzedni element między *n* i *m* razy, ale tyle razy, ile to możliwe.|`"\d{3,5}?"`|„166”, „17668”<br /><br /> „193”, „024” w ciągu „193024”|  
  
 [Powrót do początku](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>Konstrukty grupowania wstecznego  
 Dopasowywanie wsteczne umożliwia kolejne identyfikacje uprzednio dopasowanego podwyrażenia w tym samym wyrażeniu regularnym. W poniższej tabeli wymieniono konstrukcje dopasowywania wstecznego obsługiwane przez wyrażenia regularne w .NET. Aby uzyskać więcej informacji, zobacz [konstrukcje dopasowywania wstecznego](backreference-constructs-in-regular-expressions.md).  
  
|Konstrukcja dopasowywania wstecznego|Opis|Wzorzec|Dopasowania|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *Numer*|Dopasowanie wsteczne. Dopasowuje wartość numerowanego podwyrażenia.|`(\w)\1`|„ee” w ciągu „seek”|  
|`\k<` *Nazwa* `>`|Nazwane dopasowanie wsteczne. Dopasowuje wartość nazwanego wyrażenia.|`(?<char>\w)\k<char>`|„ee” w ciągu „seek”|  
  
 [Powrót do początku](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>Konstrukty naprzemienne  
 Konstrukcje zmiany modyfikują wyrażenie regularne, aby umożliwić dopasowanie typu albo/albo. Te konstrukcje obejmują elementy języka wyszczególnione w poniższej tabeli. Aby uzyskać więcej informacji, zobacz [konstrukcje](alternation-constructs-in-regular-expressions.md).  
  
|Konstrukcje zmiany|Opis|Wzorzec|Dopasowania|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|Dopasowuje dowolny jeden element oddzielonych pionowy pasek (&#124;) znaków.|<code>th(e&#124;is&#124;at)</code>|„the”, „this” w ciągu „this is the day. "|  
|`(?(` *wyrażenie* `)` *tak* <code>&#124;</code> *nie* `)`|Dopasowuje *tak* Jeśli wzorzec wyrażenia regularnego wyznaczony przez *wyrażenie* pasuje; w przeciwnym razie dopasowuje opcjonalną część *nie* części. *wyrażenie* jest interpretowane jako asercja o zerowej szerokości.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|„A10”, „910” w ciągu „A10 C103 910”|  
|`(?(` *Nazwa* `)` *tak* <code>&#124;</code> *nie* `)`|Dopasowuje *tak* Jeśli *nazwa*, nazwana lub ponumerowana grupa przechwywtywania została dopasowana; w przeciwnym razie dopasowuje opcjonalną część *nie*.|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|Dogs.jpg, „Yiska playing.jpg” w ciągu „Dogs.jpg "Yiska playing.jpg"”|  
  
 [Powrót do początku](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>Zastępstwa  
 Podstawienia są elementami języka wyrażeń regularnych, które są obsługiwane we wzorcach zamieniania. Aby uzyskać więcej informacji, zobacz [podstawienia](substitutions-in-regular-expressions.md). Metaznaki wymienione w poniższej tabeli są niepodzielnymi asercjami o zerowej szerokości.  
  
|Znak|Opis|Wzorzec|Wzorzec zamieniania|Ciąg wejściowy|Ciąg wynikowy|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` *Numer*|Podstawia podciąg dopasowany przez grupę *numer*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|„one two”|„two one”|  
|`${` *Nazwa* `}`|Podstawia podciąg dopasowany przez nazwaną grupę *nazwa*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|„one two”|„two one”|  
|`$$`|Podstawia literał „$”.|`\b(\d+)\s?USD`|`$$$1`|„103 USD”|„$103”|  
|`$&`|Podstawia kopię całego dopasowania.|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|``$` ``|Podstawia cały tekst ciągu wejściowego przed dopasowaniem.|`B+`|``$` ``|„AABBCC”|„AAAACC”|  
|`$'`|Podstawia cały tekst ciągu wejściowego po dopasowaniu.|`B+`|`$'`|„AABBCC”|„AACCCC”|  
|`$+`|Podstawia ostatnią przechwyconą grupę.|`B+(C+)`|`$+`|„AABBCCDD”|"AACCDD"|  
|`$_`|Podstawia cały ciąg wejściowy.|`B+`|`$_`|„AABBCC”|„AAAABBCCCC”|  
  
 [Powrót do początku](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>Opcje wyrażeń regularnych  
 Można określić opcje sterujące sposobem, w jaki aparat wyrażeń regularnych interpretuje wzorzec wyrażenia regularnego. Wiele z tych opcji można określić jako wbudowane (we wzorcu wyrażenia regularnego) lub jako jedną lub więcej <xref:System.Text.RegularExpressions.RegexOptions> stałe. W tym krótkim opisie wymieniono tylko opcje określane w tekście. Aby uzyskać więcej informacji dotyczących wbudowania i <xref:System.Text.RegularExpressions.RegexOptions> opcji, zapoznaj się z artykułem [Regular Expression Options](regular-expression-options.md).  
  
 Opcję określaną w tekście można określić na dwa sposoby:  
  
-   Za pomocą [innej konstrukcji](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, w której znak minus (-) przed opcją lub zestawem opcji powoduje wyłączenie tych opcji. Na przykład `(?i-mn)` włącza dopasowanie bez uwzględniania wielkości liter (`i`), wyłącza tryb wielowierszowy (`m`) i wyłącza nienazwane przechwycenia grup (`n`) wyłączone. Ta opcja jest stosowana do wzorca wyrażenia regularnego od czasu zdefiniowania opcji i działa do końca wzorca lub punktu, w którym inna konstrukcja odwróci działanie opcji.  
  
-   Za pomocą [konstrukcja grupująca](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*Podwyrażenie*`)`, która definiuje opcje dla określonej grupy.  
  
 Aparat wyrażeń regularnych .NET obsługuje następujące opcje wbudowane.  
  
|Opcja|Opis|Wzorzec|Dopasowania|  
|------------|-----------------|-------------|-------------|  
|`i`|Używa dopasowywania bez uwzględniania wielkości liter.|`\b(?i)a(?-i)a\w+\b`|„aardvark”, „aaaAuto” w ciągu „aardvark AAAuto aaaAuto Adam breakfast”|  
|`m`|Używa trybu wielowierszowego. `^` i `$` pasuje do początku i końcu wiersza, zamiast początku i końca ciągu.|Aby uzyskać przykład, zobacz sekcję "Tryb wielowierszowy" w [Regular Expression Options](regular-expression-options.md).||  
|`n`|Nie przechwytuje nienazwanych grup.|Aby uzyskać przykład, zobacz sekcję "Tylko jawne Przechwytywanie" w [Regular Expression Options](regular-expression-options.md).||  
|`s`|Używa trybu jednowierszowego.|Aby uzyskać przykład, zobacz sekcję "Tryb jednowierszowy" w [Regular Expression Options](regular-expression-options.md).||  
|`x`|Ignoruje niepoprzedzony znakiem ucieczki znak odstępu we wzorcu wyrażenia regularnego.|`\b(?x) \d+ \s \w+`|„1 aardvark”, „2 cats” w ciągu „1 aardvark 2 cats IV centurions”|  
  
 [Powrót do początku](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>Różne konstruktory  
 Konstrukcje inne służą do modyfikowania wzorca wyrażenia regularnego lub dostarczania informacji na jego temat. W poniższej tabeli wymieniono różne konstrukcje obsługiwane przez .NET. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](miscellaneous-constructs-in-regular-expressions.md).  
  
|Konstrukcja|Definicja|Przykład|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|Ustawia lub wyłącza opcje, takie jak ignorowanie wielkości liter w środku wzorca. Aby uzyskać więcej informacji, zobacz [Regular Expression Options](regular-expression-options.md).|`\bA(?i)b\w+\b` dopasowuje ciągi "ABA", "Able" w "Stanie akt ABA"|  
|`(?#` *Komentarz* `)`|Komentarz w tekście. Komentarz kończy się przy pierwszym nawiasie zamykającym.|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [do końca wiersza]|Komentarz trybu X. Komentarz rozpoczyna się od niekodowanego `#` i kontynuuje do końca wiersza.|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Regular Expressions](regular-expressions.md)
- [Klasy wyrażeń regularnych](the-regular-expression-object-model.md)
- [Przykłady wyrażeń regularnych](regular-expression-examples.md)
- [Wyrażeń regularnych — podręczny wykaz (do pobrania w formacie programu Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Wyrażeń regularnych — podręczny wykaz (do pobrania w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
