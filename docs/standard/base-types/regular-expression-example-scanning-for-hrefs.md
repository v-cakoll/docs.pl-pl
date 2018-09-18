---
title: 'Przykład wyrażenia regularnego: wyszukiwanie wartości HREF'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6fe667ca908b2a4ba16e34e8e74dd39ca01f153
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070829"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Przykład wyrażenia regularnego: wyszukiwanie wartości HREF
W poniższym przykładzie wyszukuje ciąg wejściowy i wyświetla wszystkie href = "...", wartości i ich lokalizacji w ciągu.  
  
## <a name="the-regex-object"></a>Obiekt Regex  
 Ponieważ `DumpHRefs` metodę można wywoływać wielokrotnie z kodu użytkownika, używa ona `static` (`Shared` w języku Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody. To umożliwia aparatowi wyrażeń regularnych i wyrażeń regularnych w pamięci podręcznej i pozwala uniknąć konieczności tworzenia wystąpienia nowego <xref:System.Text.RegularExpressions.Regex> obiektu każdym wywołaniu metody. A <xref:System.Text.RegularExpressions.Match> obiekt jest następnie używany do iterowania po wszystkie dopasowania w ciągu.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 W poniższym przykładzie pokazano następnie wywołania `DumpHRefs` metody.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Definicję wzorca wyrażenia regularnego `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`href`|Jest zgodny z ciągiem literału "href". Dopasowanie jest rozróżniana wielkość liter.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`=`|Dopasowuje znak równości.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|<code>(?:\["'\](?<1>\[^"'\]*)["']&#124;(?<1>\S+))</code>|Pasuje do jednej z następujących czynności bez przypisywania wynik do przechwyconej grupy:<br /> <ul><li><p>Cudzysłów lub apostrof, w którym następuje zero lub więcej wystąpień dowolnego znaku innego niż cudzysłów lub apostrof, w którym następuje cudzysłów lub apostrof. Grupa o nazwie `1` znajduje się w tym wzorcu.</p></li><li><p>Co najmniej jeden znak inny niż biały. Grupa o nazwie `1` znajduje się w tym wzorcu.</p></li></ul>|  
|`(?<1>[^"']*)`|Przypisać zero lub więcej wystąpień dowolnego znaku innego niż cudzysłów lub apostrof grupa przechwytywania o nazwie `1`.|  
|`(?<1>\S+)`|Przypisz co najmniej jeden znak inny niż biały do grupa przechwytywania o nazwie `1`.|  
  
## <a name="match-result-class"></a>Dopasuj wynik klasy  
 Wyniki wyszukiwania są przechowywane w <xref:System.Text.RegularExpressions.Match> klasy, która zapewnia dostęp do wszystkich podciągów wyodrębnionych przez wyszukiwanie. Również pamięta ciąg wyszukiwany i wyrażenie regularne jest używane, dzięki czemu można wywoływać <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody do wykonania, której ostatni z nich zakończyło się innym uruchamianie wyszukiwania.  
  
## <a name="explicitly-named-captures"></a>Przechwytuje wyraźnie nazwane  
 W tradycyjnych wyrażeń regularnych nawiasów przechwytywania są automatycznie numerowane. Prowadzi to do dwa problemy. Najpierw wyrażenia regularnego jest modyfikowany przez wstawiania lub usuwania zestaw nawiasów, muszą zostać przepisane aby odzwierciedlały nową numerację cały kod, który odwołuje się do przechwytywania numerowanej. Po drugie ponieważ często różnych zestawów nawiasów jest używana do udostępniania dwóch wyrażeń alternatywnych dopasowanie dopuszczalna, może być trudno określić, które z dwóch wyrażeń faktycznie zwróciło wynik.  
  
 Aby rozwiązać te problemy <xref:System.Text.RegularExpressions.Regex> klasa obsługuje składnię `(?<name>…)` przechwytywania dopasowanie do określonego miejsca (gniazdo może mieć nazwę, za pomocą ciąg lub liczba całkowita; liczb całkowitych można odwołać szybciej). W efekcie alternatywne dopasowania dla tego samego ciągu, który wszystkie może zostać skierowany do tej samej lokalizacji. W przypadku konfliktu ostatnim dopasowaniem upuścić na gniazdo jest udanych dopasowań. (Jednak uzyskać pełną listę wiele dopasowań dla jednego miejsca jest dostępna. Zobacz <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji, aby uzyskać szczegółowe informacje.)  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
