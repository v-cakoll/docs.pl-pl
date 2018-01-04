---
title: "Najlepsze rozwiązania dotyczące używania ciągów w .NET"
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
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a4b92cd9d6b880f23d6acaf9e38e685184ec3bfe
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-using-strings-in-net"></a>Najlepsze rozwiązania dotyczące używania ciągów w .NET
<a name="top"></a>Zapewnia zaawansowaną obsługę programowania zlokalizowanych i uniwersalnych aplikacji .NET i można łatwo zastosować konwencje bieżącej kultury lub określoną kulturę, podczas wykonywania typowych operacji, takich jak sortowanie i wyświetlanie ciągów. Ale sortowania i porównywania ciągów nie zawsze jest operacją zależne od kultury. Na przykład ciągów, które są używane wewnętrznie aplikacji zwykle powinny być traktowane identycznie we wszystkich języków. Kiedy kulturalnie niezależne ciągu danych, takich jak XML tagi, HTML tagi, nazwy użytkowników, ścieżki do pliku i nazwy obiektów systemowych są interpretowane, tak jakby były zależne od kultury, kod aplikacji może być może ulec subtelnych błędów, niską wydajnością, a w niektórych przypadkach problemy z zabezpieczeniami.  
  
 W tym temacie sprawdza, czy sortowanie ciągów, porównania i metod wielkość liter w programie .NET, przedstawiono zalecenia dotyczące wybierania odpowiedniej metody obsługi ciągów i udostępnia dodatkowe informacje na temat metody obsługi ciągu. Sprawdza także sposób sformatowanych danych, takich jak dane liczbowe i danych daty i godziny, jest obsługiwane dla wyświetlania i magazynu.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Zalecenia dotyczące użycia ciągu](#recommendations_for_string_usage)  
  
-   [Jawne określenie Porównywnania ciągów](#specifying_string_comparisons_explicitly)  
  
-   [Szczegóły porównania ciągów](#the_details_of_string_comparison)  
  
-   [Wybranie elementu StringComparison dla wywołania metody](#choosing_a_stringcomparison_member_for_your_method_call)  
  
-   [Typowe metody porównania ciągów w .NET](#common_string_comparison_methods_in_the_net_framework)  
  
-   [Metody, które pośrednio przeprowadzenia porównania ciągu](#methods_that_perform_string_comparison_indirectly)  
  
-   [Wyświetlanie i przechowywanie sformatowanych danych](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>Zalecenia dotyczące korzystania z ciągów  
 Podczas pracy z platformą .NET tych zaleceń proste używania ciągów:  
  
-   Użyj przeciążeń, które jawnie określić zasady porównanie ciągu operacje na ciągach. Zazwyczaj ten proces obejmuje wywołania przeciążenia metody, które ma parametr typu <xref:System.StringComparison>.  
  
-   Użyj <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla porównania jako bezpieczne do dopasowania ciągu niezależne od kultury domyślnej.  
  
-   Użyj porównań z <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> w celu poprawy wydajności.  
  
-   Użyj operacje na ciągach, które są oparte na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> po wyświetleniu danych wyjściowych dla użytkownika.  
  
-   Użyj innych niż przypadku <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> na podstawie wartości zamiast operacje na ciągach <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> gdy wynik porównania ma zależnej znaczenia (symbolicznych, np.).  
  
-   Użyj <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> zamiast metody <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody, gdy NORMALIZUJ ciągi do porównania.  
  
-   Użyj przeciążenia <xref:System.String.Equals%2A?displayProperty=nameWithType> metody, aby sprawdzić, czy dwa ciągi są takie same.  
  
-   Użyj <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody sortowanie ciągów nie w celu sprawdzenia pod kątem równości.  
  
-   Zależne od kultury formatowania używać do wyświetlania danych innych niż ciąg, takie jak liczb i dat, w interfejsie użytkownika. Użyj formatowania z kulturą niezmienną do utrwalenia danych innych niż ciąg w formie ciągu.  
  
 Użyj parametrów uniknąć następujących wskazówek:  
  
-   Nie należy używać przeciążeń, które nie mają jawnie lub niejawnie określania zasad porównanie ciągu operacje na ciągach.  
  
-   Nie używaj na podstawie operacje na ciągach <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> w większości przypadków. Jest jednym z kilku wyjątków, gdy są przechowywanie danych zależnej znaczenie, ale kulturalnie niezależny.  
  
-   Nie używaj przeciążenia <xref:System.String.Compare%2A?displayProperty=nameWithType> lub <xref:System.String.CompareTo%2A> — metoda i testowania dla wartości zwracanej równą zero, aby określić, czy dwa ciągi są takie same.  
  
-   Nie używaj zależne od kultury formatowania do utrwalenia danych numerycznych lub daty i godziny dane w postaci ciągu.  
  
 [Powrót do początku](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>Jawne określenie porównywania ciągów  
 Większość metod manipulowania ciągami w .NET jest przeciążony. Zazwyczaj co najmniej jedno z przeciążeń zaakceptować ustawienia domyślne, inne Zaakceptuj nie ustawienia domyślne, a zamiast tego zdefiniuj precyzyjnego, w którym ciągi mają być porównywane lub modyfikowany w zakresie. Większość metod, które nie są oparte na wartościach domyślnych zawiera parametr typu <xref:System.StringComparison>, który jest jawnie określa zasady porównania ciągów, kultury i przypadku wyliczenie. W poniższej tabeli opisano <xref:System.StringComparison> elementy członkowskie wyliczenia.  
  
|Element członkowski StringComparison|Opis|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|Przeprowadza porównanie z uwzględnieniem wielkości liter przy użyciu bieżącej kultury.|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Wykonuje porównania bez uwzględniania wielkości liter, przy użyciu bieżącej kultury.|  
|<xref:System.StringComparison.InvariantCulture>|Przeprowadza porównanie z uwzględnieniem wielkości liter użyta Niezmienna kultura.|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Wykonuje porównania bez uwzględniania wielkości liter, użyta Niezmienna kultura.|  
|<xref:System.StringComparison.Ordinal>|Przeprowadza porównanie liczby porządkowej.|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|Przeprowadza porównanie porządkowych bez uwzględniania wielkości liter.|  
  
 Na przykład <xref:System.String.IndexOf%2A> metodę, która zwraca indeks podciągu w <xref:System.String> obiekt, który reprezentuje znak lub ciąg, ma dziewięć przeciążeń:  
  
-   <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>, i <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, która domyślnie wyszukiwaniu porządkowej (z uwzględnieniem wielkości liter i niezależnych od kultury) dla znaku w ciągu.  
  
-   <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, domyślnie wyszukuje uwzględniania wielkości liter i zależne od kultury podciągu w ciągu.  
  
-   <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, i <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, który obejmuje parametr typu <xref:System.StringComparison> formularza porównania należy określić, która umożliwia.  
  
 Zaleca się wybranie przeciążenia, które nie są używane wartości domyślne, z następujących powodów:  
  
-   Niektóre przeciążenia z parametrów domyślnych (te, które Wyszukaj <xref:System.Char> w wystąpienia ciągu) wykonać porównanie liczby porządkowej, inne osoby (pliki, które wyszukaj ciąg w wystąpienia ciągu) są zależne od kultury. Jest trudne do zapamiętania, którego metoda korzysta z którego wartość domyślna i łatwo pomylić przeciążeń.  
  
-   Celem kod, który korzysta z wartości domyślne dla wywołania metody nie jest jasne. W poniższym przykładzie opiera się na wartości domyślne, trudno wiedzieć, czy rzeczywiście dewelopera przeznaczone numeru porządkowego lub językowe porównywania dwóch ciągów lub czy przypadków różnica między `protocol` i "http" może spowodować, że testowanie równości Aby przywrócić `false`.  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 Ogólnie rzecz biorąc zaleca się wywołania metody, która nie zależy od ustawień domyślnych, ponieważ sprawia, że celem kod jednoznaczne. Kod, to z kolei ułatwia bardziej czytelny i łatwiejsze do debugowania i obsługa. Poniższy przykład dotyczy pytań o poprzednim przykładzie. Powoduje wyczyść to {numer porządkowy porównania jest używany i czy różnice w przypadku są ignorowane.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [Powrót do początku](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>Szczegóły dotyczące porównania ciągów  
 Porównanie ciągów jest centralnym wielu powiązanych z ciągami operacji, szczególnie sortowania i testowanie pod kątem równości. Sortowanie ciągów w określonej kolejności: Jeśli "Mój" występuje przed "string" posortowaną listę ciągów, "Mój" należy porównać co najwyżej "string". Ponadto porównanie niejawnie definiuje równości. Operacja porównywania zwraca zero dla ciągów, które uzna za takie same. Dobrym interpretacji jest ciąg ani nie przekracza innych. Największe znaczenie operacji dotyczących ciągi zawierają jedną lub obie z poniższych procedur: porównanie z innego ciągu i wykonywanie operacji sortowania dobrze zdefiniowany.  
  
 Jednak obliczenia dwa ciągi równości lub porządek sortowania nie przekazuje jeden poprawny wynik; wynik jest zależna od kryteriów używanych do porównania ciągów. W szczególności porównanie ciągu z liczby porządkowej lub które są oparte na wielkość liter i sortowanie konwencje bieżącej kultury lub kulturą niezmienną (niezależne od ustawień regionalnych kultury oparte na języku angielskim) może wygenerować różne wyniki.  
  
<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>Porównywanie ciągów, które używają bieżącej kultury  
 Jedno kryterium polega na użyciu konwencje bieżącej kultury, podczas porównywania ciągów. Porównanie, które są oparte na bieżącej kultury użyć bieżącej kultury wątku lub ustawień regionalnych. Jeśli kultura nie jest ustawiony przez użytkownika, domyślne ustawienie w **Opcje regionalne** okna w Panelu sterowania. Zawsze należy używać porównań, które są oparte na bieżącej kultury, gdy dane są zależnej odpowiednich i odzwierciedla interakcji z użytkownikiem z uwzględnieniem kultury.  
  
 Jednak zachowania porównania i wielkość liter w .NET zmienia się po zmianie kultury. Dzieje się tak, gdy aplikacja wykonuje na komputerze, który ma inną kulturę niż komputer, na którym został opracowany, aplikacji lub podczas wykonywania wątku zmiany jego kultury. To zachowanie jest zamierzone, ale pozostaje on z systemem innym niż oczywiste dla wielu deweloperów. Poniższy przykład przedstawia różnice w porządku sortowania USA Angielski ("pl pl") i szwedzki kultur ("sv-SE"). Należy zauważyć, że wyrazy "ångström", "Windows" i "Visual Studio" pojawiają się w różnych miejscach w tablicach posortowane ciąg.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 Porównania bez uwzględniania wielkości liter, które używają bieżącej kultury są takie same jak zależne od kultury porównań, z wyjątkiem tego, że Ignoruj wielkość liter, zgodnie z ustawieniem bieżącej kultury wątku. To zachowanie może sam manifestu w również kolejność sortowania.  
  
 Porównania, które korzystają bezpośrednio z semantyki bieżącej kultury są domyślne dla następujących metod:  
  
-   <xref:System.String.Compare%2A?displayProperty=nameWithType>przeciążenia, które nie zawierają <xref:System.StringComparison> parametru.  
  
-   <xref:System.String.CompareTo%2A?displayProperty=nameWithType>przeciążenia.  
  
-   Wartość domyślna <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> metody i <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metody z `null` <xref:System.Globalization.CultureInfo> parametru.  
  
-   Wartość domyślna <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> metody i <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metody z `null` <xref:System.Globalization.CultureInfo> parametru.  
  
-   <xref:System.String.IndexOf%2A?displayProperty=nameWithType>przeciążenia, które akceptują <xref:System.String> jako wyszukiwanie parametru i które nie mają <xref:System.StringComparison> parametru.  
  
-   <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>przeciążenia, które akceptują <xref:System.String> jako wyszukiwanie parametru i które nie mają <xref:System.StringComparison> parametru.  
  
 W każdym przypadku firma Microsoft zaleca, aby wywoływać przeciążenia, które ma <xref:System.StringComparison> parametr, aby celem metodę wywołania Wyczyść.  
  
 Niewielkie i nie tak subtelnych błędów można wyłonić podczas-językowe ciągu jest interpretowana zależnej lub danymi ciągowymi z określonej kultury jest interpretowany za pomocą Konwencji inną kulturę. Canonical przykładem jest turecki-I problemów.  
  
 Dla niemal wszystkich alfabetach alfabetu łacińskiego, w tym stany USA Angielski, znak "i" (\u0069) jest mała litera wersja znak "I" (\u0049). Reguła wielkości liter szybko będzie domyślnie osobie Programowanie w takich kultury. Jednak alfabetu turecki ("tr-TR") obejmuje "I z kropką" znak "İ" (\u0130), czyli kapitału wersji elementu "i". Turecki także znak małe litery "i bez kropki", "ı" (\u0131), która powoduje rozpoczynanie do "I". Dzieje się to w również kultura Azerbejdżański ("az").  
  
 W związku z tym założeniom o wielkiej "litery i" lub lowercasing "I" nie są prawidłowe między wszystkich języków. Jeśli używasz domyślne przeciążenia dla procedury porównanie ciągu będą podlegać odchylenia od kultury. W przypadku innych niż językowe danych ma zostać porównane, za pomocą przeciążenia domyślny może spowodować niepożądane wyniki następujące próba wykonania porównania bez uwzględniania wielkości liter ciągów "file" i przedstawiono "Plik".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 To porównanie może spowodować problemy istotne, jeśli kultura przypadkowo jest używany w ustawieniach istotnych dla zabezpieczeń, jak w poniższym przykładzie. Wywołanie metody, takie jak `IsFileURI("file:")` zwraca `true` w przypadku bieżącej kultury stany USA Angielski, ale `false` przypadku tureckiego bieżącej kultury. W związku z tym w systemach tureckiego ktoś obejścia środków bezpieczeństwa, które blokują dostęp do bez uwzględniania wielkości liter identyfikatory URI, które rozpoczynają się od "pliku:".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 W takim przypadku ponieważ "pliku:" jest przeznaczone do interpretowane jako identyfikator z systemem innym niż języka, niezależnych od kultury, kod powinien zamiast tego można zapisać jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>Operacje na ciągach porządkowych  
 Określanie <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> -językowe porównanie, w którym są ignorowane funkcje języków naturalnych oznacza, że wartość w wywołaniu metody. Metody, które są wywoływane z tych <xref:System.StringComparison> wartości podstawa podejmowania decyzji operacji ciągu na porównania jednobajtowych zamiast wielkości liter lub równoważność tabel, które mają zdefiniowane przez kultury. W większości przypadków takie podejście najlepsze pasuje do zamierzonego interpretacji ciągi jednocześnie kod szybszy i bardziej niezawodny.  
  
 {Numer porządkowy porównania są porównywania ciągów, w których każdy bajt każdego ciągu jest porównywany bez językowe interpretacji; na przykład "windows" jest niezgodny "Windows". Jest to zasadniczo wywołanie C runtime `strcmp` funkcji. Użyj tego porównania, jeśli kontekst mówią, że ciągi powinny być dokładnie zgodne lub żądań zachowawcze odpowiednich zasad. Ponadto porównanie liczby porządkowej jest najszybszym operacji porównania, ponieważ dotyczy żadnych reguł językowe podczas określania wyniku.  
  
 Ciągów w .NET mogą zawierać osadzonych znaków wartości null. Jedną z najbardziej przejrzystego różnic między porównanie liczby porządkowej i zależne od kultury (w tym porównań, korzystających z kulturą niezmienną) dotyczy obsługi osadzonych znaków wartości null w ciągu. Następujące znaki są ignorowane, gdy używasz <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.Equals%2A?displayProperty=nameWithType> metody do wykonania porównania zależne od kultury (w tym porównań, korzystających z kulturą niezmienną). W związku z tym w zależne od kultury porównań, ciągi zawierające znaki null osadzonych jest uznawana za równa ciągów, które nie.  
  
> [!IMPORTANT]
>  Mimo że metod porównania ciągów pominięcie osadzonych znaków null ciągu metod wyszukiwania, takie jak <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, i <xref:System.String.StartsWith%2A?displayProperty=nameWithType> nie.  
  
 Poniższy przykład wykonuje zależne od kultury porównanie ciągu "Aa" podobne ciągiem, który zawiera kilka osadzonych znaki null od "A" i "a" i pokazuje, jak dwa ciągi są traktowane jako równe.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 Jednak ciągi nie są uznawane za taki sam, korzystając z liczby porządkowej porównania, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 Porównania porządkowych bez uwzględniania wielkości liter są dalej najbardziej tradycyjne podejście. To porównania Ignoruj wielkość liter w większości; na przykład "windows" pasuje "Windows". Podczas pracy nad znaki ASCII, ta zasada jest odpowiednikiem <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, ale ignoruje zwykle wielkość liter ASCII. W związku z tym dowolny znak Z [A;] (\u0041-\u005A) jest zgodna odpowiedni znak w [, z] (\u0061-\007A). Wielkość liter spoza zakresu ASCII używa tabel Niezmienna kultura. W związku z tym poniższe porównanie:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 jest odpowiednikiem (ale szybciej niż) to porównanie:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 Te porównania nadal są bardzo szybko.  
  
> [!NOTE]
>  Ciąg zachowanie systemu plików, kluczy rejestru i wartości oraz zmienne środowiskowe najlepiej jest reprezentowana przez <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.  
  
 Zarówno <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> i <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> bezpośrednio przy użyciu wartości binarnych, a są najbardziej odpowiednie do dopasowania. Jeśli nie masz pewności o ustawieniach porównania, użyj jednej z tych dwóch wartości. Jednak ponieważ wykonują porównanie po bicie one bez sortowania językowe sortowanie (na przykład słownik w języku angielskim), ale binarny porządek sortowania. Wyniki mogą wydawać się dziwne w kontekstach większość, jeśli wyświetlana dla użytkowników.  
  
 {Numer porządkowy semantyki są domyślnymi indeksami <xref:System.String.Equals%2A?displayProperty=nameWithType> przeciążenia, które nie zawierają <xref:System.StringComparison> argumentu (łącznie z operatora równości). W każdym przypadku firma Microsoft zaleca, aby wywoływać przeciążenia, które ma <xref:System.StringComparison> parametru.  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>Operacje na ciągach, które używają kultury niezmiennej  
 Porównywanie za pomocą Niezmienna kultura <xref:System.Globalization.CultureInfo.CompareInfo%2A> właściwości zwróconej przez statycznych <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. To zachowanie jest taka sama we wszystkich systemach; dowolne znaki poza zakresem jej tłumaczy na co jego zdaniem są równoważne niezmiennej znaków. Te zasady mogą być przydatne dla obsługę jeden zestaw działanie ciągu w kultur, ale często zawiera nieoczekiwane wyniki.  
  
 Porównania bez uwzględniania wielkości liter z kulturą niezmienną Użyj statycznych <xref:System.Globalization.CultureInfo.CompareInfo%2A> właściwości zwróconej przez statycznych <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwość także porównanie informacji. Wielkość różnice między te znaki przetłumaczonego są ignorowane.  
  
 Porównanie, które używają <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> i <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pracy tak samo na ciągi ASCII. Jednak <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> podejmowania decyzji w procesie językowe, które mogą nie być odpowiednie dla ciągów, które mają być interpretowane jako zestaw bajtów. `CultureInfo.InvariantCulture.CompareInfo` Sprawia, że obiekt <xref:System.String.Compare%2A> metody interpretacji niektórych zestawów znaków jako równoważne. Na przykład następujące równoważność jest prawidłowy w obszarze Niezmienna kultura:  
  
 Właściwość InvariantCulture: + ̊ = å  
  
 A MAŁA litera ŁACIŃSKA znaków "" (\u0061), po obok łączenie PIERŚCIEŃ powyżej znak "+"̊"(\u030a), jest interpretowany jako ŁACIŃSKA MAŁA litera A z PIERŚCIEŃ powyżej znak"å"(\u00e5). Jak w poniższym przykładzie pokazano, to zachowanie różni się od liczby porządkowej porównania.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 Przy interpretowaniu nazw plików, pliki cookie lub jakikolwiek inny, gdzie kombinacji takich jak "å" może występować, liczba porządkowa porównania nadal oferują zachowanie najbardziej przejrzystego i dopasowane.  
  
 Salda Niezmienna kultura ma bardzo kilka właściwości, które była przydatna do porównania. Robi porównania w sposób zależnej odpowiednich uniemożliwia jego gwarantującego równoważność pełne symboliczne, ale nie jest opcją do wyświetlenia w dowolnym kultury. Jeden z kilku powodów użyj <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> dla porównania jest do utrwalenia uporządkowanych danych do wyświetlenia cross-culturally identyczne. Na przykład jeśli plik dużej ilości danych, który zawiera listy identyfikatorów posortowane do wyświetlenia dołączony aplikacji, dodanie do tej listy wymagają wstawiania z sortowaniem niezmiennej stylu.  
  
 [Powrót do początku](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Wybieranie elementu StringComparison (porównywania ciągów tekstowych) do metody wywołania  
 W poniższej tabeli przedstawiono mapowanie z ciągu semantycznego kontekst do <xref:System.StringComparison> element członkowski wyliczenia.  
  
|Dane|Zachowanie|Odpowiednie System.StringComparison<br /><br /> value|  
|----------|--------------|-----------------------------------------------------|  
|Identyfikatory wewnętrzny z uwzględnieniem wielkości liter.<br /><br /> Identyfikatory z uwzględnieniem wielkości liter w standardy, takie jak XML i HTTP.<br /><br /> Uwzględniana wielkość liter ustawień związanych z zabezpieczeniami.|Identyfikator językowe, gdzie dokładnie bajtów.|<xref:System.StringComparison.Ordinal>|  
|Identyfikatory wewnętrzny bez uwzględniania wielkości liter.<br /><br /> Identyfikatory bez uwzględniania wielkości liter w standardy, takie jak XML i HTTP.<br /><br /> Ścieżki pliku.<br /><br /> Klucze i wartości rejestru.<br /><br /> Zmienne środowiskowe.<br /><br /> Identyfikatory zasobów (na przykład nazwy dojścia).<br /><br /> Bez uwzględniania wielkości liter ustawień związanych z zabezpieczeniami.|Identyfikator językowe, gdy case nie ma znaczenia; szczególnie danych przechowywanych w większości usług systemu Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|Niektóre utrwalonego zależnej odpowiednie dane.<br /><br /> Wyświetlanie danych językowe, które wymaga stałej sortowania.|Kulturalnie o niesprecyzowanym dane nadal zależnej.|<xref:System.StringComparison.InvariantCulture><br /><br /> —lub—<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|Dane wyświetlane dla użytkownika.<br /><br /> Większość danych wejściowych użytkownika.|Dane, które wymaga przemysłach językowe.|<xref:System.StringComparison.CurrentCulture><br /><br /> —lub—<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [Powrót do początku](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>Typowe metody porównania ciągów w .NET  
 W poniższych sekcjach opisano metody, które są najczęściej używane do porównywania ciągów.  
  
### <a name="stringcompare"></a>Funkcja String.Compare  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Jako najważniejszą interpretacji ciąg operacji należy zbadać wszystkich wystąpień tych wywołań metody do sprawdzenia, czy ciągi powinny być interpretowane zgodnie z bieżącej kultury, oddzielona od kultury (symbolicznie). Zazwyczaj jest to drugie, a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> porównania należy użyć.  
  
 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Klasy, która jest zwracana w wyniku <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> zawiera także właściwości, <xref:System.Globalization.CompareInfo.Compare%2A> metoda, która zapewnia dużą liczbą zgodnych opcje (numer porządkowy zignorowano biały znak, bez uwzględnienia kana typ i tak dalej) za pomocą klasy <xref:System.Globalization.CompareOptions> flagi wyliczenie.  
  
### <a name="stringcompareto"></a>Funkcja String.CompareTo  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Ta metoda nie oferuje obecnie przeciążenia, które określa <xref:System.StringComparison> typu. Zwykle jest możliwe do przekonwertowania tej metody do zalecanej <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formularza.  
  
 Typy, które implementują <xref:System.IComparable> i <xref:System.IComparable%601> interfejsy zaimplementować tę metodę. Ponieważ nie oferuje możliwość <xref:System.StringComparison> parametru często Implementowanie typy umożliwiają użytkownikowi określić <xref:System.StringComparer> ich konstruktora. W poniższym przykładzie zdefiniowano `FileName` klasy, których konstruktora klasy zawiera <xref:System.StringComparer> parametru. To <xref:System.StringComparer> obiekt jest następnie używany w `FileName.CompareTo` metody.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>Funkcja String.Equals  
 Domyślna interpretacji: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 <xref:System.String> Klasa umożliwia testowanie pod kątem równości, wywołując statycznych lub wystąpienia <xref:System.String.Equals%2A> przeciążenia metody lub za pomocą operatora równości statycznych. Przeciążenia i operatora domyślnie używają porównanie liczby porządkowej. Jednak nadal zalecane, aby wywoływać przeciążenia, które jawnie określa <xref:System.StringComparison> typ nawet, jeśli chcesz wykonać porównanie liczby porządkowej; ułatwia kod interpretacji ciąg wyszukiwania.  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper i String.ToLower  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Należy zachować ostrożność podczas użycia tych metod, ponieważ wymuszanie ciągu na wielkie i małe jest często używana jako małych normalizacji porównywania ciągów niezależnie od przypadku. Jeśli tak, należy rozważyć użycie porównania bez uwzględniania wielkości liter.  
  
 <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> i <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> są również dostępne metody. <xref:System.String.ToUpperInvariant%2A>jest standardowym sposobem do sprawę normalizacji. Porównania zostało nawiązane przy użyciu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> behaviorally są złożeniem dwóch wywołania: wywołanie <xref:System.String.ToUpperInvariant%2A> na zarówno argumenty typu string, jak i podczas porównywania przy użyciu <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 Przeciążenia są również dostępne do konwersji na wielkie i małe litery w określoną kulturę, przekazując <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury tej metody.  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper i Char.ToLower  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Te metody działają podobnie do <xref:System.String.ToUpper%2A?displayProperty=nameWithType> i <xref:System.String.ToLower%2A?displayProperty=nameWithType> metod opisanych w poprzedniej sekcji.  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith i String.EndsWith  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Domyślnie wykonać obie te metody porównania z uwzględnieniem kultury.  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf i String.LastIndexOf  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Brak braku spójności w sposób przeciążeń domyślne tych metod wykonywać porównania. Wszystkie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metod, które obejmują <xref:System.Char> parametru wykonać porównanie liczby porządkowej, ale domyślnie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metod, które obejmują <xref:System.String> parametru wykonać uwzględnieniem kultury porównanie.  
  
 Jeśli należy wywołać <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> lub <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> — metoda i przekaż go ciąg do zlokalizowania w bieżącym wystąpieniu, firma Microsoft zaleca, aby wywoływać przeciążenia, które jawnie określa <xref:System.StringComparison> typu. Przeciążenia, które obejmują <xref:System.Char> argument nie umożliwiają określenie <xref:System.StringComparison> typu.  
  
 [Powrót do początku](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, które pośrednio wykonują porównywania ciągu  
 Niektóre metody nie będących ciągami, mających porównania ciągów jako użyj operacji centralnej <xref:System.StringComparer> typu. <xref:System.StringComparer> Klasa obejmuje sześć właściwości statycznych, które zwracają <xref:System.StringComparer> wystąpienia których <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metod wykonania następujących typów porównywania ciągów:  
  
-   Przy użyciu bieżącej kultury porównań ciągów z uwzględnieniem kultury. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Przy użyciu bieżącej kultury porównania bez uwzględniania wielkości liter. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> właściwości.  
  
-   Niezależne od kultury porównań przy użyciu reguł porównania word Niezmienna kultura. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> właściwości.  
  
-   Przy użyciu reguł porównania programu word z kulturą niezmienną porównania bez uwzględniania wielkości liter i niezależnych od kultury. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> właściwości.  
  
-   {Numer porządkowy porównania. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> właściwości.  
  
-   Porównanie porządkowych bez uwzględniania wielkości liter. To <xref:System.StringComparer> obiekt jest zwracany przez <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort i Array.BinarySearch  
 Domyślna interpretacji: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Podczas przechowywania danych w kolekcji lub odczytać danych z bazy danych lub pliku do kolekcji przełączania bieżącej kultury może unieważnić invariants w kolekcji. <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> Metoda zakłada już sortowania elementów w tablicy do wyszukania. Aby posortować dowolny ciąg element w tablicy, <xref:System.Array.Sort%2A?displayProperty=nameWithType> wywołania metody <xref:System.String.Compare%2A?displayProperty=nameWithType> metody porządkowania poszczególne elementy. Za pomocą porównania zależne od kultury może być niebezpieczne są przeszukiwane zmiany kultury między czasem posortowanej tablicy i jego zawartość. Na przykład w poniższym kodzie, przechowywanie i pobieranie działać na modułu porównującego zapewnianej przez niejawnie `Thread.CurrentThread.CurrentCulture` właściwości. Jeśli kultura można przełączać się między wywołań `StoreNames` i `DoesNameExist`, a zwłaszcza, jeśli zawartość tablicy są zachowywane gdzieś między wywołaniami metod dwa, wyszukiwanie binarne może zakończyć się niepowodzeniem.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 Zalecana zmiana pojawia się w następującym przykładzie, który używa tej samej metody porządkowej porównania (niezależne od kultury), sortowanie i wyszukiwanie tablicy. Zmień kod znajduje odzwierciedlenie w wierszach etykietą `Line A` i `Line B` w dwóch przykładach.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 Jeśli te dane są zachowywane i przenosić między kultur i sortowanie służy do przedstawienia tych danych do użytkownika, należy rozważyć przy użyciu <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, który działa zależnej dla lepsze użytkownika dane wyjściowe, ale jest dotknięta zmiany w kultury. Poniższy przykład modyfikuje dwóch poprzednich przykładach na potrzeby sortowanie i wyszukiwanie tablicy Niezmienna kultura.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>Przykład kolekcji: konstruktor tablicy wartości funkcji mieszającej  
 Tworzenie skrótów ciągi zawiera drugi przykład operację, która ma to wpływ na podstawie informacji podanych w którym są porównywane ciągi.  
  
 Poniższy przykład tworzy <xref:System.Collections.Hashtable> obiektu przez przekazanie jej <xref:System.StringComparer> obiektu, który jest zwracany przez <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> właściwości. Ponieważ klasa <xref:System.StringComparer> która jest pochodną <xref:System.StringComparer> implementuje <xref:System.Collections.IEqualityComparer> interfejsu, jego <xref:System.Collections.IEqualityComparer.GetHashCode%2A> metoda jest używana do obliczania skrótu ciągów w tablicy skrótów.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [Powrót do początku](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>Wyświetlanie i utrzymanie sformatowanych danych  
 Podczas wyświetlania danych innych niż ciąg, takie jak liczb i dat i godzin dla użytkowników, należy sformatować je przy użyciu kultury ustawień użytkownika. Domyślnie <xref:System.String.Format%2A?displayProperty=nameWithType> — metoda i `ToString` metody typami numerycznymi i typy daty i godziny użyć bieżącej kultury wątku dla operacji formatowania. Aby jawnie określić, że metody formatowania powinien użyć bieżącej kultury, można wywoływać przeciążenia metody formatowania, który ma `provider` parametrów, takich jak <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> lub <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>i przekaż go <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości.  
  
 Jako dane binarne albo sformatowanych danych, można ją utrwalić danych innych niż ciąg. Jeśli wybierzesz opcję Zapisz go jako sformatowanych danych, należy wywołać formatowania przeciążenie metody, która obejmuje `provider` parametru i przekaż go <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Niezmienna kultura zapewnia spójny format sformatowanych danych, która jest niezależna od kultury i komputera. Z kolei trwałych danych, które jest formatowany przy użyciu kultury niż Niezmienna kultura ma kilka ograniczeń:  
  
-   Dane są prawdopodobnie się bezużyteczne, jeśli jest pobierany na komputerze, który ma inną kulturę, czy użytkownik bieżący system zmiany bieżącej kultury i próbuje pobrać dane.  
  
-   Właściwości culture na określonym komputerze może się różnić od wartości domyślnych. W dowolnym momencie użytkownik może dostosować ustawienia wyświetlania zależne od kultury. W związku z tym sformatowanych danych zapisanych w systemie nie może być do odczytu po użytkownik dostosowuje ustawienia kultury. Przenośność sformatowanych danych na komputerach jest prawdopodobnie bardziej ograniczone.  
  
-   Międzynarodowe, regionalnych lub krajowych standardy, które określają sposób formatowania liczby lub daty i godziny ulegną zmianom, a te zmiany są włączone do aktualizacji systemu operacyjnego Windows. Zmianach Konwencji formatowania danych sformatowanym przy użyciu poprzednich Konwencji może stać się niemożliwe do odczytania.  
  
 Poniższy przykład przedstawia przenośność ograniczone, będącą wynikiem do utrwalenia danych przy użyciu formatowania zależne od kultury. Przykład zapisuje tablicę wartości daty i godziny w pliku. Są one sformatowane przy użyciu konwencji kultury angielski (Stany Zjednoczone). Po aplikacji zmiany bieżącej kultury wątku francuski (Szwajcaria), próbuje odczytać zapisane wartości przy użyciu konwencji formatowania bieżącej kultury. Próba odczytania dwóch danych elementów zgłasza <xref:System.FormatException> wyjątek, a tablica teraz dat zawiera dwa niepoprawne elementy, które są równe <xref:System.DateTime.MinValue>.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 Jednak w przypadku wymiany <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości o <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> w wywołaniach <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, utrwalonego datę i godzinę danych zostanie pomyślnie przywrócone, jak przedstawiono na poniższym danych wyjściowych.  
  
```  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../../docs/standard/base-types/manipulating-strings.md)
