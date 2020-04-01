---
title: Najważniejsze wskazówki dotyczące używania ciągów w sieci .NET
description: Dowiedz się, jak efektywnie używać ciągów w aplikacjach platformy .NET.
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
ms.openlocfilehash: e633b6c1d03a3d1cd70e277395da10f70f315f16
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523975"
---
# <a name="best-practices-for-using-strings-in-net"></a>Najważniejsze wskazówki dotyczące używania ciągów w sieci .NET

.NET zapewnia szeroką obsługę tworzenia zlokalizowanych i zglobalizowanych aplikacji i ułatwia stosowanie konwencji bieżącej kultury lub określonej kultury podczas wykonywania typowych operacji, takich jak sortowanie i wyświetlanie ciągów. Ale sortowanie lub porównywanie ciągów nie zawsze jest operacją zależną od kultury. Na przykład ciągi, które są używane wewnętrznie przez aplikację zazwyczaj powinny być obsługiwane identycznie we wszystkich kulturach. Gdy dane ciągów niezależne od kultury, takie jak znaczniki XML, znaczniki HTML, nazwy użytkowników, ścieżki plików i nazwy obiektów systemowych, są interpretowane tak, jakby były wrażliwe na kulturę, kod aplikacji może podlegać subtelnym błędom, niskiej wydajności, a w niektórych przypadkach problemom z zabezpieczeniami.

W tym temacie analizuje ciąg sortowania, porównywania i metody wielkości liter w .NET, przedstawia zalecenia dotyczące wyboru odpowiedniej metody obsługi ciągów i zawiera dodatkowe informacje na temat metod obsługi ciągów. Sprawdza również, w jaki sposób sformatowane dane, takie jak dane liczbowe oraz dane daty i godziny, są obsługiwane do wyświetlania i przechowywania.

## <a name="recommendations-for-string-usage"></a>Zalecenia dotyczące użycia ciągu

Podczas tworzenia za pomocą platformy .NET należy postępować zgodnie z tymi prostymi zaleceniami podczas używania ciągów:

- Użyj przeciążenia, które jawnie określić reguły porównywania ciągów dla operacji ciągu. Zazwyczaj wiąże się to z wywołaniem przeciążenia <xref:System.StringComparison>metody, który ma parametr typu.
- Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> lub dla porównań jako bezpieczne domyślne dla dopasowania ciągów niezależnej od kultury.
- Użyj porównań <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> z lub dla lepszej wydajności.
- Użyj operacji ciągu, <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> które są oparte na podczas wyświetlania danych wyjściowych do użytkownika.
- Użyj wartości nielingwistycznych <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartości <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zamiast operacji ciągu na podstawie, gdy porównanie jest lingwistycznie nieistotne (symboliczne, na przykład).
- Użyj <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> metody zamiast metody <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> podczas normalizacji ciągów do porównania.
- Użyj przeciążenia <xref:System.String.Equals%2A?displayProperty=nameWithType> metody, aby sprawdzić, czy dwa ciągi są równe.
- Użyj <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do sortowania ciągów, a nie, aby sprawdzić równość.
- Formatowanie z uwzględnieniem kultury służy do wyświetlania w interfejsie użytkownika danych innych niż ciągi, takich jak liczby i daty. Użyj formatowania z [kulturą niezmienną,](xref:System.Globalization.CultureInfo.InvariantCulture) aby utrwalić dane niebędące ciągami w postaci ciągu.

Unikaj następujących praktyk podczas używania ciągów:

- Nie należy używać przeciążeń, które nie jawnie lub niejawnie określają reguły porównywania ciągów dla operacji ciągu.
- Nie należy używać operacji <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ciągu na podstawie w większości przypadków. Jednym z niewielu wyjątków jest, gdy utrzymują się językowo znaczące, ale kulturowo agnostyczne danych.
- Nie należy używać <xref:System.String.Compare%2A?displayProperty=nameWithType> przeciążenia <xref:System.String.CompareTo%2A> lub metody i przetestować dla zwracanej wartości zero, aby ustalić, czy dwa ciągi są równe.
- Nie należy używać formatowania zależnego od kultury do utrwalania danych liczbowych lub danych daty i godziny w postaci ciągu.

## <a name="specifying-string-comparisons-explicitly"></a>Jawne określanie porównań ciągów

Większość metod manipulowania ciągami w .NET są przeciążone. Zazwyczaj jeden lub więcej przeciążenia akceptuje ustawienia domyślne, podczas gdy inne akceptują żadnych ustawień domyślnych i zamiast tego definiują dokładny sposób, w jaki ciągi mają być porównywane lub manipulowane. Większość metod, które nie opierają się na wartości <xref:System.StringComparison>domyślne obejmują parametr typu , który jest wyliczenie, które jawnie określa reguły porównania ciągów według kultury i przypadku. W poniższej <xref:System.StringComparison> tabeli opisano elementy członkowskie wyliczenia.

|Element członkowski stringcomparison|Opis|
|-----------------------------|-----------------|
|<xref:System.StringComparison.CurrentCulture>|Wykonuje porównanie z uwzględnieniem wielkości liter przy użyciu bieżącej kultury.|
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu bieżącej kultury.|
|<xref:System.StringComparison.InvariantCulture>|Wykonuje porównanie z uwzględnieniem wielkości liter przy użyciu kultury niezmiennej.|
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu kultury niezmiennej.|
|<xref:System.StringComparison.Ordinal>|Wykonuje porównanie porządkowe.|
|<xref:System.StringComparison.OrdinalIgnoreCase>|Wykonuje porównanie porządkowe bez uwzględniania wielkości liter.|

Na przykład <xref:System.String.IndexOf%2A> metoda, która zwraca indeks podciągów w <xref:System.String> obiekcie, który pasuje do znaku lub ciągu, ma dziewięć przeciążeń:

- <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>i <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, które domyślnie wykonują porządkowe (rozróżniane wielkość liter i niewrażliwe na kulturę) wyszukują znak w ciągu.
- <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, które domyślnie wykonują wyszukiwanie podciągów z uwzględnieniem wielkości liter i kultury w ciągu.
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, które zawierają <xref:System.StringComparison> parametr typu, który umożliwia określenie postaci porównania.

Zaleca się wybranie przeciążenia, które nie używa wartości domyślnych, z następujących powodów:

- Niektóre przeciążenia z parametrów domyślnych <xref:System.Char> (te, które wyszukują w wystąpieniu ciągu) wykonać porównanie porządkowe, podczas gdy inne (te, które wyszukują ciąg w wystąpieniu ciągu) są zależne od kultury. Trudno jest zapamiętać, która metoda używa, która wartość domyślna i łatwo mylić przeciążenia.
- Intencja kodu, który opiera się na wartości domyślnych dla wywołań metody nie jest jasne. W poniższym przykładzie, który opiera się na wartościach domyślnych, trudno jest wiedzieć, czy deweloper rzeczywiście przeznaczone porządkowe lub językowe porównanie dwóch ciągów, lub czy różnica wielkości liter między `protocol` i "http" może spowodować test równości do powrotu `false`.

     [!code-csharp[Conceptual.Strings.BestPractices#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]

Ogólnie rzecz biorąc zaleca się wywołanie metody, która nie opiera się na wartości domyślnych, ponieważ sprawia, że intencji kodu jednoznaczne. To z kolei sprawia, że kod bardziej czytelny i łatwiejszy do debugowania i obsługi. Poniższy przykład odnosi się do pytań dotyczących poprzedniego przykładu. Wyjaśnia, że stosuje się porównanie porządkowe i że różnice w przypadku są ignorowane.

[!code-csharp[Conceptual.Strings.BestPractices#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
[!code-vb[Conceptual.Strings.BestPractices#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]

## <a name="the-details-of-string-comparison"></a>Szczegóły porównania ciągów

Porównanie ciągów jest sercem wielu operacji związanych z ciągami, szczególnie sortowania i testowania równości. Ciągi sortują w określonej kolejności: Jeśli "mój" pojawia się przed "ciągiem" na posortowanym liście ciągów, "mój" musi porównać mniej niż lub równe "ciąg". Ponadto porównanie niejawnie definiuje równości. Operacja porównania zwraca zero dla ciągów, które uważa za równe. Dobrą interpretacją jest to, że żaden ciąg nie jest mniejszy od drugiego. Najbardziej znaczące operacje obejmujące ciągi obejmują jedną lub obie te procedury: porównanie z innym ciągiem i wykonanie dobrze zdefiniowanej operacji sortowania.

> [!NOTE]
> Można pobrać [tabele wagi sortowania](https://www.microsoft.com/download/details.aspx?id=10921), zestaw plików tekstowych zawierających informacje o masie znaków używane w operacjach sortowania i porównywania dla systemów operacyjnych Windows oraz [domyślną tabelę elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt)— najnowszą wersję tabeli wagi sortowania dla systemów Linux i macOS. Konkretna wersja tabeli wagowej sortowania w systemach Linux i macOS zależy od wersji bibliotek [International Components for Unicode](http://site.icu-project.org/) zainstalowanych w systemie. Aby uzyskać informacje na temat wersji ICU i wersji Unicode, które implementują, zobacz [Pobieranie OIOM](http://site.icu-project.org/download).

Jednak ocena dwóch ciągów dla równości lub kolejności sortowania nie daje pojedynczy, poprawny wynik; wynik zależy od kryteriów użytych do porównania ciągów. W szczególności porównania ciągów, które są porządkowe lub które są oparte na konwencji wielkości liter i sortowania bieżącej kultury lub [kultury niezmiennej](xref:System.Globalization.CultureInfo.InvariantCulture) (kultury niezależnej od ustawień regionalnych na podstawie języka angielskiego) może przynieść różne wyniki.

Ponadto porównania ciągów przy użyciu różnych wersji platformy .NET lub przy użyciu platformy .NET w różnych systemach operacyjnych lub wersjach systemu operacyjnego mogą zwracać różne wyniki. Aby uzyskać więcej informacji, zobacz [Ciągi ciągów i Standard Unicode](xref:System.String#Unicode).

### <a name="string-comparisons-that-use-the-current-culture"></a>Porównania ciągów, które używają bieżącej kultury

Jedno kryterium polega na użyciu konwencji bieżącej kultury podczas porównywania ciągów. Porównania, które są oparte na bieżącej kultury użyć bieżącej kultury wątku lub ustawień regionalnych. Jeśli kultura nie jest ustawiona przez użytkownika, domyślnie jest to ustawienie w oknie **Opcje regionalne** w Panelu sterowania. Należy zawsze używać porównań, które są oparte na bieżącej kultury, gdy dane są lingwistycznie istotne i gdy odzwierciedla interakcję użytkownika zależne od kultury.

Jednak zachowanie porównania i wielkości liter w .NET zmienia się po zmianie kultury. Dzieje się tak, gdy aplikacja jest wykonywana na komputerze, który ma inną kulturę niż komputer, na którym aplikacja została opracowana lub gdy wątek wykonujący zmienia swoją kulturę. To zachowanie jest zamierzone, ale pozostaje nieoczywiste dla wielu deweloperów. Poniższy przykład ilustruje różnice w kolejności sortowania między kulturami języka angielskiego ("en-US") i szwedzkiego ("sv-SE"). Należy zauważyć, że wyrazy "ångström", "Windows" i "Visual Studio" pojawiają się w różnych pozycjach w posortowanych tablicach ciągów.

[!code-csharp[Conceptual.Strings.BestPractices#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
[!code-vb[Conceptual.Strings.BestPractices#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]

Porównania bez uwzględniania wielkości liter, które używają bieżącej kultury są takie same jak porównania zależne od kultury, z tą różnicą, że ignorują wielkość liter, zgodnie z podyktowanymi przez bieżącą kulturę wątku. To zachowanie może objawiać się również w zamówieniach sortowania.

Porównania, które używają bieżącej semantyki kultury są domyślne dla następujących metod:

- <xref:System.String.Compare%2A?displayProperty=nameWithType>przeciążenia, które nie <xref:System.StringComparison> zawierają parametru.
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Przeciążenia.
- Metoda <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> domyślna i <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda `null` <xref:System.Globalization.CultureInfo> z parametrem.
- Metoda <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> domyślna i <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda `null` <xref:System.Globalization.CultureInfo> z parametrem.
- <xref:System.String.IndexOf%2A?displayProperty=nameWithType>przeciążenia, które <xref:System.String> akceptują jako parametr wyszukiwania <xref:System.StringComparison> i które nie mają parametru.
- <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>przeciążenia, które <xref:System.String> akceptują jako parametr wyszukiwania <xref:System.StringComparison> i które nie mają parametru.

W każdym przypadku zaleca się wywołanie przeciążenia, który ma <xref:System.StringComparison> parametr, aby intencji wywołania metody jasne.

Subtelne i nie tak subtelne błędy mogą pojawić się, gdy nielingwistyczne dane ciągu są interpretowane lingwistycznie lub gdy dane ciągu z określonej kultury są interpretowane przy użyciu konwencji innej kultury. Przykładem kanonicznym jest problem Turecka-I.

Dla prawie wszystkich alfabetów łacińskich, w tym angielskiego amerykańskiego, znak "i" (\u0069) jest wersją małych liter znaku "I" (\u0049). Ta reguła wielkości liter szybko staje się domyślną dla kogoś programowania w takiej kulturze. Jednak alfabet turecki ("tr-TR") zawiera znak "I z kropką" znak "İ" (\u0130), który jest stołeczną wersją "i". Turecki zawiera również małe litery "i bez kropki" znak "ı" (\u0131), który kapitalizuje się na "I". Takie zachowanie występuje również w kulturze azerbejdżańskiej ("az").

W związku z tym założenia dotyczące kapitalizacji "i" lub małych liter "I" nie są prawidłowe dla wszystkich kultur. Jeśli używasz domyślne przeciążenia dla procedur porównywania ciągów, będą one podlegać wariancji między kulturami. Jeśli dane, które mają być porównywane jest nielingwistyczna, przy użyciu domyślne przeciążenia może produkować niepożądane wyniki, jak następująca próba wykonania porównania bez uwzględniania wielkości liter ciągów "plik" i "PLIK" ilustruje.

[!code-csharp[Conceptual.Strings.BestPractices#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
[!code-vb[Conceptual.Strings.BestPractices#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]

To porównanie może spowodować poważne problemy, jeśli kultura jest przypadkowo używany w ustawieniach wrażliwych na zabezpieczenia, jak w poniższym przykładzie. Wywołanie metody, `IsFileURI("file:")` `true` takie jak zwraca, jeśli bieżąca `false` kultura jest angielski w STANACH Zjednoczonych, ale jeśli bieżąca kultura jest turecka. Tak więc, w tureckich systemach, ktoś może obejść środki bezpieczeństwa, które blokują dostęp do niewrażliwych URI, które zaczynają się od "FILE:".

[!code-csharp[Conceptual.Strings.BestPractices#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
[!code-vb[Conceptual.Strings.BestPractices#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]

W takim przypadku, ponieważ "file:" ma być interpretowany jako identyfikator nielingwisty, niewrażliwy na kulturę, kod powinien być zapisywany w sposób pokazany w poniższym przykładzie:

[!code-csharp[Conceptual.Strings.BestPractices#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
[!code-vb[Conceptual.Strings.BestPractices#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]

### <a name="ordinal-string-operations"></a>Operacje ciągu porządkowego

Określenie <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartość w wywołaniu metody oznacza porównanie nielingwistyczno, w którym funkcje języków naturalnych są ignorowane. Metody, które są <xref:System.StringComparison> wywoływane z tymi wartościami podstawowe decyzje operacji ciągu na proste porównania bajtów zamiast tabel wielkości liter lub równoważności, które są parametryzowane przez kulturę. W większości przypadków to podejście najlepiej pasuje do zamierzonej interpretacji ciągów przy jednoczesnym szybszym i bardziej niezawodnym kodzie.

Porównania porządkowe są porównania ciągów, w których każdy bajt każdego ciągu jest porównywany bez interpretacji językowej; na przykład "windows" nie pasuje do "Windows". Jest to zasadniczo wywołanie `strcmp` funkcji środowiska wykonawczego języka C. Użyj tego porównania, gdy kontekst nakazuje, że ciągi powinny być dokładnie dopasowane lub wymaga konserwatywnych zasad dopasowania. Ponadto porównanie porządkowe jest najszybszą operacją porównania, ponieważ nie stosuje żadnych reguł językowych podczas określania wyniku.

Ciągi w .NET mogą zawierać osadzone znaki null. Jedną z najczystszych różnic między porównaniem porządkowym i zależnym od kultury (w tym porównaniami, które używają kultury niezmiennej) jest obsługa osadzonych znaków null w ciągu. Znaki te są ignorowane <xref:System.String.Compare%2A?displayProperty=nameWithType> podczas <xref:System.String.Equals%2A?displayProperty=nameWithType> korzystania z i metody do wykonywania porównań wrażliwych na kulturę (w tym porównania, które używają kultury niezmienne). W rezultacie w porównaniach zależnych od kultury ciągi, które zawierają osadzone znaki null, można uznać za równe ciągom, które nie.

> [!IMPORTANT]
> Chociaż metody porównywania ciągów pomijają osadzone <xref:System.String.EndsWith%2A?displayProperty=nameWithType> <xref:System.String.IndexOf%2A?displayProperty=nameWithType>znaki <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>null, metody wyszukiwania ciągów, takie jak <xref:System.String.StartsWith%2A?displayProperty=nameWithType> <xref:System.String.Contains%2A?displayProperty=nameWithType>, , , i nie.

Poniższy przykład wykonuje porównanie zależne od kultury ciągu "Aa" z podobnym ciągiem, który zawiera kilka osadzonych znaków null między "A" i "a", i pokazuje, jak dwa ciągi są uważane za równe:

[!code-csharp[Conceptual.Strings.BestPractices#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]

Jednak ciągi nie są uważane za równe podczas korzystania z porównania porządkowego, jak pokazano w poniższym przykładzie:
  
[!code-csharp[Conceptual.Strings.BestPractices#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
[!code-vb[Conceptual.Strings.BestPractices#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]

Porównania porządkowe bez uwzględniania wielkości liter są kolejnym najbardziej konserwatywnym podejściem. Te porównania ignorują większość obudowy; na przykład "windows" pasuje do "Windows". W przypadku znaków ASCII ta zasada <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>jest równoważna , z tą różnicą, że ignoruje zwykłą wielkość liter ASCII. W związku z tym dowolny znak w [A, Z] (\u0041-\u005A) pasuje do odpowiedniego znaku w [a,z] (\u0061-\007A). Obudowa poza zakresem ASCII używa tabel kultury niezmiennej. W związku z tym następujące porównanie:

[!code-csharp[Conceptual.Strings.BestPractices#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
[!code-vb[Conceptual.Strings.BestPractices#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]

jest równoważne (ale szybsze niż) to porównanie:

[!code-csharp[Conceptual.Strings.BestPractices#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
[!code-vb[Conceptual.Strings.BestPractices#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]

Te porównania są nadal bardzo szybkie.

> [!NOTE]
> Zachowanie ciągu systemu plików, kluczy i wartości rejestru oraz zmiennych <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>środowiskowych najlepiej jest reprezentować przez program .

Zarówno <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> i używać wartości binarnych bezpośrednio i najlepiej nadaje się do dopasowywania. Jeśli nie masz pewności co do ustawień porównania, użyj jednej z tych dwóch wartości. Jednak ponieważ wykonują porównanie bajtów po bajcie, nie sortują według kolejności sortowania językowego (jak słownik angielski), ale według kolejności sortowania binarnego. Wyniki mogą wyglądać dziwnie w większości kontekstów, jeśli są wyświetlane użytkownikom.

Semantyka porządkowa jest domyślna <xref:System.String.Equals%2A?displayProperty=nameWithType> dla przeciążeń, <xref:System.StringComparison> które nie zawierają argumentu (w tym operatora równości). W każdym przypadku zaleca się wywołanie przeciążenia, które ma <xref:System.StringComparison> parametr.

### <a name="string-operations-that-use-the-invariant-culture"></a>operacje ciągu, które używają kultury niezmiennej

Porównania z kultury niezmienne używać <xref:System.Globalization.CultureInfo.CompareInfo%2A> właściwości zwrócone przez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości statyczne. To zachowanie jest takie samo we wszystkich systemach; przekłada wszystkie znaki spoza jego zasięgu na to, co uważa za równoważne niezmienne znaki. Ta zasada może być przydatne do obsługi jednego zestawu zachowań ciągów w różnych kulturach, ale często zapewnia nieoczekiwane wyniki.

Porównania bez uwzględniania wielkości liter z kulturą niezmienną używają <xref:System.Globalization.CultureInfo.CompareInfo%2A> właściwości statycznej <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zwróconej przez właściwość statyczną również w celu uzyskania informacji porównawczych. Wszelkie różnice przypadków między tymi przetłumaczonymi znakami są ignorowane.

Porównania, które <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> używają i działają identycznie na ciągach ASCII. Jednak <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> podejmuje decyzje językowe, które mogą nie być odpowiednie dla ciągów, które muszą być interpretowane jako zestaw bajtów. Obiekt `CultureInfo.InvariantCulture.CompareInfo` sprawia, <xref:System.String.Compare%2A> że metoda interpretować niektóre zestawy znaków jako równoważne. Na przykład następująca równoważność jest prawidłowa w ramach kultury niezmiennej:

InvariantKultura: a + = å

ŁACIŃSKA MAŁA LITERA Znak "a" (\u0061), gdy znajduje się obok znaku "+ " 000a) (\u030a), jest interpretowany jako ŁACIŃSKA MAŁA LITERA A Z PIERŚCIENIEM POWYŻEJ ZNAKU "å" (\u00e5). Jak pokazano w poniższym przykładzie, to zachowanie różni się od porównania porządkowego.

[!code-csharp[Conceptual.Strings.BestPractices#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
[!code-vb[Conceptual.Strings.BestPractices#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]

Podczas interpretowania nazw plików, plików cookie lub czegokolwiek innego, w którym może pojawić się kombinacja, taka jak "å", porównania porządkowe nadal oferują najbardziej przejrzyste i odpowiednie zachowanie.

W sumie, niezmienna kultura ma bardzo niewiele właściwości, które sprawiają, że przydatne do porównania. Dokonuje porównania w sposób istotny językowo, co uniemożliwia mu zagwarantowanie pełnej równoważności symbolicznej, ale nie jest to wybór do wyświetlania w żadnej kulturze. Jednym z niewielu <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> powodów do użycia do porównania jest utrzymywać uporządkowane dane dla wyświetlania międzykulturowo identyczne. Na przykład jeśli duży plik danych, który zawiera listę posortowanych identyfikatorów do wyświetlania towarzyszy aplikacji, dodanie do tej listy wymagałoby wstawienia z sortowania w stylu niezmiennym.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Wybieranie elementu członkowskiego stringcomparison dla wywołania metody

W poniższej tabeli przedstawiono mapowanie z <xref:System.StringComparison> kontekstu semantycznego ciągu do elementu członkowskiego wyliczenia:

|Dane|Zachowanie|Odpowiednia kompania systemowa.string<br /><br /> value|
|----------|--------------|-----------------------------------------------------|
|Identyfikatory wewnętrzne z uwzględnieniem wielkości liter.<br /><br /> Identyfikatory z uwzględnieniem wielkości liter w standardach takich jak XML i HTTP.<br /><br /> Ustawienia związane z zabezpieczeniami z uwzględnieniem wielkości liter.|Identyfikator nielingwisty, gdzie bajty dokładnie pasują.|<xref:System.StringComparison.Ordinal>|
|Identyfikatory wewnętrzne bez uwzględniania wielkości liter.<br /><br /> Identyfikatory bez uwzględniania wielkości liter w standardach, takich jak XML i HTTP.<br /><br /> Ścieżki plików.<br /><br /> Klucze i wartości rejestru.<br /><br /> Zmienne środowiskowe.<br /><br /> Identyfikatory zasobów (na przykład nazwy uchwytów).<br /><br /> Ustawienia związane z zabezpieczeniami bez uwzględniania wielkości liter.|Identyfikator nielingwiscyjny, w przypadku gdy przypadek jest nieistotny; szczególnie danych przechowywanych w większości usług systemu Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|
|Niektóre z nich utrzymywały się, lingwistycznie istotne dane.<br /><br /> Wyświetlanie danych językowych, które wymagają stałej kolejności sortowania.|Dane agnostyczne kulturowo, które nadal mają znaczenie językowe.|<xref:System.StringComparison.InvariantCulture><br /><br /> — lub —<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|
|Dane wyświetlane użytkownikowi.<br /><br /> Większość danych wejściowych użytkownika.|Dane, które wymagają lokalnych zwyczajów językowych.|<xref:System.StringComparison.CurrentCulture><br /><br /> — lub —<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|

## <a name="common-string-comparison-methods-in-net"></a>Typowe metody porównywania ciągów w .NET

W poniższych sekcjach opisano metody, które są najczęściej używane do porównywania ciągów.

### <a name="stringcompare"></a>Funkcja String.Compare

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Jako operacja najbardziej centralna do interpretacji ciągu, wszystkie wystąpienia tych wywołań metody powinny być badane w celu ustalenia, czy ciągi powinny być interpretowane zgodnie z bieżącą kulturą lub odłączone od kultury (symbolicznie). Zazwyczaj jest to ten ostatni, <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> a zamiast tego należy użyć porównania.

Klasa, <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> która jest zwracana przez <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> właściwość, zawiera również <xref:System.Globalization.CompareInfo.Compare%2A> metodę, która zapewnia dużą liczbę opcji dopasowania (porządkowe, ignorując biały znak, ignorując typ kana i tak dalej) za pomocą wyliczenia <xref:System.Globalization.CompareOptions> flagi.

### <a name="stringcompareto"></a>Funkcja String.CompareTo

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Ta metoda nie oferuje obecnie przeciążenia, <xref:System.StringComparison> które określa typ. Zwykle można przekonwertować tę <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodę na zalecaną formę.

Typy, <xref:System.IComparable> które <xref:System.IComparable%601> implementują i interfejsy implementują tę metodę. Ponieważ nie oferuje opcji parametru, <xref:System.StringComparison> implementowanie typów często pozwalają <xref:System.StringComparer> użytkownikowi określić w ich konstruktora. Poniższy przykład definiuje `FileName` klasę, której konstruktor klasy zawiera <xref:System.StringComparer> parametr. Ten <xref:System.StringComparer> obiekt jest następnie `FileName.CompareTo` używany w metodzie.

[!code-csharp[Conceptual.Strings.BestPractices#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
[!code-vb[Conceptual.Strings.BestPractices#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]

### <a name="stringequals"></a>Funkcja String.Equals

Domyślna <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>interpretacja: .

Klasa <xref:System.String> umożliwia testowanie równości przez wywołanie przeciążenia metody statycznej lub instancji <xref:System.String.Equals%2A> lub za pomocą statycznego operatora równości. Przeciążenia i operator używać porównania porządkowego domyślnie. Jednak nadal zaleca się wywołanie przeciążenia, które <xref:System.StringComparison> jawnie określa typ, nawet jeśli chcesz wykonać porównanie porządkowe; ułatwia to wyszukiwanie kodu dla interpretacji określonego ciągu.

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper i String.ToLower

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Należy zachować ostrożność podczas korzystania z tych metod, ponieważ wymuszanie ciągu do wielkich lub małych liter jest często używany jako mała normalizacja do porównywania ciągów niezależnie od przypadku. Jeśli tak, należy rozważyć użycie porównania bez uwzględniania wielkości liter.

Dostępne <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> są również metody i metody. <xref:System.String.ToUpperInvariant%2A>jest standardowym sposobem normalizacji obudowy. Porównania dokonane <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> przy użyciu są behawioralnie skład <xref:System.String.ToUpperInvariant%2A> dwóch wywołań: wywołanie <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>obu argumentów ciągu i robi porównanie przy użyciu .

Przeciążenia są również dostępne do konwersji na wielkie i małe litery <xref:System.Globalization.CultureInfo> w określonej kulturze, przekazując obiekt, który reprezentuje tę kulturę do metody.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper i Char.ToLower

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Metody te działają podobnie <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType> do i metod opisanych w poprzedniej sekcji.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith i String.EndsWith

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Domyślnie obie te metody wykonać porównanie zależne od kultury.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf i String.LastIndexOf

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Brak spójności w jaki sposób domyślne przeciążenia tych metod wykonać porównania. Wszystkie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> i metody, <xref:System.Char> które zawierają parametr wykonać porównanie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> porządkowe, ale domyślne i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, które zawierają <xref:System.String> parametr wykonać porównanie zależne od kultury.

Jeśli wywołasz <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> lub metody i przekazać go ciąg, aby zlokalizować w bieżącym wystąpieniu, zaleca <xref:System.StringComparison> się wywołanie przeciążenie, które jawnie określa typ. Przeciążenia, które <xref:System.Char> zawierają argument nie pozwalają <xref:System.StringComparison> na określenie typu.

## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody pośrednio wykonywane porównywania ciągów

Niektóre metody bez ciągu, które mają porównanie <xref:System.StringComparer> ciągów jako operacja centralna, używają tego typu. Klasa <xref:System.StringComparer> zawiera sześć właściwości statycznych, które zwracają <xref:System.StringComparer> wystąpienia, których <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody wykonują następujące typy porównań ciągów:

- Porównania ciągów zależne od kultury przy użyciu bieżącej kultury. Ten <xref:System.StringComparer> obiekt jest <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> zwracany przez właściwość.
- Porównania bez uwzględniania wielkości liter przy użyciu bieżącej kultury. Ten <xref:System.StringComparer> obiekt jest <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> zwracany przez właściwość.
- Porównania niewrażliwe na kulturę przy użyciu reguł porównywania wyrazów kultury niezmiennej. Ten <xref:System.StringComparer> obiekt jest <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> zwracany przez właściwość.
- Porównania bez uwzględniania wielkości liter i niewrażliwe na kulturę przy użyciu reguł porównywania wyrazów kultury niezmiennej. Ten <xref:System.StringComparer> obiekt jest <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> zwracany przez właściwość.
- Porównanie porządkowe. Ten <xref:System.StringComparer> obiekt jest <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> zwracany przez właściwość.
- Porównanie porządkowe bez uwzględniania wielkości liter. Ten <xref:System.StringComparer> obiekt jest <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> zwracany przez właściwość.

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort i Array.BinarySearch

Domyślna <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>interpretacja: .

Podczas przechowywania jakichkolwiek danych w kolekcji lub odczytu utrwalonych danych z pliku lub bazy danych do kolekcji, przełączanie bieżącej kultury może unieważnić invariants w kolekcji. Metoda <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> zakłada, że elementy w tablicy, które mają być przeszukiwane są już sortowane. Aby posortować dowolny element <xref:System.Array.Sort%2A?displayProperty=nameWithType> ciągu <xref:System.String.Compare%2A?displayProperty=nameWithType> w tablicy, metoda wywołuje metodę, aby uporządkować poszczególne elementy. Za pomocą porównywarki zależne od kultury może być niebezpieczne, jeśli kultura zmienia się między czasem, że tablica jest sortowane i jego zawartość są przeszukiwane. Na przykład w poniższym kodzie magazynu i pobierania działają na modułu `Thread.CurrentThread.CurrentCulture` porównującego, który jest dostarczany niejawnie przez właściwość. Jeśli kultura może się zmieniać `StoreNames` `DoesNameExist`między wywołaniami do i , a zwłaszcza jeśli zawartość tablicy są zachowywane gdzieś między dwoma wywołaniami metody, wyszukiwanie binarne może zakończyć się niepowodzeniem.

[!code-csharp[Conceptual.Strings.BestPractices#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]

Zalecana odmiana pojawia się w poniższym przykładzie, który używa tej samej metody porównania porządkowego (niewrażliwe na kulturę) zarówno do sortowania i wyszukiwania tablicy. Kod zmiany jest odzwierciedlany w `Line A` wierszach oznaczonych etykietą i `Line B` w dwóch przykładach.

[!code-csharp[Conceptual.Strings.BestPractices#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
[!code-vb[Conceptual.Strings.BestPractices#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]

Jeśli te dane są zachowywane i przenoszone między kulturami, a sortowanie jest <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>używane do prezentowania tych danych użytkownikowi, można rozważyć użycie , który działa lingwistycznie dla lepszych danych wyjściowych użytkownika, ale nie ma wpływu na zmiany w kulturze. Poniższy przykład modyfikuje dwa poprzednie przykłady, aby użyć kultury niezmiennej do sortowania i wyszukiwania tablicy.

[!code-csharp[Conceptual.Strings.BestPractices#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
[!code-vb[Conceptual.Strings.BestPractices#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]

### <a name="collections-example-hashtable-constructor"></a>Przykład kolekcji: Konstruktor hashtable

Ciągi mieszania stanowi drugi przykład operacji, na którą ma wpływ sposób porównywania ciągów.

Poniższy przykład wystąpienia <xref:System.Collections.Hashtable> obiektu, przekazując <xref:System.StringComparer> go obiekt, <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> który jest zwracany przez właściwość. Ponieważ <xref:System.StringComparer> klasa, która jest <xref:System.StringComparer> pochodną <xref:System.Collections.IEqualityComparer> implementuje <xref:System.Collections.IEqualityComparer.GetHashCode%2A> interfejs, jego metoda jest używana do obliczania kodu mieszania ciągów w tabeli mieszania.

[!code-csharp[Conceptual.Strings.BestPractices#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
[!code-vb[Conceptual.Strings.BestPractices#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]

## <a name="displaying-and-persisting-formatted-data"></a>Wyświetlanie i utrwalanie sformatowanych danych

Podczas wyświetlania użytkownikom danych innych niż ciąg, takich jak liczby, daty i godziny, sformatować je przy użyciu ustawień kulturowych użytkownika. Domyślnie wszystkie następujące elementy używają bieżącej kultury wątku w operacjach formatowania:

- Interpolowane ciągi obsługiwane przez kompilatory [języka C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic.](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- Operacje łączenia ciągów, które używają operatorów łączenia Języka <xref:System.String.Concat%2A?displayProperty=nameWithType> [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) lub Visual [Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) lub które bezpośrednio wywołują metodę.
- Metoda. <xref:System.String.Format%2A?displayProperty=nameWithType>
- Metody `ToString` typów liczbowych oraz typy daty i godziny.

Aby jawnie określić, że ciąg powinien być sformatowany przy użyciu konwencji wyznaczonej kultury lub [kultury niezmiennej,](xref:System.Globalization.CultureInfo.InvariantCulture)można wykonać następujące czynności:

- Podczas korzystania <xref:System.String.Format%2A?displayProperty=nameWithType> `ToString` z i metody, wywołać `provider` przeciążenie, <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>który ma <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> parametr, <xref:System.Globalization.CultureInfo> takich jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> lub , i <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> przekazać go właściwość, wystąpienie, które reprezentuje żądaną kulturę lub właściwości.

- Dla łączenia ciągów nie zezwalaj kompilatorowi na wykonywanie żadnych niejawnych konwersji. Zamiast tego należy wykonać jawną `ToString` konwersję, `provider` wywołując przeciążenie, które ma parametr. Na przykład kompilator niejawnie używa bieżącej <xref:System.Double> kultury podczas konwertowania wartości na ciąg w następującym kodzie Języka C#:

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  Zamiast tego można jawnie określić kulturę, której konwencje formatowania <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> są używane w konwersji, wywołując metodę, tak jak wykonuje to następujący kod Języka C#:

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- W przypadku interpolacji ciągu zamiast przypisywania interpolowanego ciągu do <xref:System.String> <xref:System.FormattableString>instancji należy przypisać go do pliku . Następnie można wywołać jego <xref:System.FormattableString.ToString?displayProperty=nameWithType> metoda produkcji ciąg wynik, który odzwierciedla konwencje bieżącej kultury lub można wywołać <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodę do tworzenia ciąg wynik, który odzwierciedla konwencje określonej kultury. Można również przekazać ciąg formattable do <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metody statycznej do produkcji ciąg wynik, który odzwierciedla konwencje kultury niezmienne. To podejście pokazano w poniższym przykładzie. (Dane wyjściowe z przykładu odzwierciedla bieżącą kulturę en-US.)

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

Można utrwalić dane bez ciągu jako dane binarne lub jako sformatowane dane. Jeśli zdecydujesz się zapisać go jako sformatowane dane, należy wywołać przeciążenie metody formatowania, który zawiera `provider` parametr i przekazać go <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Kultura niezmienna zapewnia spójny format dla sformatowanych danych, który jest niezależny od kultury i maszyny. Z drugiej strony utrwalanie danych, które są sformatowane przy użyciu kultur innych niż kultura niezmienna ma szereg ograniczeń:

- Dane mogą być bezużyteczne, jeśli jest pobierany w systemie, który ma inną kulturę lub jeśli użytkownik bieżącego systemu zmienia bieżącą kulturę i próbuje pobrać dane.
- Właściwości kultury na określonym komputerze mogą różnić się od wartości standardowych. W dowolnym momencie użytkownik może dostosować ustawienia wyświetlania wrażliwe na kulturę. Z tego powodu sformatowane dane zapisane w systemie mogą nie być czytelne po dostosowaniu ustawień kulturowych przez użytkownika. Przenośność sformatowanych danych na komputerach może być jeszcze bardziej ograniczona.
- Międzynarodowe, regionalne lub krajowe standardy regulujące formatowanie liczb lub dat i godzin zmieniają się w czasie, a zmiany te są włączane do aktualizacji systemu operacyjnego Windows. Po zmianie konwencji formatowania dane sformatowane przy użyciu poprzednich konwencji mogą stać się nieczytelne.

Poniższy przykład ilustruje ograniczoną przenośność, która wynika z używania formatowania zależnego od kultury do utrwalania danych. W przykładzie zapisuje tablicę wartości daty i godziny do pliku. Są one sformatowane przy użyciu konwencji kultury angielskiej (Stany Zjednoczone). Po aplikacji zmienia bieżącą kulturę wątku na francuski (Szwajcaria), próbuje odczytać zapisane wartości przy użyciu konwencji formatowania bieżącej kultury. Próba odczytu dwóch elementów danych <xref:System.FormatException> zgłasza wyjątek, a tablica dat zawiera teraz <xref:System.DateTime.MinValue>dwa niepoprawne elementy, które są równe .

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Jednak jeśli właściwość zostanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zastąpiona <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> w <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>wywołaniach do i , utrwalone dane daty i godziny zostanie pomyślnie przywrócone, jak pokazano na poniższym wyjściu:

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```
