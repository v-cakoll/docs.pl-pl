---
title: "Kwantyfikatory w wyrażeniach regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db1c3af1bb3ad207278eed64a8fb2ef8ed6dc465
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="quantifiers-in-regular-expressions"></a>Kwantyfikatory w wyrażeniach regularnych
Kwantyfikatory Określ liczbę wystąpień znaku, grupy lub klasy znaku musi być obecny w danych wejściowych znaleźć dopasowanie.  W poniższej tabeli wymieniono Kwantyfikatory obsługiwany przez platformę .NET.  
  
|Zachłanne kwantyfikatora|Opóźnieniem kwantyfikatora|Opis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Dopasowuje zero lub więcej razy.|  
|`+`|`+?`|Dopasowuje jeden lub więcej razy.|  
|`?`|`??`|Dopasowuje zero lub jeden raz.|  
|`{` *n* `}`|`{` *n* `}?`|Takie same  *n*  razy.|  
|`{` *n* `,}`|`{` *n* `,}?`|Zgodne z co najmniej  *n*  razy.|  
|`{` *n*  `,` *m*`}`|`{` *n*  `,` *m*`}?`|Zgodny z  *n*  do *m* razy.|  
  
 Ilości `n` i `m` są stałe całkowite. Zwykle Kwantyfikatory są intensywnie; spowodują one aparat wyrażenia regularnego do dopasowania dowolną liczbę wystąpień konkretnych wzorców, jak to możliwe. Dołączanie `?` znak kwantyfikator sprawia, że opóźnieniem; ta powoduje, że aparat wyrażenia regularnego do dopasowania możliwie jak najmniejszej liczby wystąpień. Pełny opis różnicy między Kwantyfikatory intensywnie i opóźnieniem, zobacz sekcję [ustawienia Greedy i Kwantyfikatory opóźniające](#Greedy) dalszej części tego tematu.  
  
> [!IMPORTANT]
>  Kwantyfikatory zagnieżdżenia (na przykład jako wzorzec wyrażenia regularnego `(a*)*` jest) może zwiększyć liczby porównań, które należy wykonać aparat wyrażeń regularnych, jako funkcja wykładnicza liczbę znaków w ciągu wejściowym. Aby uzyskać więcej informacji dotyczących tego zachowania i jego obejścia, zobacz [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Kwantyfikatory wyrażeń regularnych  
 W poniższych sekcjach wymieniono Kwantyfikatory obsługiwane w wyrażeniach regularnych programu .NET.  
  
> [!NOTE]
>  Jeśli *, +,?, {, i} znaki zostaną napotkane w wzorzec wyrażenia regularnego, aparat wyrażeń regularnych interpretuje je jako Kwantyfikatory lub część konstrukcji kwantyfikatora o ile nie są objęte [znak klasy](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Interpretować je jako znaki poza klasą znaków, musi wprowadzić je poprzedzając kreski ułamkowej odwróconej. Na przykład ciąg `\*` w wyrażeniu regularnym wzorzec jest interpretowana jako literału gwiazdki ("\*") znaków.  
  
### <a name="match-zero-or-more-times-"></a>Dopasowanie do zera lub więcej razy: *  
 `*` Kwantyfikatora zgodny z poprzednim elementem zero lub więcej razy. Jest to równoważne `{0,}` kwantyfikatora. `*`jest intensywnie kwantyfikatora, którego opóźnieniem równoważne jest `*?`.  
  
 Poniższy przykład przedstawia tego wyrażenia regularnego. Dziewięć cyfr w ciągu wejściowym, pięć odpowiada wzorzec i cztery (`95`, `929`, `9129`, i `9919`) czy nie.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`91*`|Zgodne "9" następuje zero lub więcej znaków "1".|  
|`9*`|Zgodne zero lub więcej znaków "9".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-one-or-more-times-"></a>Dopasowuje jeden lub więcej razy: +  
 `+` Kwantyfikatora zgodny z poprzednim elementem jeden lub więcej razy. Jest to równoważne `{1,}`. `+`jest intensywnie kwantyfikatora, którego opóźnieniem równoważne jest `+?`.  
  
 Na przykład, wyrażenie regularne `\ban+\w*?\b` próbuje dopasować całe wyrazy, które zaczynają się od litery `a` następuje co najmniej jedno wystąpienie litery `n`. Poniższy przykład przedstawia tego wyrażenia regularnego. Wyrażenie regularne dopasowuje wyrazy `an`, `annual`, `announcement`, i `antique`, a poprawnie nie odpowiada `autumn` i `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an+`|Dopasowanie jako "" następuje co najmniej jeden znak "n".|  
|`\w*?`|Dopasowuje znak słowa zero lub więcej razy, ale jako kilka razy, jak to możliwe.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-zero-or-one-time-"></a>Dopasowanie do zera lub raz:?  
 `?` Kwantyfikator dopasowuje podczas poprzedniego elementu zero lub jeden. Jest to równoważne `{0,1}`. `?`jest intensywnie kwantyfikatora, którego opóźnieniem równoważne jest `??`.  
  
 Na przykład, wyrażenie regularne `\ban?\b` próbuje dopasować całe wyrazy, które zaczynają się od litery `a` następuje zero lub jeden wystąpienia litery `n`. Innymi słowy, próbuje dopasować słowa `a` i `an`. Poniższy przykład przedstawia tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an?`|Dopasowanie jako "" następuje zero lub jeden znak "n".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-exactly-n-times-n"></a>Dopasowuje dokładnie n razy: {n}  
 `{`  *n*  `}` Kwantyfikatora zgodny z poprzednim elementem dokładnie  *n*  razy, gdzie  *n* jest liczbą całkowitą. `{`*n*`}`jest intensywnie kwantyfikatora, którego opóźnieniem równoważne jest `{`  *n*  `}?`.  
  
 Na przykład, wyrażenie regularne `\b\d+\,\d{3}\b` próbuje dopasować granicy word następuje co najmniej jeden cyfr dziesiętnych, następuje trzech cyfr dziesiętnych następuje granic programu word. Poniższy przykład przedstawia tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\,`|Dopasowuje znak przecinkami.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-at-least-n-times-n"></a>Dopasowuje co najmniej n razy: {n,}  
 `{`  *n*  `,}` Kwantyfikatora zgodny z poprzednim elementem co najmniej  *n*  razy, gdzie  *n* jest liczbą całkowitą. `{`*n*`,}`jest intensywnie kwantyfikatora, którego opóźnieniem równoważne jest `{`  *n*  `}?`.  
  
 Na przykład, wyrażenie regularne `\b\d{2,}\b\D+` próbuje dopasować granicy word następuje co najmniej dwie cyfry następuje granic programu word i cyfra —. Poniższy przykład przedstawia tego wyrażenia regularnego. Wyrażenia regularnego nie powiedzie się dopasować frazę `"7 days"` ponieważ zawiera ona tylko jedną cyfrę, ale pomyślnie odpowiada fraz `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d{2,}`|Zgodne z co najmniej dwóch cyfr dziesiętnych.|  
|`\b`|Dopasowuje granicę wyrazu.|  
|`\D+`|Zgodne z co najmniej jedną cyfrę z systemem innym niż dziesiętnych.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Dopasowanie między czasu n i m: {n, m}  
 `{`  *n*  `,` *m* `}` kwantyfikatora zgodny z poprzednim elementem co najmniej  *n*  godzinach ale nie więcej niż *m* razy, gdzie  *n*  i *m* są liczbami całkowitymi. `{`*n*`,`*m* `}` jest intensywnie kwantyfikatora, którego opóźnieniem równoważne jest `{`  *n*  `,` *m*`}?`.  
  
 W poniższym przykładzie, wyrażenie regularne `(00\s){2,4}` próbuje dopasować od dwóch do czterech wystąpień dwóch zero cyfr spację. Należy pamiętać, że końcowa część ciąg wejściowy zawiera ten wzorzec pięć razy zamiast maksymalnie cztery. Jednak początkowego fragmentu tego podciąg (do obszaru i piątej pary zer) odpowiada wzorzec wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Zgodne Zero lub więcej razy (dopasowanie opóźnieniem): *?  
 `*?` Kwantyfikatora zgodny z poprzednim elementem zero lub więcej razy, ale jako kilka razy, jak to możliwe. Jest odpowiednikiem opóźnieniem intensywnie kwantyfikatora `*`.  
  
 W poniższym przykładzie, wyrażenie regularne `\b\w*?oo\w*?\b` dopasowuje wszystkie słowa, które zawierają ciąg znaków `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\w*?`|Zgodne zero lub więcej znaków programu word, ale liczbę znaków, jak to możliwe.|  
|`oo`|Zgodny z ciągiem "oo".|  
|`\w*?`|Zgodne zero lub więcej znaków programu word, ale liczbę znaków, jak to możliwe.|  
|`\b`|Kończy się granic programu word.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Zgodny z jedną lub więcej razy (dopasowanie opóźnieniem): +?  
 `+?` Kwantyfikatora zgodny z poprzednim elementem jeden lub więcej razy, ale jako kilka razy, jak to możliwe. Jest odpowiednikiem opóźnieniem intensywnie kwantyfikatora `+`.  
  
 Na przykład, wyrażenie regularne `\b\w+?\b` odpowiada co najmniej jeden znak oddzielone granice programu word. Poniższy przykład przedstawia tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Dopasowanie do zera lub raz (dopasowanie opóźnieniem):?  
 `??` Kwantyfikatora jest zgodny z poprzednim godziną element zero lub jeden, ale jako kilka razy, jak to możliwe. Jest odpowiednikiem opóźnieniem intensywnie kwantyfikatora `?`.  
  
 Na przykład, wyrażenie regularne `^\s*(System.)??Console.Write(Line)??\(??` próbuje dopasować ciągów "Console.Write" lub "Elementu Console.WriteLine". Ciąg mogą również obejmować "System". przed "Konsola" który może następować nawias otwierający. Ciąg musi być na początku wiersza, chociaż może być poprzedzone biały znak. Poniższy przykład przedstawia tego wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Zgodne początek strumienia wejściowego.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`(System.)??`|Zgodne zero lub jeden wystąpienie ciągu "System.".|  
|`Console.Write`|Zgodny z ciągiem "Console.Write".|  
|`(Line)??`|Zgodne zero lub jeden wystąpienie ciągu "Wiersz".|  
|`\(??`|Wystąpienie dopasowania zero lub jeden nawiasem otwierającym.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Odpowiada dokładnie n razy (dopasowanie opóźnieniem): {n}?  
 `{`  *n*  `}?` Kwantyfikatora zgodny z poprzednim elementem dokładnie `n` razy, gdzie  *n*  jest liczbą całkowitą. Jest odpowiednikiem opóźnieniem intensywnie kwantyfikatora `{`  *n*  `}+`.  
  
 W poniższym przykładzie, wyrażenie regularne `\b(\w{3,}?\.){2}?\w{3,}?\b` służy do identyfikowania adres witryny sieci Web. Należy pamiętać, że odpowiada "www.microsoft.com" i "msdn.microsoft.com", ale nie zgadza się "MojaWitrynaSieciWeb" lub "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(\w{3,}?\.)`|Zgodne z co najmniej 3 znaki programu word, ale liczbę znaków, jak to możliwe, a następnie kropką lub znak kropki. Jest to pierwsza grupa przechwytywania.|  
|`(\w{3,}?\.){2}?`|Pasuje do wzorca w pierwszej grupy dwa razy, ale kilka razy, ile to możliwe.|  
|`\b`|W celu dopasowania na granicy programu word.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Dopasowuje co najmniej n razy (dopasowanie opóźnieniem): {n,}?  
 `{`  *n*  `,}?` Kwantyfikatora zgodny z poprzednim elementem co najmniej `n` razy, gdzie  *n*  jest liczbą całkowitą, ale jako kilka razy możliwe. Jest odpowiednikiem opóźnieniem intensywnie kwantyfikatora `{`  *n*  `,}`.  
  
 Zobacz przykład `{`  *n*  `}?` kwantyfikatora w poprzedniej sekcji ilustrację. Używa wyrażenia regularnego, w tym przykładzie `{`  *n*  `,}` kwantyfikatora odpowiadające ciąg, który ma co najmniej trzy znaki następuje okres.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Dopasowania zakresu od n do m razy (dopasowanie opóźnieniem): {n, m}?  
 `{`  *n*  `,` *m* `}?` kwantyfikator dopasowuje poprzedni element między `n` i `m` razy, gdzie  *n*  i *m* są liczbami całkowitymi, ale jako kilka razy, jak to możliwe. Jest odpowiednikiem opóźnieniem intensywnie kwantyfikatora `{`  *n*  `,` *m*`}`.  
  
 W poniższym przykładzie, wyrażenie regularne `\b[A-Z](\w*\s+){1,10}?[.!?]` odpowiada zdania zawierające między wyrazami jednego do dziesięciu. Jest on zgodny wszystkich zdań w ciągu wejściowym, z wyjątkiem jedno zdanie, które zawiera wyrazy, 18.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`[A-Z]`|Zgodne wielką literę z zakresu od A do Z.|  
|`(\w*\s+)`|Zgodne zero lub więcej znaków word następuje co najmniej jeden znak odstępu. Jest to pierwsza grupa przechwytywania.|  
|`{1,10}?`|Zgodna ze wzorcem poprzedniej zakresu od 1 do 10 razy, ale kilka razy, ile to możliwe.|  
|`[.!?]`|Pasuje do jednej znaków interpunkcyjnych ".","!", lub "?".|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Kwantyfikatory intensywnie i opóźnieniem  
 Liczba Kwantyfikatory ma dwie wersje:  
  
-   Zachłanne wersji.  
  
     Zachłanne kwantyfikatora próbuje zgodny element dowolną liczbę razy.  
  
-   Wersja niezachłanne (lub opóźnieniem).  
  
     Niezachłanne kwantyfikatora próbuje zgodny element kilka razy. Zachłanne kwantyfikator można przekształcić tzw po prostu dodając `?`.  
  
 Należy wziąć pod uwagę proste wyrażenie regularne jest przeznaczona do wyodrębniania cztery ostatnie cyfry ciąg liczb, takich jak numer karty kredytowej. Wersja wyrażenie regularne, która używa `*` jest intensywnie kwantyfikatora `\b.*([0-9]{4})\b`. Jednak jeśli ciąg zawiera dwie liczb, tego wyrażenie regularne dopasowuje jak w poniższym przykładzie przedstawiono cztery ostatnie cyfry, druga liczba.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Wyrażenie regularne nie odpowiada pierwszej liczby, ponieważ `*` kwantyfikatora próbuje dopasować poprzedni element tyle razy, jak to możliwe w cały ciąg, a więc znajdzie jego dopasowuje koniec ciągu.  
  
 To nie jest zamierzone zachowanie. Zamiast tego można użyć `*?`tzw można wyodrębnić cyfr z obu numerów, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 W większości przypadków wyrażeń regularnych z kwantyfikatorami zachłanne i opóźnieniem zwrócić tego samego dopasowań. Najczęściej zwracają różne wyniki, jeśli są używane z symbolem wieloznacznym (`.`) metaznak, który dopasowuje dowolny znak.  
  
## <a name="quantifiers-and-empty-matches"></a>Kwantyfikatory i pusty dopasowań  
 Kwantyfikatory `*`, `+`, i `{`  *n*  `,` *m* `}` i ich odpowiedniki opóźnieniem nigdy nie Powtarzaj po pusta Dopasuj, jeśli znaleziono minimalną liczbę przechwytywania. Ta zasada uniemożliwia wprowadzanie nieskończone pętle dopasowań pusty Podwyrażenie po nieskończone maksymalna liczba możliwych grupy przechwytywania lub w jego pobliżu nieskończone Kwantyfikatory.  
  
 Na przykład poniższy kod przedstawia wynik wywołania <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody z wzorcem wyrażenia regularnego `(a?)*`, który dopasowuje zero lub jeden "" znak zero lub więcej razy. Należy pamiętać, że pojedynczej grupy przechwytywania przechwytuje każdego "", jak również jako <xref:System.String.Empty?displayProperty=nameWithType>, ale ten nie zostanie odnaleziony drugi odpowiednik pusta, kwantyfikatora przestanie powtarzające się powoduje, że pierwsze dopasowanie puste.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Aby wyświetlić praktyczne różnica między grupą przechwytywania, który definiuje co najmniej i maksymalną liczbę przechwytywania i taki, który definiuje stała liczba przechwytywania, należy wziąć pod uwagę wzorce wyrażenia regularnego `(a\1|(?(1)\1)){0,2}` i `(a\1|(?(1)\1)){2}`. Oba wyrażenia regularnego składają się z jednej grupy przechwytywania, która jest zdefiniowana, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(a\1`|Albo dopasowania "", wraz z wartość pierwszego przechwyconej grupy...|  
|`&#124;(?(1)`|… lub sprawdzić, czy pierwszy przechwyconej grupy została zdefiniowana. (Należy pamiętać, że `(?(1)` konstrukcja nie definiuje grupę przechwyconą.)|  
|`\1))`|Jeśli istnieje pierwszej grupy przechwycone, odpowiada jego wartości. Jeśli grupa nie istnieje, zostanie odpowiada grupie <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 Pierwsze wyrażenie regularne próbuje dopasować tego wzorca między zero a dwa razy; druga Strona, dokładnie dwa razy. Ponieważ pierwszy wzorzec osiągnie jego minimalną liczbę zbieranych z jej pierwszym przechwytywania <xref:System.String.Empty?displayProperty=nameWithType>, nigdy nie powtarza się, aby podjąć próbę dopasowania `a\1`; `{0,2}` kwantyfikatora umożliwia tylko puste dopasowań w ostatnim iteracji. Natomiast drugie wyrażenie regularne zgodne "", ponieważ jej wynikiem `a\1` po raz drugi; minimalna liczba iteracji, 2, wymusza aparat powtórzeń po pusty dopasowania.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
