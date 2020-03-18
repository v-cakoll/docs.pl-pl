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
ms.openlocfilehash: f1627248cbed0f03c6fb76ce660f9b2bf7764781
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160017"
---
# <a name="quantifiers-in-regular-expressions"></a>Kwantyfikatory w wyrażeniach regularnych
Kwantyfikatory określają, ile wystąpień klasy znaku, grupy lub znaku musi być obecnych w danych wejściowych, aby można było znaleźć dopasowanie.  W poniższej tabeli wymieniono kwantyfikatory obsługiwane przez firmę .NET.  
  
|Chciwy kwantyfikator|Kwantyfikator leniwy|Opis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Dopasuj zero lub więcej razy.|  
|`+`|`+?`|Dopasuj jeden lub więcej razy.|  
|`?`|`??`|Dopasuj zero lub jeden raz.|  
|`{`*n*`}`|`{`*n*`}?`|Dopasuj dokładnie *n* razy.|  
|`{`*n*`,}`|`{`*n*`,}?`|Dopasuj co najmniej *n* razy.|  
|`{`*n* `,` *m*`}`|`{`*n* `,` *m*`}?`|Mecz od *n* do *m* razy.|  
  
 Ilości `n` i `m` są stałymi całkowitymi. Zwykle kwantyfikatory są chciwe; powodują one aparat wyrażeń regularnych, aby dopasować jak najwięcej wystąpień określonych wzorców, jak to możliwe. Dołączanie `?` znaku do kwantyfikatora sprawia, że jest leniwy; powoduje, że aparat wyrażeń regularnych dopasowywać jak najmniejszej liczbie wystąpień, jak to możliwe. Aby uzyskać pełny opis różnicy między chciwy i leniwy kwantyfikatorów, zobacz sekcję [Chciwi i Leniwy Kwantyfikatory](#Greedy) w dalszej części tego tematu.  
  
> [!IMPORTANT]
> Kwantyfikatory zagnieżdżania `(a*)*` (na przykład, tak jak robi to wzorzec wyrażenia regularnego) mogą zwiększyć liczbę porównań, które musi wykonywać aparat wyrażeń regularnych, jako wykładnicza funkcja liczby znaków w ciągu wejściowym. Aby uzyskać więcej informacji na temat tego zachowania i jego obejścia, zobacz [Wycofywanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kwantyfikatory wyrażeń regularnych  
 W poniższych sekcjach wymieniono kwantyfikatory obsługiwane przez wyrażenia regularne .NET.  
  
> [!NOTE]
> Jeśli znaki *, +, ?, {i } zostaną napotkane we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych interpretuje je jako kwantyfikatory lub część konstrukcji kwantyfikatora, chyba że są one uwzględnione w [klasie znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Aby zinterpretować je jako literały poza klasą znaków, należy ich uniknąć, poprzedzając je ukośnikiem odwrotnym. Na przykład ciąg `\*` w wzorzec wyrażenia regularnego jest interpretowany\*jako znak literału gwiazdki (" ").  
  
### <a name="match-zero-or-more-times-"></a>Dopasuj zero lub więcej razy: *  
 Kwantyfikator `*` pasuje do poprzedniego elementu zero lub więcej razy. Jest to odpowiednik `{0,}` kwantyfikatora. `*`jest chciwym kwantyfikatorem, którego leniwym odpowiednikiem jest `*?`.  
  
 Poniższy przykład ilustruje to wyrażenie regularne. Z dziewięciu cyfr w ciągu wejściowym, pięć pasuje`95` `929`do `9219`wzoru, a cztery ( , , i `9919`) nie.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`91*`|Dopasuj "9", po którym następuje zero lub więcej znaków "1".|  
|`9*`|Dopasuj zero lub więcej znaków "9".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-one-or-more-times-"></a>Mecz jeden lub więcej razy: +  
 Kwantyfikator `+` pasuje do poprzedniego elementu jeden lub więcej razy. Jest to `{1,}`równoważne . `+`jest chciwym kwantyfikatorem, którego leniwym odpowiednikiem jest `+?`.  
  
 Na przykład wyrażenie `\ban+\w*?\b` regularne próbuje dopasować całe słowa, `a` które zaczynają się od litery, po której następuje jedno lub więcej wystąpień litery `n`. Poniższy przykład ilustruje to wyrażenie regularne. Wyrażenie regularne pasuje `an`do `annual` `announcement`słów `antique`, , i , `autumn` `all`i poprawnie nie pasuje i .  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an+`|Dopasuj literę "a", po której następuje co najmniej jedna liczba znaków "n".|  
|`\w*?`|Dopasuj znak słowa zero lub więcej razy, ale jak kilka razy.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-zero-or-one-time-"></a>Mecz zero lub jeden raz: ?  
 Kwantyfikator `?` pasuje do poprzedniego elementu zero lub jeden raz. Jest to `{0,1}`równoważne . `?`jest chciwym kwantyfikatorem, którego leniwym odpowiednikiem jest `??`.  
  
 Na przykład wyrażenie `\ban?\b` regularne próbuje dopasować całe wyrazy, które zaczynają się od litery, `a` po której następuje zero lub jedno wystąpienie litery `n`. Innymi słowy, próbuje dopasować słowa `a` `an`i . Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an?`|Dopasuj znak "a", po którym następuje zero lub jeden znak "n".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-exactly-n-times-n"></a>Dopasuj dokładnie n razy: {n}  
 Kwantyfikator `{` *n* `}` pasuje do poprzedniego elementu dokładnie *n* razy, gdzie *n* jest dowolną liczbą całkowitą. `{`*n* `}` jest chciwym kwantyfikatorem, którego leniwym odpowiednikiem jest `{` *n*`}?`.  
  
 Na przykład wyrażenie `\b\d+\,\d{3}\b` regularne próbuje dopasować granicę wyrazu, po której następuje jedna lub więcej cyfr dziesiętnych, po których następują trzy cyfry dziesiętne, po których następuje granica wyrazu. Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\,`|Dopasuj znak przecinka.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-at-least-n-times-n"></a>Dopasuj co najmniej n razy: {n,}  
 Kwantyfikator `{` *n* `,}` odpowiada poprzedzającemu elementowi co najmniej *n* razy, gdzie *n* jest dowolną liczbą całkowitą. `{`*n* `,}` jest chciwym kwantyfikatorem, którego leniwym odpowiednikiem jest `{` *n*`,}?`.  
  
 Na przykład wyrażenie `\b\d{2,}\b\D+` regularne próbuje dopasować granicę słowa, po której następuje co najmniej dwie cyfry, po których następuje granica słowa i znak niecyfrowy. Poniższy przykład ilustruje to wyrażenie regularne. Wyrażenie regularne nie pasuje `"7 days"` do frazy, ponieważ zawiera tylko jedną cyfrę dziesiętną, ale pomyślnie pasuje do fraz `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d{2,}`|Dopasuj co najmniej dwie cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  
|`\D+`|Dopasuj co najmniej jedną cyfrę niedziecową.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Mecz między n i m Czasy: {n,m}  
 Kwantyfikator `{` *n*`,`*m* `}` odpowiada poprzedniemu elementowi co najmniej *n* razy, ale nie więcej niż *m* razy, gdzie *n* i *m* są liczbami całkowitymi. `{`*n*`,`*m* `}` jest chciwym kwantyfikatorem, którego leniwym odpowiednikiem `{`jest *n*`,`*m*`}?`.  
  
 W poniższym przykładzie wyrażenie `(00\s){2,4}` regularne próbuje dopasować między dwoma i czterema wystąpieniami dwóch cyfr zerowych, po których następuje spacja. Należy zauważyć, że ostatnia część ciągu wejściowego zawiera ten wzorzec pięć razy, a nie maksymalnie cztery. Jednak tylko początkowa część tego podciągu (do spacji i piątej pary zer) pasuje do wzorca wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Mecz zero lub więcej razy (Lazy Match): *?  
 Kwantyfikator `*?` pasuje do poprzedniego elementu zero lub więcej razy, ale jak kilka razy, jak to możliwe. Jest to leniwy odpowiednik chciwego kwantyfikatora `*`.  
  
 W poniższym przykładzie wyrażenie `\b\w*?oo\w*?\b` regularne pasuje do `oo`wszystkich wyrazów, które zawierają ciąg .  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\w*?`|Dopasuj zero lub więcej znaków wyrazu, ale jak najmniej znaków.|  
|`oo`|Dopasuj ciąg "oo".|  
|`\w*?`|Dopasuj zero lub więcej znaków wyrazu, ale jak najmniej znaków.|  
|`\b`|Koniec na granicy słowa.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Mecz jeden lub więcej razy (Lazy Match): +?  
 Kwantyfikator `+?` pasuje do poprzedniego elementu jeden lub więcej razy, ale jak kilka razy, jak to możliwe. Jest to leniwy odpowiednik chciwego kwantyfikatora `+`.  
  
 Na przykład wyrażenie `\b\w+?\b` regularne pasuje do jednego lub więcej znaków oddzielonych granicami wyrazu. Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Mecz zero lub jeden raz (Lazy Match): ??  
 Kwantyfikator `??` pasuje do poprzedniego elementu zero lub jeden raz, ale jak kilka razy, jak to możliwe. Jest to leniwy odpowiednik chciwego kwantyfikatora `?`.  
  
 Na przykład wyrażenie `^\s*(System.)??Console.Write(Line)??\(??` regularne próbuje dopasować ciągi "Console.Write" lub "Console.WriteLine". Ciąg może również zawierać "System". przed "Konsolą", po czym może następował nawias otwierający. Ciąg musi znajdować się na początku wiersza, chociaż może być poprzedzony białym spacją. Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Dopasuj początek strumienia wejściowego.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`(System.)??`|Dopasuj zero lub jedno wystąpienie ciągu "System.".|  
|`Console.Write`|Dopasuj ciąg "Console.Write".|  
|`(Line)??`|Dopasuj zero lub jedno wystąpienie ciągu "Linia".|  
|`\(??`|Dopasuj zero lub jedno wystąpienie nawiasu otwierającego.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Dopasuj dokładnie n razy (Lazy Match): {n}?  
 Kwantyfikator `{` *n* `}?` odpowiada `n` poprzedzającym elementowi dokładnie razy, gdzie *n* jest dowolną liczbą całkowitą. Jest to leniwy odpowiednik chciwego `{`kwantyfikatora *n*`}`.  
  
 W poniższym przykładzie wyrażenie `\b(\w{3,}?\.){2}?\w{3,}?\b` regularne służy do identyfikowania adresu witryny sieci Web. Należy pamiętać, że pasuje do "www.microsoft.com" i "msdn.microsoft.com", ale nie pasuje do "mywebsite" lub "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(\w{3,}?\.)`|Dopasuj co najmniej 3 znaki wyrazu, ale jak najmniej znaków, a następnie znak kropki lub kropki. Jest to pierwsza grupa przechwytywania.|  
|`(\w{3,}?\.){2}?`|Dopasuj wzorzec w pierwszej grupie dwa razy, ale jak kilka razy.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Dopasuj co najmniej n razy (Lazy Match): {n,}?  
 Kwantyfikator `{` *n* `,}?` odpowiada poprzedniemu elementowi co najmniej `n` raz, gdzie *n* jest dowolną liczbą całkowitą, ale jak najmniej razy. Jest to leniwy odpowiednik chciwego `{`kwantyfikatora *n*`,}`.  
  
 Zobacz przykład `{` *dla kwantyfikatora n* `}?` w poprzedniej sekcji, aby uzyskać ilustrację. Wyrażenie regularne w tym `{`przykładzie używa kwantyfikatora *n,* `,}` aby dopasować ciąg znaków, który ma co najmniej trzy znaki, po którym następuje kropka.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Mecz między n i m Times (Lazy Match): {n,m}?  
 Kwantyfikator `{` *n*`,`*m* `}?` pasuje `n` `m` do poprzedniego elementu między i godzinami, gdzie *n* i *m* są liczbami całkowitymi, ale jak najmniej razy. Jest to `{`leniwy odpowiednik chciwego kwantyfikatora *n*`,`*m*`}`.  
  
 W poniższym przykładzie wyrażenie `\b[A-Z](\w*?\s*?){1,10}[.!?]` regularne pasuje do zdań zawierających od jednego do dziesięciu słów. Pasuje do wszystkich zdań w ciągu wejściowym z wyjątkiem jednego zdania, które zawiera 18 słów.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`[A-Z]`|Dopasuj znak wielkich liter od A do Z.|  
|`(\w*?\s*?)`|Dopasuj zero lub więcej znaków wyrazu, po których następuje co najmniej jeden znak odstępu, ale jak najmniej razy. Jest to pierwsza grupa przechwytywania.|  
|`{1,10}`|Dopasuj poprzedni wzorzec od 1 do 10 razy.|  
|`[.!?]`|Dopasuj dowolny znak interpunkcyjny ".", "!", lub "?".|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a>Chciwi i leniwi kwantyfikatory  
 Kilka kwantyfikatorów ma dwie wersje:  
  
- Chciwa wersja.  
  
     Chciwy kwantyfikator próbuje dopasować element tyle razy, ile to możliwe.  
  
- Wersja niechciwa (lub leniwa).  
  
     Kwantyfikator niechciwy próbuje dopasować element tak kilka razy, jak to możliwe. Możesz przekształcić chciwy kwantyfikator w leniwy kwantyfikator, po prostu dodając . `?`  
  
 Należy wziąć pod uwagę proste wyrażenie regularne, które ma na celu wyodrębnienie ostatnich czterech cyfr z ciągu liczb, takich jak numer karty kredytowej. Wersja wyrażenia regularnego, który `*` używa chciwy `\b.*([0-9]{4})\b`kwantyfikator jest . Jeśli jednak ciąg zawiera dwie liczby, to wyrażenie regularne pasuje tylko do ostatnich czterech cyfr drugiej liczby, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Wyrażenie regularne nie pasuje do pierwszej liczby, ponieważ `*` kwantyfikator próbuje dopasować poprzedni element tyle razy, ile to możliwe w całym ciągu, a więc znajdzie jego dopasowanie na końcu ciągu.  
  
 Nie jest to pożądane zachowanie. Zamiast tego można `*?`użyć kwantyfikatora leniwego do wyodrębnienia cyfr z obu liczb, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 W większości przypadków wyrażenia regularne z chciwymi i leniwymi kwantyfikatorami zwracają te same dopasowania. Najczęściej zwracają różne wyniki, gdy są używane z`.`metaznakiem symboli wieloznacznych ( ), który pasuje do dowolnego znaku.  
  
## <a name="quantifiers-and-empty-matches"></a>Kwantyfikatory i puste dopasowania  
 `*`Kwantyfikatory `+`, `{`i *n*`,`*m* `}` i ich leniwe odpowiedniki nigdy nie powtarzają się po pustym meczu, gdy zostanie znaleziony minimalna liczba przechwytów. Ta reguła uniemożliwia kwantyfikatorom wprowadzanie nieskończonych pętli na pustych podwyrażeniach, gdy maksymalna liczba możliwych przechwytów grup jest nieskończona lub prawie nieskończona.  
  
 Na przykład poniższy kod pokazuje wynik wywołania <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody z wzorcem `(a?)*`wyrażenia regularnego, który pasuje do zera lub jednego znaku "a" zero lub więcej razy. Należy zauważyć, że pojedyncza grupa przechwytywania przechwytuje <xref:System.String.Empty?displayProperty=nameWithType>każdy "a", jak również , ale nie ma drugiego pustego dopasowania, ponieważ pierwsze puste dopasowanie powoduje, że kwantyfikator przestaje się powtarzać.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Aby zobaczyć praktyczną różnicę między grupą przechwytywania, która definiuje minimalną i maksymalną liczbę przechwytów, a grupą definiującą stałą liczbę przechwytów, należy wziąć pod uwagę wzorce `(a\1|(?(1)\1)){0,2}` wyrażeń regularnych i `(a\1|(?(1)\1)){2}`. Oba wyrażenia regularne składają się z pojedynczej grupy przechwytywania, która jest zdefiniowana w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(a\1`|Albo dopasować "a" wraz z wartością pierwszej przechwyconej grupy ...|  
|<code>&#124;(?(1)</code>|… lub sprawdzić, czy zdefiniowano pierwszą przechwyconą grupę. (Należy zauważyć, że `(?(1)` konstrukcja nie definiuje grupy przechwytywania.)|  
|`\1))`|Jeśli istnieje pierwsza przechwycona grupa, dopasuj jej wartość. Jeśli grupa nie istnieje, grupa <xref:System.String.Empty?displayProperty=nameWithType>będzie zgodna .|  
  
 Pierwsze wyrażenie regularne próbuje dopasować ten wzorzec między 0 a dwa razy; drugi, dokładnie dwa razy. Ponieważ pierwszy wzór osiąga minimalną liczbę przechwytów z <xref:System.String.Empty?displayProperty=nameWithType>jego pierwszego przechwytywania , `a\1`nigdy nie powtarza się, aby spróbować dopasować; `{0,2}` kwantyfikator zezwala tylko na puste dopasowania w ostatniej iteracji. Natomiast drugie wyrażenie regularne jest zgodne z "a", ponieważ ocenia `a\1` po raz drugi; minimalna liczba iteracji, 2, zmusza silnik do powtórzenia po pustym meczu.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Nawracanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
