---
title: Najlepsze praktyki dotyczące prawidłowych wyrażeń w .NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59ec9ead0fd010baccaadb1eda0f469b7b4dcb46
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Najlepsze praktyki dotyczące prawidłowych wyrażeń w .NET
<a name="top"></a> Aparat wyrażeń regularnych programu .NET to narzędzie zaawansowane, oferujący wszystkie funkcje, które przetwarza tekst w dopasowaniach wzorców, a nie na dopasowanie literały tekstowe i porównywanie. W większości przypadków dopasowanie do wzorca przebiega szybko i skutecznie. Jednak w niektórych przypadkach aparat wyrażeń regularnych może okazać się bardzo wolny. W skrajnych przypadkach może nawet pozornie przestać odpowiadać, ponieważ przetwarza stosunkowo mało danych wejściowych w ciągu kilku godzin lub nawet dni.  
  
 W tym temacie przedstawiono kilka najlepszych rozwiązań, które deweloperzy mogą zaadoptować w celu osiągnięcia optymalnej wydajności przetwarzania własnych wyrażeń regularnych. Ten temat zawiera następujące sekcje:  
  
-   [Należy wziąć pod uwagę źródła danych wejściowych](#InputSource)  
  
-   [Odpowiednią obsługę tworzenia wystąpienia obiektu](#ObjectInstantiation)  
  
-   [Przejęcie śledzenie wsteczne](#Backtracking)  
  
-   [Użyj wartości limitów czasu](#Timeouts)  
  
-   [Przechwyć tylko wtedy, gdy jest to konieczne](#Capture)  
  
-   [Tematy pokrewne](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>Wybieranie źródła danych wejściowych  
 Ogólnie rzecz biorąc, wyrażenia regularne mogą przyjmować dwa typy danych wejściowych: ograniczone i nieograniczone. Ograniczone dane wejściowe to tekst pochodzący ze znanego lub wiarygodnego źródła, który ma wstępnie zdefiniowany format. Nieograniczone dane wejściowe to tekst pochodzący z niepewnego źródła, takiego jak użytkownik sieci web, mogący nie mieć wstępnie zdefiniowanego lub oczekiwanego formatu.  
  
 Wzorce wyrażeń regularnych są zazwyczaj pisane w taki sposób, aby dopasowywały prawidłowe dane wejściowe. Oznacza to, że deweloperzy sprawdzają tekst, który chcą dopasować, a następnie piszą wzorzec wyrażenia regularnego, który mu odpowiada. Następnie deweloperzy określają, czy wzorzec wymaga poprawek, testując go dla wielu prawidłowych elementów wejściowych. Gdy wzorzec pasuje do wszystkich przypuszczalnie prawidłowych danych wejściowych, jest uznawany za gotowy do produkcji i można go dołączyć do wydawanej aplikacji. Dzięki temu wzorzec wyrażenia regularnego nadaje się do dopasowywania ograniczonych danych wejściowych. Jednak nie powoduje to, że wzorzec ten jest odpowiedni do porównywania nieograniczonych danych wejściowych.  
  
 Aby dopasować nieograniczone dane wejściowe, wyrażenie regularne musi być w stanie efektywnie obsłużyć trzy rodzaje tekstu:  
  
-   Tekst, który pasuje do wzorca wyrażenia regularnego.  
  
-   Tekst, który nie pasuje do wzorca wyrażenia regularnego.  
  
-   Tekst, który prawie pasuje do wzorca wyrażenia regularnego.  
  
 Ostatni typ tekstu jest szczególnie problematyczny dla wyrażeń regularnych, które zostały napisane do obsługi ograniczonych danych wejściowych. Jeśli tego wyrażenia regularnego również jest oparta na szeroką gamę [śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md), aparat wyrażeń regularnych może przeznaczyć długi ilość czasu (w niektórych przypadkach wiele godzin lub dni) przetwarzania pozornie nieszkodliwe tekstu.  
  
> [!WARNING]
>  W poniższym przykładzie użyto wyrażenia regularnego, które jest podatne na nadmierne korzystanie z wycofywania, przez co istnieje duże prawdopodobieństwo odrzucenia prawidłowych adresów e-mail. Nie należy stosować go w procedurze weryfikacji adresów e-mail. Jeśli chcesz wyrażenie regularne, która weryfikuje adresów e-mail, zobacz [porady: Sprawdź, czy ciągów jest prawidłowy Format wiadomości E-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
 Rozważmy na przykład bardzo często używane, ale wyjątkowo problematyczne wyrażenie regularne służące do weryfikacji aliasów adresów e-mail. Wyrażenie regularne `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` są zapisywane do przetworzenia, co jest uważany za prawidłowy adres e-mail, które składa się ze znaków alfanumerycznych, następuje zero lub więcej znaków, które mogą być alfanumeryczne, kropki i łączniki. Wyrażenie regularne musi być zakończone znakiem alfanumerycznym. Jednak, jak pokazuje poniższy przykład, mimo że wyrażenie regularne obsługuje z łatwością prawidłowe dane wejściowe, jego wydajność jest nieefektywna podczas przetwarzania niemal prawidłowych danych wejściowych.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 Dane wyjściowe z przykładu pokazują, że aparat wyrażeń regularnych przetwarza prawidłowe aliasy adresów e-mail w prawie takim samym interwale czasowym, niezależnie od ich długości. Z drugiej strony, kiedy niemal prawidłowy adres e-mail zawiera więcej niż pięć znaków, dla każdego dodatkowego znaku w ciągu czas przetwarzania w przybliżeniu wzrasta dwukrotnie. Oznacza to, że przetwarzanie niemal prawidłowego 28-znakowego ciągu będzie trwało prawie godzinę, a przetwarzanie niemal prawidłowego 33-znakowego ciągu będzie trwało prawie cały dzień.  
  
 Ponieważ wyrażenie regularne zostało opracowane z uwzględnieniem wyłącznie formatu danych wejściowych do dopasowania, wyrażenie regularne nie uwzględnia danych wejściowych, które nie pasują do wzorca. To z kolei może spowodować, że nieograniczone dane wejściowe, które niemal odpowiadają wzorcowi wyrażenia regularnego, znacząco obniżą wydajność.  
  
 Aby rozwiązać ten problem, można wykonać następujące czynności:  
  
-   Podczas tworzenia wzorca należy uwzględnić wpływ wycofywania na wydajność aparatu wyrażeń regularnych, szczególnie jeśli wyrażenie regularne jest przeznaczone do przetwarzania nieograniczonych danych wejściowych. Aby uzyskać więcej informacji, zobacz [zająć bezpłatnie z śledzenie wsteczne](#Backtracking) sekcji.  
  
-   Wyrażenie regularne należy dokładnie sprawdzić, używając nieprawidłowych i niemal prawidłowych danych wejściowych, a także prawidłowych danych wejściowych. Aby losowo wygenerować danych wejściowych dla określonego wyrażenia regularnego, można użyć [Rafał](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/), który jest narzędziem eksploracji wyrażenia regularnego Microsoft Research.  
  
 [Powrót do początku](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>Odpowiednia obsługa tworzenia wystąpienia obiektu  
 Istotą. Model obiektów wyrażeń regularnych w sieci jest <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> klasy, która reprezentuje aparat wyrażeń regularnych. Często jednym największy czynnik, który wpływa na wydajność wyrażenie regularne jest sposobu, w jaki <xref:System.Text.RegularExpressions.Regex> jest używany aparat. Definiowanie wyrażenia regularnego polega na ścisłym sprzęganiu aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Czy sprzężenia procesu, czy obejmuje utworzenie wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu przez przekazanie jej konstruktora wzorzec wyrażenia regularnego lub wywołanie metody statycznej, przekazując wzorzec wyrażenia regularnego wraz z ciągu do analizy, jest konieczność jednego kosztowne.  
  
> [!NOTE]
>  Bardziej szczegółowe omówienie skutki wydajności za pomocą wyrażeń regularnych interpretowany i skompilowany, zobacz [optymalizacji wydajności wyrażenie regularne, część II: pobieranie bezpłatnie z śledzenie wsteczne](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) w blogu zespołu BCL.  
  
 Można sprzęgnąć aparat wyrażeń regularnych z konkretnym wzorcem wyrażenia regularnego, a następnie użyć aparatu, aby dopasować tekst na kilka sposobów:  
  
-   Należy wywołać dopasowywanie do wzorca metodą statyczną, takich jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. Nie wymaga to tworzenia wystąpienia obiektu wyrażenia regularnego.  
  
-   Można utworzyć wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu i wywołanie metody wystąpienia dopasowywanie do wzorca interpretowany wyrażenia regularnego. Jest to domyślna metoda do tworzenia powiązania aparatu wyrażeń regularnych z wzorcem wyrażenia regularnego. Wynika, gdy <xref:System.Text.RegularExpressions.Regex> utworzeniu wystąpienia obiektu bez `options` argument, który zawiera <xref:System.Text.RegularExpressions.RegexOptions.Compiled> flagi.  
  
-   Można utworzyć wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu i wywołanie metody wystąpienia dopasowywanie do wzorca skompilowane wyrażenia regularnego. Obiektów wyrażeń regularnych stanowią skompilowany wzorców, kiedy <xref:System.Text.RegularExpressions.Regex> o utworzeniu wystąpienia obiektu `options` argument, który zawiera <xref:System.Text.RegularExpressions.RegexOptions.Compiled> flagi.  
  
-   Możesz utworzyć specjalnych <xref:System.Text.RegularExpressions.Regex> obiekt, który jest ściśle powiązane ze wzorcem wyrażenia regularnego określonego go skompilować i zapisać go do zestawu autonomicznego. Można to zrobić przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody.  
  
 Sposób, w jaki są wywoływane metody dopasowywania wyrażeń regularnych, może mieć znaczący wpływ na działanie aplikacji. W poniższych sekcjach omówiono, kiedy używać wywołań metod statycznych oraz interpretowanych i skompilowanych wyrażeń regularnych, aby poprawić wydajność aplikacji.  
  
> [!IMPORTANT]
>  Jeśli to samo wyrażenie regularne jest używane wielokrotnie w wywołaniach metod lub jeśli obiekty wyrażeń regularnych są często używane w aplikacji, sposób wywoływania metody (statyczny, interpretowany, skompilowany) znacząco wpływa na wydajność.  
  
### <a name="static-regular-expressions"></a>Statyczne wyrażenia regularne  
 Statyczne metody wyrażeń regularnych są zalecane jako alternatywa dla wielokrotnego tworzenia wystąpienia obiektu wyrażenia regularnego z tym samym wyrażeniem regularnym. W przeciwieństwie do wzorców wyrażeń regularnych używanych przez obiekty wyrażeń regularnych, kody operacji lub skompilowana składnia języka Microsoft Intermediate Language (MSIL) z wzorców używanych w wywołaniach metod wystąpień są buforowane wewnętrznie przez aparat wyrażeń regularnych.  
  
 Na przykład program obsługi zdarzeń często wywołuje inną metodę do weryfikacji danych wejściowych użytkownika. Znajduje to odzwierciedlenie w poniższym kodzie, w którym <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> zdarzenia są używane do wywoływania metody o nazwie `IsValidCurrency`, który sprawdza, czy użytkownik wprowadził symbol waluty, a następnie co najmniej jedną cyfrę.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 Bardzo mało wydajne implementacja `IsValidCurrency` metody przedstawiono w poniższym przykładzie. Należy pamiętać, że każde wywołanie metody reinstantiates <xref:System.Text.RegularExpressions.Regex> obiekt o takim wzorcu. To z kolei oznacza, że wzorzec wyrażenia regularnego należy kompilować podczas każdego wywołania metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 Należy zastąpić ten niewydajny kod z wywołaniem do statycznego <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody. Eliminuje to potrzebę utworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu zawsze ma zostać wywołana metoda dopasowywanie do wzorca i umożliwia aparat wyrażeń regularnych można pobrać wersję skompilowane wyrażenia regularnego z pamięci podręcznej.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 Domyślnie buforowanych jest piętnaście ostatnio używanych statycznych wzorców wyrażeń regularnych. Dla aplikacji, które wymagają większej liczby buforowanych statyczne wyrażenia regularne, można dostosować rozmiar pamięci podręcznej przez ustawienie <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> właściwości.  
  
 Wyrażenie regularne `\p{Sc}+\s*\d+` używany w tym przykładzie sprawdza, czy ciąg wejściowy składa się z symbolu waluty i co najmniej jedną cyfrę. Definicję wzorca pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}+`|Dopasowanie do jednego lub większej liczby symboli Unicode w kategorii Waluta.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretowany vs. Skompilowane wyrażenia regularne  
 Wzorce wyrażenie regularne, które nie są powiązane z aparatu wyrażenia regularnego przy użyciu specyfikacji <xref:System.Text.RegularExpressions.RegexOptions.Compiled> interpretowania opcji. Kiedy tworzone jest wystąpienie obiektu wyrażenia regularnego, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji. Gdy wywoływana jest metoda wystąpienia, kody operacji są konwertowane do języka MSIL i wykonywane przy użyciu kompilatora JIT. Podobnie, kiedy jest wywoływania statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na zestaw kodów operacji i przechowuje je w pamięci podręcznej. Następnie konwertuje te kody operacji na język MSIL, dzięki czemu mogą zostać wykonane za pomocą kompilatora JIT. Interpretowane wyrażenia regularne ograniczają czas uruchamiania kosztem wolniejszego czasu wykonania. Z tego powodu najlepiej stosować je, kiedy wyrażenie regularne jest używane w małej liczbie wywołań metod lub jeśli dokładna liczba wywołań metod wyrażenia regularnego jest nieznana, ale oczekuje się, że będzie mała. Wraz ze wzrostem liczby wywołań metod przyrost wydajności związany ze skróceniem czasu uruchamiania jest coraz mniejszy wskutek wolniejszego wykonywania.  
  
 Wzorce wyrażenie regularne, które są powiązane z aparatu wyrażenia regularnego przy użyciu specyfikacji <xref:System.Text.RegularExpressions.RegexOptions.Compiled> opcji są kompilowane. Oznacza to, że kiedy jest tworzone wystąpienie obiektu wyrażenia regularnego lub kiedy jest wywoływana statyczna metoda wyrażenia regularnego i wyrażenie regularne nie jest znajdowane w pamięci podręcznej, aparat wyrażeń regularnych konwertuje wyrażenie regularne na pośredni zestaw kodów operacji, które następnie konwertuje na język MSIL. Kiedy metoda jest wywoływana, kompilator JIT wykonuje kod języka MSIL. W przeciwieństwie do interpretowanych wyrażeń regularnych, skompilowane wyrażenia regularne wydłużają czas uruchamiania, ale wykonanie pojedynczych metod dopasowania do wzorca jest szybsze. W rezultacie korzyści w zakresie wydajności wynikające z kompilowania wyrażeń regularnych rosną proporcjonalnie do liczby wywoływanych metod wyrażeń regularnych.  
  
 Podsumowując, zaleca się używać interpretowanych wyrażeń regularnych, kiedy stosunkowo rzadko są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Zaleca się używać skompilowanych wyrażeń regularnych, kiedy stosunkowo często są wywoływane metody wyrażeń regularnych z określonym wyrażeniem regularnym. Dokładny próg, przy którym mniejsza szybkość wykonywania interpretowanych wyrażeń regularnych przewyższa korzyści z redukcji czasu uruchamiania, lub próg, przy którym wolniejsze uruchamianie skompilowanych wyrażeń regularnych przewyższa korzyści z większej szybkości wykonywania, jest trudny do określenia. Zależy to od wielu czynników, w tym od złożoności wyrażenia regularnego i konkretnych danych, które to wyrażenie przetwarza. Aby określić, czy interpretowane lub skompilować wyrażeń regularnych oferują najlepszą wydajność dla danego scenariusza określonej aplikacji, można użyć <xref:System.Diagnostics.Stopwatch> klasy do porównania czas wykonywania.  
  
 Poniższy przykład porównuje wydajności skompilowany i interpretowany wyrażeń regularnych podczas odczytywania pierwszych dziesięciu zdań i podczas odczytywania wszystkich zdań w tekście Theodore Dreiser *Financier*. Dane wyjściowe z przykładu pokazują, że przy zaledwie dziesięciu wywołaniach metod dopasowania wyrażenia regularnego interpretowane wyrażenie regularne oferuje lepszą wydajność niż skompilowane wyrażenie regularne. Jednak skompilowane wyrażenie regularne oferuje lepszą wydajność dla dużej liczby wywołań (w tym przypadku ponad 13 000).  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 Wzorzec wyrażenia regularnego używane w tym przykładzie `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|<code>(\r?\n)&#124;,?\s)</code>|Dopasowanie do zera lub jednego znaku powrotu karetki, po którym występuje znak nowego wiersza, albo do zera lub jednego przecinka, po którym występuje znak odstępu.|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Dopasowanie do zera lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym występuje zero albo jeden znak powrotu karetki i znak nowego wiersza lub zero albo jeden przecinek, po którym następuje znak odstępu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`[.?:;!]`|Dopasowanie do kropki, znaku zapytania, dwukropka, średnika lub wykrzyknika.|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>Wyrażenia regularne: kompilowane do zestawu.  
 .NET umożliwia również tworzenie zestawu, który zawiera skompilowane wyrażenia regularnego. Przenosi to czynnik wpływający na wydajność kompilowania wyrażeń regularnych z czasu wykonywania na czas projektowania. Jednak to także wiąże się z dodatkową pracą: konieczne jest zdefiniowanie wyrażane regularnych z wyprzedzeniem i skompilowanie ich do zestawu. Kompilator może następnie odwołać się do tego zestawu podczas kompilowania kodu źródłowego, który używa wyrażeń regularnych zestawu. Każdy skompilowane wyrażenia regularnego w zestawie jest reprezentowany przez klasę, która jest pochodną <xref:System.Text.RegularExpressions.Regex>.  
  
 Aby skompilować wyrażeń regularnych do zestawu, należy wywołać <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> — metoda i przekaż go, tablicy <xref:System.Text.RegularExpressions.RegexCompilationInfo> obiekty reprezentujące wyrażeń regularnych do skompilowania, i <xref:System.Reflection.AssemblyName> obiekt, który zawiera informacje na temat zestawu jako utworzony.  
  
 Zaleca się, aby kompilować wyrażenia regularne do zestawu w następujących sytuacjach:  
  
-   Jeśli jesteś deweloperem składników, który chce utworzyć bibliotekę wyrażeń regularnych do wielokrotnego użytku.  
  
-   Jeśli oczekujesz, że metody dopasowania do wzorca wyrażenia regularnego będą wywoływane nieokreśloną liczbę razy — od jednego lub dwóch wywołań do kilku tysięcy wywołań. W przeciwieństwie do skompilowanych lub interpretowanych wyrażeń regularnych, wyrażenia regularne, które są kompilowane do oddzielnych zestawów, oferują stałą wydajność bez względu na liczbę wywołań metody.  
  
 Jeśli skompilowane wyrażenia regularne są używane w celu optymalizacji wydajności, nie należy używać odbicia w celu utworzenia zestawu, załadowania aparatu wyrażeń regularnych i wykonania jego metod dopasowania do wzorca. Wymaga to unikania dynamicznego kompilowania wzorców wyrażeń regularnych i określenia wszelkich opcji dopasowania do wzorca (np. z uwzględnieniem wielkości liter) w czasie tworzenia zestawu. Wymaga to również odseparowania kodu, który tworzy zestaw, od kodu, który używa wyrażenia regularnego.  
  
 W poniższym przykładzie pokazano, w jaki sposób utworzyć zestaw zawierający skompilowane wyrażenie regularne. Tworzy zestaw o nazwie `RegexLib.dll` z klasy pojedyncze wyrażenie regularne, `SentencePattern`, zawierający wyrażenia regularnego dopasowanie zdanie wzorzec używany w [interpretowane vs. Skompilowane wyrażenia regularne](#Interpreted) sekcji.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 Podczas kompilowania do pliku wykonywalnego i uruchom przykład tworzy zestaw o nazwie `RegexLib.dll`. Wyrażenie regularne jest reprezentowany przez klasę o nazwie `Utilities.RegularExpressions.SentencePattern` która jest pochodną <xref:System.Text.RegularExpressions.Regex>. W poniższym przykładzie użyto następnie skompilowane wyrażenia regularnego do wyodrębnienia zdań w tekście Theodore Dreiser *Financier*.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [Powrót do początku](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>Przejmowanie kontroli nad wycofywaniem  
 Zazwyczaj aparat wyrażeń regularnych używa progresji liniowej do przechodzenia przez ciąg wejściowy i porównywania go ze wzorcem wyrażenia regularnego. Jednakże, gdy Kwantyfikatory nieokreślony, takie jak `*`, `+`, i `?` są używane w wzorzec wyrażenia regularnego, aparat wyrażeń regularnych może dać część pomyślne wyniki pasujące częściowo i powrócić do poprzednio zapisanego stanu Aby wyszukać pomyślnego dopasowania dla całego wzorca. Proces ten jest znany pod nazwą wycofywania.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na śledzenie wsteczne, zobacz [szczegóły zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) i [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Aby uzyskać szczegółowe omówienie śledzenie wsteczne, zobacz [optymalizacji wydajności wyrażenie regularne, część II: biorąc bezpłatnie z śledzenie wsteczne](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) w blogu zespołu BCL.  
  
 Obsługa wycofywania daje wyrażeniom regularnym duże możliwości i elastyczność. Dodatkowo odpowiedzialność za kontrolowanie operacji aparatu wyrażeń regularnych spada na deweloperów wyrażeń regularnych. Ponieważ deweloperzy często nie są tego świadomi, błędne użycie wycofywania lub nadmierne poleganie na wycofywaniu często odgrywa najbardziej znaczącą rolę w zmniejszeniu wydajności wyrażeń regularnych. W scenariuszu najgorszego przypadku czas wykonywania może podwajać się dla każdego dodatkowego znaku w ciągu wejściowym. W rzeczywistości przy nadmiernym wykorzystaniu wycofywania łatwo jest stworzyć programowy odpowiednik pętli nieskończonej, jeżeli dane wejściowe niemal pasują do wzorca wyrażenia regularnego; przetwarzanie relatywnie krótkiego ciągu wejściowego może zająć aparatowi wyrażeń regularnych kilka godzin, a nawet dni.  
  
 Często efektem użycia wycofywania jest obniżenie wydajności w aplikacjach, mimo że używanie wycofywania nie jest niezbędne dla dopasowania. Na przykład, wyrażenie regularne `\b\p{Lu}\w*\b` dopasowuje wszystkie słowa zaczynające się wielką literę, jak to pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-|-|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\p{Lu}`|Dopasowanie do dowolnej wielkiej litery.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Ponieważ granica wyrazu nie jest tym samym co znak słowa ani jego podzbiorem, nie ma możliwości, aby aparat wyrażeń regularnych przekroczył granicę wyrazu podczas dopasowywania znaków słowa. Oznacza to, że dla tego wyrażenia regularnego wycofywanie może nigdy nie przyczynić się do sukcesu jakiegokolwiek dopasowania, może za to obniżyć wydajność, ponieważ aparat wyrażeń regularnych musi zapisać swój stan podczas każdego pomyślnie zakończonego wstępnego dopasowania znaku słowa.  
  
 Jeśli okaże się, że śledzenie wsteczne nie jest konieczne, należy ją wyłączyć za pomocą `(?>``subexpression``)` element języka. W poniższym przykładzie jest analizowana składnia ciągu wejściowego przy użyciu dwóch wyrażeń regularnych. Pierwsza strona, `\b\p{Lu}\w*\b`, opiera się na śledzenie wsteczne. Druga Strona, `\b\p{Lu}(?>\w*)\b`, wyłącza śledzenie wsteczne. Jak wynika z przykładu, oba wyrażenia regularne dały ten sam wynik.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 W wielu przypadkach wycofywanie jest niezbędne dla dopasowania wzorca wyrażenia regularnego do tekstu wejściowego. Należy pamiętać, że nadmierne używanie wycofywania może poważnie obniżyć wydajność i stworzyć wrażanie, ze aplikacja przestała odpowiadać. W szczególności ma to miejsce, kiedy kwantyfikatory są zagnieżdżane i tekst, który pasuje do zewnętrznego podwyrażenia, jest podzbiorem tekstu, który pasuje do wewnętrznego podwyrażenia.  
  
> [!WARNING]
>  Oprócz unikania nadmiernego wykorzystania wycofywania należy używać funkcji limitu czasu, aby zagwarantować, że nadmierne używanie wycofywania nie obniży poważnie wydajności wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [wartości limitu czasu użycia](#Timeouts) sekcji.  
  
 Na przykład wzorzec wyrażenia regularnego `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` jest przeznaczony do dopasowania liczby części, która składa się z co najmniej jeden znak alfanumeryczny. Jakiekolwiek dodatkowe znaki mogą być znakami alfanumerycznymi, łącznikami, podkreśleniami lub kropkami, ale ostatni znak musi być alfanumeryczny. Znak dolara przerywa numer części. W niektórych przypadkach ten wzorzec wyrażenia regularnego może pokazać bardzo niską wydajnością, ponieważ są zagnieżdżone Kwantyfikatory i Podwyrażenie `[0-9A-Z]` jest podzbiorem Podwyrażenie `[-.\w]*`.  
  
 W takich przypadkach można zoptymalizować wydajność wyrażenia regularnego, usuwając zagnieżdżone kwantyfikatory i zastępując zewnętrzne podwyrażenie asercją wyprzedzającą lub wsteczną o zerowej szerokości. Asercje wyprzedzające i wsteczne są kotwicami; nie przesuwają wskaźnika w ciągu wejściowym, ale „patrzą” do przodu lub wstecz, aby sprawdzić, czy określony warunek został spełniony. Na przykład można przepisany wyrażenia regularnego numer części `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Definicję tego wzorca wyrażenia regularnego pokazano w poniższej tabeli.  
  
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
  
 Język wyrażeń regularnych programu .NET obejmuje następujące elementy języka, których można użyć w celu wyeliminowania kwantyfikatorami zagnieżdżonymi. Aby uzyskać więcej informacji, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
|Element języka|Opis|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|Pozytywna asercja wyprzedzająca o zerowej szerokości. Szukaj przed bieżącą pozycję, aby określić, czy `subexpression` pasującej do ciągu wejściowego.|  
|`(?!` `subexpression` `)`|Negatywna asercja wyprzedzająca o zerowej szerokości. Szukaj przed bieżącą pozycję, aby określić, czy `subexpression` nie pasuje do ciągu wejściowego.|  
|`(?<=` `subexpression` `)`|Pozytywna asercja wsteczna o zerowej szerokości. Szukaj za bieżącą pozycję, aby określić, czy `subexpression` pasującej do ciągu wejściowego.|  
|`(?<!` `subexpression` `)`|Negatywna asercja wsteczna o zerowej szerokości. Szukaj za bieżącą pozycję, aby określić, czy `subexpression` nie pasuje do ciągu wejściowego.|  
  
 [Powrót do początku](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>Używanie wartości limitu czasu  
 Jeśli wyrażenie regularne przetwarza dane wejściowe, które niemal pasują do wzorca wyrażenia regularnego, często może nadmiernie używać wycofywania, co znacznie wpływa na wydajność. Oprócz dokładnego rozważenia użycia wycofywania i przetestowania wyrażenia regularnego pod kątem niemal dopasowanych danych wejściowych, zawsze należy ustawić wartość limitu czasu, aby zagwarantować, że efekt nadmiernego używania wycofywania, jeżeli wystąpi, będzie jak najmniejszy.  
  
 Interwał limitu czasu wyrażenia regularnego określa czas, przez jaki aparat wyrażeń regularnych będzie szukał pojedynczego dopasowania, zanim zostanie przekroczony limit czasu. Domyślny limit czasu wynosi <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, co oznacza, że wyrażenie regularne zostanie nie upłynął limit czasu. Można zastąpić tę wartość i zdefiniować interwał limitu czasu w następujący sposób:  
  
-   Podając wartości limitu czasu podczas tworzenia wystąpienia można <xref:System.Text.RegularExpressions.Regex> obiektu przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktora.  
  
-   Przez wywołanie metody statycznej wzorca dopasowania metody, takie jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, która zawiera `matchTimeout` parametru.  
  
-   Dla skompilowanych wyrażeń regularnych, które są tworzone przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> — metoda, przez wywołanie konstruktora, który ma parametr typu <xref:System.TimeSpan>.  
  
 Jeśli zdefiniowano interwał limitu czasu i nie znaleziono dopasowania na końcu tego zakresu, metoda wyrażenia regularnego zgłasza <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> wyjątku. W obsłudze wyjątków można wybrać ponowienie próby dopasowywania z dłuższym interwałem limitu czasu, zrezygnować z próby dopasowania i założyć, że dopasowanie nie istnieje, lub zrezygnować z próby dopasowania i zarejestrować informacje o wyjątku na potrzeby późniejszej analizy.  
  
 W poniższym przykładzie zdefiniowano `GetWordData` metodę, która tworzy wyrażenia regularnego z interwał limitu czasu milisekund 350 do obliczenia liczbę słów i średnia liczba znaków w edytorze w dokumencie tekstowym. Jeśli upłynie limit czasu operacji dopasowywania, interwał limitu czasu jest zwiększana o 350 milisekund i <xref:System.Text.RegularExpressions.Regex> obiekt jest ponownie skonkretyzowanym. Jeżeli nowy interwał limitu czasu przekroczy 1 sekundę, metoda ponownie zgłosi wyjątek do obiektu wywołującego.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [Powrót do początku](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>Przechwytywanie tylko wtedy, gdy jest to konieczne  
 Wyrażeń regularnych programu .NET obsługuje wiele konstrukcji grupowania, które pozwalają na grupowanie wzorzec wyrażenia regularnego do użyto jednego lub więcej. Konstrukcji grupowania najczęściej używane w języku wyrażenie regularne .NET jest `(` *Podwyrażenie*`)`, który definiuje grupę przechwyconą numerowane i `(?<` *nazwa* `>` *Podwyrażenie*`)`, który definiuje nazwaną grupę przechwytywania. Konstrukcje grupujące są niezbędne do tworzenia odwołań wstecznych i do definiowania podwyrażeń, do których jest stosowany kwantyfikator.  
  
 Jednak zastosowanie tych elementów języka jest kosztowne. Spowodują one <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości można wypełniać za pomocą najnowszej bez nazwy lub o nazwie przechwytywanie, a jeśli przechwyceniu konstrukcji grupowania pojedynczego wiele podciągów w ciągu wejściowym wypełnić również <xref:System.Text.RegularExpressions.CaptureCollection>obiektu zwróconego przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości określonej grupy przechwytywania w wielu <xref:System.Text.RegularExpressions.Capture> obiektów.  
  
 Często konstrukcje grupujące są używane w wyrażeniach regularnych tylko po to, aby można było zastosować do nich kwantyfikatory, i grupy przechwytywane przez te podwyrażenia nie są następnie używane. Na przykład, wyrażenie regularne `\b(\w+[;,]?\s?)+[.?!]` zaprojektowano w celu przechwycenia całe zdanie. W poniższej tabeli opisano elementy języka, w tym wzorzec wyrażenia regularnego i ich wpływ na <xref:System.Text.RegularExpressions.Match> obiektu <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`[;,]?`|Dopasowanie do zera lub jednego przecinka albo średnika.|  
|`\s?`|Dopasowuje zero lub jeden znak odstępu.|  
|`(\w+[;,]?\s?)+`|Dopasowanie do jednego lub większej liczby wystąpień jednego lub większej liczby znaków słowa, po którym następuje opcjonalny przecinek lub średnik, po którym następuje opcjonalny znak odstępu. To definiuje pierwszą grupę przechwytywania, która jest niezbędna, aby kombinacja wielu znaków słowa (tzn. słowo), po których następuje opcjonalny znak interpunkcyjny, była powtarzana do momentu, kiedy aparat wyrażeń regularnych osiągnie koniec zdania.|  
|`[.?!]`|Dopasowanie do kropki, znaku zapytania lub wykrzyknika.|  
  
 Jak przedstawiono na poniższym przykładzie, po znalezieniu dopasowania, zarówno <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> obiekty są wypełniane przy użyciu przechwytywane z dopasowania. W takim przypadku grupę przechwyconą `(\w+[;,]?\s?)` istnieje, aby `+` kwantyfikatora może odnosić się do niego, dzięki czemu wzorzec wyrażenia regularnego do dopasowania każdego wyrazu w zdaniu na wyraz. W przeciwnym razie dopasowanie nastąpi dla ostatniego wyrazu w zdaniu.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 Kiedy używa się podwyrażeń tylko w celu zastosowania do nich kwantyfikatorów, a przechwytywany tekst nie jest ważny, należy wyłączyć przechwytywanie grup. Na przykład `(?:``subexpression``)` element języka uniemożliwia Przechwytywanie podciągów grupy, do którego jest stosowany. W poniższym przykładzie wzorzec wyrażenia regularnego z poprzedniego przykładu jest zmieniana na `\b(?:\w+[;,]?\s?)+[.?!]`. Jak pokazano na dane wyjściowe, uniemożliwia aparat wyrażenie regularne wypełnianie <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 Przechwytywanie można wyłączyć na jeden z poniższych sposobów:  
  
-   Użyj `(?:``subexpression``)` element języka. Ten element zapobiega przechwytywaniu dopasowanych podciągów w grupie, do której jest stosowany. Nie wyłącza przechwytywania podciągów w grupach zagnieżdżonych.  
  
-   Użyj <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> opcji. Wyłącza wszystkie nienazwane lub niejawne przechwytywania we wzorcu wyrażenia regularnego. Tej opcji tylko podciągi zgodnych o nazwie grupy zdefiniowane z `(?<``name``>``subexpression``)` , można przechwycić element języka. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Flagi mogą zostać przekazane do `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub `options` parametr <xref:System.Text.RegularExpressions.Regex> statycznej metody dopasowania.  
  
-   Użyj `n` opcji `(?imnsx)` element języka. Powoduje to wyłączenie wszystkich nienazwanych lub niejawnych przechwytywań od miejsca we wzorcu wyrażenia regularnego, w którym znajduje się ten element. Przechwytywane są wyłączone albo aż do zakończenia wzorca lub do czasu `(-n)` opcja umożliwia przechwytywanie bez nazwy ani niejawnych. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).  
  
-   Użyj `n` opcji `(?imnsx:``subexpression``)` element języka. Ta opcja powoduje wyłączenie wszystkich nienazwanych lub niejawne przechwytywania w `subexpression`. Przechwytywania przez jakiekolwiek nienazwane lub niejawne zagnieżdżone grupy przechwytywania również są wyłączone.  
  
 [Powrót do początku](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Sprawdza, czy implementacja aparat wyrażeń regularnych programu .NET. W tym temacie skupiono się na elastyczności wyrażeń regularnych i wyjaśniono odpowiedzialność deweloperów za zapewnienie wydajnych i niezawodnych operacji aparatu wyrażeń regularnych.|  
|[Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Informacje, co to jest wycofywanie i jak wpływa na wydajność wyrażeń regularnych oraz analiza elementów języka, które dostarczają alternatywy dla wycofywania.|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera opis elementów języka wyrażeń regularnych programu .NET i łącza do szczegółowa dokumentacja dla każdego elementu języka.|
