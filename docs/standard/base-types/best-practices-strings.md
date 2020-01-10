---
title: Najlepsze rozwiązania dotyczące używania ciągów w programie .NET
description: Dowiedz się, jak efektywnie używać ciągów w aplikacjach .NET.
ms.date: 05/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework],searching
- best practices,string comparison and sorting
- strings [.NET Framework],best practices
- strings [.NET Framework],basic string operations
- sorting strings
- strings [.NET Framework],sorting
- string comparison [.NET Framework],best practices
- string sorting
- comparing strings
- strings [.NET Framework],comparing
ms.assetid: b9f0bf53-e2de-4116-8ce9-d4f91a1df4f7
ms.openlocfilehash: c88776ea9d8ba17d86767b704e8b0eaff5b6cb89
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711483"
---
# <a name="best-practices-for-using-strings-in-net"></a>Najlepsze rozwiązania dotyczące używania ciągów w programie .NET

Platforma .NET zapewnia rozbudowaną obsługę tworzenia zlokalizowanych i globalnych aplikacji oraz ułatwia stosowanie Konwencji dla bieżącej kultury lub określonej kultury podczas wykonywania typowych operacji, takich jak sortowanie i wyświetlanie ciągów. Jednak sortowanie lub Porównywanie ciągów nie zawsze jest operacją zależną od kultury. Na przykład ciągi, które są używane wewnętrznie przez aplikację zwykle, powinny być obsługiwane identycznie we wszystkich kulturach. Gdy dane niezależne od kultury, takie jak tagi XML, Tagi HTML, nazwy użytkowników, ścieżki plików i nazwy obiektów systemowych, są interpretowane tak, jakby były wrażliwe na kulturę, kod aplikacji może podlegać rozdrobnym usterkom, złej wydajności i, w niektórych przypadkach, Problemy z zabezpieczeniami.

W tym temacie opisano metody sortowania, porównywania i wielkości liter w programie .NET, przedstawiono zalecenia dotyczące wybierania odpowiedniej metody obsługi ciągów i zawiera dodatkowe informacje na temat metod obsługi ciągów. Bada także, jak sformatowane dane, takie jak dane liczbowe oraz dane daty i godziny, są obsługiwane na potrzeby wyświetlania i przechowywania.

## <a name="recommendations-for-string-usage"></a>Zalecenia dotyczące użycia ciągów

Podczas opracowywania przy użyciu platformy .NET należy przestrzegać następujących prostych zaleceń w przypadku używania ciągów:

- Używaj przeciążeń, które jawnie określają reguły porównywania ciągów dla operacji na ciągach. Zazwyczaj wymaga to wywołania przeciążenia metody, która ma parametr typu <xref:System.StringComparison>.
- Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> do porównań jako bezpieczny domyślny dla dopasowania ciągu niezależny od.
- Użyj porównania z <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> w celu uzyskania lepszej wydajności.
- Użyj operacji na ciągach, które są oparte na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> podczas wyświetlania danych wyjściowych dla użytkownika.
- Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartości innych niż lingwistyczne zamiast operacji na ciągach w oparciu o <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>, gdy porównanie jest istotna dla języka (na przykład symboliczny).
- Użyj metody <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> zamiast metody <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> podczas normalizowania ciągów do porównania.
- Użyj przeciążenia metody <xref:System.String.Equals%2A?displayProperty=nameWithType>, aby sprawdzić, czy dwa ciągi są równe.
- Użyj metod <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType>, aby sortować ciągi, a nie sprawdzaj równości.
- Użyj formatowania z uwzględnieniem kultury, aby wyświetlić dane niebędące ciągami, takie jak liczby i daty, w interfejsie użytkownika. Używaj formatowania z [kulturą niezmienną](xref:System.Globalization.CultureInfo.InvariantCulture) , aby utrwalać dane niebędące ciągami w postaci ciągów.

W przypadku używania ciągów należy unikać następujących praktyk:

- Nie należy używać przeciążeń, które nie jawnie lub niejawnie określają reguły porównywania ciągów dla operacji na ciągach.
- Nie używaj w większości przypadków operacji na ciągach opartych na <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>. Jednym z kilku wyjątków jest to, że w przypadku utrwalania w sposób istotny, ale kulturalnie niezależny od dane.
- Nie należy używać przeciążenia metody <xref:System.String.Compare%2A?displayProperty=nameWithType> lub <xref:System.String.CompareTo%2A> i testu dla zwracanej wartości zero, aby określić, czy dwa ciągi są równe.
- Nie używaj formatowania z uwzględnieniem kultury, aby zachować dane liczbowe lub dane daty i godziny w postaci ciągu.

## <a name="specifying-string-comparisons-explicitly"></a>Jawne określanie porównywania ciągów

Większość metod manipulowania ciągami w .NET jest przeciążona. Zazwyczaj co najmniej jedno Przeciążenie przyjmuje ustawienia domyślne, natomiast inne nie akceptują żadnych ustawień domyślnych, a zamiast tego definiują precyzyjne metody porównywania ciągów lub manipulowania nimi. Większość metod, które nie bazują na wartościach domyślnych, zawiera parametr typu <xref:System.StringComparison>, który jest wyliczeniem, które jawnie określa reguły dla porównania ciągów przez kulturę i wielkość liter. W poniższej tabeli opisano elementy członkowskie wyliczenia <xref:System.StringComparison>.

|StringComparison element członkowski|Opis|
|-----------------------------|-----------------|
|<xref:System.StringComparison.CurrentCulture>|Wykonuje porównanie z rozróżnianiem wielkości liter przy użyciu bieżącej kultury.|
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu bieżącej kultury.|
|<xref:System.StringComparison.InvariantCulture>|Wykonuje porównanie z rozróżnianiem wielkości liter przy użyciu niezmiennej kultury.|
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu niezmiennej kultury.|
|<xref:System.StringComparison.Ordinal>|Wykonuje porównanie porządkowe.|
|<xref:System.StringComparison.OrdinalIgnoreCase>|Wykonuje porównanie porządkowe bez uwzględniania wielkości liter.|

Na przykład Metoda <xref:System.String.IndexOf%2A>, która zwraca indeks podciągu w obiekcie <xref:System.String>, który pasuje do znaku lub ciągu, ma dziewięć przeciążeń:

- <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>i <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, która domyślnie wykonuje numer porządkowy (bez uwzględniania wielkości liter i kultury) Wyszukiwanie znaku w ciągu.
- <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, które domyślnie wykonują wyszukiwanie podciągów z uwzględnieniem wielkości liter i w ciągu.
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, które zawierają parametr typu <xref:System.StringComparison>, który umożliwia określenie formy porównania.

Zalecamy wybranie przeciążenia, które nie używa wartości domyślnych, z następujących powodów:

- Niektóre przeciążenia z domyślnymi parametrami (które wyszukują <xref:System.Char> w wystąpieniu ciągu) wykonują porównanie porządkowe, natomiast inne (te, które wyszukują ciąg w wystąpieniu ciągu) są zależne od kultury. Trudno jest pamiętać, która metoda używa tej wartości domyślnej i łatwej do odróżnienia przeciążenia.
- Zamiar kodu, który opiera się na wartościach domyślnych dla wywołań metod, nie jest jasne. W poniższym przykładzie, który opiera się na wartościach domyślnych, trudno jest wiedzieć, czy deweloper rzeczywiście zamierzy liczbę porządkową lub językową, porównując dwa ciągi lub czy różnica wielkości liter między `protocol` i "http" może spowodować, że test równości zwróci `false`.

     [!code-csharp[Conceptual.Strings.BestPractices#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]

Ogólnie rzecz biorąc zalecamy wywołanie metody, która nie polega na wartościach domyślnych, ponieważ sprawia, że zamiar kodu jest niejednoznaczny. Dzięki temu kod staje się bardziej czytelny i łatwiejszy w debugowaniu i obsłudze. Poniższy przykład dotyczy odpowiedzi na pytania dotyczące poprzedniego przykładu. Sprawia, że jest ono jasne, że jest używane porównanie porządkowe oraz że różnice w przypadku są ignorowane.

[!code-csharp[Conceptual.Strings.BestPractices#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
[!code-vb[Conceptual.Strings.BestPractices#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]

## <a name="the-details-of-string-comparison"></a>Szczegóły porównania ciągów

Porównanie ciągów jest sercem wielu operacji związanych z ciągami, szczególnie sortowania i testowania pod kątem równości. Ciągi są sortowane w określonej kolejności: Jeśli "my" pojawia się przed "String" na posortowanej liście ciągów, "my" musi być porównane lub równe "String". Ponadto porównanie niejawnie definiuje równość. Operacja porównywania zwraca wartość zero dla ciągów, które uzna za równe. Dobrą interpretacją jest to, że żaden ciąg nie jest mniejszy od drugiego. Większość znaczących operacji obejmujących ciągi zawierają jedną lub obie te procedury: porównanie z innym ciągiem i wykonywanie dobrze zdefiniowanej operacji sortowania.

> [!NOTE]
> Można pobrać [tabele wagi sortowania](https://www.microsoft.com/download/details.aspx?id=10921), zestaw plików tekstowych, które zawierają informacje o wagach znaków używanych w operacjach sortowania i porównywania dla systemów operacyjnych Windows, a także [domyślną tabelę elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), najnowszą wersję tabeli Sortuj wagi dla systemu Linux i macOS. Określona wersja tabeli posortowanych wag w systemie Linux i macOS zależy od wersji [międzynarodowych składników dla bibliotek Unicode](http://site.icu-project.org/) zainstalowanych w systemie. Aby uzyskać informacje na temat wersji ICU i wersji standardu Unicode, które implementują, zobacz [pobieranie ICU](http://site.icu-project.org/download).

Jednak Ocena dwóch ciągów dla równości lub kolejności sortowania nie daje pojedynczego prawidłowego wyniku; wyniki są zależne od kryteriów używanych do porównywania ciągów. W szczególności porównania ciągów, które są numerami porządkowymi lub które są oparte na konwencjach wielkości liter i sortowania bieżącej kultury lub [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture) (niezależny od kultury opartej na języku angielskim) mogą generować różne wyniki.

Ponadto porównania ciągów przy użyciu różnych wersji programu .NET lub programu .NET w różnych systemach operacyjnych lub wersjach systemu operacyjnego mogą zwracać różne wyniki. Aby uzyskać więcej informacji, zobacz [ciągi i standard Unicode](xref:System.String#Unicode).

### <a name="string-comparisons-that-use-the-current-culture"></a>Porównania ciągów, które używają bieżącej kultury

Jedno kryterium obejmuje stosowanie Konwencji bieżącej kultury podczas porównywania ciągów. Porównania, które są oparte na bieżącej kulturze, wykorzystują bieżącą kulturę lub ustawienia regionalne wątku. Jeśli kultura nie jest ustawiona przez użytkownika, domyślnie jest to ustawienie w oknie **Opcje regionalne** w panelu sterowania. Należy zawsze używać porównań, które są oparte na bieżącej kulturze, gdy dane są istotne dla kultury, a kiedy odzwierciedlają interakcję z użytkownikiem uwzględniającą kulturę.

Jednak porównanie i wielkość liter w programie .NET zmieniają się po zmianie kultury. Dzieje się tak, gdy aplikacja jest wykonywana na komputerze z inną kulturą niż komputer, na którym aplikacja została opracowana, lub gdy wątek wykonawczy zmienia jego kulturę. To zachowanie jest zamierzone, ale pozostaje nieoczywista dla wielu deweloperów. Poniższy przykład ilustruje różnice w kolejności sortowania między kulturą w Stanach Zjednoczonych ("en-US") i szwedzkim ("SV-SE"). Zwróć uwagę, że słowa "Ångström", "Windows" i "Visual Studio" pojawiają się w różnych pozycjach w posortowanych tablicach ciągów.

[!code-csharp[Conceptual.Strings.BestPractices#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
[!code-vb[Conceptual.Strings.BestPractices#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]

Porównania bez uwzględniania wielkości liter, które używają bieżącej kultury, są takie same jak porównania uwzględniające kulturę, z tą różnicą, że ignorowanie wielkości liter jako podyktowanych przez bieżącą kulturę wątku. Takie zachowanie może być również w porządku sortowania.

Porównania, które używają bieżącej semantyki kultury, są domyślne dla następujących metod:

- <xref:System.String.Compare%2A?displayProperty=nameWithType> przeciążeń, które nie zawierają <xref:System.StringComparison> parametru.
- przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType>.
- Domyślną metodą <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> i metodą <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> z parametrem <xref:System.Globalization.CultureInfo> `null`.
- Domyślną metodą <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> i metodą <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> z parametrem <xref:System.Globalization.CultureInfo> `null`.
- <xref:System.String.IndexOf%2A?displayProperty=nameWithType> przeciążenia, które akceptują <xref:System.String> jako parametr wyszukiwania i nie mają parametru <xref:System.StringComparison>.
- <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> przeciążenia, które akceptują <xref:System.String> jako parametr wyszukiwania i nie mają parametru <xref:System.StringComparison>.

W każdym przypadku zalecamy wywołanie przeciążenia, które ma parametr <xref:System.StringComparison>, aby uniemożliwić metodę wywołania metody.

Subtelne i nietak rozdrobne usterki mogą naciągać się, gdy dane nielingwistyczne nie są interpretowane językowo lub gdy dane ciągów z określonej kultury są interpretowane przy użyciu konwencji innej kultury. Przykładem kanonicznym jest problem z tureckim I.

W przypadku niemal wszystkich alfabetów łacińskich, w tym w języku angielskim (Stany Zjednoczone), znak "i" (\u0069) to mała wersja znaku "I" (\u0049). Ta reguła wielkości liter jest szybko zmieniana na wartość domyślną dla programowania osób w takiej kulturze. Alfabet turecki ("TR-TR") zawiera jednak znak "i" (\u0130), czyli "i" w Wielkiej wersji "i". Turecki zawiera również małe litery "i bez kropki", "ı" (\u0131), które zaczynają się od litery "I". To zachowanie występuje również w kulturze azerski ("AZ").

W związku z tym, założenia dotyczące Wielkiej litery "i" lub "lowercasing" nie są prawidłowe we wszystkich kulturach. Jeśli użyjesz domyślnych przeciążeń dla procedur porównywania ciągów, będą one podlegać wariancji między kulturami. Jeśli dane, które mają być porównane, nie są językowe, użycie domyślnych przeciążeń może dawać niepożądane wyniki, ponieważ poniżej podjęto próbę wykonania porównania ciągów "File" i "FILE" bez uwzględniania wielkości liter.

[!code-csharp[Conceptual.Strings.BestPractices#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
[!code-vb[Conceptual.Strings.BestPractices#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]

To porównanie może spowodować znaczne problemy, jeśli kultura jest przypadkowo używana w ustawieniach zabezpieczeń, jak w poniższym przykładzie. Wywołanie metody, takie jak `IsFileURI("file:")` zwraca `true`, jeśli bieżącą kulturą jest angielski (Stany Zjednoczone), ale `false` Jeśli bieżącą kulturą jest turecki. W takim przypadku, w systemach tureckich, ktoś może obejść środki bezpieczeństwa, które blokują dostęp do identyfikatorów URI bez uwzględniania wielkości liter zaczynających się od "FILE:".

[!code-csharp[Conceptual.Strings.BestPractices#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
[!code-vb[Conceptual.Strings.BestPractices#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]

W tym przypadku, ponieważ "plik:" ma być interpretowany jako niezależny od języka, kod powinien być zapisany, jak pokazano w następującym przykładzie:

[!code-csharp[Conceptual.Strings.BestPractices#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
[!code-vb[Conceptual.Strings.BestPractices#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]

### <a name="ordinal-string-operations"></a>Operacje na ciągach porządkowych

Określenie wartości <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> w wywołaniu metody oznacza, że nie jest to porównanie lingwistyczne, w którym funkcje języków naturalnych są ignorowane. Metody, które są wywoływane z tymi <xref:System.StringComparison> wartościami podstawowe decyzje operacji na ciągach w przypadku porównywanych bajtów zamiast wielkości liter lub tabel równoważności, które są sparametryzowane przez kulturę. W większości przypadków takie podejście najlepiej pasuje do zamierzonej interpretacji ciągów podczas szybszego wykonywania kodu i bardziej niezawodnego.

Porównania porządkowe to porównania ciągów, w których każdy bajt każdego ciągu jest porównywany bez interpretacji językowej; na przykład "Windows" nie pasuje do "Windows". Jest to zasadniczo wywołanie funkcji `strcmp` środowiska uruchomieniowego języka C. Użyj tego porównania, gdy kontekst określa, że ciągi powinny być dokładnie dopasowane lub wymagające ostrożnej zgodności z zasadami. Ponadto, porównanie porządkowe jest najszybszą operacją porównywania, ponieważ nie stosuje żadnych reguł lingwistycznych podczas określania wyniku.

Ciągi w programie .NET mogą zawierać osadzone znaki o wartości null. Jedną z najwyraźniejszych różnic między porównaniem porządkowym i kulturowym (w tym porównaniami korzystającymi z niezmiennej kultury) jest obsługa osadzonych znaków null w ciągu. Te znaki są ignorowane w przypadku używania metod <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.Equals%2A?displayProperty=nameWithType> do wykonywania porównań z uwzględnieniem kultury (w tym porównania, które używają niezmiennej kultury). W związku z tym w porównaniach wrażliwych na kulturę ciągi zawierające osadzone znaki null mogą być traktowane jako równe ciągom, które nie.

> [!IMPORTANT]
> Chociaż metody porównywania ciągów zignorują osadzone znaki null, metody wyszukiwania ciągów, takie jak <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>i <xref:System.String.StartsWith%2A?displayProperty=nameWithType> nie.

Poniższy przykład wykonuje porównanie z uwzględnieniem kultury ciągu "AA" z podobnym ciągiem, który zawiera kilka osadzonych znaków o wartości null między "A" i "a" i pokazuje, jak dwa ciągi są uważane za równe:

[!code-csharp[Conceptual.Strings.BestPractices#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]

Jednak ciągi nie są uważane za równe w przypadku używania porównania porządkowego, jak pokazano na poniższym przykładzie:
  
[!code-csharp[Conceptual.Strings.BestPractices#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
[!code-vb[Conceptual.Strings.BestPractices#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]

Porównywanie porządkowe bez uwzględniania wielkości liter jest kolejnym najbardziej rygorystycznym podejściem. Te porównania ignorują większość wielkości liter; na przykład "Windows" dopasowuje "Windows". W przypadku znaków ASCII te zasady są równoważne <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, z tą różnicą, że ignoruje zwykłe wielkości liter ASCII. W związku z tym każdy znak w [A, Z] (\u0041-\u005A) pasuje do odpowiadającego mu znaku w [a, z] (\u0061-\007A). Wielkość liter poza zakresem ASCII używa tabel niezmiennej kultury. W związku z tym następujące porównanie:

[!code-csharp[Conceptual.Strings.BestPractices#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
[!code-vb[Conceptual.Strings.BestPractices#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]

jest odpowiednikiem (ale szybszym niż) tego porównania:

[!code-csharp[Conceptual.Strings.BestPractices#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
[!code-vb[Conceptual.Strings.BestPractices#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]

Te porównania są nadal bardzo szybkie.

> [!NOTE]
> Zachowanie ciągu w systemie plików, kluczach rejestru i wartościach oraz zmienne środowiskowe najlepiej reprezentowane przez <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.

Zarówno <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, jak i <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> używają wartości binarnych bezpośrednio i są najbardziej odpowiednie do dopasowania. Gdy nie masz pewności co do ustawień porównania, użyj jednej z tych dwóch wartości. Jednak ze względu na to, że wykonują porównywanie bajt po bajcie, nie sortuje według języka porządku sortowania (na przykład słownika angielskiego), ale według binarnej kolejności sortowania. Wyniki mogą wyglądać nieparzystie w większości kontekstów, jeśli są wyświetlane użytkownikom.

Semantyka porządkowa jest wartością domyślną dla przeciążeń <xref:System.String.Equals%2A?displayProperty=nameWithType>, które nie zawierają <xref:System.StringComparison> argumentu (w tym operatora równości). W każdym przypadku zalecamy wywołanie przeciążenia z parametrem <xref:System.StringComparison>.

### <a name="string-operations-that-use-the-invariant-culture"></a>operacje na ciągach, które używają niezmiennej kultury

Porównania z kulturą niezmienną używają właściwości <xref:System.Globalization.CultureInfo.CompareInfo%2A> zwróconej przez właściwość statycznej <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Takie zachowanie jest takie samo w przypadku wszystkich systemów; tłumaczy wszelkie znaki spoza zakresu na to, co jest uważane za równoważne znaki niezmienne. Te zasady mogą być przydatne do obsługi jednego zestawu zachowań ciągów między kulturami, ale często zapewniają nieoczekiwane wyniki.

Porównania bez uwzględniania wielkości liter z kulturą niezmienną Użyj statycznej właściwości <xref:System.Globalization.CultureInfo.CompareInfo%2A> zwróconej przez właściwość statycznego <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>, aby uzyskać również informacje dotyczące porównania. Wszelkie różnice wielkości liter między tymi przetłumaczonymi znakami są ignorowane.

Porównania wykorzystujące <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> i <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> działają identycznie na ciągach ASCII. Jednakże <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> podejmuje decyzje lingwistyczne, które mogą nie być odpowiednie dla ciągów, które muszą być interpretowane jako zestaw bajtów. Obiekt `CultureInfo.InvariantCulture.CompareInfo` sprawia, że metoda <xref:System.String.Compare%2A> interpretuje niektóre zestawy znaków jako równoważne. Na przykład następująca równoważność jest prawidłowa dla niezmiennej kultury:

InvariantCulture: a + ̊ = a

Mała litera "a" (\u0061), gdy jest obok znaku ŁĄCZĄCego powyżej znak "+" ̊ "(\u030a), jest interpretowana jako mała litera A z PIERŚCIENIem powyżej znaku" a "(\u00e5). Jak pokazano na poniższym przykładzie, to zachowanie różni się od porównania liczb porządkowych.

[!code-csharp[Conceptual.Strings.BestPractices#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
[!code-vb[Conceptual.Strings.BestPractices#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]

W przypadku interpretacji nazw plików, plików cookie lub innych elementów, w których może się pojawić kombinacja, taka jak "a", porównania porządkowe nadal zapewniają najbardziej przejrzyste i niedopasowane zachowanie.

W przypadku niezmiennej kultura ma bardzo kilka właściwości, które ułatwiają porównywanie. Jest to porównywane w sposób istotny, który uniemożliwia mu zagwarantowanie pełnego równoważności symbolicznej, ale nie jest to możliwe do wyświetlania w żadnej kulturze. Jedną z kilku powodów użycia <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> do porównania jest utrwalanie uporządkowanych danych dla różnych kulturowo identycznych ekranów. Na przykład jeśli plik danych o dużym rozmiarze zawierający listę posortowanych identyfikatorów dla wyświetlania towarzyszy aplikacji, dodanie do tej listy będzie wymagało wstawienia z sortowaniem w stylu niezmiennym.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Wybieranie elementu członkowskiego StringComparison dla wywołania metody

Poniższa tabela zawiera opis mapowania z kontekstu ciągu semantycznego do elementu członkowskiego wyliczenia <xref:System.StringComparison>:

|Dane|Zachowanie|Odpowiadający system. StringComparison<br /><br /> {1&gt;value&lt;1}|
|----------|--------------|-----------------------------------------------------|
|Identyfikatory wewnętrzne z uwzględnieniem wielkości liter.<br /><br /> Identyfikatory z uwzględnieniem wielkości liter w standardach, takich jak XML i HTTP.<br /><br /> Ustawienia związane z zabezpieczeniami z uwzględnieniem wielkości liter.|Identyfikator niebędący językiem, gdzie bajty są dokładnie zgodne.|<xref:System.StringComparison.Ordinal>|
|Identyfikatory wewnętrzne bez uwzględniania wielkości liter.<br /><br /> Identyfikatory bez uwzględniania wielkości liter w standardach, takich jak XML i HTTP.<br /><br /> Ścieżki plików.<br /><br /> Klucze i wartości rejestru.<br /><br /> Zmienne środowiskowe.<br /><br /> Identyfikatory zasobów (na przykład nazwy uchwytów).<br /><br /> Ustawienia związane z zabezpieczeniami bez uwzględniania wielkości liter.|Identyfikator niebędący językiem, gdzie przypadek jest nieistotny; szczególnie dane przechowywane w większości usług systemu Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|
|Pewne utrwalone, językowe dane.<br /><br /> Wyświetlanie danych lingwistycznych, które wymagają stałego porządku sortowania.|Kulturowo niezależny od dane, które nadal są istotne dla języka.|<xref:System.StringComparison.InvariantCulture><br /><br /> lub<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|
|Dane wyświetlane użytkownikowi.<br /><br /> Większość danych wejściowych użytkownika.|Dane wymagające lokalnego języka.|<xref:System.StringComparison.CurrentCulture><br /><br /> lub<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|

## <a name="common-string-comparison-methods-in-net"></a>Typowe metody porównywania ciągów w programie .NET

W poniższych sekcjach opisano metody, które są najczęściej używane do porównywania ciągów.

### <a name="stringcompare"></a>Funkcja String.Compare

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Jako że operacja najważniejsza do interpretacji ciągów, wszystkie wystąpienia tych wywołań metod powinny być badane w celu określenia, czy ciągi powinny być interpretowane zgodnie z bieżącą kulturą, czy też odwoływać się od kultury (symbolicznie). Zwykle jest to ostatni i zamiast tego należy użyć porównania <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Klasa <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>, która jest zwracana przez właściwość <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType>, zawiera również metodę <xref:System.Globalization.CompareInfo.Compare%2A>, która zapewnia dużą liczbę pasujących opcji (numer porządkowy, ignorowanie białego znaku, ignorowanie typu kana itd.) za pomocą wyliczenia flag <xref:System.Globalization.CompareOptions>.

### <a name="stringcompareto"></a>Funkcja String.CompareTo

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Ta metoda obecnie nie oferuje przeciążenia, które określa typ <xref:System.StringComparison>. Jest to zazwyczaj możliwe, aby przekonwertować tę metodę na <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formularz zalecany.

Typy implementujące interfejsy <xref:System.IComparable> i <xref:System.IComparable%601> implementują tę metodę. Ponieważ nie oferuje on opcji parametru <xref:System.StringComparison>, implementacja typów często zezwala użytkownikowi na określenie <xref:System.StringComparer> w konstruktorze. W poniższym przykładzie zdefiniowano klasę `FileName`, której Konstruktor klasy zawiera parametr <xref:System.StringComparer>. Ten obiekt <xref:System.StringComparer> jest następnie używany w metodzie `FileName.CompareTo`.

[!code-csharp[Conceptual.Strings.BestPractices#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
[!code-vb[Conceptual.Strings.BestPractices#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]

### <a name="stringequals"></a>Funkcja String.Equals

Domyślna interpretacja: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Klasa <xref:System.String> umożliwia przetestowanie pod kątem równości przez wywołanie statycznego lub wystąpienia przeciążenia metody <xref:System.String.Equals%2A> lub przy użyciu operatora statycznej równości. Przeciążenia i operator domyślnie używają porównania porządkowego. Jednak nadal zalecamy wywołanie przeciążenia, które jawnie określa typ <xref:System.StringComparison>, nawet jeśli chcesz wykonać porównanie porządkowe; Dzięki temu można łatwiej wyszukiwać kod dla określonej interpretacji ciągów.

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper i String.ToLower

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Należy zachować ostrożność w przypadku korzystania z tych metod, ponieważ wymuszanie ciągu do wielkich lub małych liter jest często używane jako mała normalizacja do porównywania ciągów, niezależnie od wielkości liter. Jeśli tak, rozważ użycie porównania bez uwzględniania wielkości liter.

Dostępne są również metody <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> i <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType>. <xref:System.String.ToUpperInvariant%2A> jest standardowym sposobem normalizacji wielkości liter. Porównania wykonywane przy użyciu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> są zachowaniem składu dwóch wywołań: wywoływanie <xref:System.String.ToUpperInvariant%2A> na obu argumentach ciągów i wykonywanie porównania przy użyciu <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Przeciążenia są również dostępne do konwersji na wielkie i małe litery w określonej kulturze, przekazując obiekt <xref:System.Globalization.CultureInfo>, który reprezentuje tę kulturę do metody.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper i Char.ToLower

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Metody te działają podobnie do <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> metodami opisanymi w poprzedniej sekcji.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith i String.EndsWith

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Domyślnie obie te metody wykonują porównanie z uwzględnieniem kultury.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf i String.LastIndexOf

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Brak spójności w sposobie wykonywania porównań przez domyślne przeciążenia tych metod. Wszystkie metody <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, które zawierają parametr <xref:System.Char> wykonują porównanie porządkowe, ale domyślne metody <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, które zawierają parametr <xref:System.String>, wykonują porównanie z uwzględnieniem kultury.

Jeśli wywołasz metodę <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> i przekażemy ciąg do zlokalizowania w bieżącym wystąpieniu, zalecamy wywołanie przeciążenia, które jawnie określa typ <xref:System.StringComparison>. Przeciążenia, które zawierają argument <xref:System.Char>, nie pozwalają na określenie typu <xref:System.StringComparison>.

## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, które pośrednio wykonują Porównywanie ciągów

Niektóre metody niebędące ciągami, które mają porównanie ciągów jako operacji centralnej, używają typu <xref:System.StringComparer>. Klasa <xref:System.StringComparer> obejmuje sześć właściwości statycznych, które zwracają <xref:System.StringComparer> wystąpienia, których <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody wykonują następujące typy porównań ciągów:

- Porównania ciągów zależnych od kultury przy użyciu bieżącej kultury. Ten obiekt <xref:System.StringComparer> jest zwracany przez właściwość <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType>.
- Porównania bez uwzględniania wielkości liter przy użyciu bieżącej kultury. Ten obiekt <xref:System.StringComparer> jest zwracany przez właściwość <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType>.
- Porównania niewrażliwe na kulturę przy użyciu reguł porównania wyrazów niezmiennej kultury. Ten obiekt <xref:System.StringComparer> jest zwracany przez właściwość <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType>.
- Porównania bez uwzględniania wielkości liter i nieuwzględniania kultur przy użyciu reguł porównania wyrazów niezmiennej kultury. Ten obiekt <xref:System.StringComparer> jest zwracany przez właściwość <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType>.
- Porównanie porządkowe. Ten obiekt <xref:System.StringComparer> jest zwracany przez właściwość <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType>.
- Porównanie porządkowe bez uwzględniania wielkości liter. Ten obiekt <xref:System.StringComparer> jest zwracany przez właściwość <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType>.

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort i Array.BinarySearch

Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

W przypadku przechowywania danych w kolekcji lub odczytywania utrwalonych danych z pliku lub bazy danych do kolekcji, przełączenie bieżącej kultury może spowodować unieważnienie niezmiennych w kolekcji. Metoda <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> zakłada, że elementy w tablicy, które mają być przeszukiwane, są już posortowane. Aby posortować dowolny element ciągu w tablicy, Metoda <xref:System.Array.Sort%2A?displayProperty=nameWithType> wywołuje metodę <xref:System.String.Compare%2A?displayProperty=nameWithType>, aby zamówić poszczególne elementy. Użycie funkcji porównującej uwzględniającej kulturę może być niebezpieczne, jeśli kultura zmieni się między posortowaną tablicą a jego zawartością jest przeszukiwana. Na przykład, w poniższym kodzie, magazyn i pobieranie działają na porównującej, który jest dostarczany niejawnie przez właściwość `Thread.CurrentThread.CurrentCulture`. Jeśli kultura może zmienić między wywołaniami `StoreNames` i `DoesNameExist`, a zwłaszcza jeśli zawartość tablicy jest utrwalana między dwoma wywołaniami metod, wyszukiwanie binarne może zakończyć się niepowodzeniem.

[!code-csharp[Conceptual.Strings.BestPractices#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]

W poniższym przykładzie zostanie wyświetlona zalecana odmiana, która używa tej samej wartości porządkowej (bez uwzględniania kultury) zarówno do sortowania, jak i do przeszukiwania tablicy. Kod zmiany jest odzwierciedlony w wierszach z etykietą `Line A` i `Line B` w dwóch przykładach.

[!code-csharp[Conceptual.Strings.BestPractices#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
[!code-vb[Conceptual.Strings.BestPractices#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]

Jeśli te dane są utrwalane i przenoszone między kulturami, a sortowanie jest używane do prezentowania tych danych użytkownikowi, można rozważyć użycie <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, który działa w sposób językowy w celu uzyskania lepszych danych wyjściowych użytkownika, ale nie ma wpływ na zmiany w kulturze. Poniższy przykład modyfikuje dwa poprzednie przykłady, aby użyć niezmiennej kultury do sortowania i przeszukiwania tablicy.

[!code-csharp[Conceptual.Strings.BestPractices#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
[!code-vb[Conceptual.Strings.BestPractices#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]

### <a name="collections-example-hashtable-constructor"></a>Przykład kolekcji: Konstruktor Hashtable

Ciągi mieszania zawierają drugi przykład operacji, na które ma wpływ, w jaki sposób ciągi są porównywane.

Poniższy przykład tworzy wystąpienie obiektu <xref:System.Collections.Hashtable> przez przekazanie go do <xref:System.StringComparer> obiektu, który jest zwracany przez właściwość <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType>. Ponieważ Klasa <xref:System.StringComparer>, która pochodzi od <xref:System.StringComparer> implementuje interfejs <xref:System.Collections.IEqualityComparer>, jego Metoda <xref:System.Collections.IEqualityComparer.GetHashCode%2A> służy do obliczania kodu skrótu ciągów w tabeli skrótów.

[!code-csharp[Conceptual.Strings.BestPractices#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
[!code-vb[Conceptual.Strings.BestPractices#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]

## <a name="displaying-and-persisting-formatted-data"></a>Wyświetlanie i utrwalanie sformatowanych danych

W przypadku wyświetlania danych niebędących ciągami, takich jak liczby i daty i godziny, sformatuj je przy użyciu ustawień kultury użytkownika. Domyślnie następujące wszystkie używają bieżącej kultury wątku w operacjach formatowania:

- Ciągi interpolowane obsługiwane przez kompilatory [C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) .
- Operacje łączenia ciągów wykorzystujące operatory łączenia [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) lub [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) lub bezpośrednio wywołujące metodę <xref:System.String.Concat%2A?displayProperty=nameWithType>.
- Metoda <xref:System.String.Format%2A?displayProperty=nameWithType>.
- Metody `ToString` typów liczbowych i typów dat i godzin.

Aby jawnie określić, że ciąg powinien być sformatowany przy użyciu konwencji określonej kultury lub [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture), można wykonać następujące czynności:

- Korzystając z metod <xref:System.String.Format%2A?displayProperty=nameWithType> i `ToString`, wywołaj Przeciążenie, które ma `provider` parametr, taki jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> lub <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>, i przekaż mu Właściwość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, <xref:System.Globalization.CultureInfo> wystąpienie, które reprezentuje pożądaną kulturę, lub właściwość <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.

- W przypadku łączenia ciągów nie Zezwalaj kompilatorowi na wykonywanie jakichkolwiek niejawnych konwersji. Zamiast tego należy wykonać jawną konwersję, wywołując Przeciążenie `ToString`, które ma parametr `provider`. Na przykład kompilator niejawnie używa bieżącej kultury podczas konwertowania wartości <xref:System.Double> na ciąg w poniższym C# kodzie:

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  Zamiast tego można jawnie określić kulturę, której konwencje formatowania są używane w konwersji, wywołując metodę <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType>, jak w poniższym C# kodzie:

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- W przypadku interpolacji ciągów zamiast przypisywania ciągu interpolowanego do wystąpienia <xref:System.String>, należy przypisać go do <xref:System.FormattableString>. Następnie można wywołać metodę <xref:System.FormattableString.ToString?displayProperty=nameWithType> utworzyć ciąg wynikowy, który odzwierciedla konwencje bieżącej kultury, lub wywołać metodę <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>, aby utworzyć ciąg wynikowy, który odzwierciedla konwencje określonej kultury. Możesz również przekazać ciąg formatu do statycznej metody <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType>, aby utworzyć ciąg wynikowy, który odzwierciedla konwencje niezmiennej kultury. To podejście pokazano w poniższym przykładzie. (Dane wyjściowe z przykładu odzwierciedlają bieżącą kulturę en-US).

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

Dane niebędące ciągami mogą być utrwalane jako dane binarne lub dane sformatowane. Jeśli zdecydujesz się zapisać ją jako sformatowane dane, należy wywołać Przeciążenie metody formatowania, które zawiera parametr `provider` i przekazać go do właściwości <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Kultura niezmienna zapewnia spójny format sformatowanych danych, które są niezależne od kultury i maszyny. W przeciwieństwie do utrwalania danych, które są formatowane przy użyciu kultur innych niż kultura niezmienna, ma wiele ograniczeń:

- Dane mogą być bezużyteczne, jeśli są pobierane w systemie, który ma inną kulturę, lub jeśli użytkownik bieżącego systemu zmienia bieżącą kulturę i próbuje pobrać dane.
- Właściwości kultury na określonym komputerze mogą różnić się od wartości standardowych. W dowolnym momencie użytkownik może dostosować ustawienia wyświetlania z uwzględnieniem kultury. W związku z tym sformatowane dane zapisane w systemie mogą nie zostać odczytane, gdy użytkownik dostosowuje ustawienia kulturowe. Przenośność sformatowanych danych między komputerami może być jeszcze bardziej ograniczona.
- Międzynarodowe, regionalne lub krajowe standardy, które regulują formatowanie liczb lub dat i godzin zmiany czasu, i te zmiany są włączane do aktualizacji systemu operacyjnego Windows. W przypadku zmiany Konwencji formatowania dane sformatowane przy użyciu poprzednich Konwencji mogą stać się nieczytelne.

Poniższy przykład ilustruje ograniczoną przenośność, która wynika z używania formatowania z uwzględnieniem kultury do utrwalania danych. Przykład zapisuje tablicę wartości daty i godziny do pliku. Są one sformatowane przy użyciu Konwencji kultury angielskiej (Stany Zjednoczone). Gdy aplikacja zmieni bieżącą kulturę wątku na francuski (Szwajcaria), próbuje odczytać zapisane wartości przy użyciu Konwencji formatowania bieżącej kultury. Próba odczytania dwóch elementów danych zgłasza wyjątek <xref:System.FormatException>, a tablica dat zawiera teraz dwa niepoprawne elementy, które są równe <xref:System.DateTime.MinValue>.

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

Jeśli jednak zamienisz Właściwość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> na <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> w wywołaniach <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, utrwalone dane daty i godziny zostaną pomyślnie przywrócone, ponieważ następujące dane wyjściowe pokazują:

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```

## <a name="see-also"></a>Zobacz także

- [Manipulowanie ciągami](manipulating-strings.md)
