---
title: Kwantyfikatory w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 788229053f5702b44c6ac351b59ad1c464e4e133
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633640"
---
# <a name="quantifiers-in-regular-expressions"></a>Kwantyfikatory w wyrażeniach regularnych
Kwantyfikatory Określ, ile wystąpień znak, grupa lub Klasa znaków musi znajdować się w danych wejściowych, aby dopasowanie zakończyło się można znaleźć.  W poniższej tabeli wymieniono kwantyfikatorów poparte .NET.  
  
|Zachłanne kwantyfikator|Kwantyfikatorem opóźniającym|Opis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Dopasowuje zero lub więcej razy.|  
|`+`|`+?`|Dopasowuje jeden lub więcej razy.|  
|`?`|`??`|Dopasowuje zero lub jeden raz.|  
|`{` *n* `}`|`{` *n* `}?`|Dokładnie *n* razy.|  
|`{` *n* `,}`|`{` *n* `,}?`|Zgodne z co najmniej *n* razy.|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|Dopasowuje od *n* do *m* razy.|  
  
 Ilości `n` i `m` są stałe całkowite. Zazwyczaj Kwantyfikatory są zachłanne; mogą spowodować, że aparat wyrażenia regularnego dopasowuje dowolną liczbę wystąpień danego wzorców, jak to możliwe. Dołączanie `?` znak kwantyfikator sprawia, że z opóźnieniem; sprawia, że aparat wyrażeń regularnych dopasować jak najmniejszej liczby wystąpień, jak to możliwe. Aby uzyskać pełny opis różnicy między Kwantyfikatory zachłanne i z opóźnieniem, zobacz sekcję [Greedy i Kwantyfikatory opóźniające](#Greedy) w dalszej części tego tematu.  
  
> [!IMPORTANT]
>  Zagnieżdżanie kwantyfikatory (na przykład, jako wzorca wyrażenia regularnego `(a*)*` jest) można zwiększyć liczbę porównania, które należy wykonać aparat wyrażeń regularnych, jak funkcja wykładnicza liczbę znaków w ciągu wejściowym. Aby uzyskać więcej informacji dotyczących tego zachowania i jego obejścia, zobacz [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kwantyfikatory wyrażeń regularnych  
 W poniższych sekcjach wymieniono kwantyfikatorów poparte wyrażeń regularnych programu .NET.  
  
> [!NOTE]
>  Jeśli *, +,?, {, i} znaki zostaną napotkane we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych interpretuje je jako Kwantyfikatory lub jej część kwantyfikator konstrukcji, chyba że są one uwzględnione w [klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Interpretowanie je jako znaki literału poza klasą znak, możesz je ucieczki poprzedzając je znakiem kreski ułamkowej odwróconej. Na przykład ciąg `\*` w wyrażeniu regularnym wzorzec jest interpretowany jako literał gwiazdki ("\*") znaków.  
  
### <a name="match-zero-or-more-times-"></a>Odpowiada Zero lub więcej razy: *  
 `*` Kwantyfikator dopasowuje poprzedni element zero lub więcej razy. Jest to równoważne `{0,}` kwantyfikator. `*` jest zachłanne kwantyfikator, którego opóźnieniem odpowiednik to `*?`.  
  
 Poniższy przykład ilustruje tego wyrażenia regularnego. Dziewięć cyfr w ciągu wejściowym, pięciu pasuje wzorzec i cztery (`95`, `929`, `9219`, i `9919`) nie obsługują.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`91*`|Dopasowuje "9", po której następuje zero lub więcej znaków "1".|  
|`9*`|Dopasowuje zero lub więcej znaków "9".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-one-or-more-times-"></a>Dopasuj jeden lub więcej razy: +  
 `+` Kwantyfikator dopasowuje poprzedzający element jeden lub więcej razy. Jest to równoważne `{1,}`. `+` jest zachłanne kwantyfikator, którego opóźnieniem odpowiednik to `+?`.  
  
 Na przykład, wyrażenie regularne `\ban+\w*?\b` próbuje dopasować całe wyrazy, które zaczynają się od litery `a` następuje co najmniej jednego wystąpienia litery `n`. Poniższy przykład ilustruje tego wyrażenia regularnego. Wyrażenie regularne dopasowuje wyrazy `an`, `annual`, `announcement`, i `antique`i poprawnie ulegnie awarii dopasować `autumn` i `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an+`|Uwzględnij wiadomość "" następuje jeden lub więcej znaków "n".|  
|`\w*?`|Dopasuj znak wyrazu, zero lub więcej razy, ale jak tyle razy, ile to możliwe.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-zero-or-one-time-"></a>Odpowiada Zero lub jeden raz:?  
 `?` Kwantyfikator dopasowuje poprzedni element zero lub jeden czas. Jest to równoważne `{0,1}`. `?` jest zachłanne kwantyfikator, którego opóźnieniem odpowiednik to `??`.  
  
 Na przykład, wyrażenie regularne `\ban?\b` próbuje dopasować całe wyrazy, które zaczynają się od litery `a` następuje zero lub jeden wystąpień litery `n`. Innymi słowy, próbuje dopasować słów `a` i `an`. Poniższy przykład ilustruje tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an?`|Uwzględnij wiadomość "" następuje zero lub jeden znak "n".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-exactly-n-times-n"></a>Dopasuj dokładnie n razy: {n}  
 `{` *n* `}` kwantyfikator dopasowuje poprzedzający element dokładnie *n* razy, gdzie *n* jest dowolną liczbą całkowitą. `{`*n* `}` jest zachłanne kwantyfikator, którego opóźnieniem odpowiednik to `{` *n*`}?`.  
  
 Na przykład, wyrażenie regularne `\b\d+\,\d{3}\b` próbuje dopasować granicę wyrazu, następuje jeden lub więcej cyfr dziesiętnych następują trzy cyfry dziesiętne, następuje granica wyrazu. Poniższy przykład ilustruje tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\,`|Dopasowuje znak przecinka.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-at-least-n-times-n"></a>Dopasowuje co najmniej n razy: {n,}  
 `{` *n* `,}` kwantyfikator dopasowuje poprzedni element co najmniej *n* razy, gdzie *n* jest dowolną liczbą całkowitą. `{`*n* `,}` jest zachłanne kwantyfikator, którego opóźnieniem odpowiednik to `{` *n*`,}?`.  
  
 Na przykład, wyrażenie regularne `\b\d{2,}\b\D+` próbuje dopasować granicę wyrazu, a następnie co najmniej dwie cyfry, następuje granica wyrazu a znak niebędący cyfrą. Poniższy przykład ilustruje tego wyrażenia regularnego. Wyrażenie regularne nie powiedzie się dopasować frazę `"7 days"` , ponieważ zawiera ona tylko jedną cyfrę dziesiętną, ale pomyślnie odpowiada zwrotów `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d{2,}`|Dopasowuje co najmniej dwie cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  
|`\D+`|Dopasowuje co najmniej jedną cyfrę niebędący cyfrą dziesiętną.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Dopasowanie między wartościami godziny n i m: {n, m}  
 `{` *n*`,`*m* `}` kwantyfikator dopasowuje poprzedni element co najmniej *n* razy, ale nie więcej niż *m*  razy, gdzie *n* i *m* są liczbami całkowitymi. `{`*n*`,`*m* `}` jest zachłanne kwantyfikator, którego opóźnieniem odpowiednik to `{` *n*`,`*m* `}?`.  
  
 W poniższym przykładzie, wyrażenie regularne `(00\s){2,4}` próbuje dopasować między dwoma i czterema wystąpieniami dwóch cyfr, zerowego następuje spacja. Należy pamiętać, że końcowa część ciąg wejściowy zawiera ten wzorzec pięciokrotnie zamiast maksymalnie cztery. Jednak początkowego fragmentu to substring (maksymalnie miejsce i piąty pary zera) pasuje do wzorca wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Odpowiada Zero lub więcej razy (dopasowanie z opóźnieniem): *?  
 `*?` Kwantyfikator dopasowuje poprzedni element zero lub więcej razy, ale jak tyle razy, ile to możliwe. Jest powolne odpowiednik metody zachłannego kwantyfikator `*`.  
  
 W poniższym przykładzie, wyrażenie regularne `\b\w*?oo\w*?\b` dopasowuje wszystkie wyrazy, które zawierają ciąg `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\w*?`|Dopasowuje zero lub więcej znaków słowa, ale liczbę znaków, jak to możliwe.|  
|`oo`|Pasuje do ciągu "wprowadzaniem".|  
|`\w*?`|Dopasowuje zero lub więcej znaków słowa, ale liczbę znaków, jak to możliwe.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Odpowiada jednej lub więcej razy (dopasowanie z opóźnieniem): +?  
 `+?` Kwantyfikator dopasowuje poprzedzający element jeden lub więcej razy, ale jak tyle razy, ile to możliwe. Jest powolne odpowiednik metody zachłannego kwantyfikator `+`.  
  
 Na przykład, wyrażenie regularne `\b\w+?\b` dopasowuje jeden lub więcej znaków oddzielonych granicy słowa. Poniższy przykład ilustruje tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Odpowiada Zero lub jeden raz (dopasowanie z opóźnieniem):?  
 `??` Kwantyfikator dopasowuje poprzedni element zero lub jeden podczas, ale jak tyle razy, ile to możliwe. Jest powolne odpowiednik metody zachłannego kwantyfikator `?`.  
  
 Na przykład, wyrażenie regularne `^\s*(System.)??Console.Write(Line)??\(??` próbuje dopasować ciągi "Console.Write —" lub "Elementu Console.WriteLine". Ciąg może również zawierać "System". przed "Konsoli" który może następować nawias otwierający. Ciąg musi być na początku wiersza, chociaż może być poprzedzona znakiem odstępu. Poniższy przykład ilustruje tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Dopasowuje początek strumienia wejściowego.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`(System.)??`|Dopasowuje zero lub jeden wystąpienie ciągu "System.".|  
|`Console.Write`|Pasuje do ciągu "Console.Write —".|  
|`(Line)??`|Dopasowuje zero lub jeden wystąpienie ciągu "Wiersz".|  
|`\(??`|Dopasowanie zera lub jednego wystąpienia nawias otwierający.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Odpowiada dokładnie n razy (dopasowanie z opóźnieniem): {n}?  
 `{` *n* `}?` kwantyfikator dopasowuje poprzedzający element dokładnie `n` razy, gdzie *n* jest dowolną liczbą całkowitą. Jest powolne odpowiednik metody zachłannego kwantyfikator `{` *n*`}+`.  
  
 W poniższym przykładzie, wyrażenie regularne `\b(\w{3,}?\.){2}?\w{3,}?\b` służy do identyfikowania adres witryny sieci Web. Należy pamiętać, jego pasuje do "www.microsoft.com" i "msdn.microsoft.com", ale nie pasuje "MojaWitrynaSieciWeb" lub "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(\w{3,}?\.)`|Dopasowuje co najmniej 3 znaków słowa, ale liczbę znaków, jak to możliwe, następuje kropka lub znak kropki. Jest to pierwsza grupa przechwytywania.|  
|`(\w{3,}?\.){2}?`|Pasuje do wzorca, w pierwszej grupie dwa razy, ale tyle razy, ile to możliwe.|  
|`\b`|Zakończ dopasowanie na granicy wyrazu.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Dopasowuje co najmniej n razy (dopasowanie z opóźnieniem): {n,}?  
 `{` *n* `,}?` kwantyfikator dopasowuje poprzedni element co najmniej `n` razy, gdzie *n* jest dowolną liczbą całkowitą, ale jak tyle razy, ile to możliwe. Jest powolne odpowiednik metody zachłannego kwantyfikator `{` *n*`,}`.  
  
 Zobacz przykład `{` *n* `}?` kwantyfikator w poprzedniej sekcji do celów informacyjnych. Używa wyrażenia regularnego, w tym przykładzie `{` *n* `,}` kwantyfikator próby dopasowania ciągu, który ma co najmniej trzy znaki następuje kropka.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Zgodność między n i m razy (dopasowanie z opóźnieniem): {n, m}?  
 `{` *n*`,`*m* `}?` kwantyfikator dopasowuje poprzedni element między `n` i `m` razy, gdzie *n* i *m* są liczbami całkowitymi, ale jak tyle razy, ile to możliwe. Jest powolne odpowiednik metody zachłannego kwantyfikator `{` *n*`,`*m*`}`.  
  
 W poniższym przykładzie, wyrażenie regularne `\b[A-Z](\w*\s+){1,10}?[.!?]` odpowiada zdania zawierające między wyrazami jednego do dziesięciu. Dopasowuje wszystkie zdania w ciągu wejściowym, z wyjątkiem jedno zdanie, które zawiera wyrazy 18.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`[A-Z]`|Dopasowuje znak wielkie litery od A do Z.|  
|`(\w*\s+)`|Dopasowuje zero lub więcej znaków słowa, następuje co najmniej jeden znak odstępu. Jest to pierwsza grupa przechwytywania.|  
|`{1,10}?`|Dopasowuje poprzedni wzorzec między 1 a 10 razy, ale tyle razy, jak to możliwe.|  
|`[.!?]`|Pasuje do jednej znaków interpunkcyjnych ".","!", lub "?".|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Kwantyfikatory zachłanne i z opóźnieniem  
 Liczba Kwantyfikatory są dwie wersje:  
  
- Zachłanne wersji.  
  
     Zachłanne kwantyfikator próbuje dopasować element dowolną liczbę razy.  
  
- Wersja niezachłanne (lub z opóźnieniem).  
  
     Niezachłanne kwantyfikator próbuje dopasować element tyle razy, jak to możliwe. Można przekształcić w zachłanne kwantyfikator kwantyfikatorem opóźniającym, po prostu dodając `?`.  
  
 Należy wziąć pod uwagę prostych wyrażeń regularnych, które ma na celu prowadzenie cztery ostatnie cyfry ciąg liczb, takie jak numer karty kredytowej. Wersja wyrażenia regularnego, który używa `*` jest zachłanne kwantyfikator `\b.*([0-9]{4})\b`. Jednak jeśli ciąg zawiera dwie liczby, tego wyrażenia regularnego dopasowuje jak w poniższym przykładzie przedstawiono cztery ostatnie cyfry, druga liczba.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Wyrażenie regularne nie jest zgodna z liczbą pierwszą, ponieważ `*` kwantyfikator próbuje dopasować poprzedni element tyle razy, jak to możliwe w ciągu całego, a więc znajdzie jego dopasowanie na końcu ciągu.  
  
 Nie jest żądane zachowanie. Zamiast tego można użyć `*?`kwantyfikatorem opóźniającym wyodrębniania cyfr z obu numerów, co ilustruje poniższy przykład.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 W większości przypadków wyrażeń regularnych bez znaczących Kwantyfikatory zachłanne podręczne i leniwa zwracać ten sam dopasowań. Najczęściej zwracają różne wyniki, jeśli są używane za pomocą symbolu wieloznacznego (`.`) metaznak, który dopasowuje dowolny znak.  
  
## <a name="quantifiers-and-empty-matches"></a>Kwantyfikatory i puste dopasowań  
 Kwantyfikatory `*`, `+`, i `{` *n*`,`*m* `}` i ich odpowiedniki z opóźnieniem nigdy nie Powtórz po pustą pasuje, gdy minimalna Znaleziono wiele przechwytywania. Ta zasada uniemożliwia Kwantyfikatory wprowadzania pętli nieskończonej na pusty Podwyrażenie dopasowuje, jeśli maksymalna liczba możliwych grupy przechwytywania to nieskończoną lub w pobliżu nieskończone.  
  
 Na przykład, poniższy kod przedstawia wynik wywołania <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody z wzorcem wyrażenia regularnego `(a?)*`, który dopasowuje zero lub jeden "" znak zero lub więcej razy. Należy pamiętać, że pojedynczej grupy przechwytywania przechwytuje każdego "" jako także <xref:System.String.Empty?displayProperty=nameWithType>, ale nie ma drugi pusty dopasowania, ponieważ pierwsze dopasowanie pusty powoduje kwantyfikator zatrzymać powtarzające się.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Aby wyświetlić praktyczne różnicę między grupy przechwytywania, który definiuje co najmniej i maksymalną liczbę oraz danych, który definiuje stałą liczbą przechwytywania, należy wziąć pod uwagę wzorce wyrażeń regularnych `(a\1|(?(1)\1)){0,2}` i `(a\1|(?(1)\1)){2}`. Oba wyrażenia regularne składa się z pojedynczej grupy przechwytywania, która jest zdefiniowana, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(a\1`|Dopasowanie albo "", oraz wartość pierwszej przechwyconej grupy...|  
|<code>&#124;(?(1)</code>|… lub sprawdzić, czy zdefiniowano pierwszej przechwyconej grupy. (Należy pamiętać, że `(?(1)` konstrukcja nie definiuje grupę przechwytywania.)|  
|`\1))`|Jeśli istnieje pierwszej przechwyconej grupy, odpowiada jego wartości. Jeśli grupa nie istnieje, grupa będzie odpowiadał <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 Pierwsze wyrażenie regularne próbuje dopasować tego wzorca między i cechujące się dwa razy; druga Strona, dokładnie dwa razy. Ponieważ pierwszy wzorzec osiągnie jego minimalną liczbę przechwytywania przy użyciu jego pierwszym przechwytywania <xref:System.String.Empty?displayProperty=nameWithType>, nigdy nie jest powtarzany próbuje dopasować `a\1`; `{0,2}` kwantyfikator umożliwia tylko puste dopasowań w ostatniej iteracji. Z kolei drugie wyrażenie regularne jest zgodny "", ponieważ był oceniany `a\1` po raz drugi; wymusza minimalną liczbę iteracji, 2, aparat powtórzyć po dopasowaniu puste.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
