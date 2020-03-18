---
title: Najważniejsze wskazówki dotyczące używania ciągów w dołów w dołce.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711483"
---
# <a name="best-practices-for-using-strings-in-net"></a>Najważniejsze wskazówki dotyczące używania ciągów w dołów w dołce.

.NET zapewnia szeroką obsługę tworzenia zlokalizowanych i zglobalizowanych aplikacji i ułatwia stosowanie konwencji bieżącej kultury lub określonej kultury podczas wykonywania typowych operacji, takich jak sortowanie i wyświetlanie ciągów. Ale sortowanie lub porównywanie ciągów nie zawsze jest operacją uwzględniającą kulturę. Na przykład ciągi, które są używane wewnętrznie przez aplikację zazwyczaj powinny być obsługiwane identycznie we wszystkich kulturach. Gdy niezależne kulturowo dane ciągów, takie jak tagi XML, tagi HTML, nazwy użytkowników, ścieżki plików i nazwy obiektów systemowych, są interpretowane tak, jakby były zależne od kultury, kod aplikacji może podlegać subtelnym błędom, niskiej wydajności, a w niektórych przypadkach kwestii bezpieczeństwa.

W tym temacie przeanalizowano metody sortowania, porównywania i obudowy ciągów w platformie .NET, przedstawiono zalecenia dotyczące wybierania odpowiedniej metody obsługi ciągów i zawiera dodatkowe informacje na temat metod obsługi ciągów. Sprawdza również, w jaki sposób sformatowane dane, takie jak dane liczbowe oraz dane daty i godziny, są obsługiwane do wyświetlania i przechowywania.

## <a name="recommendations-for-string-usage"></a>Zalecenia dotyczące użycia ciągów

Podczas tworzenia z .NET, postępuj zgodnie z tymi prostymi zaleceniami podczas korzystania z ciągów:

- Użyj przeciążenia, które jawnie określają reguły porównywania ciągów dla operacji ciągu. Zazwyczaj wiąże się to wywołanie przeciążenia metody, który ma parametr typu <xref:System.StringComparison>.
- Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> lub dla porównań jako bezpieczne domyślne dla mieszania ciągów kultury agnostyków.
- Użyj porównań <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> z lub dla lepszej wydajności.
- Użyj operacji ciągu, <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> które są oparte na podczas wyświetlania danych wyjściowych dla użytkownika.
- Użyj wartości niejęzykowych <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> zamiast operacji <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ciągu na podstawie, gdy porównanie jest nieistotne językowo (na przykład symboliczne).
- Użyj <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> metody zamiast <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody podczas normalizacji ciągów do porównania.
- Użyj przeciążenia <xref:System.String.Equals%2A?displayProperty=nameWithType> metody, aby sprawdzić, czy dwa ciągi są równe.
- Użyj <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody sortowania ciągów, a nie do sprawdzania równości.
- Formatowanie zależne od kultury służy do wyświetlania danych nieciągowych, takich jak liczby i daty, w interfejsie użytkownika. Użyj formatowania z [kultury niezmiennej,](xref:System.Globalization.CultureInfo.InvariantCulture) aby utrwalić dane nieciągwu w postaci ciągu.

Należy unikać następujących praktyk podczas używania ciągów:

- Nie należy używać przeciążeń, które nie jawnie lub niejawnie określają reguły porównywania ciągów dla operacji ciągu.
- Nie należy używać operacji <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ciągu na podstawie w większości przypadków. Jednym z niewielu wyjątków jest, gdy są utrzymujące się językowo znaczące, ale kulturowo agnostyk danych.
- Nie należy używać <xref:System.String.Compare%2A?displayProperty=nameWithType> przeciążenia <xref:System.String.CompareTo%2A> lub metody i test dla wartości zwracanej zero, aby określić, czy dwa ciągi są równe.
- Nie należy używać formatowania zależnego od kultury do utrwalania danych liczbowych lub danych daty i godziny w postaci ciągu.

## <a name="specifying-string-comparisons-explicitly"></a>Jawne określanie porównań ciągów

Większość metod manipulowania ciągami w .NET jest przeciążona. Zazwyczaj jedno lub więcej przeciążeń akceptuje ustawienia domyślne, podczas gdy inne akceptują żadnych wartości domyślnych i zamiast tego definiują dokładny sposób porównywania lub manipulowania ciągami. Większość metod, które nie opierają się na wartości <xref:System.StringComparison>domyślne obejmują parametr typu , który jest wyliczenie, które jawnie określa reguły porównywania ciągów według kultury i przypadku. W poniższej <xref:System.StringComparison> tabeli opisano elementy członkowskie wyliczenia.

|Element członkowski StringComparison|Opis|
|-----------------------------|-----------------|
|<xref:System.StringComparison.CurrentCulture>|Wykonuje porównanie z uwzględnieniem wielkości liter przy użyciu bieżącej kultury.|
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu bieżącej kultury.|
|<xref:System.StringComparison.InvariantCulture>|Wykonuje porównanie z uwzględnieniem wielkości liter przy użyciu kultury niezmiennej.|
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu kultury niezmiennej.|
|<xref:System.StringComparison.Ordinal>|Wykonuje porównanie z rzędu.|
|<xref:System.StringComparison.OrdinalIgnoreCase>|Wykonuje porównanie pisane z uwzględnieniem wielkości liter.|

Na przykład <xref:System.String.IndexOf%2A> metoda, która zwraca indeks podciągu <xref:System.String> w obiekcie, który pasuje do znaku lub ciągu, ma dziewięć przeciążeń:

- <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>i <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, które domyślnie wykonują wyszukiwanie znaków w ciągu szeregowym (z uwzględnieniem wielkości liter i niewrażliwena na kulturę).
- <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, które domyślnie wykonują wyszukiwanie podciągów w ciągu z uwzględnieniem wielkości liter i kultury.
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, które zawierają <xref:System.StringComparison> parametr typu, który umożliwia podanie formy porównania.

Zaleca się wybranie przeciążenia, które nie używa wartości domyślnych, z następujących powodów:

- Niektóre przeciążenia z parametrami domyślnymi <xref:System.Char> (te, które wyszukują w wystąpieniu ciągu) wykonać porównanie liczby głosów, podczas gdy inne (te, które wyszukują ciąg w wystąpieniu ciągu) są zależne od kultury. Trudno jest zapamiętać, która metoda używa wartości domyślnej i łatwo pomylić przeciążenia.
- Intencja kodu, który opiera się na wartości ach domyślnych dla wywołań metody nie jest jasne. W poniższym przykładzie, który opiera się na wartości domyślne, trudno jest wiedzieć, czy deweloper rzeczywiście przeznaczone do ordinal `protocol` lub lingwistyczne porównanie dwóch ciągów lub czy różnica przypadków między i "http" może spowodować test równości do zwrócenia `false`.

     [!code-csharp[Conceptual.Strings.BestPractices#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]

Ogólnie rzecz biorąc zaleca się wywołanie metody, która nie opiera się na wartości domyślne, ponieważ sprawia, że intencji kodu jednoznaczne. To z kolei sprawia, że kod bardziej czytelny i łatwiejsze do debugowania i konserwacji. Poniższy przykład odnosi się do pytań dotyczących poprzedniego przykładu. Wyjaśnia ona, że stosuje się porównanie liczba głosów i że różnice w przypadku są ignorowane.

[!code-csharp[Conceptual.Strings.BestPractices#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
[!code-vb[Conceptual.Strings.BestPractices#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]

## <a name="the-details-of-string-comparison"></a>Szczegóły porównania ciągów

Porównanie ciągów jest sercem wielu operacji związanych z ciągami, szczególnie sortowania i testowania równości. Ciągi sortują w określonej kolejności: Jeśli "mój" pojawia się przed "ciągiem" na posortowanej liście ciągów, "mój" musi porównywać mniej lub równe "ciągowi". Ponadto porównanie niejawnie definiuje równość. Operacja porównania zwraca zero dla ciągów, które uzna za równe. Dobrą interpretacją jest to, że żaden ciąg nie jest mniejszy niż drugi. Najbardziej znaczące operacje obejmujące ciągi obejmują jedną lub obie z tych procedur: porównanie z innym ciągiem i wykonywanie dobrze zdefiniowanej operacji sortowania.

> [!NOTE]
> Możesz pobrać [tabele wagi sortowania,](https://www.microsoft.com/download/details.aspx?id=10921)zestaw plików tekstowych, które zawierają informacje o wagach znaków używanych w operacjach sortowania i porównywania dla systemów operacyjnych Windows, oraz [domyślną tabelę elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), najnowszą wersję tabeli wagi sortowania dla systemów Linux i macOS. Określona wersja tabeli wagi sortowania w systemach Linux i macOS zależy od wersji bibliotek [International Components for Unicode](http://site.icu-project.org/) zainstalowanych w systemie. Aby uzyskać informacje na temat wersji ICU i wersji Unicode, które implementują, zobacz [Pobieranie ICU](http://site.icu-project.org/download).

Jednak oceny dwóch ciągów dla równości lub kolejności sortowania nie daje jeden, poprawny wynik; wynik zależy od kryteriów używanych do porównywania ciągów. W szczególności porównania ciągów, które są porządkowe lub które są oparte na konwencjach wielkości i sortowania bieżącej kultury lub [kultury niezmiennej](xref:System.Globalization.CultureInfo.InvariantCulture) (kultury lokalizalnej opartej na języku angielskim) mogą dawać różne wyniki.

Ponadto porównania ciągów przy użyciu różnych wersji programu .NET lub przy użyciu .NET w różnych systemach operacyjnych lub wersjach systemu operacyjnego mogą zwracać różne wyniki. Aby uzyskać więcej informacji, zobacz [Ciągi znaków i Standard Unicode](xref:System.String#Unicode).

### <a name="string-comparisons-that-use-the-current-culture"></a>Porównania ciągów, które używają bieżącej kultury

Jedno kryterium polega na użyciu konwencji bieżącej kultury podczas porównywania ciągów. Porównania, które są oparte na bieżącej kultury użyć bieżącej kultury wątku lub ustawień regionalnych. Jeśli kultura nie jest ustawiona przez użytkownika, domyślnie ustawienie w oknie **Opcje regionalne** w Panelu sterowania. Należy zawsze używać porównań, które są oparte na bieżącej kultury, gdy dane są istotne językowo i gdy odzwierciedla interakcji użytkownika zależne od kultury.

Jednak porównanie i zachowanie wielkości liter w .NET zmienia się po zmianie kultury. Dzieje się tak, gdy aplikacja jest wykonywana na komputerze, który ma inną kulturę niż komputer, na którym aplikacja została opracowana lub gdy wątek wykonujący zmienia swoją kulturę. To zachowanie jest zamierzone, ale pozostaje nieoczywiste dla wielu deweloperów. Poniższy przykład ilustruje różnice w kolejności sortowania między kulturami angielskiego ("en-US") i szwedzkimi ("sv-SE"). Należy zauważyć, że wyrazy "ångström", "Windows" i "Visual Studio" są wyświetlane w różnych pozycjach w posortowanych tablicach ciągów.

[!code-csharp[Conceptual.Strings.BestPractices#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
[!code-vb[Conceptual.Strings.BestPractices#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]

Porównania bez uwzględniania wielkości liter, które używają bieżącej kultury są takie same jak porównania zależne od kultury, z tą różnicą, że ignorują wielkość liter podyktowaną bieżącą kulturą wątku. To zachowanie może objawiać się również w zamówieniach sortowania.

Porównania, które używają bieżącej semantyki kultury są domyślne dla następujących metod:

- <xref:System.String.Compare%2A?displayProperty=nameWithType>przeciążenia, które <xref:System.StringComparison> nie zawierają parametru.
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Przeciążenia.
- Metoda <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> domyślna i <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda `null` <xref:System.Globalization.CultureInfo> z parametrem.
- Metoda <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> domyślna i <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda `null` <xref:System.Globalization.CultureInfo> z parametrem.
- <xref:System.String.IndexOf%2A?displayProperty=nameWithType>przeciążenia, <xref:System.String> które akceptują jako parametr wyszukiwania <xref:System.StringComparison> i które nie mają parametru.
- <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>przeciążenia, <xref:System.String> które akceptują jako parametr wyszukiwania <xref:System.StringComparison> i które nie mają parametru.

W każdym przypadku zaleca się wywołanie przeciążenia, który ma <xref:System.StringComparison> parametr, aby intencji wywołania metody jasne.

Subtelne i nie tak subtelne błędy mogą pojawić się, gdy dane ciągów niejęzykowych jest interpretowany językowo lub gdy dane ciągów z określonej kultury jest interpretowany przy użyciu konwencji innej kultury. Przykładem kanonicznym jest problem turecko-i.

W przypadku prawie wszystkich alfabetów łacińskich, w tym angielskiego amerykańskiego, znak "i" (\u0069) jest wersją małych liter znaku "I" (\u0049). Ta reguła obudowy szybko staje się domyślną dla kogoś programowania w takiej kulturze. Jednak alfabet turecki ("tr-TR") zawiera znak "I z kropką" "İ" (\u0130), który jest kapitalistyą "i". Turecki zawiera również małe litery "i bez kropki" znak, "ı" (\u0131), który wykorzystuje do "I". To zachowanie występuje również w kulturze Azerbejdżańskiej ("az").

Dlatego założenia dotyczące kapitalizacji "i" lub obniżenia "i" nie są ważne wśród wszystkich kultur. Jeśli używasz domyślne przeciążenia dla procedur porównywania ciągów, będą one podlegać wariancji między kulturami. Jeśli dane, które mają być porównywane jest niejęzykowych, przy użyciu przeciążenia domyślne może spowodować niepożądane wyniki, jak pokazano następującą próbę wykonania porównania bez uwzględniania wielkości liter ciągów "plik" i "FILE" i lustruje.

[!code-csharp[Conceptual.Strings.BestPractices#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
[!code-vb[Conceptual.Strings.BestPractices#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]

To porównanie może spowodować poważne problemy, jeśli kultura jest przypadkowo używany w ustawieniach poufnych zabezpieczeń, jak w poniższym przykładzie. Wywołanie metody, `IsFileURI("file:")` `true` takie jak zwraca, jeśli bieżąca `false` kultura jest angielski amerykański, ale jeśli bieżąca kultura jest turecki. W związku z tym w systemach tureckich ktoś może obejść środki bezpieczeństwa, które blokują dostęp do identyfikatorów URI bez uwzględniania wielkości liter, które zaczynają się od "FILE:".

[!code-csharp[Conceptual.Strings.BestPractices#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
[!code-vb[Conceptual.Strings.BestPractices#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]

W takim przypadku, ponieważ "plik:" ma być interpretowany jako niejęzykowy, nieczuły na kulturę identyfikator, zamiast tego kod powinien być napisany w następujący sposób:

[!code-csharp[Conceptual.Strings.BestPractices#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
[!code-vb[Conceptual.Strings.BestPractices#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]

### <a name="ordinal-string-operations"></a>Operacje ciągów ordinalnych

Określenie <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartość w wywołaniu metody oznacza porównanie nielingwistyczne, w którym funkcje języków naturalnych są ignorowane. Metody, które są wywoływane z tych <xref:System.StringComparison> wartości podstawowych decyzji dotyczących operacji ciągu na proste porównania bajtów zamiast tabel wielkości liter lub równoważności, które są parametryzowane przez kulturę. W większości przypadków takie podejście najlepiej pasuje do zamierzonej interpretacji ciągów, jednocześnie czyniąc kod szybszym i bardziej niezawodnym.

Porównania ordynacyjne to porównania ciągów, w których każdy bajt każdego ciągu jest porównywany bez interpretacji językowej; na przykład "windows" nie pasuje do "Windows". Jest to zasadniczo wywołanie funkcji `strcmp` wykonywania C. Użyj tego porównania, gdy kontekst dyktuje, że ciągi powinny być dokładnie dopasowane lub wymaga konserwatywnych zasad dopasowania. Ponadto porównanie liczba głosów jest najszybszą operacją porównywania, ponieważ nie stosuje żadnych reguł językowych podczas określania wyniku.

Ciągi w .NET mogą zawierać osadzone znaki null. Jedną z najczystszych różnic między porównaniem liczby i kultury (w tym porównania, które używają kultury niezmiennej) dotyczy obsługi osadzonych znaków null w ciągu. Znaki te są ignorowane podczas <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.Equals%2A?displayProperty=nameWithType> używania i metody do wykonywania porównań zależnych od kultury (w tym porównań, które używają kultury niezmienne). W rezultacie w porównaniach zależnych od kultury ciągi zawierające osadzone znaki null można uznać za równe ciągom, które tego nie robią.

> [!IMPORTANT]
> Chociaż metody porównywania ciągów pomijają osadzone <xref:System.String.Contains%2A?displayProperty=nameWithType>znaki <xref:System.String.EndsWith%2A?displayProperty=nameWithType> <xref:System.String.IndexOf%2A?displayProperty=nameWithType>null, metody wyszukiwania ciągów, takie jak , , , <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>i <xref:System.String.StartsWith%2A?displayProperty=nameWithType> nie.

Poniższy przykład wykonuje porównanie zależne od kultury ciągu "Aa" z podobnym ciągiem, który zawiera kilka osadzonych znaków null między "A" i "a" i pokazuje, jak dwa ciągi są uważane za równe:

[!code-csharp[Conceptual.Strings.BestPractices#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]

Jednak ciągi nie są uważane za równe podczas korzystania z porównania liczba, jak pokazano w poniższym przykładzie:
  
[!code-csharp[Conceptual.Strings.BestPractices#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
[!code-vb[Conceptual.Strings.BestPractices#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]

Niewrażliwe na wielkość liter porównania liczba głosów to kolejne najbardziej konserwatywne podejście. Porównania te ignorują większość obudowy; na przykład "windows" pasuje do "Windows". W przypadku znaków ASCII, ta <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>zasada jest równoważna , z tą różnicą, że ignoruje zwykłą obudowę ASCII. W związku z tym dowolny znak w [A, Z] (\u0041-\u005A) pasuje do odpowiedniego znaku w [a,z] (\u0061-\007A). Obudowa poza zakresem ASCII używa tabel kultury niezmiennej. W związku z tym następujące porównanie:

[!code-csharp[Conceptual.Strings.BestPractices#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
[!code-vb[Conceptual.Strings.BestPractices#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]

jest odpowiednikiem (ale szybciej niż) to porównanie:

[!code-csharp[Conceptual.Strings.BestPractices#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
[!code-vb[Conceptual.Strings.BestPractices#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]

Te porównania są nadal bardzo szybkie.

> [!NOTE]
> Zachowanie ciągów systemu plików, kluczy rejestru i wartości oraz zmiennych środowiskowych jest najlepiej reprezentowane przez . <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>

Oba <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> i używać wartości binarnych bezpośrednio i najlepiej nadają się do dopasowania. Jeśli nie masz pewności co do ustawień porównania, użyj jednej z tych dwóch wartości. Jednak ponieważ wykonują porównanie bajt po bajcie, nie sortują według kolejności sortowania językowego (jak słownik angielski), ale według binarnej kolejności sortowania. Wyniki mogą wyglądać nieparzyste w większości kontekstów, jeśli są wyświetlane użytkownikom.

Semantyka liczba mięsiniczna jest domyślną wartością dla <xref:System.String.Equals%2A?displayProperty=nameWithType> przeciążeń, które nie zawierają argumentu <xref:System.StringComparison> (w tym operatora równości). W każdym przypadku zaleca się wywołanie przeciążenia, który ma <xref:System.StringComparison> parametr.

### <a name="string-operations-that-use-the-invariant-culture"></a>operacje ciągu, które używają kultury niezmiennej

Porównania z kultury niezmiennej <xref:System.Globalization.CultureInfo.CompareInfo%2A> użyć właściwości zwrócone przez właściwość static. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> To zachowanie jest takie samo we wszystkich systemach; przekłada żadnych znaków poza jego zakres do tego, co uważa za równoważne niezmienne znaki. Ta zasada może być przydatne do obsługi jednego zestawu zachowanie ciągów w różnych kulturach, ale często zapewnia nieoczekiwane wyniki.

Porównania bez uwzględniania wielkości liter z kulturą niezmienną używają właściwości statycznej <xref:System.Globalization.CultureInfo.CompareInfo%2A> zwracanej przez właściwość statyczną <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> również w celu uzyskania informacji o porównaniach. Wszelkie różnice przypadków między tymi przetłumaczonymi znakami są ignorowane.

Porównania, które <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> używają i działają identycznie na ciągi ASCII. Jednak <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> sprawia, że decyzje językowe, które mogą nie być odpowiednie dla ciągów, które muszą być interpretowane jako zestaw bajtów. Obiekt `CultureInfo.InvariantCulture.CompareInfo` sprawia, <xref:System.String.Compare%2A> że metoda interpretuje niektóre zestawy znaków jako równoważne. Na przykład następująca równoważność jest prawidłowa w ramach kultury niezmiennej:

NiezmiennaKultura: a + = å

MAŁA LITERA LATIN Znak "a" (\u0061), gdy znajduje się obok PIERŚCIENIA ŁĄCZĄCEGO POWYŻEJ znaku "+ " "" (\u030a), jest interpretowana jako MAŁA LITERA A Z PIERŚCIENIEM POWYŻEJ ZNAKU "å" (\u00e5). Jak pokazano w poniższym przykładzie, to zachowanie różni się od porównania liczba mięsień.

[!code-csharp[Conceptual.Strings.BestPractices#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
[!code-vb[Conceptual.Strings.BestPractices#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]

Podczas interpretowania nazw plików, plików cookie lub czegokolwiek innego, w którym może pojawić się kombinacja, taka jak "å", porównania liczba głosów nadal oferują najbardziej przejrzyste i dopasowane zachowanie.

W sumie kultury niezmiennej ma bardzo niewiele właściwości, które sprawiają, że przydatne do porównania. Dokonuje porównania w sposób istotny językowo, co uniemożliwia mu zagwarantowanie pełnej równoważności symbolicznej, ale nie jest wyborem do wyświetlania w żadnej kulturze. Jednym z niewielu <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> powodów, dla których warto użyć do porównania, jest utrzymanie uporządkowanych danych dla wyświetlania między kulturowo identycznymi. Na przykład jeśli duży plik danych, który zawiera listę posortowanych identyfikatorów do wyświetlania towarzyszy aplikacji, dodanie do tej listy wymagałoby wstawienia z sortowaniem w stylu niezmiennym.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Wybór elementu członkowskiego StringComparison dla wywołania metody

W poniższej tabeli przedstawiono mapowanie z kontekstu <xref:System.StringComparison> ciągu semantycznego do elementu członkowskiego wyliczenia:

|Dane|Zachowanie|Odpowiednie porównanie system.stringi<br /><br /> wartość|
|----------|--------------|-----------------------------------------------------|
|Identyfikatory wewnętrzne uwzględniające wielkość liter.<br /><br /> Identyfikatory z uwzględnieniem wielkości liter w standardach, takich jak XML i HTTP.<br /><br /> Ustawienia związane z zabezpieczeniami uwzględniane wielkości liter.|Identyfikator niejęzykowy, w którym bajty są dokładnie zgodne.|<xref:System.StringComparison.Ordinal>|
|Identyfikatory wewnętrzne niewrażliwe na wielkość liter.<br /><br /> Identyfikatory niewrażliwe na wielkość liter w standardach, takich jak XML i HTTP.<br /><br /> Ścieżki plików.<br /><br /> Klucze rejestru i wartości.<br /><br /> Zmienne środowiskowe.<br /><br /> Identyfikatory zasobów (na przykład nazwy uchwytów).<br /><br /> Ustawienia związane z zabezpieczeniami nieuwzględniane wielkości liter.|Identyfikator niejęzykowy, w przypadku gdy przypadek jest nieistotny; zwłaszcza dane przechowywane w większości usług systemowych Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|
|Niektóre utrwaliły się, istotne językowo dane.<br /><br /> Wyświetlanie danych językowych, które wymagają stałej kolejności sortowania.|Kulturowo niezależne dane, które nadal są istotne językowo.|<xref:System.StringComparison.InvariantCulture><br /><br /> — lub —<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|
|Dane wyświetlane użytkownikowi.<br /><br /> Większość danych wejściowych użytkownika.|Dane, które wymagają lokalnych zwyczajów językowych.|<xref:System.StringComparison.CurrentCulture><br /><br /> — lub —<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|

## <a name="common-string-comparison-methods-in-net"></a>Typowe metody porównywania ciągów w .NET

W poniższych sekcjach opisano metody, które są najczęściej używane do porównywania ciągów.

### <a name="stringcompare"></a>Funkcja String.Compare

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Jako operacja najbardziej centralna interpretacji ciągu, wszystkie wystąpienia tych wywołań metody powinny być badane w celu ustalenia, czy ciągi powinny być interpretowane zgodnie z bieżącej kultury lub odłączony od kultury (symbolicznie). Zazwyczaj jest to ten ostatni, <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> a zamiast tego należy użyć porównania.

Klasa, <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> która jest zwracana <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> przez właściwość, <xref:System.Globalization.CompareInfo.Compare%2A> zawiera również metodę, która zapewnia dużą liczbę opcji dopasowania (liczba mięsień, ignorując biały <xref:System.Globalization.CompareOptions> znak, ignorując typ kana i tak dalej) za pomocą wyliczenia flagi.

### <a name="stringcompareto"></a>Funkcja String.CompareTo

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Ta metoda nie oferuje obecnie przeciążenia, który określa <xref:System.StringComparison> typ. Zazwyczaj można przekonwertować tę metodę <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> na zalecany formularz.

Typy, które <xref:System.IComparable> <xref:System.IComparable%601> implementują i interfejsy implementują tę metodę. Ponieważ nie oferuje opcję parametru, <xref:System.StringComparison> implementowanie typów często <xref:System.StringComparer> pozwalają użytkownikowi określić w ich konstruktora. Poniższy przykład definiuje `FileName` klasę, której konstruktor klasy zawiera <xref:System.StringComparer> parametr. Ten <xref:System.StringComparer> obiekt jest następnie `FileName.CompareTo` używany w metodzie.

[!code-csharp[Conceptual.Strings.BestPractices#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
[!code-vb[Conceptual.Strings.BestPractices#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]

### <a name="stringequals"></a>Funkcja String.Equals

Interpretacja <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>domyślna: .

Klasa <xref:System.String> umożliwia testowanie równości przez wywołanie przeciążenia metodą statyczne lub wystąpienie <xref:System.String.Equals%2A> lub za pomocą operatora równości statycznej. Przeciążenia i operator użyć porównania liczba mięsień domyślnie. Jednak nadal zaleca się wywołanie przeciążenia, który <xref:System.StringComparison> jawnie określa typ, nawet jeśli chcesz wykonać porównanie liczba; ułatwia to wyszukiwanie kodu dla określonej interpretacji ciągu.

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper i String.ToLower

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Należy zachować ostrożność podczas korzystania z tych metod, ponieważ wymuszanie ciągu na wielkie lub małe litery jest często używany jako mała normalizacja do porównywania ciągów niezależnie od przypadku. Jeśli tak, należy rozważyć użycie porównania bez uwzględniania wielkości liter.

Dostępne <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> są również metody i metody. <xref:System.String.ToUpperInvariant%2A>jest standardowym sposobem normalizacji obudowy. Porównania wykonane <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> przy użyciu są behawioralnie kompozycji dwóch wywołań: <xref:System.String.ToUpperInvariant%2A> wywołanie <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>obu argumentów ciągu i robi porównanie przy użyciu .

Przeciążenia są również dostępne do konwersji na wielkie i małe <xref:System.Globalization.CultureInfo> litery w określonej kulturze, przekazując obiekt, który reprezentuje tę kulturę do metody.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper i Char.ToLower

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Metody te działają podobnie <xref:System.String.ToUpper%2A?displayProperty=nameWithType> do <xref:System.String.ToLower%2A?displayProperty=nameWithType> metod opisanych w poprzedniej sekcji.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith i String.EndsWith

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Domyślnie obie te metody wykonują porównanie zależne od kultury.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf i String.LastIndexOf

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Istnieje brak spójności w jaki sposób domyślne przeciążenia tych metod wykonywać porównania. Wszystkie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> i metody, <xref:System.Char> które zawierają parametr wykonać porównanie liczba <xref:System.String.IndexOf%2A?displayProperty=nameWithType> głosów, ale domyślne i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, które zawierają <xref:System.String> parametr wykonać porównanie zależne od kultury.

Jeśli <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> wywołasz <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> lub metody i przekazać go ciąg, aby zlokalizować w bieżącym wystąpieniu, <xref:System.StringComparison> zaleca się wywołanie przeciążenia, który jawnie określa typ. Przeciążenia, które <xref:System.Char> zawierają argument nie pozwalają <xref:System.StringComparison> określić typ.

## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, które wykonują porównanie ciągów pośrednio

Niektóre metody nieciągowe, które mają porównanie <xref:System.StringComparer> ciągów jako operację centralną, używają tego typu. Klasa <xref:System.StringComparer> zawiera sześć właściwości statycznych, które zwracają <xref:System.StringComparer> wystąpienia, których <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody wykonują następujące typy porównań ciągów:

- Porównania ciągów zależnych od kultury przy użyciu bieżącej kultury. Ten <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> właściwość.
- Porównania bez uwzględniania wielkości liter przy użyciu bieżącej kultury. Ten <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> właściwość.
- Porównania niewrażliwe na kulturę przy użyciu reguł porównywania słów kultury niezmiennej. Ten <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> właściwość.
- Porównania bez uwzględniania wielkości liter i nieuwzględniania kultury przy użyciu reguł porównywania słów kultury niezmiennej. Ten <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> właściwość.
- Porównanie pisane. Ten <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> właściwość.
- Porównanie pism nierozróżniania wielkości liter. Ten <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> właściwość.

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort i Array.BinarySearch

Interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>domyślna: .

Podczas przechowywania jakichkolwiek danych w kolekcji lub odczytu utrwaliły dane z pliku lub bazy danych do kolekcji, przełączanie bieżącej kultury może unieważnić invariants w kolekcji. Metoda <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> zakłada, że elementy w tablicy do przeszukania są już sortowane. Aby posortować dowolny element <xref:System.Array.Sort%2A?displayProperty=nameWithType> ciągu <xref:System.String.Compare%2A?displayProperty=nameWithType> w tablicy, metoda wywołuje metodę, aby uporządkować poszczególne elementy. Przy użyciu porównania zależne od kultury może być niebezpieczne, jeśli kultura zmienia się między czasem, że tablica jest sortowana i jego zawartość są przeszukiwane. Na przykład w poniższym kodzie przechowywania i pobierania działają na comparer, który jest dostarczany niejawnie przez `Thread.CurrentThread.CurrentCulture` właściwość. Jeśli kultura może się zmieniać między wywołaniami do `StoreNames` i `DoesNameExist`, a zwłaszcza jeśli zawartość tablicy są utrwalione gdzieś między dwoma wywołaniami metody, wyszukiwanie binarne może zakończyć się niepowodzeniem.

[!code-csharp[Conceptual.Strings.BestPractices#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]

Zalecana odmiana pojawia się w poniższym przykładzie, który używa tej samej metody porównania porządkowej (niewrażliwej na kulturę) zarówno do sortowania, jak i wyszukiwania tablicy. Kod zmiany jest odzwierciedlony w `Line A` wierszach oznaczonych i `Line B` w dwóch przykładach.

[!code-csharp[Conceptual.Strings.BestPractices#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
[!code-vb[Conceptual.Strings.BestPractices#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]

Jeśli te dane są zachowywane i przenoszone między kulturami, a sortowanie jest używane <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>do prezentowania tych danych użytkownikowi, można rozważyć użycie , który działa językowo dla lepszego wyjścia użytkownika, ale nie ma wpływu na zmiany w kulturze. Poniższy przykład modyfikuje dwa poprzednie przykłady, aby użyć kultury niezmiennej do sortowania i wyszukiwania tablicy.

[!code-csharp[Conceptual.Strings.BestPractices#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
[!code-vb[Conceptual.Strings.BestPractices#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]

### <a name="collections-example-hashtable-constructor"></a>Przykład kolekcji: Konstruktor hashtable

Hashing ciągi zawiera drugi przykład operacji, która ma wpływ na sposób, w którym ciągi są porównywane.

Poniższy przykład tworzy <xref:System.Collections.Hashtable> obiekt, przekazując go <xref:System.StringComparer> obiekt, który jest <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> zwracany przez właściwość. Ponieważ <xref:System.StringComparer> klasa, która jest <xref:System.StringComparer> pochodną <xref:System.Collections.IEqualityComparer> implementuje <xref:System.Collections.IEqualityComparer.GetHashCode%2A> interfejs, jego metoda jest używana do obliczania kodu mieszania ciągów w tabeli mieszania.

[!code-csharp[Conceptual.Strings.BestPractices#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
[!code-vb[Conceptual.Strings.BestPractices#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]

## <a name="displaying-and-persisting-formatted-data"></a>Wyświetlanie i utrwalanie sformatowanych danych

Podczas wyświetlania użytkownikom danych niezwiązanych z ciągami, takich jak liczby, daty i godziny, należy je sformatować przy użyciu ustawień kulturowych użytkownika. Domyślnie wszystkie następujące używają bieżącej kultury wątku w operacjach formatowania:

- Interpolowane ciągi obsługiwane przez kompilatory [Języka C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic.](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- Operacje łączenia ciągów, które używają operatorów konkatenacji Języka <xref:System.String.Concat%2A?displayProperty=nameWithType> [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) lub Visual [Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) lub które bezpośrednio wywołają metodę.
- Metoda. <xref:System.String.Format%2A?displayProperty=nameWithType>
- Metody `ToString` typów liczbowych oraz typy daty i godziny.

Aby jawnie określić, że ciąg powinien być sformatowany przy użyciu konwencji wyznaczonej kultury lub [kultury niezmiennej,](xref:System.Globalization.CultureInfo.InvariantCulture)można wykonać następujące czynności:

- Korzystając z <xref:System.String.Format%2A?displayProperty=nameWithType> `ToString` i metody, wywołać przeciążenie, który ma `provider` parametr, takich jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> lub <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>, i przekazać go <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość, <xref:System.Globalization.CultureInfo> wystąpienie, które reprezentuje żądaną kulturę lub <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> właściwość.

- W przypadku łączenia ciągów nie zezwalaj kompilatorowi na wykonywanie niejawnych konwersji. Zamiast tego wykonaj jawną `ToString` konwersję, wywołując `provider` przeciążenie, które ma parametr. Na przykład kompilator niejawnie używa bieżącej kultury podczas konwertowania <xref:System.Double> wartości na ciąg w następującym kodzie C#:

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  Zamiast tego można jawnie określić kulturę, której konwencje formatowania <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> są używane w konwersji, wywołując metodę, tak jak wykonuje to następujący kod C#:

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- W przypadku interpolacji ciągów zamiast przypisywania interpolowany ciąg do <xref:System.String> wystąpienia, przypisać go do . <xref:System.FormattableString> Następnie można wywołać jego <xref:System.FormattableString.ToString?displayProperty=nameWithType> metoda produkować ciąg wynik, który odzwierciedla konwencje <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> bieżącej kultury lub można wywołać metodę do tworzenia ciąg wynik, który odzwierciedla konwencje określonej kultury. Można również przekazać formatowalny <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> ciąg do metody statycznej, aby utworzyć ciąg wynikowy, który odzwierciedla konwencje kultury niezmiennej. To podejście pokazano w poniższym przykładzie. (Dane wyjściowe z przykładu odzwierciedla bieżącą kulturę en US.)

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

Dane niebędące ciągami można utrzymywać jako dane binarne lub jako sformatowane dane. Jeśli zdecydujesz się zapisać go jako sformatowane dane, należy wywołać `provider` przeciążenie metodą <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> formatowania, który zawiera parametr i przekazać go właściwości. Niezmienna kultura zapewnia spójny format sformatowanych danych, który jest niezależny od kultury i maszyny. Z drugiej strony, utrwalanie danych, który jest sformatowany przy użyciu kultur innych niż kultury niezmiennej ma szereg ograniczeń:

- Dane mogą być bezużyteczne, jeśli są pobierane w systemie, który ma inną kulturę lub jeśli użytkownik bieżącego systemu zmienia bieżącą kulturę i próbuje pobrać dane.
- Właściwości kultury na określonym komputerze mogą różnić się od wartości standardowych. W dowolnym momencie użytkownik może dostosować ustawienia wyświetlania zależne od kultury. Z tego powodu sformatowane dane zapisane w systemie mogą nie być czytelne po dostosowaniu ustawień kulturowych przez użytkownika. Przenoszenie sformatowanych danych na komputerach może być jeszcze bardziej ograniczone.
- Międzynarodowe, regionalne lub krajowe standardy regulujące formatowanie liczb lub dat i godzin zmieniają się wraz z uchwycone, a zmiany te są uwzględniane w aktualizacjach systemu operacyjnego Windows. Gdy konwencje formatowania zmieniają się, dane, które zostały sformatowane przy użyciu poprzednich konwencji, mogą stać się nieczytelne.

W poniższym przykładzie przedstawiono ograniczoną przenośność wynikającą z używania formatowania zależnego od kultury do utrwalenia danych. W przykładzie zapisuje tablicę wartości daty i godziny do pliku. Są one formatowane przy użyciu konwencji kultury angielskiej (Stany Zjednoczone). Po aplikacji zmienia bieżącą kulturę wątku na francuski (Szwajcaria), próbuje odczytać zapisane wartości przy użyciu konwencji formatowania bieżącej kultury. Próba odczytania dwóch elementów danych zgłasza <xref:System.FormatException> wyjątek, a tablica dat zawiera teraz <xref:System.DateTime.MinValue>dwa niepoprawne elementy, które są równe .

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

Jeśli jednak właściwość <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> zostanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zastąpiona <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> w <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>wywołaniach i , utrwalione dane daty i godziny zostaną pomyślnie przywrócone, jak pokazano na poniższych danych wyjściowych:

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```

## <a name="see-also"></a>Zobacz też

- [Manipulowanie ciągami](manipulating-strings.md)
