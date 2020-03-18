---
title: Najważniejsze wskazówki dotyczące wyrażeń regularnych w .NET
description: Dowiedz się, jak tworzyć wydajne, skuteczne wyrażenia regularne w .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
ms.openlocfilehash: 9b09f5a2505888c6154a58a3512c94c51f89295b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124425"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Najważniejsze wskazówki dotyczące wyrażeń regularnych w .NET

Aparat wyrażeń regularnych w .NET jest potężnym, w pełni funkcjonalnym narzędziem, które przetwarza tekst na podstawie dopasowania wzorca, a nie na porównywaniu i dopasowywaniu tekstu literału. W większości przypadków dopasowanie do wzorca przebiega szybko i skutecznie. Jednak w niektórych przypadkach aparat wyrażeń regularnych może okazać się bardzo wolny. W skrajnych przypadkach może nawet pozornie przestać odpowiadać, ponieważ przetwarza stosunkowo mało danych wejściowych w ciągu kilku godzin lub nawet dni.

W tym temacie przedstawiono kilka najlepszych rozwiązań, które deweloperzy mogą zaadoptować w celu osiągnięcia optymalnej wydajności przetwarzania własnych wyrażeń regularnych.

## <a name="consider-the-input-source"></a>Należy wziąć pod uwagę źródło danych wejściowych

Ogólnie rzecz biorąc, wyrażenia regularne mogą przyjmować dwa typy danych wejściowych: ograniczone i nieograniczone. Ograniczone dane wejściowe to tekst pochodzący ze znanego lub wiarygodnego źródła, który ma wstępnie zdefiniowany format. Nieograniczone dane wejściowe to tekst pochodzący z niepewnego źródła, takiego jak użytkownik sieci web, mogący nie mieć wstępnie zdefiniowanego lub oczekiwanego formatu.

Wzorce wyrażeń regularnych są zazwyczaj pisane w taki sposób, aby dopasowywały prawidłowe dane wejściowe. Oznacza to, że deweloperzy sprawdzają tekst, który chcą dopasować, a następnie piszą wzorzec wyrażenia regularnego, który mu odpowiada. Następnie deweloperzy określają, czy wzorzec wymaga poprawek, testując go dla wielu prawidłowych elementów wejściowych. Gdy wzorzec pasuje do wszystkich przypuszczalnie prawidłowych danych wejściowych, jest uznawany za gotowy do produkcji i można go dołączyć do wydawanej aplikacji. Dzięki temu wzorzec wyrażenia regularnego nadaje się do dopasowywania ograniczonych danych wejściowych. Jednak nie powoduje to, że wzorzec ten jest odpowiedni do porównywania nieograniczonych danych wejściowych.

Aby dopasować nieograniczone dane wejściowe, wyrażenie regularne musi być w stanie efektywnie obsłużyć trzy rodzaje tekstu:

- Tekst, który pasuje do wzorca wyrażenia regularnego.

- Tekst, który nie pasuje do wzorca wyrażenia regularnego.

- Tekst, który prawie pasuje do wzorca wyrażenia regularnego.

Ostatni typ tekstu jest szczególnie problematyczny dla wyrażeń regularnych, które zostały napisane do obsługi ograniczonych danych wejściowych. Jeśli to wyrażenie regularne opiera się również na rozległym [wycofywaniu,](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)aparat wyrażeń regularnych może spędzić nadmierną ilość czasu (w niektórych przypadkach wiele godzin lub dni) przetwarzając pozornie nieszkodliwy tekst.

> [!WARNING]
> W poniższym przykładzie użyto wyrażenia regularnego, które jest podatne na nadmierne korzystanie z wycofywania, przez co istnieje duże prawdopodobieństwo odrzucenia prawidłowych adresów e-mail. Nie należy stosować go w procedurze weryfikacji adresów e-mail. Jeśli chcesz wyrażenie regularne, które sprawdza poprawność adresów e-mail, zobacz [Jak: Sprawdź, czy ciągi są w prawidłowym formacie wiadomości e-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

Rozważmy na przykład bardzo często używane, ale wyjątkowo problematyczne wyrażenie regularne służące do weryfikacji aliasów adresów e-mail. Wyrażenie `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` regularne jest zapisywane w celu przetworzenia prawidłowego adresu e-mail, który składa się ze znaku alfanumerycznego, po którym następuje zero lub więcej znaków, które mogą być alfanumeryczne, kropki lub łączniki. Wyrażenie regularne musi być zakończone znakiem alfanumerycznym. Jednak, jak pokazuje poniższy przykład, mimo że wyrażenie regularne obsługuje z łatwością prawidłowe dane wejściowe, jego wydajność jest nieefektywna podczas przetwarzania niemal prawidłowych danych wejściowych.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]

Dane wyjściowe z przykładu pokazują, że aparat wyrażeń regularnych przetwarza prawidłowe aliasy adresów e-mail w prawie takim samym interwale czasowym, niezależnie od ich długości. Z drugiej strony, kiedy niemal prawidłowy adres e-mail zawiera więcej niż pięć znaków, dla każdego dodatkowego znaku w ciągu czas przetwarzania w przybliżeniu wzrasta dwukrotnie. Oznacza to, że przetwarzanie niemal prawidłowego 28-znakowego ciągu będzie trwało prawie godzinę, a przetwarzanie niemal prawidłowego 33-znakowego ciągu będzie trwało prawie cały dzień.

Ponieważ wyrażenie regularne zostało opracowane z uwzględnieniem wyłącznie formatu danych wejściowych do dopasowania, wyrażenie regularne nie uwzględnia danych wejściowych, które nie pasują do wzorca. To z kolei może spowodować, że nieograniczone dane wejściowe, które niemal odpowiadają wzorcowi wyrażenia regularnego, znacząco obniżą wydajność.

Aby rozwiązać ten problem, można wykonać następujące czynności:

- Podczas tworzenia wzorca należy uwzględnić wpływ wycofywania na wydajność aparatu wyrażeń regularnych, szczególnie jeśli wyrażenie regularne jest przeznaczone do przetwarzania nieograniczonych danych wejściowych. Aby uzyskać więcej informacji, zobacz sekcję [Przejmij wycofywanie.](#take-charge-of-backtracking)

- Wyrażenie regularne należy dokładnie sprawdzić, używając nieprawidłowych i niemal prawidłowych danych wejściowych, a także prawidłowych danych wejściowych. Aby losowo wygenerować dane wejściowe dla określonego wyrażenia regularnego, można użyć [rexa](https://www.microsoft.com/research/project/rex-regular-expression-exploration/), który jest narzędziem do eksploracji wyrażeń regularnych firmy Microsoft Research.

## <a name="handle-object-instantiation-appropriately"></a>Odpowiednie obsługa wystąpienia obiektu

W samym sercu . Model obiektu wyrażenia regularnego NET <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> jest klasą, która reprezentuje aparat wyrażeń regularnych. Często największym czynnikiem wpływającym na wydajność wyrażeń <xref:System.Text.RegularExpressions.Regex> regularnych jest sposób, w jaki aparat jest używany. Definiowanie wyrażenia regularnego polega na ścisłym sprzęganiu aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Ten proces sprzężenia, czy polega <xref:System.Text.RegularExpressions.Regex> na tworzeniu obiektu przez przekazywanie jego konstruktora wzorca wyrażenia regularnego lub wywołanie metody statycznej, przekazując mu wzorzec wyrażenia regularnego wraz z ciągiem do analizy, jest z konieczności kosztowne jeden.

> [!NOTE]
> Aby uzyskać bardziej szczegółowe omówienie wpływu na wydajność przy użyciu interpretowanych i skompilowanych wyrażeń regularnych, zobacz [Optymalizacja wydajności wyrażenia regularnego, część II: Przejęcie wycofywania](https://docs.microsoft.com/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) w blogu zespołu BCL.

Można sprzęgnąć aparat wyrażeń regularnych z konkretnym wzorcem wyrażenia regularnego, a następnie użyć aparatu, aby dopasować tekst na kilka sposobów:

- Można wywołać metodę dopasowywania <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>wzorców statycznych, na przykład . Nie wymaga to tworzenia wystąpienia obiektu wyrażenia regularnego.

- Można utworzyć wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex> i wywołać metodę dopasowywania wzorców wystąpienia wyrażenia regularnego interpretowanego. Jest to domyślna metoda do tworzenia powiązania aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Wynik jest <xref:System.Text.RegularExpressions.Regex> wynikiem, gdy obiekt jest `options` tworzony bez <xref:System.Text.RegularExpressions.RegexOptions.Compiled> argumentu, który zawiera flagę.

- Można utworzyć wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex> i wywołać metodę dopasowywania wzorców wystąpienia skompilowanego wyrażenia regularnego. Obiekty wyrażenia regularnego reprezentują skompilowane wzorce, <xref:System.Text.RegularExpressions.Regex> gdy `options` obiekt jest <xref:System.Text.RegularExpressions.RegexOptions.Compiled> tworzony z argumentem zawierającym flagę.

- Można utworzyć obiekt specjalnego <xref:System.Text.RegularExpressions.Regex> przeznaczenia, który jest ściśle sprzężona z określonego wzorca wyrażenia regularnego, skompilować go i zapisać go do zestawu autonomicznego. Można to zrobić, <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> wywołując metodę.

Sposób, w jaki są wywoływane metody dopasowywania wyrażeń regularnych, może mieć znaczący wpływ na działanie aplikacji. W poniższych sekcjach omówiono, kiedy używać wywołań metod statycznych oraz interpretowanych i skompilowanych wyrażeń regularnych, aby poprawić wydajność aplikacji.

> [!IMPORTANT]
> Jeśli to samo wyrażenie regularne jest używane wielokrotnie w wywołaniach metod lub jeśli obiekty wyrażeń regularnych są często używane w aplikacji, sposób wywoływania metody (statyczny, interpretowany, skompilowany) znacząco wpływa na wydajność.

### <a name="static-regular-expressions"></a>Statyczne wyrażenia regularne

Statyczne metody wyrażeń regularnych są zalecane jako alternatywa dla wielokrotnego tworzenia wystąpienia obiektu wyrażenia regularnego z tym samym wyrażeniem regularnym. W przeciwieństwie do wzorców wyrażeń regularnych używanych przez obiekty wyrażeń regularnych kody operacji lub skompilowany język pośredni firmy Microsoft (MSIL) z wzorców używanych w wywołaniach metod statycznych są buforowane wewnętrznie przez aparat wyrażeń regularnych.

Na przykład program obsługi zdarzeń często wywołuje inną metodę do weryfikacji danych wejściowych użytkownika. Jest to odzwierciedlone w poniższym <xref:System.Windows.Forms.Button> kodzie, <xref:System.Windows.Forms.Control.Click> w którym zdarzenie formantu jest używane do wywołania metody o nazwie `IsValidCurrency`, która sprawdza, czy użytkownik wprowadził symbol waluty, po którym następuje co najmniej jedna cyfra dziesiętna.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]

Bardzo nieefektywne implementacji `IsValidCurrency` metody przedstawiono w poniższym przykładzie. Należy zauważyć, że każde wywołanie <xref:System.Text.RegularExpressions.Regex> metody reinstantiates obiektu o tym samym wzorcu. To z kolei oznacza, że wzorzec wyrażenia regularnego należy kompilować podczas każdego wywołania metody.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]

Należy zastąpić ten nieefektywny kod <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> wywołaniem metody statycznej. Eliminuje to konieczność tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu za każdym razem, gdy chcesz wywołać metodę dopasowywania wzorców i umożliwia aparatowi wyrażeń regularnych pobieranie skompilowanej wersji wyrażenia regularnego z jego pamięci podręcznej.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]

Domyślnie buforowanych jest piętnaście ostatnio używanych statycznych wzorców wyrażeń regularnych. W przypadku aplikacji, które wymagają większej liczby buforowanych statycznych wyrażeń <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> regularnych, rozmiar pamięci podręcznej można dostosować, ustawiając właściwość.

Wyrażenie `\p{Sc}+\s*\d+` regularne używane w tym przykładzie sprawdza, czy ciąg wejściowy składa się z symbolu waluty i co najmniej jednej cyfry dziesiętnej. Definicję wzorca pokazano w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`\p{Sc}+`|Dopasowanie do jednego lub większej liczby symboli Unicode w kategorii Waluta.|
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|

### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretowane a skompilowane wyrażenia regularne

Wzorce wyrażeń regularnych, które nie są <xref:System.Text.RegularExpressions.RegexOptions.Compiled> powiązane z aparatem wyrażeń regularnych za pomocą specyfikacji opcji są interpretowane. Kiedy tworzone jest wystąpienie obiektu wyrażenia regularnego, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji. Gdy wywoływana jest metoda wystąpienia, kody operacji są konwertowane do języka MSIL i wykonywane przy użyciu kompilatora JIT. Podobnie, kiedy jest wywoływania statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji i przechowuje je w pamięci podręcznej. Następnie konwertuje te kody operacji na język MSIL, dzięki czemu mogą zostać wykonane za pomocą kompilatora JIT. Interpretowane wyrażenia regularne ograniczają czas uruchamiania kosztem wolniejszego czasu wykonania. Z tego powodu najlepiej stosować je, kiedy wyrażenie regularne jest używane w małej liczbie wywołań metod lub jeśli dokładna liczba wywołań metod wyrażenia regularnego jest nieznana, ale oczekuje się, że będzie mała. Wraz ze wzrostem liczby wywołań metod przyrost wydajności związany ze skróceniem czasu uruchamiania jest coraz mniejszy wskutek wolniejszego wykonywania.

Wzorce wyrażenia regularnego, które są powiązane z <xref:System.Text.RegularExpressions.RegexOptions.Compiled> aparatem wyrażeń regularnych za pośrednictwem specyfikacji opcji są kompilowane. Oznacza to, że kiedy jest tworzone wystąpienie obiektu wyrażenia regularnego lub kiedy jest wywoływana statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na pośredni zestaw kodów operacji, które następnie konwertuje na język MSIL. Kiedy metoda jest wywoływana, kompilator JIT wykonuje kod języka MSIL. W przeciwieństwie do interpretowanych wyrażeń regularnych, skompilowane wyrażenia regularne wydłużają czas uruchamiania, ale wykonanie pojedynczych metod dopasowania do wzorca jest szybsze. W rezultacie korzyści w zakresie wydajności wynikające z kompilowania wyrażeń regularnych rosną proporcjonalnie do liczby wywoływanych metod wyrażeń regularnych.

Podsumowując, zaleca się używać interpretowanych wyrażeń regularnych, kiedy stosunkowo rzadko są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Zaleca się używać skompilowanych wyrażeń regularnych, kiedy stosunkowo często są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Dokładny próg, przy którym mniejsza szybkość wykonywania interpretowanych wyrażeń regularnych przewyższa korzyści z redukcji czasu uruchamiania, lub próg, przy którym wolniejsze uruchamianie skompilowanych wyrażeń regularnych przewyższa korzyści z większej szybkości wykonywania, jest trudny do określenia. Zależy to od wielu czynników, w tym od złożoności wyrażenia regularnego i konkretnych danych, które to wyrażenie przetwarza. Aby ustalić, czy interpretowane lub skompilowane wyrażenia regularne oferują najlepszą <xref:System.Diagnostics.Stopwatch> wydajność dla danego scenariusza aplikacji, można użyć klasy do porównania ich czas wykonania.

Poniższy przykład porównuje wydajność skompilowanych i interpretowanych wyrażeń regularnych podczas czytania pierwszych dziesięciu zdań i podczas czytania wszystkich zdań w tekście *Finansisty*Theodore'a Dreisera . Dane wyjściowe z przykładu pokazują, że przy zaledwie dziesięciu wywołaniach metod dopasowania wyrażenia regularnego interpretowane wyrażenie regularne oferuje lepszą wydajność niż skompilowane wyrażenie regularne. Jednak skompilowane wyrażenie regularne oferuje lepszą wydajność dla dużej liczby wywołań (w tym przypadku ponad 13 000).

[!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]

Wzorzec wyrażenia regularnego `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`użyty w przykładzie , jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|
|<code>(\r?\n)&#124;,?\s)</code>|Dopasowanie do zera lub jednego znaku powrotu karetki, po którym występuje znak nowego wiersza, albo do zera lub jednego przecinka, po którym występuje znak odstępu.|
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Dopasowanie do zera lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym występuje zero albo jeden znak powrotu karetki i znak nowego wiersza lub zero albo jeden przecinek, po którym następuje znak odstępu.|
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|
|`[.?:;!]`|Dopasowanie do kropki, znaku zapytania, dwukropka, średnika lub wykrzyknika.|

### <a name="regular-expressions-compiled-to-an-assembly"></a>Wyrażenia regularne: Skompilowane do zestawu

.NET umożliwia również tworzenie zestawu, który zawiera skompilowane wyrażenia regularne. Przenosi to czynnik wpływający na wydajność kompilowania wyrażeń regularnych z czasu wykonywania na czas projektowania. Jednak to także wiąże się z dodatkową pracą: konieczne jest zdefiniowanie wyrażane regularnych z wyprzedzeniem i skompilowanie ich do zestawu. Kompilator może następnie odwołać się do tego zestawu podczas kompilowania kodu źródłowego, który używa wyrażeń regularnych zestawu. Każde skompilowane wyrażenie regularne w zestawie jest reprezentowane <xref:System.Text.RegularExpressions.Regex>przez klasę, która pochodzi od .

Aby skompilować wyrażenia regularne do zestawu, należy wywołać <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexCompilationInfo> metodę i przekazać ją tablicy obiektów, <xref:System.Reflection.AssemblyName> które reprezentują wyrażenia regularne do skompilowania i obiekt, który zawiera informacje o zestaw, który ma zostać utworzony.

Zaleca się, aby kompilować wyrażenia regularne do zestawu w następujących sytuacjach:

- Jeśli jesteś deweloperem składników, który chce utworzyć bibliotekę wyrażeń regularnych do wielokrotnego użytku.

- Jeśli oczekujesz, że metody dopasowania do wzorca wyrażenia regularnego będą wywoływane nieokreśloną liczbę razy — od jednego lub dwóch wywołań do kilku tysięcy wywołań. W przeciwieństwie do skompilowanych lub interpretowanych wyrażeń regularnych, wyrażenia regularne, które są kompilowane do oddzielnych zestawów, oferują stałą wydajność bez względu na liczbę wywołań metody.

Jeśli skompilowane wyrażenia regularne są używane w celu optymalizacji wydajności, nie należy używać odbicia w celu utworzenia zestawu, załadowania aparatu wyrażeń regularnych i wykonania jego metod dopasowania do wzorca. Wymaga to unikania dynamicznego kompilowania wzorców wyrażeń regularnych i określenia wszelkich opcji dopasowania do wzorca (np. z uwzględnieniem wielkości liter) w czasie tworzenia zestawu. Wymaga to również odseparowania kodu, który tworzy zestaw, od kodu, który używa wyrażenia regularnego.

W poniższym przykładzie pokazano, w jaki sposób utworzyć zestaw zawierający skompilowane wyrażenie regularne. Tworzy zestaw o `RegexLib.dll` nazwie z jednej `SentencePattern`klasy wyrażenia regularnego, który zawiera pasujące do zdania wzorzec wyrażenia regularnego używane w [interpretowane vs skompilowane wyrażenia regularne](#interpreted-vs-compiled-regular-expressions) sekcji.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]

Gdy przykład jest kompilowany do pliku wykonywalnego `RegexLib.dll`i uruchomić, tworzy zestaw o nazwie . Wyrażenie regularne jest reprezentowane przez `Utilities.RegularExpressions.SentencePattern` klasę o nazwie, która pochodzi od <xref:System.Text.RegularExpressions.Regex>. W poniższym przykładzie użyto następnie skompilowanego wyrażenia regularnego do wyodrębnienia zdań z tekstu finansisty Theodore'a *Dreisera.*

[!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]

## <a name="take-charge-of-backtracking"></a>Przejmij kontrolę nad wycofywaniem

Zazwyczaj aparat wyrażeń regularnych używa progresji liniowej do przechodzenia przez ciąg wejściowy i porównywania go ze wzorcem wyrażenia regularnego. Jednak gdy nieokreślone kwantyfikatory, takie jak `*`, `+`, i `?` są używane w wzorcu wyrażeń regularnych, aparat wyrażeń regularnych może zrezygnować z części udanych dopasowań częściowych i powrócić do wcześniej zapisanego stanu w celu wyszukania pomyślnego dopasowania dla całego wzorca. Proces ten jest znany pod nazwą wycofywania.

> [!NOTE]
> Aby uzyskać więcej informacji na temat wycofywania, zobacz [Szczegóły zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) i [wycofywania](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Aby uzyskać szczegółowe informacje na temat wycofywania, zobacz [Optymalizacja wydajności wyrażenia regularnego, część II: Przejęcie wycofywania](https://docs.microsoft.com/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) w blogu zespołu BCL.

Obsługa wycofywania daje wyrażeniom regularnym duże możliwości i elastyczność. Dodatkowo odpowiedzialność za kontrolowanie operacji aparatu wyrażeń regularnych spada na deweloperów wyrażeń regularnych. Ponieważ deweloperzy często nie są tego świadomi, błędne użycie wycofywania lub nadmierne poleganie na wycofywaniu często odgrywa najbardziej znaczącą rolę w zmniejszeniu wydajności wyrażeń regularnych. W scenariuszu najgorszego przypadku czas wykonywania może podwajać się dla każdego dodatkowego znaku w ciągu wejściowym. W rzeczywistości przy nadmiernym wykorzystaniu wycofywania łatwo jest stworzyć programowy odpowiednik pętli nieskończonej, jeżeli dane wejściowe niemal pasują do wzorca wyrażenia regularnego; przetwarzanie relatywnie krótkiego ciągu wejściowego może zająć aparatowi wyrażeń regularnych kilka godzin, a nawet dni.

Często efektem użycia wycofywania jest obniżenie wydajności w aplikacjach, mimo że używanie wycofywania nie jest niezbędne dla dopasowania. Na przykład wyrażenie `\b\p{Lu}\w*\b` regularne pasuje do wszystkich wyrazów, które zaczynają się od znaku wielkich liter, jak pokazano w poniższej tabeli.

|Wzorce|Opis|
|-|-|
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
|`\p{Lu}`|Dopasowanie do dowolnej wielkiej litery.|
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|
|`\b`|Kończy dopasowanie na granicy wyrazu.|

Ponieważ granica wyrazu nie jest tym samym co znak słowa ani jego podzbiorem, nie ma możliwości, aby aparat wyrażeń regularnych przekroczył granicę wyrazu podczas dopasowywania znaków słowa. Oznacza to, że dla tego wyrażenia regularnego wycofywanie może nigdy nie przyczynić się do sukcesu jakiegokolwiek dopasowania, może za to obniżyć wydajność, ponieważ aparat wyrażeń regularnych musi zapisać swój stan podczas każdego pomyślnie zakończonego wstępnego dopasowania znaku słowa.

Jeśli okaże się, że wycofywanie nie jest konieczne, można go wyłączyć przy użyciu elementu `(?>subexpression)` języka, znany jako grupy atomowej. W poniższym przykładzie jest analizowana składnia ciągu wejściowego przy użyciu dwóch wyrażeń regularnych. Pierwszy, `\b\p{Lu}\w*\b`opiera się na wycofywanie. Drugi , `\b\p{Lu}(?>\w*)\b`wyłącza wycofywanie. Jak wynika z przykładu, oba wyrażenia regularne dały ten sam wynik.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]

W wielu przypadkach wycofywanie jest niezbędne dla dopasowania wzorca wyrażenia regularnego do tekstu wejściowego. Należy pamiętać, że nadmierne używanie wycofywania może poważnie obniżyć wydajność i stworzyć wrażanie, ze aplikacja przestała odpowiadać. W szczególności ma to miejsce, kiedy kwantyfikatory są zagnieżdżane i tekst, który pasuje do zewnętrznego podwyrażenia, jest podzbiorem tekstu, który pasuje do wewnętrznego podwyrażenia.

> [!WARNING]
> Oprócz unikania nadmiernego wykorzystania wycofywania należy używać funkcji limitu czasu, aby zagwarantować, że nadmierne używanie wycofywania nie obniży poważnie wydajności wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [sekcję Użyj wartości czasu.](#use-time-out-values)

Na przykład wzorzec `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` wyrażenia regularnego jest przeznaczony do dopasowania numeru części, który składa się z co najmniej jednego znaku alfanumerycznego. Jakiekolwiek dodatkowe znaki mogą być znakami alfanumerycznymi, łącznikami, podkreśleniami lub kropkami, ale ostatni znak musi być alfanumeryczny. Znak dolara przerywa numer części. W niektórych przypadkach ten wzorzec wyrażenia regularnego może wykazywać bardzo niską `[0-9A-Z]` wydajność, ponieważ kwantyfikatory są zagnieżdżone, a wyrażenie podrzędne jest podzbiorem wyrażenia podrzędnego `[-.\w]*`.

W takich przypadkach można zoptymalizować wydajność wyrażenia regularnego, usuwając zagnieżdżone kwantyfikatory i zastępując zewnętrzne podwyrażenie asercją wyprzedzającą lub wsteczną o zerowej szerokości. Asercje wyprzedzające i wsteczne są kotwicami; nie przesuwają wskaźnika w ciągu wejściowym, ale „patrzą” do przodu lub wstecz, aby sprawdzić, czy określony warunek został spełniony. Na przykład wyrażenie regularne numeru części można `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`przepisać jako . Definicję tego wzorca wyrażenia regularnego pokazano w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|
|`[0-9A-Z]`|Dopasowuje znak alfanumeryczny. Numer części musi zawierać przynajmniej jeden znak.|
|`[-.\w]*`|Dopasowanie do zera lub większej liczby wystąpień dowolnego znaku słowa, łącznika lub kropki.|
|`\$`|Dopasowanie do znaku dolara.|
|`(?<=[0-9A-Z])`|Spoglądanie w przód od kończącego znaku dolara, aby się upewnić, że znak poprzedzający jest alfanumeryczny.|
|`$`|Dopasowywanie kończy się na końcu ciągu wejściowego.|

W poniższym przykładzie pokazano użycie tego wyrażenia regularnego w celu dopasowania tablicy zawierającej możliwe numery części.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack4.cs#11)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack4.vb#11)]

Język wyrażenia regularnego w programie .NET zawiera następujące elementy języka, których można użyć do wyeliminowania kwantyfikatorów zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

|Element języka|Opis|
|----------------------|-----------------|
|`(?=` `subexpression` `)`|Pozytywna asercja wyprzedzająca o zerowej szerokości. Spójrz z wyprzedzeniem bieżącej `subexpression` pozycji, aby ustalić, czy pasuje do ciągu wejściowego.|
|`(?!` `subexpression` `)`|Negatywna asercja wyprzedzająca o zerowej szerokości. Spójrz z wyprzedzeniem bieżącej `subexpression` pozycji, aby ustalić, czy nie pasuje do ciągu wejściowego.|
|`(?<=` `subexpression` `)`|Pozytywna asercja wsteczna o zerowej szerokości. Spójrz za bieżącą pozycję, aby ustalić, czy `subexpression` pasuje do ciągu wejściowego.|
|`(?<!` `subexpression` `)`|Negatywna asercja wsteczna o zerowej szerokości. Spójrz za bieżącą pozycję, aby ustalić, czy `subexpression` nie pasuje do ciągu wejściowego.|

## <a name="use-time-out-values"></a>Używanie wartości czasu

Jeśli wyrażenie regularne przetwarza dane wejściowe, które niemal pasują do wzorca wyrażenia regularnego, często może nadmiernie używać wycofywania, co znacznie wpływa na wydajność. Oprócz dokładnego rozważenia użycia wycofywania i przetestowania wyrażenia regularnego pod kątem niemal dopasowanych danych wejściowych, zawsze należy ustawić wartość limitu czasu, aby zagwarantować, że efekt nadmiernego używania wycofywania, jeżeli wystąpi, będzie jak najmniejszy.

Interwał czasu wyrażenia regularnego definiuje okres czasu, przez który aparat wyrażeń regularnych będzie szukał pojedynczego dopasowania przed uchyliniem czasu. Domyślnym przedziałem czasu <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>jest , co oznacza, że wyrażenie regularne nie będzie uchylić. Można zastąpić tę wartość i zdefiniować przedział czasu w następujący sposób:

- Podając wartość czasu po nakreśleniu wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu przez <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> wywołanie konstruktora.

- Wywołując metodę dopasowywania wzorców statycznych, takich jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, który zawiera `matchTimeout` parametr.

- Dla skompilowanych wyrażeń regularnych, <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> które są tworzone przez wywołanie metody, wywołując konstruktora, który ma parametr typu <xref:System.TimeSpan>.

Jeśli zdefiniowano przedział czasu i dopasowanie nie zostanie znaleziony na końcu tego interwału, <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> metoda wyrażenia regularnego zgłasza wyjątek. W obsłudze wyjątków można wybrać ponowienie próby dopasowywania z dłuższym interwałem limitu czasu, zrezygnować z próby dopasowania i założyć, że dopasowanie nie istnieje, lub zrezygnować z próby dopasowania i zarejestrować informacje o wyjątku na potrzeby późniejszej analizy.

Poniższy przykład definiuje `GetWordData` metodę, która tworzy wyrażenie regularne z interwałem czasu 350 milisekund, aby obliczyć liczbę słów i średnią liczbę znaków w słowie w dokumencie tekstowym. Jeśli uchylił się uchyłowu uzgadnianego czasu <xref:System.Text.RegularExpressions.Regex> operacji, interwał czasu jest zwiększany o 350 milisekund, a obiekt zostanie ponownie uniewinnieny. Jeżeli nowy interwał limitu czasu przekroczy 1 sekundę, metoda ponownie zgłosi wyjątek do obiektu wywołującego.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]

## <a name="capture-only-when-necessary"></a>Przechwytywanie tylko wtedy, gdy jest to konieczne

Wyrażenia regularne w .NET obsługują szereg konstrukcji grupowania, które umożliwiają grupowanie wzorca wyrażeń regularnych w jedno lub więcej wyrażeń podrzędnych. Najczęściej używanymi konstrukcjami grupowania w języku `(`wyrażenia regularnego .NET są *podwyrażenie*`)`, `(?<`które definiuje numerowane grupy przechwytywania i wyrażenie*podrzędne*`)` *nazwy*`>`, które definiuje nazwaną grupę przechwytywania. Konstrukcje grupujące są niezbędne do tworzenia odwołań wstecznych i do definiowania podwyrażeń, do których jest stosowany kwantyfikator.

Jednak zastosowanie tych elementów języka jest kosztowne. Powodują one <xref:System.Text.RegularExpressions.GroupCollection> obiekt zwrócony <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> przez właściwość do wypełnienia z najnowszych nienazwanych lub nazwanych przechwytywań, a jeśli pojedyncza konstrukcja <xref:System.Text.RegularExpressions.CaptureCollection> grupowania przechwyciła wiele podciągów w ciągu wejściowym, wypełniają również obiekt zwrócony przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwość określonej grupy przechwytywania wieloma <xref:System.Text.RegularExpressions.Capture> obiektami.

Często konstrukcje grupujące są używane w wyrażeniach regularnych tylko po to, aby można było zastosować do nich kwantyfikatory, i grupy przechwytywane przez te podwyrażenia nie są następnie używane. Na przykład wyrażenie `\b(\w+[;,]?\s?)+[.?!]` regularne jest przeznaczony do przechwytywania całego zdania. W poniższej tabeli opisano elementy języka w tym <xref:System.Text.RegularExpressions.Match> wzorcu <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> wyrażenia regularnego i ich wpływ na obiekt i kolekcje.

|Wzorce|Opis|
|-------------|-----------------|
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|
|`[;,]?`|Dopasowanie do zera lub jednego przecinka albo średnika.|
|`\s?`|Dopasowuje zero lub jeden znak odstępu.|
|`(\w+[;,]?\s?)+`|Dopasowanie do jednego lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym następuje opcjonalny przecinek lub średnik, po którym następuje opcjonalny znak odstępu. To definiuje pierwszą grupę przechwytywania, która jest niezbędna, aby kombinacja wielu znaków słowa (tzn. słowo), po których następuje opcjonalny znak interpunkcyjny, była powtarzana do momentu, kiedy aparat wyrażeń regularnych osiągnie koniec zdania.|
|`[.?!]`|Dopasowanie do kropki, znaku zapytania lub wykrzyknika.|

Jak pokazano w poniższym przykładzie, po <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.CaptureCollection> znalezieniu dopasowania zarówno i obiekty są wypełniane przechwytów z dopasowania. W takim przypadku istnieje `(\w+[;,]?\s?)` grupa przechwytywania, `+` dzięki czemu można zastosować do niej kwantyfikator, co umożliwia dopasowaniem wzorca wyrażenia regularnego do każdego wyrazu w zdaniu. W przeciwnym razie dopasowanie nastąpi dla ostatniego wyrazu w zdaniu.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]

Kiedy używa się podwyrażeń tylko w celu zastosowania do nich kwantyfikatorów, a przechwytywany tekst nie jest ważny, należy wyłączyć przechwytywanie grup. Na przykład `(?:subexpression)` element języka uniemożliwia grupie, do której ma zastosowanie, przechwytywanie dopasowanych podciągów. W poniższym przykładzie wzorzec wyrażenia regularnego `\b(?:\w+[;,]?\s?)+[.?!]`z poprzedniego przykładu zostanie zmieniony na . Jak pokazuje dane wyjściowe, uniemożliwia aparat wyrażeń regularnych wypełniania <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcje.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]

Przechwytywanie można wyłączyć na jeden z poniższych sposobów:

- Użyj `(?:subexpression)` elementu języka. Ten element zapobiega przechwytywaniu dopasowanych podciągów w grupie, do której jest stosowany. Nie wyłącza przechwytywania podciągów w grupach zagnieżdżonych.

- Użyj <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> tej opcji. Wyłącza wszystkie nienazwane lub niejawne przechwytywania we wzorcu wyrażenia regularnego. Korzystając z tej opcji, można przechwytywać tylko podciągi, które pasują do nazwanych grup zdefiniowanych z elementem `(?<name>subexpression)` języka. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Flaga może być `options` przekazywana <xref:System.Text.RegularExpressions.Regex> do parametru konstruktora klasy lub do parametru `options` statycznej <xref:System.Text.RegularExpressions.Regex> metody dopasowywania.

- Użyj `n` opcji w `(?imnsx)` elemencie języka. Powoduje to wyłączenie wszystkich nienazwanych lub niejawnych przechwytywań od miejsca we wzorcu wyrażenia regularnego, w którym znajduje się ten element. Przechwytywanie są wyłączone do końca wzorca lub do momentu, gdy `(-n)` opcja umożliwia przechwytywanie bez nazwy lub niejawne. Aby uzyskać więcej informacji, zobacz [Różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).

- Użyj `n` opcji w `(?imnsx:subexpression)` elemencie języka. Ta opcja wyłącza wszystkie nienazwane lub `subexpression`niejawne przechwytywania w programie . Przechwytywania przez jakiekolwiek nienazwane lub niejawne zagnieżdżone grupy przechwytywania również są wyłączone.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Szczegóły dotyczące zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Sprawdza implementację aparatu wyrażeń regularnych w .NET. W tym temacie skupiono się na elastyczności wyrażeń regularnych i wyjaśniono odpowiedzialność deweloperów za zapewnienie wydajnych i niezawodnych operacji aparatu wyrażeń regularnych.|
|[Nawracanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Informacje, co to jest wycofywanie i jak wpływa na wydajność wyrażeń regularnych oraz analiza elementów języka, które dostarczają alternatywy dla wycofywania.|
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Opisuje elementy języka wyrażenia regularnego w programie .NET i zawiera łącza do szczegółowej dokumentacji dla każdego elementu języka.|
