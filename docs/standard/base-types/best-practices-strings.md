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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 50127f24bfee0c2fe49da8f285e5052d2f753696
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934939"
---
# <a name="best-practices-for-using-strings-in-net"></a>Najlepsze rozwiązania dotyczące używania ciągów w programie .NET
<a name="top"></a>Platforma .NET zapewnia rozbudowaną obsługę tworzenia zlokalizowanych i globalnych aplikacji oraz ułatwia stosowanie Konwencji dla bieżącej kultury lub określonej kultury podczas wykonywania typowych operacji, takich jak sortowanie i wyświetlanie ciągów. Jednak sortowanie lub Porównywanie ciągów nie zawsze jest operacją zależną od kultury. Na przykład ciągi, które są używane wewnętrznie przez aplikację zwykle, powinny być obsługiwane identycznie we wszystkich kulturach. Gdy dane niezależne od kultury, takie jak tagi XML, Tagi HTML, nazwy użytkowników, ścieżki plików i nazwy obiektów systemowych, są interpretowane tak, jakby były wrażliwe na kulturę, kod aplikacji może podlegać rozdrobnym usterkom, złej wydajności i, w niektórych przypadkach, Problemy z zabezpieczeniami.  
  
 W tym temacie opisano metody sortowania, porównywania i wielkości liter w programie .NET, przedstawiono zalecenia dotyczące wybierania odpowiedniej metody obsługi ciągów i zawiera dodatkowe informacje na temat metod obsługi ciągów. Bada także, jak sformatowane dane, takie jak dane liczbowe oraz dane daty i godziny, są obsługiwane na potrzeby wyświetlania i przechowywania.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Zalecenia dotyczące użycia ciągów](#recommendations_for_string_usage)  
  
- [Jawne określanie porównywania ciągów](#specifying_string_comparisons_explicitly)  
  
- [Szczegóły porównania ciągów](#the_details_of_string_comparison)  
  
- [Wybieranie elementu członkowskiego StringComparison dla wywołania metody](#choosing_a_stringcomparison_member_for_your_method_call)  
  
- [Typowe metody porównywania ciągów w programie .NET](#common_string_comparison_methods_in_the_net_framework)  
  
- [Metody, które pośrednio wykonują Porównywanie ciągów](#methods_that_perform_string_comparison_indirectly)  
  
- [Wyświetlanie i utrwalanie sformatowanych danych](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>Zalecenia dotyczące korzystania z ciągów  
 Podczas opracowywania przy użyciu platformy .NET należy przestrzegać następujących prostych zaleceń w przypadku używania ciągów:  
  
- Używaj przeciążeń, które jawnie określają reguły porównywania ciągów dla operacji na ciągach. Zwykle wymaga to wywołania przeciążenia metody z parametrem typu <xref:System.StringComparison>.  
  
- Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub<xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> do porównań jako bezpiecznie domyślnego dla dopasowania ciągu niezależny od kultury.  
  
- Używaj porównań <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> z <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> lub w celu uzyskania lepszej wydajności.  
  
- Użyj operacji na ciągach, które <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> są oparte na momencie wyświetlania danych wyjściowych dla użytkownika.  
  
- Używaj niejęzykowych <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartościowych zamiast operacji na ciągach w <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> zależności od tego, kiedy porównanie jest istotne dla języka (na przykład).  
  
- Użyj metody zamiast <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody podczas normalizacji ciągów do porównania. <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>  
  
- Użyj przeciążenia metody, <xref:System.String.Equals%2A?displayProperty=nameWithType> aby sprawdzić, czy dwa ciągi są równe.  
  
- Użyj metod <xref:System.String.CompareTo%2A?displayProperty=nameWithType> i, aby sortować ciągi, a nie sprawdzaj równości. <xref:System.String.Compare%2A?displayProperty=nameWithType>  
  
- Użyj formatowania z uwzględnieniem kultury, aby wyświetlić dane niebędące ciągami, takie jak liczby i daty, w interfejsie użytkownika. Używaj formatowania z [kulturą niezmienną](xref:System.Globalization.CultureInfo.InvariantCulture) , aby utrwalać dane niebędące ciągami w postaci ciągów.  
  
 W przypadku używania ciągów należy unikać następujących praktyk:  
  
- Nie należy używać przeciążeń, które nie jawnie lub niejawnie określają reguły porównywania ciągów dla operacji na ciągach.  
  
- Nie używaj <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> w większości przypadków operacji na ciągach. Jednym z kilku wyjątków jest to, że w przypadku utrwalania w sposób istotny, ale kulturalnie niezależny od dane.  
  
- Nie należy używać przeciążenia <xref:System.String.Compare%2A?displayProperty=nameWithType> metody lub <xref:System.String.CompareTo%2A> i testu dla zwracanej wartości zero, aby określić, czy dwa ciągi są równe.  
  
- Nie używaj formatowania z uwzględnieniem kultury, aby zachować dane liczbowe lub dane daty i godziny w postaci ciągu.  
  
 [Powrót do początku](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>Jawne określenie porównywania ciągów  
 Większość metod manipulowania ciągami w .NET jest przeciążona. Zazwyczaj co najmniej jedno Przeciążenie przyjmuje ustawienia domyślne, natomiast inne nie akceptują żadnych ustawień domyślnych, a zamiast tego definiują precyzyjne metody porównywania ciągów lub manipulowania nimi. Większość metod, które nie bazują na wartościach domyślnych, zawiera parametr typu <xref:System.StringComparison>, który jest wyliczeniem, które jawnie określa reguły dla porównania ciągów przez kulturę i wielkość liter. W poniższej tabeli opisano <xref:System.StringComparison> elementy członkowskie wyliczenia.  
  
|StringComparison element członkowski|Opis|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|Wykonuje porównanie z rozróżnianiem wielkości liter przy użyciu bieżącej kultury.|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu bieżącej kultury.|  
|<xref:System.StringComparison.InvariantCulture>|Wykonuje porównanie z rozróżnianiem wielkości liter przy użyciu niezmiennej kultury.|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter przy użyciu niezmiennej kultury.|  
|<xref:System.StringComparison.Ordinal>|Wykonuje porównanie porządkowe.|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|Wykonuje porównanie porządkowe bez uwzględniania wielkości liter.|  
  
 Na przykład <xref:System.String.IndexOf%2A> Metoda, która zwraca indeks podciągu <xref:System.String> w obiekcie, który pasuje do znaku lub ciągu, ma dziewięć przeciążeń:  
  
- <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>, i <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, która domyślnie wykonuje numer porządkowy (bez uwzględniania wielkości liter i kulturowo), wyszukiwanie znaku w ciągu.  
  
- <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, które domyślnie wykonują wyszukiwanie podciągów z uwzględnieniem wielkości liter i z uwzględnieniem ustawień kulturowych w ciągu.  
  
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, które zawierają parametr typu <xref:System.StringComparison> , który umożliwia określenie formy porównania.  
  
 Zalecamy wybranie przeciążenia, które nie używa wartości domyślnych, z następujących powodów:  
  
- Niektóre przeciążenia z domyślnymi parametrami (te, które <xref:System.Char> wyszukują w wystąpieniu ciągu) wykonują porównanie porządkowe, natomiast inne (te, które wyszukują ciąg w wystąpieniu ciągu) są zależne od kultury. Trudno jest pamiętać, która metoda używa tej wartości domyślnej i łatwej do odróżnienia przeciążenia.  
  
- Zamiar kodu, który opiera się na wartościach domyślnych dla wywołań metod, nie jest jasne. W poniższym przykładzie, który opiera się na wartościach domyślnych, trudno jest wiedzieć, czy deweloper rzeczywiście zaproponował numer porządkowy, czy też jest porównywany z dwoma ciągami, czy `protocol` też różnica wielkości liter między i "http" może spowodować równość testów do zwrócenia `false`.  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 Ogólnie rzecz biorąc zalecamy wywołanie metody, która nie polega na wartościach domyślnych, ponieważ sprawia, że zamiar kodu jest niejednoznaczny. Dzięki temu kod staje się bardziej czytelny i łatwiejszy w debugowaniu i obsłudze. Poniższy przykład dotyczy odpowiedzi na pytania dotyczące poprzedniego przykładu. Sprawia, że jest ono jasne, że jest używane porównanie porządkowe oraz że różnice w przypadku są ignorowane.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [Powrót do początku](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>Szczegóły dotyczące porównania ciągów  
 Porównanie ciągów jest sercem wielu operacji związanych z ciągami, szczególnie sortowania i testowania pod kątem równości. Ciągi są sortowane w określonej kolejności: Jeśli "my" pojawia się przed "String" w posortowanej liście ciągów, "my" musi być porównywany z "ciągiem" lub "w". Ponadto porównanie niejawnie definiuje równość. Operacja porównywania zwraca wartość zero dla ciągów, które uzna za równe. Dobrą interpretacją jest to, że żaden ciąg nie jest mniejszy od drugiego. Większość znaczących operacji obejmujących ciągi zawierają jedną lub obie te procedury: porównanie z innym ciągiem i wykonywanie dobrze zdefiniowanej operacji sortowania.  

> [!NOTE]
> Można pobrać [tabele wagi sortowania](https://www.microsoft.com/download/details.aspx?id=10921), zestaw plików tekstowych, które zawierają informacje o wagach znaków używanych w operacjach sortowania i porównywania dla systemów operacyjnych Windows, a także [domyślną tabelę elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), Najnowsza wersja tabeli Sortuj wagi dla systemów Linux i macOS. Określona wersja tabeli posortowanych wag w systemie Linux i macOS zależy od wersji [międzynarodowych składników dla bibliotek Unicode](http://site.icu-project.org/) zainstalowanych w systemie. Aby uzyskać informacje na temat wersji ICU i wersji standardu Unicode, które implementują, zobacz [pobieranie ICU](http://site.icu-project.org/download).

 Jednak Ocena dwóch ciągów dla równości lub kolejności sortowania nie daje pojedynczego prawidłowego wyniku; wyniki są zależne od kryteriów używanych do porównywania ciągów. W szczególności porównania ciągów, które są numerami porządkowymi lub które są oparte na konwencjach wielkości liter i sortowania bieżącej kultury lub [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture) (niezależny od kultury opartej na języku angielskim) mogą generować różne wyniki.  

Ponadto porównania ciągów przy użyciu różnych wersji programu .NET lub programu .NET w różnych systemach operacyjnych lub wersjach systemu operacyjnego mogą zwracać różne wyniki. Aby uzyskać więcej informacji, zobacz [ciągi i standard Unicode](xref:System.String#Unicode). 

<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>Porównywanie ciągów, które używają bieżącej kultury  
 Jedno kryterium obejmuje stosowanie Konwencji bieżącej kultury podczas porównywania ciągów. Porównania, które są oparte na bieżącej kulturze, wykorzystują bieżącą kulturę lub ustawienia regionalne wątku. Jeśli kultura nie jest ustawiona przez użytkownika, domyślnie jest to ustawienie w oknie **Opcje regionalne** w panelu sterowania. Należy zawsze używać porównań, które są oparte na bieżącej kulturze, gdy dane są istotne dla kultury, a kiedy odzwierciedlają interakcję z użytkownikiem uwzględniającą kulturę.  
  
 Jednak porównanie i wielkość liter w programie .NET zmieniają się po zmianie kultury. Dzieje się tak, gdy aplikacja jest wykonywana na komputerze z inną kulturą niż komputer, na którym aplikacja została opracowana, lub gdy wątek wykonawczy zmienia jego kulturę. To zachowanie jest zamierzone, ale pozostaje nieoczywista dla wielu deweloperów. Poniższy przykład ilustruje różnice w kolejności sortowania między Stanami USA Angielskie ("en-US") i szwedzki ("SV-SE"). Zwróć uwagę, że słowa "Ångström", "Windows" i "Visual Studio" pojawiają się w różnych pozycjach w posortowanych tablicach ciągów.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 Porównania bez uwzględniania wielkości liter, które używają bieżącej kultury, są takie same jak porównania uwzględniające kulturę, z tą różnicą, że ignorowanie wielkości liter jako podyktowanych przez bieżącą kulturę wątku. Takie zachowanie może być również w porządku sortowania.  
  
 Porównania, które używają bieżącej semantyki kultury, są domyślne dla następujących metod:  
  
- <xref:System.String.Compare%2A?displayProperty=nameWithType>przeciążenia, które nie zawierają <xref:System.StringComparison> parametru.  
  
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>przeciążenia.  
  
- Metoda Domyślna <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> oraz Metoda z `null` parametrem<xref:System.Globalization.CultureInfo> .  
  
- Metoda Domyślna <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> oraz Metoda z `null` parametrem<xref:System.Globalization.CultureInfo> .  
  
- <xref:System.String.IndexOf%2A?displayProperty=nameWithType>przeciążenia, które akceptują <xref:System.String> jako parametr wyszukiwania i nie <xref:System.StringComparison> mają parametru.  
  
- <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>przeciążenia, które akceptują <xref:System.String> jako parametr wyszukiwania i nie <xref:System.StringComparison> mają parametru.  
  
 W każdym przypadku zalecamy wywołanie przeciążenia, które ma <xref:System.StringComparison> parametr, aby przeznaczenie metody zostało wyczyszczone.  
  
 Subtelne i nietak rozdrobne usterki mogą naciągać się, gdy dane nielingwistyczne nie są interpretowane językowo lub gdy dane ciągów z określonej kultury są interpretowane przy użyciu konwencji innej kultury. Przykładem kanonicznym jest problem z tureckim I.  
  
 Dla niemal wszystkich alfabetów łacińskich, w tym dla Stanów Zjednoczonych Angielski, znak "i" (\u0069) to mała wersja znaku "I" (\u0049). Ta reguła wielkości liter jest szybko zmieniana na wartość domyślną dla programowania osób w takiej kulturze. Alfabet turecki ("TR-TR") zawiera jednak znak "i" (\u0130), czyli "i" w Wielkiej wersji "i". Turecki zawiera również małe litery "i bez kropki", "ı" (\u0131), które zaczynają się od litery "I". To zachowanie występuje również w kulturze azerski ("AZ").  
  
 W związku z tym, założenia dotyczące Wielkiej litery "i" lub "lowercasing" nie są prawidłowe we wszystkich kulturach. Jeśli użyjesz domyślnych przeciążeń dla procedur porównywania ciągów, będą one podlegać wariancji między kulturami. Jeśli dane, które mają być porównane, nie są językowe, użycie domyślnych przeciążeń może dawać niepożądane wyniki, ponieważ poniżej podjęto próbę wykonania porównania ciągów "File" i "FILE" bez uwzględniania wielkości liter.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 To porównanie może spowodować znaczne problemy, jeśli kultura jest przypadkowo używana w ustawieniach zabezpieczeń, jak w poniższym przykładzie. Wywołanie metody, takie jak `IsFileURI("file:")` Returns `true` , jeśli bieżąca kultura jest w Stanach Zjednoczonych Angielski, ale `false` Jeśli bieżąca kultura to turecki. W takim przypadku, w systemach tureckich, ktoś może obejść środki bezpieczeństwa, które blokują dostęp do identyfikatorów URI bez uwzględniania wielkości liter zaczynających się od "FILE:".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 W tym przypadku, ponieważ "plik:" ma być interpretowany jako niezależny od języka, kod powinien być zapisany, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>Operacje na ciągach porządkowych  
 Określenie wartości <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> lub w wywołaniu metody oznacza, że jest to porównanie w języku innym niż język, w którym funkcje języków naturalnych są ignorowane. <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> Metody, które są wywoływane z <xref:System.StringComparison> tymi wartościami, podejmuje decyzje dotyczące operacji na ciągach prostych w przypadku porównywania bajtów zamiast wielkości liter lub tabel równoważności, które są sparametryzowane przez kulturę. W większości przypadków takie podejście najlepiej pasuje do zamierzonej interpretacji ciągów podczas szybszego wykonywania kodu i bardziej niezawodnego.  
  
 Porównania porządkowe to porównania ciągów, w których każdy bajt każdego ciągu jest porównywany bez interpretacji językowej; na przykład "Windows" nie pasuje do "Windows". Jest to zasadniczo wywołanie funkcji środowiska uruchomieniowego `strcmp` języka C. Użyj tego porównania, gdy kontekst określa, że ciągi powinny być dokładnie dopasowane lub wymagające ostrożnej zgodności z zasadami. Ponadto, porównanie porządkowe jest najszybszą operacją porównywania, ponieważ nie stosuje żadnych reguł lingwistycznych podczas określania wyniku.  
  
 Ciągi w programie .NET mogą zawierać osadzone znaki o wartości null. Jedną z najwyraźniejszych różnic między porównaniem porządkowym i kulturowym (w tym porównaniami korzystającymi z niezmiennej kultury) jest obsługa osadzonych znaków null w ciągu. Te znaki są ignorowane w przypadku używania <xref:System.String.Compare%2A?displayProperty=nameWithType> metod i do wykonywania porównań z uwzględnieniem kultury (w <xref:System.String.Equals%2A?displayProperty=nameWithType> tym porównań, które używają niezmiennej kultury). W związku z tym w porównaniach wrażliwych na kulturę ciągi zawierające osadzone znaki null mogą być traktowane jako równe ciągom, które nie.  
  
> [!IMPORTANT]
> Chociaż metody porównywania ciągów zignorują osadzone znaki null, metody wyszukiwania ciągów <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>takie <xref:System.String.IndexOf%2A?displayProperty=nameWithType>jak <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>,, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> ,, i nie.  
  
 Poniższy przykład wykonuje porównanie z uwzględnieniem kultury ciągu "AA" z podobnym ciągiem, który zawiera kilka osadzonych znaków o wartości null między "A" i "a" i pokazuje, jak dwa ciągi są uważane za równe.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 Jednak ciągi nie są uważane za równe w przypadku używania porównania porządkowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 Porównywanie porządkowe bez uwzględniania wielkości liter jest kolejnym najbardziej rygorystycznym podejściem. Te porównania ignorują większość wielkości liter; na przykład "Windows" dopasowuje "Windows". W przypadku znaków ASCII te zasady są równoważne z <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, z tą różnicą, że ignoruje zwykłe wielkości liter ASCII. W związku z tym każdy znak w [A, Z] (\u0041-\u005A) pasuje do odpowiadającego mu znaku w [a, z] (\u0061-\007A). Wielkość liter poza zakresem ASCII używa tabel niezmiennej kultury. W związku z tym następujące porównanie:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 jest odpowiednikiem (ale szybszym niż) tego porównania:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 Te porównania są nadal bardzo szybkie.  
  
> [!NOTE]
> Zachowanie ciągu w systemie plików, kluczach rejestru i wartościach oraz zmienne środowiskowe najlepiej reprezentowane przez <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>program.  
  
 Zarówno <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> , <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> jak i używają wartości binarnych, są one najlepiej dopasowane do dopasowywania. Gdy nie masz pewności co do ustawień porównania, użyj jednej z tych dwóch wartości. Jednak ze względu na to, że wykonują porównywanie bajt po bajcie, nie sortuje według języka porządku sortowania (na przykład słownika angielskiego), ale według binarnej kolejności sortowania. Wyniki mogą wyglądać nieparzystie w większości kontekstów, jeśli są wyświetlane użytkownikom.  
  
 Semantyka porządkowa jest wartością domyślną <xref:System.String.Equals%2A?displayProperty=nameWithType> dla przeciążeń, które <xref:System.StringComparison> nie zawierają argumentu (łącznie z operatorem równości). W każdym przypadku zalecamy wywołanie przeciążenia z <xref:System.StringComparison> parametrem.  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>Operacje na ciągach, które używają kultury niezmiennej  
 Porównania z kulturą niezmienną używają <xref:System.Globalization.CultureInfo.CompareInfo%2A> właściwości zwróconej przez właściwość statyczną. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> Takie zachowanie jest takie samo w przypadku wszystkich systemów; tłumaczy wszelkie znaki spoza zakresu na to, co jest uważane za równoważne znaki niezmienne. Te zasady mogą być przydatne do obsługi jednego zestawu zachowań ciągów między kulturami, ale często zapewniają nieoczekiwane wyniki.  
  
 Porównania bez uwzględniania wielkości liter z kulturą niezmienną należy używać <xref:System.Globalization.CultureInfo.CompareInfo%2A> właściwości statycznej zwróconej <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> przez właściwość statyczną dla informacji porównawczych. Wszelkie różnice wielkości liter między tymi przetłumaczonymi znakami są ignorowane.  
  
 Porównania, które <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> używają <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> i działają identycznie na ciągach ASCII. Jednak program <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> podejmuje decyzje językowe, które mogą nie być odpowiednie dla ciągów, które muszą być interpretowane jako zestaw bajtów. Obiekt sprawia, <xref:System.String.Compare%2A> że metoda interpretuje niektóre zestawy znaków jako równoważne. `CultureInfo.InvariantCulture.CompareInfo` Na przykład następująca równoważność jest prawidłowa dla niezmiennej kultury:  
  
 InvariantCulture: a + ̊ = a  
  
 Mała litera "a" (\u0061), gdy jest obok znaku ŁĄCZĄCego powyżej znak "+" ̊ "(\u030a), jest interpretowana jako mała litera A z PIERŚCIENIem powyżej znaku" a "(\u00e5). Jak pokazano na poniższym przykładzie, to zachowanie różni się od porównania liczb porządkowych.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 W przypadku interpretacji nazw plików, plików cookie lub innych elementów, w których może się pojawić kombinacja, taka jak "a", porównania porządkowe nadal zapewniają najbardziej przejrzyste i niedopasowane zachowanie.  
  
 W przypadku niezmiennej kultura ma bardzo kilka właściwości, które ułatwiają porównywanie. Jest to porównywane w sposób istotny, który uniemożliwia mu zagwarantowanie pełnego równoważności symbolicznej, ale nie jest to możliwe do wyświetlania w żadnej kulturze. Jedną z kilku powodów użycia <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> do porównania jest utrwalanie uporządkowanych danych dla różnych kulturowo identycznych ekranów. Na przykład jeśli plik danych o dużym rozmiarze zawierający listę posortowanych identyfikatorów dla wyświetlania towarzyszy aplikacji, dodanie do tej listy będzie wymagało wstawienia z sortowaniem w stylu niezmiennym.  
  
 [Powrót do początku](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Wybieranie elementu StringComparison (porównywania ciągów tekstowych) do metody wywołania  
 Poniższa tabela zawiera opis mapowania z kontekstu ciągu semantycznego do <xref:System.StringComparison> elementu członkowskiego wyliczenia.  
  
|Dane|Zachowanie|Odpowiadający system. StringComparison<br /><br /> value|  
|----------|--------------|-----------------------------------------------------|  
|Identyfikatory wewnętrzne z uwzględnieniem wielkości liter.<br /><br /> Identyfikatory z uwzględnieniem wielkości liter w standardach, takich jak XML i HTTP.<br /><br /> Ustawienia związane z zabezpieczeniami z uwzględnieniem wielkości liter.|Identyfikator niebędący językiem, gdzie bajty są dokładnie zgodne.|<xref:System.StringComparison.Ordinal>|  
|Identyfikatory wewnętrzne bez uwzględniania wielkości liter.<br /><br /> Identyfikatory bez uwzględniania wielkości liter w standardach, takich jak XML i HTTP.<br /><br /> Ścieżki plików.<br /><br /> Klucze i wartości rejestru.<br /><br /> Zmienne środowiskowe.<br /><br /> Identyfikatory zasobów (na przykład nazwy uchwytów).<br /><br /> Ustawienia związane z zabezpieczeniami bez uwzględniania wielkości liter.|Identyfikator niebędący językiem, gdzie przypadek jest nieistotny; szczególnie dane przechowywane w większości usług systemu Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|Pewne utrwalone, językowe dane.<br /><br /> Wyświetlanie danych lingwistycznych, które wymagają stałego porządku sortowania.|Kulturowo niezależny od dane, które nadal są istotne dla języka.|<xref:System.StringComparison.InvariantCulture><br /><br /> —lub—<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|Dane wyświetlane użytkownikowi.<br /><br /> Większość danych wejściowych użytkownika.|Dane wymagające lokalnego języka.|<xref:System.StringComparison.CurrentCulture><br /><br /> —lub—<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [Powrót do początku](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>Typowe metody porównywania ciągów w programie .NET  
 W poniższych sekcjach opisano metody, które są najczęściej używane do porównywania ciągów.  
  
### <a name="stringcompare"></a>Funkcja String.Compare  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 Jako że operacja najważniejsza do interpretacji ciągów, wszystkie wystąpienia tych wywołań metod powinny być badane w celu określenia, czy ciągi powinny być interpretowane zgodnie z bieżącą kulturą, czy też odwoływać się od kultury (symbolicznie). Zwykle jest to ostatni i <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> zamiast tego należy użyć porównania.  
  
 Klasa, która jest zwracana <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> przez <xref:System.Globalization.CompareInfo.Compare%2A> właściwość, również zawiera metodę, która zapewnia dużą liczbę pasujących opcji (numer porządkowy, ignorowanie białego znaku, ignorowanie typu kana itd.) za pomocą <xref:System.Globalization.CompareOptions>flagi <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Licznik.  
  
### <a name="stringcompareto"></a>Funkcja String.CompareTo  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 Ta metoda obecnie nie oferuje przeciążenia, które określa <xref:System.StringComparison> typ. Zwykle jest możliwe przekonwertowanie tej metody na zalecaną <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formę.  
  
 Typy, które <xref:System.IComparable> implementują <xref:System.IComparable%601> interfejsy i implementują tę metodę. Ponieważ nie oferuje opcji <xref:System.StringComparison> parametru, implementacja typów często zezwala użytkownikowi na <xref:System.StringComparer> określenie w konstruktorze. W poniższym przykładzie zdefiniowano `FileName` klasę, której Konstruktor klasy <xref:System.StringComparer> zawiera parametr. Ten <xref:System.StringComparer> obiekt jest następnie używany `FileName.CompareTo` w metodzie.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>Funkcja String.Equals  
 Domyślna interpretacja <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>:.  
  
 Klasa umożliwia przetestowanie pod kątem równości przez wywołanie <xref:System.String.Equals%2A> metody statycznej lub przeciążenia lub użycie statycznego operatora równości. <xref:System.String> Przeciążenia i operator domyślnie używają porównania porządkowego. Mimo to nadal zalecamy wywołanie przeciążenia, które jawnie określa typ nawet w <xref:System.StringComparison> przypadku, gdy chcesz wykonać porównanie porządkowe; ułatwia to wyszukiwanie w kodzie dla określonej interpretacji ciągów.  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper i String.ToLower  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 Należy zachować ostrożność w przypadku korzystania z tych metod, ponieważ wymuszanie ciągu do wielkich lub małych liter jest często używane jako mała normalizacja do porównywania ciągów, niezależnie od wielkości liter. Jeśli tak, rozważ użycie porównania bez uwzględniania wielkości liter.  
  
 Dostępne są <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> również metody i.<xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> <xref:System.String.ToUpperInvariant%2A>jest standardowym sposobem normalizacji wielkości liter. Porównania wykonywane przy <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> użyciu są zachowaniem składu dwóch wywołań: wywoływanie <xref:System.String.ToUpperInvariant%2A> dla obu argumentów ciągów i wykonywanie porównania przy użyciu <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 Przeciążenia są również dostępne do przekonwertowania na wielkie i małe litery w określonej kulturze, przekazując <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę kulturę do metody.  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper i Char.ToLower  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 Metody te działają podobnie <xref:System.String.ToUpper%2A?displayProperty=nameWithType> jak metody i <xref:System.String.ToLower%2A?displayProperty=nameWithType> opisane w poprzedniej sekcji.  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith i String.EndsWith  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 Domyślnie obie te metody wykonują porównanie z uwzględnieniem kultury.  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf i String.LastIndexOf  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 Brak spójności w sposobie wykonywania porównań przez domyślne przeciążenia tych metod. Wszystkie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> <xref:System.Char> i <xref:System.String.IndexOf%2A?displayProperty=nameWithType> <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> <xref:System.String> metody, które zawierają parametr, wykonują porównanie porządkowe, ale domyślne i metody, które zawierają parametr, są zależne od kultury <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> prowadzone.  
  
 W przypadku wywołania <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> metody lub <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> i przekazania do niej ciągu w celu zlokalizowania w bieżącym wystąpieniu zalecamy wywołanie <xref:System.StringComparison> przeciążenia, które jawnie określa typ. Przeciążenia, które zawierają <xref:System.Char> argument, nie pozwalają na <xref:System.StringComparison> określenie typu.  
  
 [Powrót do początku](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, które pośrednio wykonują porównywania ciągu  
 Niektóre metody niebędące ciągami, które mają porównanie ciągów jako operacji centralnej <xref:System.StringComparer> używają typu. Klasa zawiera sześć właściwości statycznych, które zwracają <xref:System.StringComparer> wystąpienia, <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> których metody wykonują następujące typy porównań ciągów: <xref:System.StringComparer>  
  
- Porównania ciągów zależnych od kultury przy użyciu bieżącej kultury. Ten <xref:System.StringComparer> obiekt jest zwracany <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> przez właściwość.  
  
- Porównania bez uwzględniania wielkości liter przy użyciu bieżącej kultury. Ten <xref:System.StringComparer> obiekt jest zwracany <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> przez właściwość.  
  
- Porównania niewrażliwe na kulturę przy użyciu reguł porównania wyrazów niezmiennej kultury. Ten <xref:System.StringComparer> obiekt jest zwracany <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> przez właściwość.  
  
- Porównania bez uwzględniania wielkości liter i nieuwzględniania kultur przy użyciu reguł porównania wyrazów niezmiennej kultury. Ten <xref:System.StringComparer> obiekt jest zwracany <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> przez właściwość.  
  
- Porównanie porządkowe. Ten <xref:System.StringComparer> obiekt jest zwracany <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> przez właściwość.  
  
- Porównanie porządkowe bez uwzględniania wielkości liter. Ten <xref:System.StringComparer> obiekt jest zwracany <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> przez właściwość.  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort i Array.BinarySearch  
 Domyślna interpretacja <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>:.  
  
 W przypadku przechowywania danych w kolekcji lub odczytywania utrwalonych danych z pliku lub bazy danych do kolekcji, przełączenie bieżącej kultury może spowodować unieważnienie niezmiennych w kolekcji. <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> Metoda zakłada, że elementy w tablicy, które mają być przeszukiwane, są już posortowane. Aby posortować dowolny element ciągu w tablicy, <xref:System.Array.Sort%2A?displayProperty=nameWithType> Metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> wywołuje metodę w celu uporządkowania poszczególnych elementów. Użycie funkcji porównującej uwzględniającej kulturę może być niebezpieczne, jeśli kultura zmieni się między posortowaną tablicą a jego zawartością jest przeszukiwana. Na przykład, w poniższym kodzie, magazyn i pobieranie działają na porównującej, który jest dostarczany niejawnie przez `Thread.CurrentThread.CurrentCulture` właściwość. Jeśli kultura może zmienić między wywołaniami do `StoreNames` i `DoesNameExist`, a zwłaszcza jeśli zawartość tablicy jest utrwalana między dwoma wywołaniami metod, wyszukiwanie binarne może zakończyć się niepowodzeniem.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 W poniższym przykładzie zostanie wyświetlona zalecana odmiana, która używa tej samej wartości porządkowej (bez uwzględniania kultury) zarówno do sortowania, jak i do przeszukiwania tablicy. Kod zmiany jest widoczny w wierszach oznaczonych `Line A` i `Line B` w dwóch przykładach.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 Jeśli te dane są utrwalane i przenoszone między kulturami, a sortowanie służy do prezentowania tych danych użytkownikowi, można rozważyć użycie <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, który działa w sposób językowy dla lepszych danych wyjściowych użytkownika, ale nie ma wpływ na zmiany w kulturze. Poniższy przykład modyfikuje dwa poprzednie przykłady, aby użyć niezmiennej kultury do sortowania i przeszukiwania tablicy.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>Przykład kolekcji: Hashtable — Konstruktor  
 Ciągi mieszania zawierają drugi przykład operacji, na które ma wpływ, w jaki sposób ciągi są porównywane.  
  
 Poniższy przykład tworzy wystąpienie <xref:System.Collections.Hashtable> obiektu przez przekazanie go do <xref:System.StringComparer> obiektu <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> , który jest zwracany przez właściwość. Ponieważ Klasa <xref:System.StringComparer> , która pochodzi od <xref:System.StringComparer> implementuje <xref:System.Collections.IEqualityComparer> interfejs, jego <xref:System.Collections.IEqualityComparer.GetHashCode%2A> Metoda jest używana do obliczania kodu skrótu ciągów w tabeli skrótów.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [Powrót do początku](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>Wyświetlanie i utrzymanie sformatowanych danych

W przypadku wyświetlania danych niebędących ciągami, takich jak liczby i daty i godziny, sformatuj je przy użyciu ustawień kultury użytkownika. Domyślnie następujące wszystkie używają bieżącej kultury wątku w operacjach formatowania:

- Ciągi interpolowane obsługiwane przez kompilatory [C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) .

- Operacje łączenia ciągów wykorzystujące operatory łączenia [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) lub [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) lub bezpośrednio wywołujące <xref:System.String.Concat%2A?displayProperty=nameWithType> metodę.

- <xref:System.String.Format%2A?displayProperty=nameWithType> Metoda.

- `ToString` Metody typów liczbowych i typów dat i godzin.

Aby jawnie określić, że ciąg powinien być sformatowany przy użyciu konwencji określonej kultury lub [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture), można wykonać następujące czynności:

- Przy użyciu <xref:System.String.Format%2A?displayProperty=nameWithType> metod i `ToString` Wywołaj Przeciążenie, które ma <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> `provider` parametr, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> taki jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> lub, i przekaż go właściwości, <xref:System.Globalization.CultureInfo> wystąpienie, które reprezentuje żądany Kultura lub <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> właściwość.  

- W przypadku łączenia ciągów nie Zezwalaj kompilatorowi na wykonywanie jakichkolwiek niejawnych konwersji. Zamiast tego należy wykonać jawną konwersję, `ToString` wywołując Przeciążenie `provider` z parametrem. Na przykład kompilator niejawnie używa bieżącej kultury podczas konwertowania <xref:System.Double> wartości na ciąg w poniższym C# kodzie:

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  Zamiast tego można jawnie określić kulturę, której konwencje formatowania są używane w konwersji, wywołując <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodę, tak jak w poniższym C# kodzie:

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- W przypadku interpolacji ciągów zamiast przypisywania do <xref:System.String> wystąpienia ciągu interpolowanego, należy przypisać go <xref:System.FormattableString>do. Następnie można wywołać <xref:System.FormattableString.ToString?displayProperty=nameWithType> metodę generującą ciąg wynikowy, który odzwierciedla konwencje bieżącej kultury, lub <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> wywołać metodę, aby utworzyć ciąg wynikowy, który odzwierciedla konwencje określonej kultury. Możesz również przekazać ciąg formatu do metody statycznej <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> , aby utworzyć ciąg wynikowy, który odzwierciedla konwencje niezmiennej kultury. To podejście pokazano w poniższym przykładzie. (Dane wyjściowe z przykładu odzwierciedlają bieżącą kulturę en-US).

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

Dane niebędące ciągami mogą być utrwalane jako dane binarne lub dane sformatowane. Jeśli zdecydujesz się zapisać ją jako sformatowane dane, należy wywołać Przeciążenie metody formatowania, które zawiera `provider` parametr i przekazać go do <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Kultura niezmienna zapewnia spójny format sformatowanych danych, które są niezależne od kultury i maszyny. W przeciwieństwie do utrwalania danych, które są formatowane przy użyciu kultur innych niż kultura niezmienna, ma wiele ograniczeń:  
  
- Dane mogą być bezużyteczne, jeśli są pobierane w systemie, który ma inną kulturę, lub jeśli użytkownik bieżącego systemu zmienia bieżącą kulturę i próbuje pobrać dane.  
  
- Właściwości kultury na określonym komputerze mogą różnić się od wartości standardowych. W dowolnym momencie użytkownik może dostosować ustawienia wyświetlania z uwzględnieniem kultury. W związku z tym sformatowane dane zapisane w systemie mogą nie zostać odczytane, gdy użytkownik dostosowuje ustawienia kulturowe. Przenośność sformatowanych danych między komputerami może być jeszcze bardziej ograniczona.  
  
- Międzynarodowe, regionalne lub krajowe standardy, które regulują formatowanie liczb lub dat i godzin zmiany czasu, i te zmiany są włączane do aktualizacji systemu operacyjnego Windows. W przypadku zmiany Konwencji formatowania dane sformatowane przy użyciu poprzednich Konwencji mogą stać się nieczytelne.  
  
 Poniższy przykład ilustruje ograniczoną przenośność, która wynika z używania formatowania z uwzględnieniem kultury do utrwalania danych. Przykład zapisuje tablicę wartości daty i godziny do pliku. Są one sformatowane przy użyciu Konwencji kultury angielskiej (Stany Zjednoczone). Gdy aplikacja zmieni bieżącą kulturę wątku na francuski (Szwajcaria), próbuje odczytać zapisane wartości przy użyciu Konwencji formatowania bieżącej kultury. Próba odczytania dwóch elementów danych zgłasza <xref:System.FormatException> wyjątek, a tablica dat zawiera teraz dwa niepoprawne elementy, które są <xref:System.DateTime.MinValue>równe.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 Jeśli <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> jednak zastąpisz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwość w wywołaniach do <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, utrwalone dane daty i godziny zostaną pomyślnie przywrócone, jak pokazano poniżej.  
  
```console  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>Zobacz także

- [Manipulowanie ciągami](../../../docs/standard/base-types/manipulating-strings.md)
