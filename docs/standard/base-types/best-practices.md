---
title: Najlepsze rozwiązania dotyczące wyrażeń regularnych w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 271042fc167331def9e427cd4fc8b510e5f2f32e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925727"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Najlepsze rozwiązania dotyczące wyrażeń regularnych w programie .NET
<a name="top"></a> Aparat wyrażeń regularnych w programie .NET jest to zaawansowane, w pełni funkcjonalne narzędzie, które przetwarza tekst oparty na dopasowania do wzorca zamiast porównywać i dopasowywać tekst dosłownie. W większości przypadków dopasowanie do wzorca przebiega szybko i skutecznie. Jednak w niektórych przypadkach aparat wyrażeń regularnych może okazać się bardzo wolny. W skrajnych przypadkach może nawet pozornie przestać odpowiadać, ponieważ przetwarza stosunkowo mało danych wejściowych w ciągu kilku godzin lub nawet dni.  
  
 W tym temacie przedstawiono kilka najlepszych rozwiązań, które deweloperzy mogą zaadoptować w celu osiągnięcia optymalnej wydajności przetwarzania własnych wyrażeń regularnych. Ten temat zawiera następujące sekcje:  
  
-   [Należy wziąć pod uwagę źródło danych wejściowych](#InputSource)  
  
-   [Obsługa tworzenia wystąpienia obiektu odpowiednio](#ObjectInstantiation)  
  
-   [Przejmowanie kontroli nad wycofywaniem](#Backtracking)  
  
-   [Używanie wartości limitu czasu](#Timeouts)  
  
-   [Przechwytywanie tylko wtedy, gdy jest to konieczne](#Capture)  
  
-   [Tematy pokrewne](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>Wybieranie źródła danych wejściowych  
 Ogólnie rzecz biorąc, wyrażenia regularne mogą przyjmować dwa typy danych wejściowych: ograniczone i nieograniczone. Ograniczone dane wejściowe to tekst pochodzący ze znanego lub wiarygodnego źródła, który ma wstępnie zdefiniowany format. Nieograniczone dane wejściowe to tekst pochodzący z niepewnego źródła, takiego jak użytkownik sieci web, mogący nie mieć wstępnie zdefiniowanego lub oczekiwanego formatu.  
  
 Wzorce wyrażeń regularnych są zazwyczaj pisane w taki sposób, aby dopasowywały prawidłowe dane wejściowe. Oznacza to, że deweloperzy sprawdzają tekst, który chcą dopasować, a następnie piszą wzorzec wyrażenia regularnego, który mu odpowiada. Następnie deweloperzy określają, czy wzorzec wymaga poprawek, testując go dla wielu prawidłowych elementów wejściowych. Gdy wzorzec pasuje do wszystkich przypuszczalnie prawidłowych danych wejściowych, jest uznawany za gotowy do produkcji i można go dołączyć do wydawanej aplikacji. Dzięki temu wzorzec wyrażenia regularnego nadaje się do dopasowywania ograniczonych danych wejściowych. Jednak nie powoduje to, że wzorzec ten jest odpowiedni do porównywania nieograniczonych danych wejściowych.  
  
 Aby dopasować nieograniczone dane wejściowe, wyrażenie regularne musi być w stanie efektywnie obsłużyć trzy rodzaje tekstu:  
  
-   Tekst, który pasuje do wzorca wyrażenia regularnego.  
  
-   Tekst, który nie pasuje do wzorca wyrażenia regularnego.  
  
-   Tekst, który prawie pasuje do wzorca wyrażenia regularnego.  
  
 Ostatni typ tekstu jest szczególnie problematyczny dla wyrażeń regularnych, które zostały napisane do obsługi ograniczonych danych wejściowych. Jeśli wyrażenie regularne opiera się również na rozbudowane [wycofywania](../../../docs/standard/base-types/backtracking-in-regular-expressions.md), aparat wyrażeń regularnych poświęcić dużej ilość czasu (w niektórych przypadkach wiele godzin lub dni) przetwarzanie pozornie niewielkiej tekstu.  
  
> [!WARNING]
>  W poniższym przykładzie użyto wyrażenia regularnego, które jest podatne na nadmierne korzystanie z wycofywania, przez co istnieje duże prawdopodobieństwo odrzucenia prawidłowych adresów e-mail. Nie należy stosować go w procedurze weryfikacji adresów e-mail. Jeżeli potrzebujesz wyrażenia regularnego weryfikującego adresy e-mail, zobacz [jak: Verify that Strings Are in Valid Email Format](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
 Rozważmy na przykład bardzo często używane, ale wyjątkowo problematyczne wyrażenie regularne służące do weryfikacji aliasów adresów e-mail. Wyrażenie regularne `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` są zapisywane do przetworzenia, co jest uważany za prawidłowy adres e-mail, która składa się z znaku alfanumerycznego, w którym następuje zero lub więcej znaków, które mogą być alfanumeryczne, kropki lub łączniki. Wyrażenie regularne musi być zakończone znakiem alfanumerycznym. Jednak, jak pokazuje poniższy przykład, mimo że wyrażenie regularne obsługuje z łatwością prawidłowe dane wejściowe, jego wydajność jest nieefektywna podczas przetwarzania niemal prawidłowych danych wejściowych.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 Dane wyjściowe z przykładu pokazują, że aparat wyrażeń regularnych przetwarza prawidłowe aliasy adresów e-mail w prawie takim samym interwale czasowym, niezależnie od ich długości. Z drugiej strony, kiedy niemal prawidłowy adres e-mail zawiera więcej niż pięć znaków, dla każdego dodatkowego znaku w ciągu czas przetwarzania w przybliżeniu wzrasta dwukrotnie. Oznacza to, że przetwarzanie niemal prawidłowego 28-znakowego ciągu będzie trwało prawie godzinę, a przetwarzanie niemal prawidłowego 33-znakowego ciągu będzie trwało prawie cały dzień.  
  
 Ponieważ wyrażenie regularne zostało opracowane z uwzględnieniem wyłącznie formatu danych wejściowych do dopasowania, wyrażenie regularne nie uwzględnia danych wejściowych, które nie pasują do wzorca. To z kolei może spowodować, że nieograniczone dane wejściowe, które niemal odpowiadają wzorcowi wyrażenia regularnego, znacząco obniżą wydajność.  
  
 Aby rozwiązać ten problem, można wykonać następujące czynności:  
  
-   Podczas tworzenia wzorca należy uwzględnić wpływ wycofywania na wydajność aparatu wyrażeń regularnych, szczególnie jeśli wyrażenie regularne jest przeznaczone do przetwarzania nieograniczonych danych wejściowych. Aby uzyskać więcej informacji, zobacz [zająć przejmowanie kontroli nad wycofywaniem](#Backtracking) sekcji.  
  
-   Wyrażenie regularne należy dokładnie sprawdzić, używając nieprawidłowych i niemal prawidłowych danych wejściowych, a także prawidłowych danych wejściowych. Aby losowo wygenerować danych wejściowych dla poszczególnych wyrażeń regularnych, możesz użyć [Rex](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/), czyli narzędzia do eksplorowania wyrażeń regularnych przez firmę Microsoft Research.  
  
 [Powrót do początku](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>Odpowiednia obsługa tworzenia wystąpienia obiektu  
 Serce. Model obiektów wyrażeń regularnych w sieci jest <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> klasy, która reprezentuje aparat wyrażeń regularnych. Często pojedynczy czynnik największy, który ma wpływ na wydajność wyrażeń regularnych jest sposobu, w którym <xref:System.Text.RegularExpressions.Regex> używany jest silnik. Definiowanie wyrażenia regularnego polega na ścisłym sprzęganiu aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Czy Proces sprzęgania, czy dotyczy tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu przez przekazanie jego konstruktorowi wzorca wyrażenia regularnego lub wywołanie metody statycznej przez przekazanie jej wzorca wyrażenia regularnego wraz z ciągiem do analizy, jest z konieczności kosztowny.  
  
> [!NOTE]
>  Aby uzyskać bardziej szczegółowe omówienie jego wpływu użycia zinterpretowanych i skompilowanych wyrażeń regularnych na wydajność, zobacz [Optymalizowanie wydajności wyrażeń regularnych, część II: biorąc przejmowanie kontroli nad wycofywaniem](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) w blogu zespołu BCL.  
  
 Można sprzęgnąć aparat wyrażeń regularnych z konkretnym wzorcem wyrażenia regularnego, a następnie użyć aparatu, aby dopasować tekst na kilka sposobów:  
  
-   Można wywołać statyczną metodę dopasowania do wzorca, taką jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. Nie wymaga to tworzenia wystąpienia obiektu wyrażenia regularnego.  
  
-   Można utworzyć wystąpienie <xref:System.Text.RegularExpressions.Regex> obiektu i wywołać metodę wystąpienia do dopasowania do wzorca interpretowanego wyrażenia regularnego. Jest to domyślna metoda do tworzenia powiązania aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Powoduje to podczas <xref:System.Text.RegularExpressions.Regex> jest tworzone wystąpienie obiektu bez `options` argument, który zawiera <xref:System.Text.RegularExpressions.RegexOptions.Compiled> flagi.  
  
-   Można utworzyć wystąpienie <xref:System.Text.RegularExpressions.Regex> obiektu i wywołać metodę wystąpienia do dopasowania do wzorca skompilowanego wyrażenia regularnego. Obiekty wyrażeń regularnych reprezentują skompilowane wzorce, gdy <xref:System.Text.RegularExpressions.Regex> jest tworzone wystąpienie obiektu za pomocą `options` argument, który zawiera <xref:System.Text.RegularExpressions.RegexOptions.Compiled> flagi.  
  
-   Można utworzyć specjalny <xref:System.Text.RegularExpressions.Regex> obiekt, który jest ściśle sprzężony z określonym wzorcem wyrażenia regularnego, skompilować go i zapisać go do niezależnego zestawu. Można to zrobić, wywołując <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody.  
  
 Sposób, w jaki są wywoływane metody dopasowywania wyrażeń regularnych, może mieć znaczący wpływ na działanie aplikacji. W poniższych sekcjach omówiono, kiedy używać wywołań metod statycznych oraz interpretowanych i skompilowanych wyrażeń regularnych, aby poprawić wydajność aplikacji.  
  
> [!IMPORTANT]
>  Jeśli to samo wyrażenie regularne jest używane wielokrotnie w wywołaniach metod lub jeśli obiekty wyrażeń regularnych są często używane w aplikacji, sposób wywoływania metody (statyczny, interpretowany, skompilowany) znacząco wpływa na wydajność.  
  
### <a name="static-regular-expressions"></a>Statyczne wyrażenia regularne  
 Statyczne metody wyrażeń regularnych są zalecane jako alternatywa dla wielokrotnego tworzenia wystąpienia obiektu wyrażenia regularnego z tym samym wyrażeniem regularnym. W przeciwieństwie do wzorców wyrażeń regularnych używanych przez obiekty wyrażeń regularnych, kody operacji lub skompilowana składnia języka Microsoft Intermediate Language (MSIL) z wzorców używanych w wywołaniach metod wystąpień są buforowane wewnętrznie przez aparat wyrażeń regularnych.  
  
 Na przykład program obsługi zdarzeń często wywołuje inną metodę do weryfikacji danych wejściowych użytkownika. Znajduje to odzwierciedlenie w poniższym kodzie, w którym <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zdarzeń jest używane do wywołania metody o nazwie `IsValidCurrency`, która sprawdza, czy użytkownik wprowadził symbol waluty, a następnie co najmniej jedną cyfrę dziesiętną.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 Bardzo nieefektywną implementację metody `IsValidCurrency` pokazano w poniższym przykładzie. Należy zauważyć, że każde wywołanie metody ponowne tworzy wystąpienie <xref:System.Text.RegularExpressions.Regex> obiektu tego samego wzorca. To z kolei oznacza, że wzorzec wyrażenia regularnego należy kompilować podczas każdego wywołania metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 Należy zamienić ten nieefektywny kod za pomocą wywołania statycznej <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody. Eliminuje to potrzebę tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu każdorazowo, aby wywołać metodę dopasowania do wzorca i umożliwia aparatowi wyrażeń regularnych pobieranie skompilowanych wersji wyrażeń regularnych ze swojej pamięci podręcznej.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 Domyślnie buforowanych jest piętnaście ostatnio używanych statycznych wzorców wyrażeń regularnych. W przypadku aplikacji wymagających większej liczby buforowanych statycznych wyrażeń regularnych można dostosować rozmiar pamięci podręcznej, ustawiając <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> właściwości.  
  
 Wyrażenie regularne `\p{Sc}+\s*\d+` używanego w tym przykładzie, sprawdza, czy ciąg wejściowy zawiera symbol waluty i przynajmniej jedną cyfrę dziesiętną. Definicję wzorca pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}+`|Dopasowanie do jednego lub większej liczby symboli Unicode w kategorii Waluta.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretowane a Skompilowane wyrażenia regularne  
 Wzorce wyrażeń regularnych, które nie są powiązane aparatem wyrażeń regularnych przez specyfikację <xref:System.Text.RegularExpressions.RegexOptions.Compiled> opcji są interpretowane. Kiedy tworzone jest wystąpienie obiektu wyrażenia regularnego, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji. Gdy wywoływana jest metoda wystąpienia, kody operacji są konwertowane do języka MSIL i wykonywane przy użyciu kompilatora JIT. Podobnie, kiedy jest wywoływania statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji i przechowuje je w pamięci podręcznej. Następnie konwertuje te kody operacji na język MSIL, dzięki czemu mogą zostać wykonane za pomocą kompilatora JIT. Interpretowane wyrażenia regularne ograniczają czas uruchamiania kosztem wolniejszego czasu wykonania. Z tego powodu najlepiej stosować je, kiedy wyrażenie regularne jest używane w małej liczbie wywołań metod lub jeśli dokładna liczba wywołań metod wyrażenia regularnego jest nieznana, ale oczekuje się, że będzie mała. Wraz ze wzrostem liczby wywołań metod przyrost wydajności związany ze skróceniem czasu uruchamiania jest coraz mniejszy wskutek wolniejszego wykonywania.  
  
 Wzorce wyrażeń regularnych, które są powiązane aparatem wyrażeń regularnych przez specyfikację <xref:System.Text.RegularExpressions.RegexOptions.Compiled> opcji są kompilowane. Oznacza to, że kiedy jest tworzone wystąpienie obiektu wyrażenia regularnego lub kiedy jest wywoływana statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na pośredni zestaw kodów operacji, które następnie konwertuje na język MSIL. Kiedy metoda jest wywoływana, kompilator JIT wykonuje kod języka MSIL. W przeciwieństwie do interpretowanych wyrażeń regularnych, skompilowane wyrażenia regularne wydłużają czas uruchamiania, ale wykonanie pojedynczych metod dopasowania do wzorca jest szybsze. W rezultacie korzyści w zakresie wydajności wynikające z kompilowania wyrażeń regularnych rosną proporcjonalnie do liczby wywoływanych metod wyrażeń regularnych.  
  
 Podsumowując, zaleca się używać interpretowanych wyrażeń regularnych, kiedy stosunkowo rzadko są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Zaleca się używać skompilowanych wyrażeń regularnych, kiedy stosunkowo często są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Dokładny próg, przy którym mniejsza szybkość wykonywania interpretowanych wyrażeń regularnych przewyższa korzyści z redukcji czasu uruchamiania, lub próg, przy którym wolniejsze uruchamianie skompilowanych wyrażeń regularnych przewyższa korzyści z większej szybkości wykonywania, jest trudny do określenia. Zależy to od wielu czynników, w tym od złożoności wyrażenia regularnego i konkretnych danych, które to wyrażenie przetwarza. Aby określić, czy interpretowane czy kompilowane najlepszą wydajność dla konkretnego scenariusza aplikacji oferują wyrażenia regularne, można użyć <xref:System.Diagnostics.Stopwatch> klasy w celu porównania ich czasów wykonania.  
  
 W poniższym przykładzie porównano wydajność skompilowanych i interpretowanych wyrażeń regularnych podczas czytania pierwszych dziesięciu zdań i podczas czytania wszystkich zdań powieści theodore'a dreisera *The Financier*. Dane wyjściowe z przykładu pokazują, że przy zaledwie dziesięciu wywołaniach metod dopasowania wyrażenia regularnego interpretowane wyrażenie regularne oferuje lepszą wydajność niż skompilowane wyrażenie regularne. Jednak skompilowane wyrażenie regularne oferuje lepszą wydajność dla dużej liczby wywołań (w tym przypadku ponad 13 000).  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 Definicję wzorca wyrażenia regularnego użytych w tym przykładzie `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|<code>(\r?\n)&#124;,?\s)</code>|Dopasowanie do zera lub jednego znaku powrotu karetki, po którym występuje znak nowego wiersza, albo do zera lub jednego przecinka, po którym występuje znak odstępu.|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Dopasowanie do zera lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym występuje zero albo jeden znak powrotu karetki i znak nowego wiersza lub zero albo jeden przecinek, po którym następuje znak odstępu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`[.?:;!]`|Dopasowanie do kropki, znaku zapytania, dwukropka, średnika lub wykrzyknika.|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>Wyrażenia regularne: kompilowane do zestawu.  
 .NET umożliwia także utworzenie zestawu zawierającego skompilowane wyrażenia regularne. Przenosi to czynnik wpływający na wydajność kompilowania wyrażeń regularnych z czasu wykonywania na czas projektowania. Jednak to także wiąże się z dodatkową pracą: konieczne jest zdefiniowanie wyrażane regularnych z wyprzedzeniem i skompilowanie ich do zestawu. Kompilator może następnie odwołać się do tego zestawu podczas kompilowania kodu źródłowego, który używa wyrażeń regularnych zestawu. Każde skompilowane wyrażenie regularne w zestawie jest reprezentowane przez klasę, która pochodzi od klasy <xref:System.Text.RegularExpressions.Regex>.  
  
 Aby skompilować wyrażenia regularne do zestawu, należy wywołać <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> metody i przekazać do niej tablicę z <xref:System.Text.RegularExpressions.RegexCompilationInfo> obiektami, które reprezentują wyrażenia regularne, które mają być skompilowane, oraz <xref:System.Reflection.AssemblyName> obiektu, który zawiera informacje o zestawie, który ma być utworzony.  
  
 Zaleca się, aby kompilować wyrażenia regularne do zestawu w następujących sytuacjach:  
  
-   Jeśli jesteś deweloperem składników, który chce utworzyć bibliotekę wyrażeń regularnych do wielokrotnego użytku.  
  
-   Jeśli oczekujesz, że metody dopasowania do wzorca wyrażenia regularnego będą wywoływane nieokreśloną liczbę razy — od jednego lub dwóch wywołań do kilku tysięcy wywołań. W przeciwieństwie do skompilowanych lub interpretowanych wyrażeń regularnych, wyrażenia regularne, które są kompilowane do oddzielnych zestawów, oferują stałą wydajność bez względu na liczbę wywołań metody.  
  
 Jeśli skompilowane wyrażenia regularne są używane w celu optymalizacji wydajności, nie należy używać odbicia w celu utworzenia zestawu, załadowania aparatu wyrażeń regularnych i wykonania jego metod dopasowania do wzorca. Wymaga to unikania dynamicznego kompilowania wzorców wyrażeń regularnych i określenia wszelkich opcji dopasowania do wzorca (np. z uwzględnieniem wielkości liter) w czasie tworzenia zestawu. Wymaga to również odseparowania kodu, który tworzy zestaw, od kodu, który używa wyrażenia regularnego.  
  
 W poniższym przykładzie pokazano, w jaki sposób utworzyć zestaw zawierający skompilowane wyrażenie regularne. Tworzy zestaw o nazwie `RegexLib.dll` z pojedynczą klasą wyrażeń regularnych, `SentencePattern`, który zawiera wyrażenia regularnego dopasowującego zdania wzorzec używany w [interpretowane vs. Skompilowanych wyrażeń regularnych](#Interpreted) sekcji.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 Kiedy przykładu jest kompilowany do pliku wykonywalnego i uruchamiany, tworzy zestaw o nazwie `RegexLib.dll`. Wyrażenie regularne jest reprezentowane przez klasę o nazwie `Utilities.RegularExpressions.SentencePattern` , jest tworzony na podstawie <xref:System.Text.RegularExpressions.Regex>. W poniższym przykładzie użyto następnie skompilowane wyrażenie regularne, aby wyodrębnić zdania z powieści theodore'a dreisera *The Financier*.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [Powrót do początku](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>Przejmowanie kontroli nad wycofywaniem  
 Zazwyczaj aparat wyrażeń regularnych używa progresji liniowej do przechodzenia przez ciąg wejściowy i porównywania go ze wzorcem wyrażenia regularnego. Jednak gdy nieokreślone Kwantyfikatory, takie jak `*`, `+`, i `?` są używane we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych może dać częściowo udanych dopasowań i powrócić do wcześniej zapisanego stanu w celu wyszukiwania udanych dopasowań dla całego wzorca. Proces ten jest znany pod nazwą wycofywania.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących wycofywania, zobacz [szczegóły zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) i [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Aby uzyskać szczegółowe omówienie wycofywania, zobacz [Optymalizowanie wydajności wyrażeń regularnych, część II: biorąc przejmowanie kontroli nad wycofywaniem](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) w blogu zespołu BCL.  
  
 Obsługa wycofywania daje wyrażeniom regularnym duże możliwości i elastyczność. Dodatkowo odpowiedzialność za kontrolowanie operacji aparatu wyrażeń regularnych spada na deweloperów wyrażeń regularnych. Ponieważ deweloperzy często nie są tego świadomi, błędne użycie wycofywania lub nadmierne poleganie na wycofywaniu często odgrywa najbardziej znaczącą rolę w zmniejszeniu wydajności wyrażeń regularnych. W scenariuszu najgorszego przypadku czas wykonywania może podwajać się dla każdego dodatkowego znaku w ciągu wejściowym. W rzeczywistości przy nadmiernym wykorzystaniu wycofywania łatwo jest stworzyć programowy odpowiednik pętli nieskończonej, jeżeli dane wejściowe niemal pasują do wzorca wyrażenia regularnego; przetwarzanie relatywnie krótkiego ciągu wejściowego może zająć aparatowi wyrażeń regularnych kilka godzin, a nawet dni.  
  
 Często efektem użycia wycofywania jest obniżenie wydajności w aplikacjach, mimo że używanie wycofywania nie jest niezbędne dla dopasowania. Na przykład, wyrażenie regularne `\b\p{Lu}\w*\b` dopasowuje wszystkie wyrazy rozpoczynające się od wielkiej litery, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-|-|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\p{Lu}`|Dopasowanie do dowolnej wielkiej litery.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Ponieważ granica wyrazu nie jest tym samym co znak słowa ani jego podzbiorem, nie ma możliwości, aby aparat wyrażeń regularnych przekroczył granicę wyrazu podczas dopasowywania znaków słowa. Oznacza to, że dla tego wyrażenia regularnego wycofywanie może nigdy nie przyczynić się do sukcesu jakiegokolwiek dopasowania, może za to obniżyć wydajność, ponieważ aparat wyrażeń regularnych musi zapisać swój stan podczas każdego pomyślnie zakończonego wstępnego dopasowania znaku słowa.  
  
 Jeśli okaże się, że używanie wycofywania nie jest konieczne, można ją wyłączyć, używając `(?>subexpression)` element języka. W poniższym przykładzie jest analizowana składnia ciągu wejściowego przy użyciu dwóch wyrażeń regularnych. Pierwsza strona, `\b\p{Lu}\w*\b`, jest używane wycofywanie. Druga Strona, `\b\p{Lu}(?>\w*)\b`, wycofywanie jest wyłączone. Jak wynika z przykładu, oba wyrażenia regularne dały ten sam wynik.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 W wielu przypadkach wycofywanie jest niezbędne dla dopasowania wzorca wyrażenia regularnego do tekstu wejściowego. Należy pamiętać, że nadmierne używanie wycofywania może poważnie obniżyć wydajność i stworzyć wrażanie, ze aplikacja przestała odpowiadać. W szczególności ma to miejsce, kiedy kwantyfikatory są zagnieżdżane i tekst, który pasuje do zewnętrznego podwyrażenia, jest podzbiorem tekstu, który pasuje do wewnętrznego podwyrażenia.  
  
> [!WARNING]
>  Oprócz unikania nadmiernego wykorzystania wycofywania należy używać funkcji limitu czasu, aby zagwarantować, że nadmierne używanie wycofywania nie obniży poważnie wydajności wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [użycie wartości limitu czasu](#Timeouts) sekcji.  
  
 Na przykład wzorzec wyrażenia regularnego `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` jest przeznaczony do dopasowania numeru części, która składa się z co najmniej jeden znak alfanumeryczny. Jakiekolwiek dodatkowe znaki mogą być znakami alfanumerycznymi, łącznikami, podkreśleniami lub kropkami, ale ostatni znak musi być alfanumeryczny. Znak dolara przerywa numer części. W niektórych przypadkach ten wzorzec wyrażenia regularnego może cechować bardzo słabą wydajnością, ponieważ Kwantyfikatory są zagnieżdżone, a Podwyrażenie `[0-9A-Z]` jest podzbiorem podwyrażenia `[-.\w]*`.  
  
 W takich przypadkach można zoptymalizować wydajność wyrażenia regularnego, usuwając zagnieżdżone kwantyfikatory i zastępując zewnętrzne podwyrażenie asercją wyprzedzającą lub wsteczną o zerowej szerokości. Asercje wyprzedzające i wsteczne są kotwicami; nie przesuwają wskaźnika w ciągu wejściowym, ale „patrzą” do przodu lub wstecz, aby sprawdzić, czy określony warunek został spełniony. Na przykład, wyrażenie regularne numeru części można inaczej jako `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Definicję tego wzorca wyrażenia regularnego pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
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
  
 Język wyrażeń regularnych w programie .NET zawiera następujące elementy języka, które można użyć w celu wyeliminowania kwantyfikatorów zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
|Element języka|Opis|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|Pozytywna asercja wyprzedzająca o zerowej szerokości. Spoglądanie w przód od aktualnej pozycji, aby określić, czy `subexpression` pasuje do ciągu wejściowego.|  
|`(?!` `subexpression` `)`|Negatywna asercja wyprzedzająca o zerowej szerokości. Spoglądanie w przód od aktualnej pozycji, aby określić, czy `subexpression` nie pasuje do ciągu wejściowego.|  
|`(?<=` `subexpression` `)`|Pozytywna asercja wsteczna o zerowej szerokości. Patrzy aktualnej pozycji, aby określić, czy `subexpression` pasuje do ciągu wejściowego.|  
|`(?<!` `subexpression` `)`|Negatywna asercja wsteczna o zerowej szerokości. Patrzy aktualnej pozycji, aby określić, czy `subexpression` nie pasuje do ciągu wejściowego.|  
  
 [Powrót do początku](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>Używanie wartości limitu czasu  
 Jeśli wyrażenie regularne przetwarza dane wejściowe, które niemal pasują do wzorca wyrażenia regularnego, często może nadmiernie używać wycofywania, co znacznie wpływa na wydajność. Oprócz dokładnego rozważenia użycia wycofywania i przetestowania wyrażenia regularnego pod kątem niemal dopasowanych danych wejściowych, zawsze należy ustawić wartość limitu czasu, aby zagwarantować, że efekt nadmiernego używania wycofywania, jeżeli wystąpi, będzie jak najmniejszy.  
  
 Interwał limitu czasu wyrażenia regularnego określa czas, przez jaki aparat wyrażeń regularnych będzie szukał pojedynczego dopasowania, zanim zostanie przekroczony limit czasu. Domyślny interwał limitu czasu wynosi <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, co oznacza, że wyrażenie regularne będzie nie przekraczają limit czasu. Można zastąpić tę wartość i zdefiniować interwał limitu czasu w następujący sposób:  
  
-   Ustawiając wartość limitu czasu podczas tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktora.  
  
-   Przez wywołanie statycznego dopasowania do wzorca metody, takie jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, który zawiera `matchTimeout` parametru.  
  
-   Dla skompilowanych wyrażeń regularnych, które są tworzone przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metoda, przez wywołanie konstruktora, który ma parametr typu <xref:System.TimeSpan>.  
  
 Jeśli zdefiniowano interwał limitu czasu i dopasowanie nie znajduje się na końcu tego interwału, metoda wyrażenia regularnego zgłasza <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> wyjątku. W obsłudze wyjątków można wybrać ponowienie próby dopasowywania z dłuższym interwałem limitu czasu, zrezygnować z próby dopasowania i założyć, że dopasowanie nie istnieje, lub zrezygnować z próby dopasowania i zarejestrować informacje o wyjątku na potrzeby późniejszej analizy.  
  
 W poniższym przykładzie zdefiniowano `GetWordData` metody, która tworzy wystąpienie wyrażenia regularnego z interwałem limitu czasu 350 milisekund i oblicza liczbę wyrazów oraz średnią liczbę znaków w słowie w dokumencie tekstowym. Jeśli upłynie limit czasu operacji dopasowywania, interwał limitu czasu jest zwiększana o 350 milisekund i <xref:System.Text.RegularExpressions.Regex> obiektu jest tworzone ponownie. Jeżeli nowy interwał limitu czasu przekroczy 1 sekundę, metoda ponownie zgłosi wyjątek do obiektu wywołującego.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [Powrót do początku](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>Przechwytywanie tylko wtedy, gdy jest to konieczne  
 Wyrażenia regularne w .NET obsługują szereg konstrukcji grupujących, które pozwalają grupować wzorzec wyrażenia regularnego do co najmniej jeden podwyrażenia. Konstrukcje grupowania najczęściej używanych w języku wyrażeń regularnych platformy .NET są `(` *Podwyrażenie*`)`, która definiuje numerowaną grupę przechwytywania, i `(?<` *nazwa* `>` *Podwyrażenie*`)`, która definiuje nazwaną grupę przechwytywania. Konstrukcje grupujące są niezbędne do tworzenia odwołań wstecznych i do definiowania podwyrażeń, do których jest stosowany kwantyfikator.  
  
 Jednak zastosowanie tych elementów języka jest kosztowne. Powodują one <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości, które ma zostać wypełniony przy użyciu najnowszych, ostatnio nienazwanymi i nazwanymi przechwytywaniami, a jeżeli pojedyncza konstrukcja grupująca ma przechwyconych wiele podciągów w ciągu wejściowym, wypełniają one również <xref:System.Text.RegularExpressions.CaptureCollection>obiektu zwróconego przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości określonej grupy przechwytywania z wieloma <xref:System.Text.RegularExpressions.Capture> obiektów.  
  
 Często konstrukcje grupujące są używane w wyrażeniach regularnych tylko po to, aby można było zastosować do nich kwantyfikatory, i grupy przechwytywane przez te podwyrażenia nie są następnie używane. Na przykład, wyrażenie regularne `\b(\w+[;,]?\s?)+[.?!]` jest przeznaczona do pobierania całe zdanie. W poniższej tabeli opisano elementy języka, w tym wzorcu wyrażenia regularnego i ich wpływ na <xref:System.Text.RegularExpressions.Match> obiektu <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`[;,]?`|Dopasowanie do zera lub jednego przecinka albo średnika.|  
|`\s?`|Dopasowuje zero lub jeden znak odstępu.|  
|`(\w+[;,]?\s?)+`|Dopasowanie do jednego lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym następuje opcjonalny przecinek lub średnik, po którym następuje opcjonalny znak odstępu. To definiuje pierwszą grupę przechwytywania, która jest niezbędna, aby kombinacja wielu znaków słowa (tzn. słowo), po których następuje opcjonalny znak interpunkcyjny, była powtarzana do momentu, kiedy aparat wyrażeń regularnych osiągnie koniec zdania.|  
|`[.?!]`|Dopasowanie do kropki, znaku zapytania lub wykrzyknika.|  
  
 Jak w poniższym przykładzie pokazano, gdy zostanie znalezione dopasowanie, oba <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> obiekty są wypełnione przechwytywaniami z dopasowania. W takim przypadku grupę przechwyconą `(\w+[;,]?\s?)` istnieje tak, aby `+` kwantyfikator można zastosować, co umożliwia wzorzec wyrażenia regularnego do dopasowania każdego wyrazu w zdaniu. W przeciwnym razie dopasowanie nastąpi dla ostatniego wyrazu w zdaniu.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 Kiedy używa się podwyrażeń tylko w celu zastosowania do nich kwantyfikatorów, a przechwytywany tekst nie jest ważny, należy wyłączyć przechwytywanie grup. Na przykład `(?:subexpression)` element języka zapobiega przechwytywaniu dopasowanych podciągów przez grupę, do której jest stosowany. W poniższym przykładzie wzorzec wyrażenia regularnego z poprzedniego przykładu jest zmieniana na `\b(?:\w+[;,]?\s?)+[.?!]`. Dane wyjściowe pokazują, że uniemożliwia aparat wyrażeń regularnych wypełnianie <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 Przechwytywanie można wyłączyć na jeden z poniższych sposobów:  
  
-   Użyj `(?:subexpression)` element języka. Ten element zapobiega przechwytywaniu dopasowanych podciągów w grupie, do której jest stosowany. Nie wyłącza przechwytywania podciągów w grupach zagnieżdżonych.  
  
-   Użyj <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> opcji. Wyłącza wszystkie nienazwane lub niejawne przechwytywania we wzorcu wyrażenia regularnego. Tej opcji tylko podciągi, które pasują do nazwanych grup zdefiniowanych za `(?<name>subexpression)` elementu języka, które mogą być przechwytywane. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Flagi mogą być przekazywane do `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub `options` parametru <xref:System.Text.RegularExpressions.Regex> statycznej metody dopasowania.  
  
-   Użyj `n` opcji `(?imnsx)` element języka. Powoduje to wyłączenie wszystkich nienazwanych lub niejawnych przechwytywań od miejsca we wzorcu wyrażenia regularnego, w którym znajduje się ten element. Przechwytywania są wyłączone do końca wzorca lub do momentu `(-n)` opcji umożliwiającej nienazwane lub niejawne przechwytywania. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).  
  
-   Użyj `n` opcji `(?imnsx:subexpression)` element języka. Ta opcja wyłącza wszystkie nienazwane lub niejawne przechwytywania w obiekcie `subexpression`. Przechwytywania przez jakiekolwiek nienazwane lub niejawne zagnieżdżone grupy przechwytywania również są wyłączone.  
  
 [Powrót do początku](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Analizuje implementację aparatu wyrażeń regularnych programu .NET. W tym temacie skupiono się na elastyczności wyrażeń regularnych i wyjaśniono odpowiedzialność deweloperów za zapewnienie wydajnych i niezawodnych operacji aparatu wyrażeń regularnych.|  
|[Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Informacje, co to jest wycofywanie i jak wpływa na wydajność wyrażeń regularnych oraz analiza elementów języka, które dostarczają alternatywy dla wycofywania.|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|W tym artykule opisano elementy języka wyrażeń regularnych w programie .NET i zawiera łącza do szczegółowej dokumentacji każdego elementu języka.|
