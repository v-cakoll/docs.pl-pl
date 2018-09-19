---
title: Najlepsze rozwiązania dotyczące używania ciągów w programie .NET
ms.date: 09/13/2018
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
ms.openlocfilehash: 6114553c6bcdac8521c80c10f470d4c38b15e738
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988741"
---
# <a name="best-practices-for-using-strings-in-net"></a>Najlepsze rozwiązania dotyczące używania ciągów w programie .NET
<a name="top"></a> .NET zapewnia rozbudowaną obsługę dla rozwoju zlokalizowane i uniwersalnych aplikacji i ułatwia zastosowanie Konwencji kultury bieżącej lub określonej kultury, podczas wykonywania typowych operacji, takich jak sortowanie i wyświetlanie ciągów. Ale sortowania i porównywania ciągów nie zawsze jest to operacja wrażliwość na ustawienia kulturowe. Na przykład ciągów, które są używane wewnętrznie przez aplikację zwykle powinny być traktowane identycznie we wszystkich kulturach. Kiedy dane ciągu kulturalnie niezależne, takie jak XML tagów, HTML tagów, nazwy użytkowników, ścieżki do plików i nazwy obiektów systemowych są interpretowane tak, jakby były one zależne od kultury, kod aplikacji może być zastrzeżeniem subtelnych błędów, niską wydajnością i w niektórych przypadkach problemy z zabezpieczeniami.  
  
 W tym temacie sprawdza, czy sortowanie ciągów, porównanie i wielkość liter w wyrazie metod na platformie .NET, przedstawiono zalecenia dotyczące wybierania właściwej metody obsługi ciągów i zapewnia dodatkowe informacje na temat metod obsługi ciągów. Również sprawdza, czy jak sformatowane dane, takie jak dane liczbowe i dane daty i godziny odbywa się do wyświetlania i przechowywania.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Zalecenia dotyczące korzystania z ciągów](#recommendations_for_string_usage)  
  
-   [Jawne określenie porównywania ciągów](#specifying_string_comparisons_explicitly)  
  
-   [Szczegóły dotyczące porównania ciągów](#the_details_of_string_comparison)  
  
-   [Wybieranie elementu StringComparison dla wywołania metody](#choosing_a_stringcomparison_member_for_your_method_call)  
  
-   [Wspólne metody porównania ciągu w .NET](#common_string_comparison_methods_in_the_net_framework)  
  
-   [Metody, które pośrednio wykonują porównywania ciągów](#methods_that_perform_string_comparison_indirectly)  
  
-   [Wyświetlanie i utrzymanie sformatowanych danych](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>Zalecenia dotyczące korzystania z ciągów  
 Podczas tworzenia przy użyciu platformy .NET tych zaleceń proste korzystając z ciągami:  
  
-   Użyj przeciążeń, które jawnie określenie reguł porównania ciągu dla operacji na ciągach. Zazwyczaj polega to na wywołanie przeciążenia metody, które ma parametr typu <xref:System.StringComparison>.  
  
-   Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> porównania jako domyślnym bezpieczne dopasowania ciągu niezależne od kultury.  
  
-   Użyj porównania z wartością <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> zapewnienia lepszej wydajności.  
  
-   Użyj operacji na ciągach, które są oparte na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> podczas wyświetlania danych wyjściowych dla użytkownika.  
  
-   Użyj nielingwistyczne <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> na podstawie wartości zamiast operacje na ciągach <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> gdy wynik porównania jest bez znaczenia językowo (symbolicznych, na przykład).  
  
-   Użyj <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> zamiast metody <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody, gdy NORMALIZUJ ciągi do porównania.  
  
-   Używanie przeciążenia <xref:System.String.Equals%2A?displayProperty=nameWithType> metodę, aby sprawdzić, czy dwa ciągi są równe.  
  
-   Użyj <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody sortowania ciągów nie pod kątem równości.  
  
-   Wrażliwość na ustawienia kulturowe formatowania używać do wyświetlania danych niebędących ciągami, takich jak liczb i dat, w interfejsie użytkownika. Użyj formatowania z kulturą niezmienną do utrwalenia danych innych niż ciąg w postaci ciągu.  
  
 Korzystając z ciągów, należy unikać następujące rozwiązania:  
  
-   Nie należy używać przeciążenia, które nie obsługują jawnie lub niejawnie określenie reguł porównania ciągu dla operacji na ciągach.  
  
-   Nie używaj operacji na ciągach na podstawie <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> w większości przypadków. Jest jedną z pewnymi wyjątkami, gdy są utrwalanie językowo istotnych, ale kulturalnie niezależny od danych.  
  
-   Nie używaj przeciążenia <xref:System.String.Compare%2A?displayProperty=nameWithType> lub <xref:System.String.CompareTo%2A> metody i testowania dla wartości zwracanej równą zero, aby sprawdzić, czy dwa ciągi są równe.  
  
-   Nie używaj formatowania kultury można utrwalić dane liczbowe lub dane daty i godziny w postaci ciągu.  
  
 [Powrót do początku](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>Jawne określenie porównywania ciągów  
 Większość metod manipulowania ciągami w programie .NET są przeciążone. Zazwyczaj co najmniej jedno z przeciążeń Zaakceptuj ustawienia domyślne, inne akceptować żadnych ustawień domyślnych, a zamiast tego zdefiniuj precyzyjne, w którym ciągi są porównywane lub zmieniane. Większość metod, które nie są oparte na wartościach domyślnych zawiera parametr typu <xref:System.StringComparison>, który jest wyliczenie, które jawnie określa reguły porównywania ciągów, kultura i przypadek. W poniższej tabeli opisano <xref:System.StringComparison> elementów członkowskich wyliczenia.  
  
|Element członkowski StringComparison|Opis|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|Wykonuje porównania uwzględniającego wielkość liter, przy użyciu bieżącej kultury.|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter, przy użyciu bieżącej kultury.|  
|<xref:System.StringComparison.InvariantCulture>|Wykonuje porównania uwzględniającego wielkość liter, przy użyciu niezmiennej kultury.|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Wykonuje porównanie bez uwzględniania wielkości liter, przy użyciu niezmiennej kultury.|  
|<xref:System.StringComparison.Ordinal>|Wykonuje porównanie porządkowe.|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|Wykonuje porównanie porządkowe bez uwzględniania wielkości liter.|  
  
 Na przykład <xref:System.String.IndexOf%2A> metody, która zwraca indeks podciągu w <xref:System.String> obiekt, który dopasowuje znak lub ciąg ma dziewięć przeciążeń:  
  
-   <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>, i <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, domyślnie wyszukiwanie porządkowe (wielkość liter i niewrażliwość na ustawienia kulturowe) znaku w ciągu.  
  
-   <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, domyślnie wyszukuje liter i z uwzględnieniem wrażliwość na ustawienia kulturowe podciągu w ciągu.  
  
-   <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, które zawierają parametr typu <xref:System.StringComparison> umożliwiająca postaci porównania, należy określić.  
  
 Zaleca się, że wybrano przeciążenia, które nie używają wartości domyślnych, z następujących powodów:  
  
-   Niektóre przeciążenia przy użyciu parametrów domyślnych (te, które Wyszukaj <xref:System.Char> w wystąpieniu ciągu) wykonać porównanie porządkowe, podczas gdy inne osoby (te, które wyszukania ciągu w wystąpieniu ciągu) są zależne od kultury. Jest trudne do zapamiętania, wartość domyślna, która korzysta z metody i łatwo pomylić przeciążenia.  
  
-   Celem kod, który opiera się na wartości domyślne dla wywołania metody nie jest jasne. W poniższym przykładzie, który opiera się na wartości domyślne, trudno wiedzieć, czy programista chciał faktycznie numeru porządkowego lub lingwistyczne porównanie dwóch ciągów lub czy wielkość różnica między `protocol` i "http" może spowodować, że test pod kątem równości Aby zwrócić `false`.  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 Ogólnie rzecz biorąc zaleca się, wywołać metodę, która nie zależy od ustawień domyślnych, ponieważ sprawia, że celem kod jednoznaczną. To, z kolei sprawia, że kod bardziej czytelne i łatwiejsze debugowanie i obsługa. Poniższy przykład usuwa pytań o w poprzednim przykładzie. Powoduje wyczyść oznacza porządkowego porównania jest używana i że różnice w przypadku są ignorowane.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [Powrót do początku](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>Szczegóły dotyczące porównania ciągów  
 Porównanie ciągów jest sercem wiele powiązanych z ciągami operacji, szczególnie sortowania i testowanie pod kątem równości. Posortować ciągi w określonej kolejności: Jeśli "Mój" pojawia się przed "string", w posortowanej listy ciągów, "Mój" należy porównać mniejsze niż lub równe "string". Ponadto porównanie niejawnie definiuje równości. Operacja porównania zwraca zero dla ciągów, które uzna za równe. Interpretacja dobre jest ani ciągu jest mniejszy od drugiego. Największe znaczenie obejmującego ciągi dołączyć jedno lub oba z następujących procedur: porównanie z innego ciągu i wykonywania operacji sortowania dobrze zdefiniowane.  

> [!NOTE]
> Możesz pobrać [tabele wagi sortowania](https://www.microsoft.com/en-us/download/details.aspx?id=10921), zbiór plików tekstowych, które zawierają informacje o wagi znaku w operacjach sortowania i porównywania dla systemów operacyjnych Windows, a [domyślne Unicode Tabela elementów sortowania](https://www.unicode.org/Public/UCA/latest/allkeys.txt), najnowszą wersję tabeli wagi sortowania dla systemów Linux i macOS. Określoną wersję tabeli wagi sortowania w systemie Linux i macOS jest zależna od wersji [składniki międzynarodowego standardu Unicode](http://site.icu-project.org/) biblioteki zainstalowane w systemie. Informacje na temat ICU wersji i wersje Unicode, które implementują, zobacz [pobieranie ICU](http://site.icu-project.org/download).

 Jednak obliczenia dwa ciągi dla równości lub kolejności sortowania nie uzyskanie wyniku pojedynczą, poprawne; wynik zależy od kryteria używane do porównywania ciągów. W szczególności porównań ciągów, które są porządkowe, lub które są oparte na wielkość liter w wyrazie i sortowanie Konwencji kultury bieżącej lub niezmiennej kultury (w języku angielskim — na podstawie kultury niezależne od ustawień regionalnych) mogą wygenerować różne wyniki.  

Ponadto porównań ciągów przy użyciu różnych wersji programu .NET lub przy użyciu platformy .NET na różne systemy operacyjne i wersje systemu operacyjnego może zwracać różne wyniki. Aby uzyskać więcej informacji, zobacz [ciągów i Unicode Standard](xref:System.String#Unicode). 

<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>Porównywanie ciągów, które używają bieżącej kultury  
 Jedno kryterium polega na użyciu konwencji bieżącej kultury, podczas porównywania ciągów. Porównania, które są oparte na bieżącej kultury, użyj bieżącą kulturę wątku lub ustawień regionalnych. Jeśli kultura nie jest ustawiony przez użytkownika, wartość domyślna to ustawienie w **Opcje regionalne** okna w Panelu sterowania. Zawsze należy używać porównania, które są oparte na bieżącej kultury, gdy dane znajdują się lingwistycznie i odzwierciedla interakcji z użytkownikiem wrażliwość na ustawienia kulturowe.  
  
 Zachowanie porównania i wielkość liter w wyrazie na platformie .NET zmiany jednak po zmianie kultury. Dzieje się tak, gdy aplikacja wykonuje na komputerze, który ma inną kulturę niż komputer, na którym aplikacja została opracowana, lub gdy wątek wykonujący zmienia jego kultury. To zachowanie jest zamierzone, lecz pozostaje bez oczywiste dla wielu deweloperów. Poniższy przykład ilustruje różnice w kolejności sortowania Stanów Zjednoczonych Korona kultur ("sv-SE") i angielski ("en US"). Pamiętaj, że wyrazy "ångström", "Windows" i "Visual Studio" wydawać się w różnych miejscach w tablicach posortowany ciągu.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 Porównania bez uwzględniania wielkości liter, które używają bieżącej kultury są takie same jak zależne od kultury porównań, z tą różnicą, że ignorowanie wielkości liter, zgodnie z ustawieniem bieżącej kultury wątku. To zachowanie może objawiać w kolejności sortowania, jak również.  
  
 Porównania, które używają bieżącej kultury semantyka są domyślne dla następujących metod:  
  
-   <xref:System.String.Compare%2A?displayProperty=nameWithType> przeciążenia, które nie zawierają <xref:System.StringComparison> parametru.  
  
-   <xref:System.String.CompareTo%2A?displayProperty=nameWithType> przeciążenia.  
  
-   Wartość domyślna <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> metody i <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metody z `null` <xref:System.Globalization.CultureInfo> parametru.  
  
-   Wartość domyślna <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> metody i <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metody z `null` <xref:System.Globalization.CultureInfo> parametru.  
  
-   <xref:System.String.IndexOf%2A?displayProperty=nameWithType> przeciążenia, które akceptują <xref:System.String> jako wyszukiwanie parametr i nie mają <xref:System.StringComparison> parametru.  
  
-   <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> przeciążenia, które akceptują <xref:System.String> jako wyszukiwanie parametr i nie mają <xref:System.StringComparison> parametru.  
  
 W każdym przypadku firma Microsoft zaleca wywołanie przeciążenia, które ma <xref:System.StringComparison> parametr, aby utworzyć przeznaczenie metody wywołania Wyczyść.  
  
 Subtelnym, nie dlatego subtelnych błędów może pojawić się podczas językowo interpretowania danych innych niż ciąg lub dane ciągu od określonej kultury jest interpretowany przy użyciu konwencji kultury innej. Canonical przykładem jest turecki-I problemów.  
  
 Dla prawie wszystkie litery alfabetu łacińskiego, łącznie z USA Angielski, znak "i" (\u0069) jest wersję znaku "I" (\u0049). Reguła wielkość liter w wyrazie szybko będzie domyślnie niepowołanym programowania w takich kultury. Jednak alfabetu turecki ("tr-TR") zawiera "I z dot" znak "İ" (\u0130), która jest wersją kapitałowych z "i". Turecki obejmuje również znak małe litery "i bez kropki", "ı" (\u0131), która powoduje rozpoczynanie do "I". Dzieje się to w także kulturze Azerbejdżański ("az").  
  
 W związku z tym założeniom o pisaniu "i" lub West "I" są nieprawidłowe wśród wszystkich kultur. Jeśli używasz domyślne przeciążenia dla procedury porównania ciągu, będą podlegać odchylenie od kultury. Jeśli dane do porównania jest niejęzykowy, za pomocą przeciążenia domyślnego może spowodować niepożądane wyniki jako następującej próbie wykonania porównania bez uwzględniania wielkości ciągi "file" i "Plik" przedstawia.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 To porównanie może spowodować znaczące problemy, jeżeli kulturę przypadkowo jest używany w ustawieniami istotnymi dla zabezpieczeń, jak w poniższym przykładzie. Wywołanie metody, takie jak `IsFileURI("file:")` zwraca `true` Jeśli bieżącą kulturą jest Stanów Zjednoczonych Angielski, ale `false` przypadku lira bieżącej kultury. W związku z tym, w systemach lira ktoś obejścia środków bezpieczeństwa, które blokują dostęp do bez uwzględniania wielkości liter identyfikatorów URI, które zaczynają się od "pliku:".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 W tym przypadku ponieważ "pliku:" jest przeznaczony do być interpretowane jako identyfikator nielingwistyczne, niezależnych od kultury, kod zamiast zapisywane są jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>Operacje na ciągach porządkowych  
 Określanie <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartość w wywołaniu metody oznacza nielingwistyczne porównania, w którym funkcje językiem naturalnym są ignorowane. Metody, które są wywoływane przy użyciu tych <xref:System.StringComparison> wartości bazowej parametry operacji decyzje dotyczące porównania jednobajtowych zamiast wielkość liter w wyrazie lub równoważności tabel, które są parametryzowane przez kulturę. W większości przypadków to najlepsze podejście pasuje do zamierzonego interpretacji ciągi podczas wprowadzania kodu w szybszy i bardziej niezawodny.  
  
 Porównania liczb porządkowych są porównań ciągów, w których poszczególne bajty każdego ciągu jest porównywany bez interpretacji językowej; na przykład "windows" niezgodne "Windows". To jest zasadniczo wywołanie do środowiska uruchomieniowego C `strcmp` funkcji. Użyj tego porównania, jeśli kontekst mówią, że ciągi powinny być dopasowane dokładnie lub żądań zachowawcze odpowiadające im zasady. Ponadto porównania porządkowego jest najszybszy operacji porównania, ponieważ dotyczy żadnych reguł językowej podczas określania wyników.  
  
 Ciągi w programie .NET może zawierać osadzone znaki o wartości null. Jedną z najbardziej przejrzystego różnic między porównanie porządkowe i kultury (w tym porównania, które używają niezmiennej kultury) dotyczy obsługi osadzone znaki o wartości null w ciągu. Następujące znaki są ignorowane, gdy używasz <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.Equals%2A?displayProperty=nameWithType> metody służące do wykonywania porównań kultury (w tym porównania, które używają niezmiennej kultury). W rezultacie porównywaniu wrażliwość na ustawienia kulturowe, ciągi zawierające znaki null osadzonego jest uznawana za równa ciągów, które nie obsługują.  
  
> [!IMPORTANT]
>  Mimo że metod porównujących zignorować osadzone znaki o wartości null, ciąg wyszukiwania metody takie jak <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, i <xref:System.String.StartsWith%2A?displayProperty=nameWithType> nie obsługują.  
  
 Poniższy przykład wykonuje porównanie zależne od kultury ciągu "Aa", z podobnych ciąg, który zawiera kilka osadzone znaki o wartości null, od "A" i "a" i pokazuje, jak dwa ciągi są uznawane za równe.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 Jednak ciągi nie są uważane za równe korzystania porównanie porządkowe, co ilustruje poniższy przykład.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 Porównania liczb porządkowych bez uwzględniania wielkości liter są dalej najbardziej zachowawcze podejście. Bok te porównania Ignoruj wielkość liter w wyrazie większość; na przykład "windows" pasuje do "Windows". Podczas pracy z zestawu znaków ASCII, zasada ta jest równoważna <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, chyba że ignoruje zwykle liter ASCII. W związku z tym, dowolny znak w [A, Z] (\u0041-\u005A) pasuje do odpowiedniego znaku w [, z] (\u0061-\007A). Tabele Niezmienna kultura są używane w wielkości liter spoza zakresu ASCII. W związku z tym poniższe porównanie:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 jest równoważna (ale szybciej niż) to porównanie:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 Są to porównania nadal bardzo szybko.  
  
> [!NOTE]
>  Parametry zachowania systemu plików, kluczy rejestru i wartości oraz zmienne środowiskowe najlepiej jest reprezentowany przez <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.  
  
 Zarówno <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> i <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> używać wartości binarnych bezpośrednio i są dopasowane do dopasowania. Jeśli nie masz pewności o ustawieniach porównania, użyj jednej z tych dwóch wartości. Jednak ponieważ wykonują porównania bajt po bajcie, ich bez sortowania przez porządek sortowania lingwistyczne (np. angielski słownika), ale przez binarny porządek sortowania. Wyniki mogą dziwne w kontekstach większość, jeśli wyświetlana dla użytkowników.  
  
 Numer porządkowy semantyka jest ustawieniem domyślnym dla <xref:System.String.Equals%2A?displayProperty=nameWithType> przeciążenia, które nie zawierają <xref:System.StringComparison> argumentu (łącznie z operatorem równości). W każdym przypadku firma Microsoft zaleca wywołanie przeciążenia, które ma <xref:System.StringComparison> parametru.  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>Operacje na ciągach, które używają kultury niezmiennej  
 Porównanie przy użyciu niezmiennej kultury <xref:System.Globalization.CultureInfo.CompareInfo%2A> zwróconą przez statyczną właściwość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. To zachowanie jest takie same we wszystkich systemach; tłumaczy je dowolne znaki poza zakresem, na co jego zdaniem są równoważne znaki niezmienna. Ta zasada może być przydatne przy zachowaniu jeden zestaw parametrów zachowanie różnych kultur, ale często zawiera nieoczekiwane wyniki.  
  
 Porównania bez uwzględniania wielkości liter z kulturą niezmienną używa się statycznej <xref:System.Globalization.CultureInfo.CompareInfo%2A> zwróconą przez statyczną właściwość <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwość również informacje dotyczące porównania. Wielkość różnice między tymi liczba przetłumaczonych znaków są ignorowane.  
  
 Porównania, które używają <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> i <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> działają tak samo na ciągi znaków ASCII. Jednak <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> sprawia, że językowej decyzje, które mogą nie być odpowiednie dla ciągów, które mają być interpretowany jako zbiór bajtów. `CultureInfo.InvariantCulture.CompareInfo` Sprawia, że obiekt <xref:System.String.Compare%2A> metoda interpretacji niektórych zestawów znaków jako równoważne. Na przykład następujące równoważności jest prawidłowa w ramach niezmiennej kultury:  
  
 InvariantCulture: + ̊ = å  
  
 A ŁACIŃSKI MAŁA litera znak "" (\u0061), gdy znajduje się obok znaku łączenie RING ABOVE "+"̊"(\u030a) jest interpretowany jako ŁACIŃSKI małej litery A WITH RING ABOVE znak"å"(\u00e5). Jak pokazano na poniższym przykładzie, to zachowanie różni się od porównania porządkowego.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 Interpretując nazw plików, pliki cookie lub cokolwiek innego, gdzie kombinację, takie jak "å" mogą być wyświetlane, numer porządkowy porównania zaoferowaniu zachowanie najbardziej przejrzystego i dopasowane.  
  
 Na saldo Niezmienna kultura ma tylko kilka właściwości, które ułatwiają przydatne w przypadku porównywania. Robi porównania w sposób lingwistycznie uniemożliwia jego gwarantujących pełne symboliczne równoważności, ale nie jest wyborem do wyświetlenia w żadnej kultury. Jedną z kilku powodów używania <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> porównania jest do utrwalenia danych uporządkowanych do wyświetlenia międzykulturowe identyczne. Na przykład jeśli plik dużych ilości danych, który zawiera posortowany identyfikatorów do wyświetlania dołączonych aplikacji, dodanie do tej listy wymagałoby wstawiania przy użyciu niezmiennej stylu sortowania.  
  
 [Powrót do początku](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Wybieranie elementu StringComparison (porównywania ciągów tekstowych) do metody wywołania  
 W poniższej tabeli przedstawiono mapowanie z ciągu semantycznego kontekstu do <xref:System.StringComparison> element członkowski wyliczenia.  
  
|Dane|Zachowanie|Odpowiednie System.StringComparison<br /><br /> value|  
|----------|--------------|-----------------------------------------------------|  
|Wielkość liter identyfikatory wewnętrznego.<br /><br /> Wielkość liter identyfikatory standardów, takich jak XML i HTTP.<br /><br /> Wielkość liter ustawienia związane z zabezpieczeniami.|Identyfikator nielingwistyczne, gdzie dokładnie bajtów.|<xref:System.StringComparison.Ordinal>|  
|Bez uwzględniania wielkości liter identyfikatory wewnętrznego.<br /><br /> Bez uwzględniania wielkości liter identyfikatory standardów, takich jak XML i HTTP.<br /><br /> Ścieżki plików.<br /><br /> Klucze i wartości rejestru.<br /><br /> Zmienne środowiskowe.<br /><br /> Identyfikatory zasobów (na przykład nazwy dojścia).<br /><br /> Bez uwzględniania wielkości liter ustawienia związane z zabezpieczeniami.|Identyfikator nielingwistyczne, w których przypadku nie ma znaczenia; szczególnie danych przechowywanych w większości usług systemu Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|Niektóre utrwalonych lingwistycznie dane.<br /><br /> Wyświetlanie danych językowe, które wymaga stałej sortowania.|Kulturalnie niezależny od danych, które nadal są lingwistycznie.|<xref:System.StringComparison.InvariantCulture><br /><br /> —lub—<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|Dane wyświetlane użytkownikowi.<br /><br /> Większość dane wejściowe użytkownika.|Dane, które wymaga przemysłach językowej.|<xref:System.StringComparison.CurrentCulture><br /><br /> —lub—<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [Powrót do początku](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>Wspólne metody porównania ciągu w .NET  
 W poniższych sekcjach opisano metody, które są najczęściej używane do porównywania ciągów.  
  
### <a name="stringcompare"></a>Funkcja String.Compare  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Jak najbardziej decydujące znaczenie dla interpretacji ciągu operacja wszystkich wystąpień tych wywołań metody wywołuje należy zbadać, czy ciągi powinny być interpretowane zgodnie z bieżącą kulturą, czy oddzielona od kultury (symbolicznie). Typowo, jest ostatnim, a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> porównania, które powinny być używane zamiast tego.  
  
 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Klasy, która jest zwracana przez <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> zawiera także właściwości, <xref:System.Globalization.CompareInfo.Compare%2A> metodę, która zawiera dużą liczbę pasujących opcje (numer porządkowy ignoruje biały znak, wpisz znaki kana ignorowanie i tak dalej) poprzez <xref:System.Globalization.CompareOptions> flagi wyliczenie.  
  
### <a name="stringcompareto"></a>Funkcja String.CompareTo  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Ta metoda nie oferuje obecnie przeciążenia, które określa <xref:System.StringComparison> typu. Zazwyczaj można przekonwertować tej metody zalecanej <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formularza.  
  
 Typami, które implementują <xref:System.IComparable> i <xref:System.IComparable%601> interfejsów zaimplementować tę metodę. Ponieważ nie oferuje możliwości <xref:System.StringComparison> parametru, często typy zawierające implementację zezwolić użytkownikowi na określenie <xref:System.StringComparer> w ich konstruktora. W poniższym przykładzie zdefiniowano `FileName` klasy, której Konstruktor klasy zawiera <xref:System.StringComparer> parametru. To <xref:System.StringComparer> obiekt jest następnie używany w `FileName.CompareTo` metody.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>Funkcja String.Equals  
 Domyślna interpretacja: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 <xref:System.String> Klasa umożliwia testowanie dla równości, wywołując statycznych lub wystąpienia <xref:System.String.Equals%2A> przeciążenia metody, lub za pomocą operatora równości statyczne. Przeciążenia i operator używa porównania porządkowego domyślnie. Jednak nadal zaleca się wywołania przeciążenia, które jawnie określa <xref:System.StringComparison> wpisz nawet, jeśli chcesz wykonać porównanie porządkowe; to sprawia, że łatwiej wyszukiwania kodu na interpretację ciągu.  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper i String.ToLower  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Należy zachować ostrożność podczas użycia tych metod, ponieważ wymuszanie ciąg na wielkie i małe litery jest często używana jako małych normalizacji porównywania ciągów, niezależnie od wielkości liter. Jeśli tak, należy rozważyć użycie porównania bez uwzględniania wielkości liter.  
  
 <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> i <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> dostępne są również metody. <xref:System.String.ToUpperInvariant%2A> jest standardowym sposobem do normalizacji przypadek. Porównania zostało nawiązane przy użyciu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> są behaviorally kompozycji dwóch wywołań: wywołanie <xref:System.String.ToUpperInvariant%2A> zarówno argumenty typu string, jak i wykonując porównanie przy użyciu <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 Przeciążenia są także dostępne do konwersji na wielkie i małe litery w określonej kulturze, przekazując <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę kulturę do metody.  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper i Char.ToLower  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Te metody działają podobnie jak <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> metod opisanych w poprzedniej sekcji.  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith i String.EndsWith  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Domyślnie obie te metody wykonać porównanie zależne od kultury.  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf i String.LastIndexOf  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Brak spójności działanie domyślne przeciążenia metody te porównania jest. Wszystkie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metod, które obejmują <xref:System.Char> parametru wykonać porównanie porządkowe, ale domyślne <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metod, które obejmują <xref:System.String> parametru wykonać wrażliwość na ustawienia kulturowe porównanie.  
  
 Jeśli wywołasz <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> metody i przekazać ją ciąg do zlokalizowania w bieżącym wystąpieniu, firma Microsoft zaleca wywołanie przeciążenia, które jawnie określa <xref:System.StringComparison> typu. Przeciążenia, które obejmują <xref:System.Char> argumentu nie pozwalają na określenie <xref:System.StringComparison> typu.  
  
 [Powrót do początku](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, które pośrednio wykonują porównywania ciągu  
 Niektóre metody niebędących ciągami, mających porównywania ciągów jako użyj operacji centralnej <xref:System.StringComparer> typu. <xref:System.StringComparer> Klasa zawiera sześć właściwości statyczne, które zwracają <xref:System.StringComparer> wystąpienia, którego <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody wykonywania następujących rodzajów porównań ciągów:  
  
-   Porównania ciągów zależne od kultury, przy użyciu bieżącej kultury. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Porównania bez uwzględniania wielkości liter, przy użyciu bieżącej kultury. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> właściwości.  
  
-   Za pomocą reguł porównywania word niezmiennej kultury niezależnych od kultury porównań. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Porównania bez uwzględniania wielkości liter i niewrażliwość na ustawienia kulturowe, za pomocą reguł porównywania word niezmiennej kultury. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> właściwości.  
  
-   Porównanie porządkowe. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> właściwości.  
  
-   Porównanie porządkowe bez uwzględniania wielkości liter. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort i Array.BinarySearch  
 Domyślna interpretacja: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 W przypadku przechowywania danych w kolekcji lub odczytać danych z pliku lub bazy danych do kolekcji, przełączanie bieżącej kultury może unieważnić invariants w kolekcji. <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> Metoda zakłada, że elementów w tablicy, które mają być wyszukiwane są już sortowane. Aby posortować dowolny element ciągu w tablicy, <xref:System.Array.Sort%2A?displayProperty=nameWithType> wywołania metody <xref:System.String.Compare%2A?displayProperty=nameWithType> metody, aby uporządkować poszczególne elementy. Za pomocą porównania kultury może być niebezpieczne, ponieważ zmiany kultury między czasem, że tablica jest posortowana i jego zawartość zostaną przeszukane. Na przykład, poniższy kod, przechowywania i pobierania działają na modułu porównującego, który jest dostarczane niejawnie przez `Thread.CurrentThread.CurrentCulture` właściwości. Jeśli kultury może się zmieniać między wywołania `StoreNames` i `DoesNameExist`, a zwłaszcza wtedy, gdy zawartość tablicy są zachowywane gdzieś między wywołaniami dwie metody, wyszukiwanie binarne może zakończyć się niepowodzeniem.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 Zalecana zmiana pojawi się w poniższym przykładzie, który używa tej samej metody porównanie porządkowe (niewrażliwość na ustawienia kulturowe) do sortowania i wyszukiwania tablicy. Zmienianie kodu jest odzwierciedlana w wierszach etykietą `Line A` i `Line B` w dwóch przykładach.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 Jeśli te dane są zachowywane i przenosić między kultur i sortowanie służy do prezentowania tych danych do użytkownika, należy rozważyć przy użyciu <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, który działa językowo, aby lepiej użytkownika danych wyjściowych, ale jest niezależny od zmian w kulturze. Poniższy przykład modyfikuje dwóch poprzednich przykładach na potrzeby niezmiennej kultury sortowania i wyszukiwania w tablicy.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>Przykład kolekcji: konstruktor tablicy wartości funkcji mieszającej  
 Mieszanie ciągów zawiera drugi przykład operacji, która ma to wpływ na podstawie informacji podanych w którym ciągi są porównywane.  
  
 Poniższy przykład tworzy wystąpienie <xref:System.Collections.Hashtable> obiektu przez przekazanie jej <xref:System.StringComparer> obiektu, który jest zwracany przez <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> właściwości. Ponieważ klasa <xref:System.StringComparer> , jest tworzony na podstawie <xref:System.StringComparer> implementuje <xref:System.Collections.IEqualityComparer> interfejsu, jego <xref:System.Collections.IEqualityComparer.GetHashCode%2A> metoda jest używana do obliczenia skrótu ciągów w tabeli wyznaczania wartości skrótu.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [Powrót do początku](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>Wyświetlanie i utrzymanie sformatowanych danych  
 Podczas wyświetlania danych niebędących ciągami, takich jak liczby i daty i godziny dla użytkowników, należy je sformatować przy użyciu ustawienia kultury użytkownika. Domyślnie <xref:System.String.Format%2A?displayProperty=nameWithType> metody i `ToString` metody typów numerycznych oraz typów daty i godziny używają bieżącej kultury wątku operacji formatowania. Aby jawnie określić, że metoda formatowania, należy użyć bieżącej kultury, można wywoływać przeciążenia metody formatowania, która ma `provider` parametru, takie jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> lub <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>i przekaż go <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości.  
  
 Jako dane binarne lub jak sformatowane dane, jednak można utrwalić danych innych niż ciąg. Jeśli użytkownik chce zapisać ją jak sformatowane dane, należy wywołać formatowania przeciążenia metody, która obejmuje `provider` parametru i przekaż go <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Niezmienna kultura zapewnia spójny format sformatowanych danych, który jest niezależny od kultury i maszyny. Z kolei utrwalanie danych, która jest formatowana przy użyciu kultury innej niż niezmiennej kultury ma kilka ograniczeń:  
  
-   Dane są prawdopodobnie bezużyteczne, jeśli jest pobierana w systemie, który ma inną kulturę, lub jeśli użytkownik bieżący system Bieżąca kultura jest zmieniana i podejmie próbę pobrania danych.  
  
-   Właściwości kultury na określonym komputerze może różnić się od wartości standardowych. W dowolnym momencie użytkownik może dostosować ustawienia wyświetlania zależne od kultury. W związku z tym sformatowanych danych, który jest zapisywany w systemie może nie można odczytać po użytkownik dostosowuje ustawienia kultury. Przenośność sformatowane dane na komputerach jest mogą być jeszcze bardziej ograniczona.  
  
-   Standardy międzynarodowe, regionalne lub krajowe, które określają sposób formatowania liczby lub daty i godziny, zmień wraz z upływem czasu, a te zmiany są włączone do aktualizacji systemu operacyjnego Windows. Gdy zmienią się konwencje formatowania danych, którą sformatowano przy użyciu poprzednich Konwencji nie będzie można odczytać.  
  
 Poniższy przykład ilustruje przenośność ograniczone, będącą wynikiem przy użyciu formatowania kultury do utrwalenia danych. Przykład zapisuje tablicę wartości daty i godziny pliku. Są one formatowane przy użyciu konwencji kultury angielski (Stany Zjednoczone). Po jej zmian bieżącej kultury wątku na francuski (Szwajcaria), próbuje odczytać zapisane wartości przy użyciu konwencji formatowania bieżącej kultury. Próba odczytania dwa dane elementy zgłasza <xref:System.FormatException> wyjątek, a tablica daty teraz zawiera dwa niepoprawne elementy, które są równe <xref:System.DateTime.MinValue>.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 Jednak w przypadku wymiany <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwość o <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> w wywołaniach do <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, utrwalonych datę i godzinę danych zostały pomyślnie przywrócone, co ilustruje poniższy danych wyjściowych.  
  
```  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>Zobacz także

- [Manipulowanie ciągami](../../../docs/standard/base-types/manipulating-strings.md)
