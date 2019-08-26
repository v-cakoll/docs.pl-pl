---
title: Najlepsze rozwiązania dotyczące wyrażeń regularnych w programie .NET
description: Dowiedz się, jak tworzyć wydajne, efektywne wyrażenia regularne w programie .NET.
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
ms.custom: serodec18
ms.openlocfilehash: 8d887bb32d1bdd398353d00aba16c2cc8adfcacb
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988819"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Najlepsze rozwiązania dotyczące wyrażeń regularnych w programie .NET
<a name="top"></a>Aparat wyrażeń regularnych w programie .NET to zaawansowane, w pełni funkcjonalne narzędzie, które przetwarza tekst na podstawie dopasowania do wzorców zamiast porównywania i dopasowywania tekstu w postaci literału. W większości przypadków dopasowanie do wzorca przebiega szybko i skutecznie. Jednak w niektórych przypadkach aparat wyrażeń regularnych może okazać się bardzo wolny. W skrajnych przypadkach może nawet pozornie przestać odpowiadać, ponieważ przetwarza stosunkowo mało danych wejściowych w ciągu kilku godzin lub nawet dni.  
  
 W tym temacie przedstawiono kilka najlepszych rozwiązań, które deweloperzy mogą zaadoptować w celu osiągnięcia optymalnej wydajności przetwarzania własnych wyrażeń regularnych. Ten temat zawiera następujące sekcje:  
  
- [Rozważ źródło danych wejściowych](#InputSource)  
  
- [Odpowiednio Obsługuj Tworzenie wystąpienia obiektu](#ObjectInstantiation)  
  
- [Przejmowanie opłaty za wycofywanie](#Backtracking)  
  
- [Użyj wartości limitu czasu](#Timeouts)  
  
- [Przechwyć tylko w razie potrzeby](#Capture)  
  
- [Tematy pokrewne](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>Wybieranie źródła danych wejściowych  
 Ogólnie rzecz biorąc, wyrażenia regularne mogą przyjmować dwa typy danych wejściowych: ograniczone i nieograniczone. Ograniczone dane wejściowe to tekst pochodzący ze znanego lub wiarygodnego źródła, który ma wstępnie zdefiniowany format. Nieograniczone dane wejściowe to tekst pochodzący z niepewnego źródła, takiego jak użytkownik sieci web, mogący nie mieć wstępnie zdefiniowanego lub oczekiwanego formatu.  
  
 Wzorce wyrażeń regularnych są zazwyczaj pisane w taki sposób, aby dopasowywały prawidłowe dane wejściowe. Oznacza to, że deweloperzy sprawdzają tekst, który chcą dopasować, a następnie piszą wzorzec wyrażenia regularnego, który mu odpowiada. Następnie deweloperzy określają, czy wzorzec wymaga poprawek, testując go dla wielu prawidłowych elementów wejściowych. Gdy wzorzec pasuje do wszystkich przypuszczalnie prawidłowych danych wejściowych, jest uznawany za gotowy do produkcji i można go dołączyć do wydawanej aplikacji. Dzięki temu wzorzec wyrażenia regularnego nadaje się do dopasowywania ograniczonych danych wejściowych. Jednak nie powoduje to, że wzorzec ten jest odpowiedni do porównywania nieograniczonych danych wejściowych.  
  
 Aby dopasować nieograniczone dane wejściowe, wyrażenie regularne musi być w stanie efektywnie obsłużyć trzy rodzaje tekstu:  
  
- Tekst, który pasuje do wzorca wyrażenia regularnego.  
  
- Tekst, który nie pasuje do wzorca wyrażenia regularnego.  
  
- Tekst, który prawie pasuje do wzorca wyrażenia regularnego.  
  
 Ostatni typ tekstu jest szczególnie problematyczny dla wyrażeń regularnych, które zostały napisane do obsługi ograniczonych danych wejściowych. Jeśli to wyrażenie regularne opiera się również na rozbudowanej operacji wycofywania, aparat wyrażeń regularnych może poświęcać niezależny czas (w niektórych przypadkach, wiele godzin lub dni) przetwarzanie pozornie niewielkiej ilości tekstu. [](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)  
  
> [!WARNING]
> W poniższym przykładzie użyto wyrażenia regularnego, które jest podatne na nadmierne korzystanie z wycofywania, przez co istnieje duże prawdopodobieństwo odrzucenia prawidłowych adresów e-mail. Nie należy stosować go w procedurze weryfikacji adresów e-mail. Jeśli chcesz, aby wyrażenie regularne, które sprawdza poprawność adresów e-mail [, zapoznaj się z tematem How to: Sprawdź, czy ciągi są w prawidłowym](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)formacie poczty e-mail.  
  
 Rozważmy na przykład bardzo często używane, ale wyjątkowo problematyczne wyrażenie regularne służące do weryfikacji aliasów adresów e-mail. Wyrażenie `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` regularne jest zapisywane w celu przetworzenia, co oznacza, że jest to prawidłowy adres e-mail, który składa się z znaku alfanumerycznego, po którym następuje zero lub więcej znaków, które mogą być alfanumeryczne, kropki lub łączniki. Wyrażenie regularne musi być zakończone znakiem alfanumerycznym. Jednak, jak pokazuje poniższy przykład, mimo że wyrażenie regularne obsługuje z łatwością prawidłowe dane wejściowe, jego wydajność jest nieefektywna podczas przetwarzania niemal prawidłowych danych wejściowych.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 Dane wyjściowe z przykładu pokazują, że aparat wyrażeń regularnych przetwarza prawidłowe aliasy adresów e-mail w prawie takim samym interwale czasowym, niezależnie od ich długości. Z drugiej strony, kiedy niemal prawidłowy adres e-mail zawiera więcej niż pięć znaków, dla każdego dodatkowego znaku w ciągu czas przetwarzania w przybliżeniu wzrasta dwukrotnie. Oznacza to, że przetwarzanie niemal prawidłowego 28-znakowego ciągu będzie trwało prawie godzinę, a przetwarzanie niemal prawidłowego 33-znakowego ciągu będzie trwało prawie cały dzień.  
  
 Ponieważ wyrażenie regularne zostało opracowane z uwzględnieniem wyłącznie formatu danych wejściowych do dopasowania, wyrażenie regularne nie uwzględnia danych wejściowych, które nie pasują do wzorca. To z kolei może spowodować, że nieograniczone dane wejściowe, które niemal odpowiadają wzorcowi wyrażenia regularnego, znacząco obniżą wydajność.  
  
 Aby rozwiązać ten problem, można wykonać następujące czynności:  
  
- Podczas tworzenia wzorca należy uwzględnić wpływ wycofywania na wydajność aparatu wyrażeń regularnych, szczególnie jeśli wyrażenie regularne jest przeznaczone do przetwarzania nieograniczonych danych wejściowych. Aby uzyskać więcej informacji, zobacz sekcję [przejmowanie opłaty za wycofywanie](#Backtracking) .  
  
- Wyrażenie regularne należy dokładnie sprawdzić, używając nieprawidłowych i niemal prawidłowych danych wejściowych, a także prawidłowych danych wejściowych. Aby losowo wygenerować dane wejściowe dla określonego wyrażenia regularnego, możesz użyć [Narzędzia Rex](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/), który jest narzędziem do eksploracji wyrażenia regularnego z Microsoft Research.  
  
 [Powrót do początku](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>Odpowiednia obsługa tworzenia wystąpienia obiektu  
 W serca. Model obiektów wyrażeń regularnych sieci jest <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> klasą, która reprezentuje aparat wyrażeń regularnych. Często jeden największy czynnik wpływający na wydajność wyrażeń regularnych jest sposobem, w <xref:System.Text.RegularExpressions.Regex> jaki aparat jest używany. Definiowanie wyrażenia regularnego polega na ścisłym sprzęganiu aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Ten proces sprzęgania, niezależnie od tego, czy <xref:System.Text.RegularExpressions.Regex> obejmuje utworzenie wystąpienia obiektu przez przekazanie jego konstruktora wzorca wyrażenia regularnego, czy wywołanie metody statycznej przez przekazanie jej wzorca wyrażenia regularnego wraz z ciągiem do analizy, jest z konieczności kosztowna.  
  
> [!NOTE]
> Aby zapoznać się z bardziej szczegółowym omówieniem implikacji wydajności przy użyciu interpretowanych i skompilowanych [wyrażeń regularnych, zobacz Optymalizowanie wydajności wyrażeń regularnych, część II: Przejęcie opłaty](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) za wycofywanie w blogu zespołu BCL.  
  
 Można sprzęgnąć aparat wyrażeń regularnych z konkretnym wzorcem wyrażenia regularnego, a następnie użyć aparatu, aby dopasować tekst na kilka sposobów:  
  
- Można wywołać statyczną metodę dopasowania do wzorca, taką jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. Nie wymaga to tworzenia wystąpienia obiektu wyrażenia regularnego.  
  
- Można utworzyć <xref:System.Text.RegularExpressions.Regex> wystąpienie obiektu i wywołać metodę dopasowania wystąpienia do wzorca interpretowanego wyrażenia regularnego. Jest to domyślna metoda do tworzenia powiązania aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Powstaje po <xref:System.Text.RegularExpressions.Regex> utworzeniu wystąpienia obiektu `options` bez argumentu, który zawiera <xref:System.Text.RegularExpressions.RegexOptions.Compiled> flagę.  
  
- Można utworzyć <xref:System.Text.RegularExpressions.Regex> wystąpienie obiektu i wywołać metodę dopasowania wystąpienia do wzorca skompilowanego wyrażenia regularnego. Obiekty wyrażeń regularnych reprezentują skompilowane wzorce, <xref:System.Text.RegularExpressions.Regex> gdy obiekt jest skonkretyzowany `options` przy użyciu argumentu, który zawiera <xref:System.Text.RegularExpressions.RegexOptions.Compiled> flagę.  
  
- Można utworzyć obiekt specjalnego przeznaczenia <xref:System.Text.RegularExpressions.Regex> , który jest ściśle połączony z określonym wzorcem wyrażenia regularnego, skompilować go i zapisać w autonomicznym zestawie. W tym celu należy wywołać <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodę.  
  
 Sposób, w jaki są wywoływane metody dopasowywania wyrażeń regularnych, może mieć znaczący wpływ na działanie aplikacji. W poniższych sekcjach omówiono, kiedy używać wywołań metod statycznych oraz interpretowanych i skompilowanych wyrażeń regularnych, aby poprawić wydajność aplikacji.  
  
> [!IMPORTANT]
> Jeśli to samo wyrażenie regularne jest używane wielokrotnie w wywołaniach metod lub jeśli obiekty wyrażeń regularnych są często używane w aplikacji, sposób wywoływania metody (statyczny, interpretowany, skompilowany) znacząco wpływa na wydajność.  
  
### <a name="static-regular-expressions"></a>Statyczne wyrażenia regularne  
 Statyczne metody wyrażeń regularnych są zalecane jako alternatywa dla wielokrotnego tworzenia wystąpienia obiektu wyrażenia regularnego z tym samym wyrażeniem regularnym. W przeciwieństwie do wzorców wyrażeń regularnych używanych przez obiekty wyrażeń regularnych, kody operacji lub skompilowana składnia języka Microsoft Intermediate Language (MSIL) z wzorców używanych w wywołaniach metod wystąpień są buforowane wewnętrznie przez aparat wyrażeń regularnych.  
  
 Na przykład program obsługi zdarzeń często wywołuje inną metodę do weryfikacji danych wejściowych użytkownika. Jest to odzwierciedlone w poniższym kodzie, w którym <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> zdarzenie kontrolki służy do wywołania metody o nazwie `IsValidCurrency`, która sprawdza, czy użytkownik wprowadził symbol waluty, po którym następuje co najmniej jedna cyfra dziesiętna.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 W poniższym przykładzie pokazano bardzo wydajną `IsValidCurrency` implementację metody. Należy zauważyć, że każde wywołanie metody retworzy <xref:System.Text.RegularExpressions.Regex> wystąpienie obiektu z tym samym wzorcem. To z kolei oznacza, że wzorzec wyrażenia regularnego należy kompilować podczas każdego wywołania metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 Ten nieefektywny kod należy zastąpić wywołaniem metody statycznej <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> . Eliminuje to konieczność tworzenia wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex> za każdym razem, gdy chcesz wywołać metodę dopasowania do wzorca, i umożliwia aparatowi wyrażeń regularnych pobieranie skompilowanej wersji wyrażenia regularnego z jego pamięci podręcznej.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 Domyślnie buforowanych jest piętnaście ostatnio używanych statycznych wzorców wyrażeń regularnych. W przypadku aplikacji, które wymagają większej liczby buforowanych statycznych wyrażeń regularnych, rozmiar pamięci podręcznej można dostosować przez ustawienie <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> właściwości.  
  
 Wyrażenie `\p{Sc}+\s*\d+` regularne, które jest używane w tym przykładzie, sprawdza, czy ciąg wejściowy zawiera symbol waluty i co najmniej jedną cyfrę dziesiętną. Definicję wzorca pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}+`|Dopasowanie do jednego lub większej liczby symboli Unicode w kategorii Waluta.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretowane a Skompilowane wyrażenia regularne  
 Wzorce wyrażeń regularnych, które nie są powiązane z aparatem wyrażeń regularnych przez specyfikację <xref:System.Text.RegularExpressions.RegexOptions.Compiled> opcji, są interpretowane. Kiedy tworzone jest wystąpienie obiektu wyrażenia regularnego, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji. Gdy wywoływana jest metoda wystąpienia, kody operacji są konwertowane do języka MSIL i wykonywane przy użyciu kompilatora JIT. Podobnie, kiedy jest wywoływania statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji i przechowuje je w pamięci podręcznej. Następnie konwertuje te kody operacji na język MSIL, dzięki czemu mogą zostać wykonane za pomocą kompilatora JIT. Interpretowane wyrażenia regularne ograniczają czas uruchamiania kosztem wolniejszego czasu wykonania. Z tego powodu najlepiej stosować je, kiedy wyrażenie regularne jest używane w małej liczbie wywołań metod lub jeśli dokładna liczba wywołań metod wyrażenia regularnego jest nieznana, ale oczekuje się, że będzie mała. Wraz ze wzrostem liczby wywołań metod przyrost wydajności związany ze skróceniem czasu uruchamiania jest coraz mniejszy wskutek wolniejszego wykonywania.  
  
 Wzorce wyrażeń regularnych, które są powiązane z aparatem wyrażeń regularnych przez specyfikację <xref:System.Text.RegularExpressions.RegexOptions.Compiled> opcji, są kompilowane. Oznacza to, że kiedy jest tworzone wystąpienie obiektu wyrażenia regularnego lub kiedy jest wywoływana statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na pośredni zestaw kodów operacji, które następnie konwertuje na język MSIL. Kiedy metoda jest wywoływana, kompilator JIT wykonuje kod języka MSIL. W przeciwieństwie do interpretowanych wyrażeń regularnych, skompilowane wyrażenia regularne wydłużają czas uruchamiania, ale wykonanie pojedynczych metod dopasowania do wzorca jest szybsze. W rezultacie korzyści w zakresie wydajności wynikające z kompilowania wyrażeń regularnych rosną proporcjonalnie do liczby wywoływanych metod wyrażeń regularnych.  
  
 Podsumowując, zaleca się używać interpretowanych wyrażeń regularnych, kiedy stosunkowo rzadko są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Zaleca się używać skompilowanych wyrażeń regularnych, kiedy stosunkowo często są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Dokładny próg, przy którym mniejsza szybkość wykonywania interpretowanych wyrażeń regularnych przewyższa korzyści z redukcji czasu uruchamiania, lub próg, przy którym wolniejsze uruchamianie skompilowanych wyrażeń regularnych przewyższa korzyści z większej szybkości wykonywania, jest trudny do określenia. Zależy to od wielu czynników, w tym od złożoności wyrażenia regularnego i konkretnych danych, które to wyrażenie przetwarza. Aby określić, czy interpretowane lub skompilowane wyrażenia regularne oferują najlepszą wydajność dla konkretnego scenariusza aplikacji, można użyć <xref:System.Diagnostics.Stopwatch> klasy do porównania czasów wykonania.  
  
 Poniższy przykład porównuje wydajność skompilowanych i interpretowanych wyrażeń regularnych podczas odczytywania pierwszych dziesięciu zdań i odczytuje wszystkie zdania w tekście powieści Theodore'a dreisera Dreiser *Financier*. Dane wyjściowe z przykładu pokazują, że przy zaledwie dziesięciu wywołaniach metod dopasowania wyrażenia regularnego interpretowane wyrażenie regularne oferuje lepszą wydajność niż skompilowane wyrażenie regularne. Jednak skompilowane wyrażenie regularne oferuje lepszą wydajność dla dużej liczby wywołań (w tym przypadku ponad 13 000).  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 Wzorzec wyrażenia regularnego używany w przykładzie, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|<code>(\r?\n)&#124;,?\s)</code>|Dopasowanie do zera lub jednego znaku powrotu karetki, po którym występuje znak nowego wiersza, albo do zera lub jednego przecinka, po którym występuje znak odstępu.|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Dopasowanie do zera lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym występuje zero albo jeden znak powrotu karetki i znak nowego wiersza lub zero albo jeden przecinek, po którym następuje znak odstępu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`[.?:;!]`|Dopasowanie do kropki, znaku zapytania, dwukropka, średnika lub wykrzyknika.|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>Wyrażenia regularne: Skompilowano do zestawu  
 Program .NET umożliwia również tworzenie zestawu zawierającego skompilowane wyrażenia regularne. Przenosi to czynnik wpływający na wydajność kompilowania wyrażeń regularnych z czasu wykonywania na czas projektowania. Jednak wymaga to również pewnej dodatkowej pracy: Wyrażenia regularne należy definiować z wyprzedzeniem i kompilować do zestawu. Kompilator może następnie odwołać się do tego zestawu podczas kompilowania kodu źródłowego, który używa wyrażeń regularnych zestawu. Każde skompilowane wyrażenie regularne w zestawie jest reprezentowane przez klasę, która pochodzi od <xref:System.Text.RegularExpressions.Regex>.  
  
 Aby kompilować wyrażenia regularne do zestawu, należy wywołać metodę i <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> przekazać do niej <xref:System.Text.RegularExpressions.RegexCompilationInfo> tablicę obiektów reprezentujących wyrażenia regularne do skompilowania oraz <xref:System.Reflection.AssemblyName> obiekt, który zawiera informacje na temat zestawu, który ma być utworzony.  
  
 Zaleca się, aby kompilować wyrażenia regularne do zestawu w następujących sytuacjach:  
  
- Jeśli jesteś deweloperem składników, który chce utworzyć bibliotekę wyrażeń regularnych do wielokrotnego użytku.  
  
- Jeśli oczekujesz, że metody dopasowania do wzorca wyrażenia regularnego będą wywoływane nieokreśloną liczbę razy — od jednego lub dwóch wywołań do kilku tysięcy wywołań. W przeciwieństwie do skompilowanych lub interpretowanych wyrażeń regularnych, wyrażenia regularne, które są kompilowane do oddzielnych zestawów, oferują stałą wydajność bez względu na liczbę wywołań metody.  
  
 Jeśli skompilowane wyrażenia regularne są używane w celu optymalizacji wydajności, nie należy używać odbicia w celu utworzenia zestawu, załadowania aparatu wyrażeń regularnych i wykonania jego metod dopasowania do wzorca. Wymaga to unikania dynamicznego kompilowania wzorców wyrażeń regularnych i określenia wszelkich opcji dopasowania do wzorca (np. z uwzględnieniem wielkości liter) w czasie tworzenia zestawu. Wymaga to również odseparowania kodu, który tworzy zestaw, od kodu, który używa wyrażenia regularnego.  
  
 W poniższym przykładzie pokazano, w jaki sposób utworzyć zestaw zawierający skompilowane wyrażenie regularne. Tworzy zestaw o nazwie `RegexLib.dll` z pojedynczą `SentencePattern`klasą wyrażenia regularnego,, która zawiera wzorzec [wyrażenia regularnego pasującego do zdania używany w interpretowaniu a. Skompilowano sekcję](#Interpreted) wyrażeń regularnych.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 Gdy przykład jest kompilowany do pliku wykonywalnego i uruchamiany, tworzy zestaw o nazwie `RegexLib.dll`. Wyrażenie regularne jest reprezentowane przez klasę o nazwie `Utilities.RegularExpressions.SentencePattern` , która pochodzi od. <xref:System.Text.RegularExpressions.Regex> Poniższy przykład używa skompilowanego wyrażenia regularnego, aby wyodrębnić zdania z tekstu powieści Theodore'a dreisera Dreiser *Financier*.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [Powrót do początku](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>Przejmowanie kontroli nad wycofywaniem  
 Zazwyczaj aparat wyrażeń regularnych używa progresji liniowej do przechodzenia przez ciąg wejściowy i porównywania go ze wzorcem wyrażenia regularnego. Jednak gdy nieokreślone Kwantyfikatory, takie `*`jak `+`, i `?` są używane we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych może dać część udanych częściowych dopasowań i powrócić do wcześniej zapisanego stanu Aby wyszukać pomyślne dopasowanie dla całego wzorca. Proces ten jest znany pod nazwą wycofywania.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat wycofywania, zobacz [Szczegóły zachowania wyrażenia regularnego](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) i wycofywania. [](../../../docs/standard/base-types/backtracking-in-regular-expressions.md) Aby uzyskać szczegółowe omówienie wycofywania, zobacz [Optymalizowanie wydajności wyrażeń regularnych, część II: Przejęcie opłaty](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) za wycofywanie w blogu zespołu BCL.  
  
 Obsługa wycofywania daje wyrażeniom regularnym duże możliwości i elastyczność. Dodatkowo odpowiedzialność za kontrolowanie operacji aparatu wyrażeń regularnych spada na deweloperów wyrażeń regularnych. Ponieważ deweloperzy często nie są tego świadomi, błędne użycie wycofywania lub nadmierne poleganie na wycofywaniu często odgrywa najbardziej znaczącą rolę w zmniejszeniu wydajności wyrażeń regularnych. W scenariuszu najgorszego przypadku czas wykonywania może podwajać się dla każdego dodatkowego znaku w ciągu wejściowym. W rzeczywistości przy nadmiernym wykorzystaniu wycofywania łatwo jest stworzyć programowy odpowiednik pętli nieskończonej, jeżeli dane wejściowe niemal pasują do wzorca wyrażenia regularnego; przetwarzanie relatywnie krótkiego ciągu wejściowego może zająć aparatowi wyrażeń regularnych kilka godzin, a nawet dni.  
  
 Często efektem użycia wycofywania jest obniżenie wydajności w aplikacjach, mimo że używanie wycofywania nie jest niezbędne dla dopasowania. Na przykład wyrażenie `\b\p{Lu}\w*\b` regularne dopasowuje wszystkie wyrazy rozpoczynające się od wielkiej litery, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-|-|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\p{Lu}`|Dopasowanie do dowolnej wielkiej litery.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Ponieważ granica wyrazu nie jest tym samym co znak słowa ani jego podzbiorem, nie ma możliwości, aby aparat wyrażeń regularnych przekroczył granicę wyrazu podczas dopasowywania znaków słowa. Oznacza to, że dla tego wyrażenia regularnego wycofywanie może nigdy nie przyczynić się do sukcesu jakiegokolwiek dopasowania, może za to obniżyć wydajność, ponieważ aparat wyrażeń regularnych musi zapisać swój stan podczas każdego pomyślnie zakończonego wstępnego dopasowania znaku słowa.  
  
 Jeśli okaże się, że wycofywanie nie jest konieczne, można je wyłączyć za pomocą `(?>subexpression)` elementu języka. W poniższym przykładzie jest analizowana składnia ciągu wejściowego przy użyciu dwóch wyrażeń regularnych. Pierwszy, `\b\p{Lu}\w*\b`, korzysta z wycofywania. Druga, `\b\p{Lu}(?>\w*)\b`, wyłącza wycofywanie. Jak wynika z przykładu, oba wyrażenia regularne dały ten sam wynik.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 W wielu przypadkach wycofywanie jest niezbędne dla dopasowania wzorca wyrażenia regularnego do tekstu wejściowego. Należy pamiętać, że nadmierne używanie wycofywania może poważnie obniżyć wydajność i stworzyć wrażanie, ze aplikacja przestała odpowiadać. W szczególności ma to miejsce, kiedy kwantyfikatory są zagnieżdżane i tekst, który pasuje do zewnętrznego podwyrażenia, jest podzbiorem tekstu, który pasuje do wewnętrznego podwyrażenia.  
  
> [!WARNING]
> Oprócz unikania nadmiernego wykorzystania wycofywania należy używać funkcji limitu czasu, aby zagwarantować, że nadmierne używanie wycofywania nie obniży poważnie wydajności wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz sekcję [użycie wartości limitu czasu](#Timeouts) .  
  
 Na przykład wzorzec `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` wyrażenia regularnego jest przeznaczony do dopasowania do numeru części, który składa się z co najmniej jednego znaku alfanumerycznego. Jakiekolwiek dodatkowe znaki mogą być znakami alfanumerycznymi, łącznikami, podkreśleniami lub kropkami, ale ostatni znak musi być alfanumeryczny. Znak dolara przerywa numer części. W niektórych przypadkach ten wzorzec wyrażenia regularnego może wykazywać bardzo niską wydajność, ponieważ Kwantyfikatory są zagnieżdżone, a ponieważ `[0-9A-Z]` Podwyrażenie jest podzbiorem podwyrażenia `[-.\w]*`.  
  
 W takich przypadkach można zoptymalizować wydajność wyrażenia regularnego, usuwając zagnieżdżone kwantyfikatory i zastępując zewnętrzne podwyrażenie asercją wyprzedzającą lub wsteczną o zerowej szerokości. Asercje wyprzedzające i wsteczne są kotwicami; nie przesuwają wskaźnika w ciągu wejściowym, ale „patrzą” do przodu lub wstecz, aby sprawdzić, czy określony warunek został spełniony. Na przykład wyrażenie regularne numeru części można napisać jako `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Definicję tego wzorca wyrażenia regularnego pokazano w poniższej tabeli.  
  
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
  
 Język wyrażeń regularnych w programie .NET zawiera następujące elementy języka, których można użyć w celu wyeliminowania kwantyfikatorów zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [Konstrukcje grupujące](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
|Element języka|Opis|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|Pozytywna asercja wyprzedzająca o zerowej szerokości. Sprawdź przed bieżącą pozycją, aby określić, `subexpression` czy pasuje do ciągu wejściowego.|  
|`(?!` `subexpression` `)`|Negatywna asercja wyprzedzająca o zerowej szerokości. Sprawdź przed bieżącą pozycją, aby określić, `subexpression` czy nie pasuje do ciągu wejściowego.|  
|`(?<=` `subexpression` `)`|Pozytywna asercja wsteczna o zerowej szerokości. Sprawdź za bieżącą pozycję, aby określić, `subexpression` czy pasuje do ciągu wejściowego.|  
|`(?<!` `subexpression` `)`|Negatywna asercja wsteczna o zerowej szerokości. Sprawdź za bieżącą pozycję, aby określić, `subexpression` czy nie pasuje do ciągu wejściowego.|  
  
 [Powrót do początku](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>Używanie wartości limitu czasu  
 Jeśli wyrażenie regularne przetwarza dane wejściowe, które niemal pasują do wzorca wyrażenia regularnego, często może nadmiernie używać wycofywania, co znacznie wpływa na wydajność. Oprócz dokładnego rozważenia użycia wycofywania i przetestowania wyrażenia regularnego pod kątem niemal dopasowanych danych wejściowych, zawsze należy ustawić wartość limitu czasu, aby zagwarantować, że efekt nadmiernego używania wycofywania, jeżeli wystąpi, będzie jak najmniejszy.  
  
 Interwał limitu czasu wyrażenia regularnego określa czas, przez jaki aparat wyrażeń regularnych będzie szukał pojedynczego dopasowania, zanim zostanie przekroczony limit czasu. Domyślny limit czasu wynosi <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, co oznacza, że limit czasu wyrażenia regularnego nie zostanie przekroczony. Można zastąpić tę wartość i zdefiniować interwał limitu czasu w następujący sposób:  
  
- Przez podanie wartości limitu czasu podczas tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu przez <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> wywołanie konstruktora.  
  
- Wywołując statyczną metodę dopasowania do wzorca, taką jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, która zawiera `matchTimeout` parametr.  
  
- Dla skompilowanych wyrażeń regularnych, które są tworzone przez <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> wywołanie metody, przez wywołanie konstruktora, który ma parametr typu. <xref:System.TimeSpan>  
  
 Jeśli zdefiniowano interwał limitu czasu i dopasowanie nie zostanie znalezione na końcu interwału, metoda wyrażenia regularnego zgłasza <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> wyjątek. W obsłudze wyjątków można wybrać ponowienie próby dopasowywania z dłuższym interwałem limitu czasu, zrezygnować z próby dopasowania i założyć, że dopasowanie nie istnieje, lub zrezygnować z próby dopasowania i zarejestrować informacje o wyjątku na potrzeby późniejszej analizy.  
  
 W poniższym przykładzie zdefiniowano `GetWordData` metodę, która tworzy wystąpienie wyrażenia regularnego z interwałem limitu czasu wynoszącym 350 milisekund, aby obliczyć liczbę słów i średnią liczbę znaków w wyrazie w dokumencie tekstowym. W przypadku przekroczenia limitu czasu dla operacji dopasowywania przekroczenie interwału czasowego zwiększa <xref:System.Text.RegularExpressions.Regex> się o 350 milisekund, a obiekt jest ponownie tworzony. Jeżeli nowy interwał limitu czasu przekroczy 1 sekundę, metoda ponownie zgłosi wyjątek do obiektu wywołującego.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [Powrót do początku](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>Przechwytywanie tylko wtedy, gdy jest to konieczne  
 Wyrażenia regularne w programie .NET obsługują szereg konstrukcji grupujących, które pozwalają grupować wzorzec wyrażenia regularnego w jedno lub więcej podwyrażeń. Najczęściej używane konstrukcje grupujące w języku wyrażeń regularnych programu .NET to `(`Podwyrażenie`)`, które definiuje numerowaną grupę przechwytywania i `(?<`Podwyrażenie *nazwy*`>`, która definiuje nazwaną grupę przechwytywania. `)` Konstrukcje grupujące są niezbędne do tworzenia odwołań wstecznych i do definiowania podwyrażeń, do których jest stosowany kwantyfikator.  
  
 Jednak zastosowanie tych elementów języka jest kosztowne. Powodują <xref:System.Text.RegularExpressions.GroupCollection> , że obiekt zwracany <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> przez właściwość jest wypełniany najnowszymi nienazwanymi lub nazwanymi przechwycenimi, a jeśli jedna konstrukcja grupowania przechwyciła wiele podciągów w ciągu wejściowym, wypełnia również <xref:System.Text.RegularExpressions.CaptureCollection>obiekt zwrócony przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwość określonej grupy przechwytywania z wieloma <xref:System.Text.RegularExpressions.Capture> obiektami.  
  
 Często konstrukcje grupujące są używane w wyrażeniach regularnych tylko po to, aby można było zastosować do nich kwantyfikatory, i grupy przechwytywane przez te podwyrażenia nie są następnie używane. Na przykład wyrażenie `\b(\w+[;,]?\s?)+[.?!]` regularne służy do przechwytywania całego zdania. W poniższej tabeli opisano elementy języka w tym wzorcu wyrażenia regularnego i ich wpływ na <xref:System.Text.RegularExpressions.Match> <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> obiekty i <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcje.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`[;,]?`|Dopasowanie do zera lub jednego przecinka albo średnika.|  
|`\s?`|Dopasowuje zero lub jeden znak odstępu.|  
|`(\w+[;,]?\s?)+`|Dopasowanie do jednego lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym następuje opcjonalny przecinek lub średnik, po którym następuje opcjonalny znak odstępu. To definiuje pierwszą grupę przechwytywania, która jest niezbędna, aby kombinacja wielu znaków słowa (tzn. słowo), po których następuje opcjonalny znak interpunkcyjny, była powtarzana do momentu, kiedy aparat wyrażeń regularnych osiągnie koniec zdania.|  
|`[.?!]`|Dopasowanie do kropki, znaku zapytania lub wykrzyknika.|  
  
 Jak pokazano na poniższym przykładzie, gdy zostanie znalezione dopasowanie, zarówno <xref:System.Text.RegularExpressions.GroupCollection> obiekty, jak i <xref:System.Text.RegularExpressions.CaptureCollection> są wypełniane za pomocą przechwytywania z dopasowania. W takim przypadku Grupa `(\w+[;,]?\s?)` przechwytywania istnieje, aby `+` można było do niej zastosować kwantyfikator, co umożliwia wzorce wyrażenia regularnego dopasowywania każdego wyrazu w zdaniu. W przeciwnym razie dopasowanie nastąpi dla ostatniego wyrazu w zdaniu.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 Kiedy używa się podwyrażeń tylko w celu zastosowania do nich kwantyfikatorów, a przechwytywany tekst nie jest ważny, należy wyłączyć przechwytywanie grup. Na przykład `(?:subexpression)` element Language uniemożliwia grupę, do której odnosi się przed przechwyceniem dopasowanych podciągów. W poniższym przykładzie wzorzec wyrażenia regularnego z poprzedniego przykładu jest zmieniany na `\b(?:\w+[;,]?\s?)+[.?!]`. Jak widać w danych wyjściowych, uniemożliwia aparatowi wyrażeń regularnych <xref:System.Text.RegularExpressions.GroupCollection> zapełnianie <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji i.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 Przechwytywanie można wyłączyć na jeden z poniższych sposobów:  
  
- Użyj elementu `(?:subexpression)` języka. Ten element zapobiega przechwytywaniu dopasowanych podciągów w grupie, do której jest stosowany. Nie wyłącza przechwytywania podciągów w grupach zagnieżdżonych.  
  
- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Użyj opcji. Wyłącza wszystkie nienazwane lub niejawne przechwytywania we wzorcu wyrażenia regularnego. W przypadku korzystania z tej opcji tylko podciągi, które pasują do nazwanych `(?<name>subexpression)` grup zdefiniowanych za pomocą elementu language, mogą być przechwytywane. `options` <xref:System.Text.RegularExpressions.Regex> `options` Flagę można przesłać do parametru konstruktora<xref:System.Text.RegularExpressions.Regex> klasy lub do parametru statycznej metody dopasowywania. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>  
  
- `n` Użyj opcji `(?imnsx)` w elemencie języka. Powoduje to wyłączenie wszystkich nienazwanych lub niejawnych przechwytywań od miejsca we wzorcu wyrażenia regularnego, w którym znajduje się ten element. Przechwytywanie jest wyłączone do końca wzorca lub do czasu, `(-n)` gdy opcja włącza nienazwane lub niejawne przechwycenia. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).  
  
- `n` Użyj opcji `(?imnsx:subexpression)` w elemencie języka. Ta opcja wyłącza wszystkie nienazwane lub niejawne `subexpression`przechwycenia w. Przechwytywania przez jakiekolwiek nienazwane lub niejawne zagnieżdżone grupy przechwytywania również są wyłączone.  
  
 [Powrót do początku](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Bada implementację aparatu wyrażeń regularnych w programie .NET. W tym temacie skupiono się na elastyczności wyrażeń regularnych i wyjaśniono odpowiedzialność deweloperów za zapewnienie wydajnych i niezawodnych operacji aparatu wyrażeń regularnych.|  
|[Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Informacje, co to jest wycofywanie i jak wpływa na wydajność wyrażeń regularnych oraz analiza elementów języka, które dostarczają alternatywy dla wycofywania.|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Opisuje elementy języka wyrażeń regularnych w programie .NET i zawiera linki do szczegółowej dokumentacji dla każdego elementu języka.|
