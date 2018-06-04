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
ms.openlocfilehash: b270559e9e73e18bebb29e36b815268d5426a940
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728683"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Przykład wyrażenia regularnego: wyszukiwanie wartości HREF
Poniższy przykład wyszukuje ciąg wejściowy i wyświetla wszystkie href = "..." wartości i ich lokalizacji w ciągu.  
  
## <a name="the-regex-object"></a>Obiekt Regex  
 Ponieważ `DumpHRefs` metoda może być wywołana wiele razy z kodu użytkownika, używa `static` (`Shared` w języku Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody. To umożliwia aparat wyrażeń regularnych do pamięci podręcznej z wyrażeniem regularnym i pozwala uniknąć ponoszenia dodatkowych nakładów na uruchamianiu nową <xref:System.Text.RegularExpressions.Regex> obiektu zawsze ma zostać wywołana metoda. A <xref:System.Text.RegularExpressions.Match> obiekt jest następnie używany do iterowania po wszystkich dopasowań w ciągu.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Poniższy przykład przedstawia następnie wywołania `DumpHRefs` metody.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Wzorzec wyrażenia regularnego `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`href`|Zgodny z ciągiem literału "href". Dopasowanie jest rozróżniana wielkość liter.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`=`|Zgodne znaku równości.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|<code>(?:\["'\](?<1>\[^"'\]*)["']&#124;(?<1>\S+))</code>|Pasuje do jednej z następujących bez przypisywanie wynik do przechwyconej grupy:<br /> <ul><li><p>Znak cudzysłowu lub apostrof, a następnie zero lub więcej wystąpień dowolnych znaków innych niż cudzysłów lub apostrof następuje znak cudzysłowu lub apostrof. Grupa o nazwie `1` znajduje się w tym wzorcu.</p></li><li><p>Co najmniej jeden z systemem innym niż biały znak. Grupa o nazwie `1` znajduje się w tym wzorcu.</p></li></ul>|  
|`(?<1>[^"']*)`|Przypisz zero lub więcej wystąpień dowolnych znaków innych niż cudzysłów lub apostrof do przechwytywania grupy o nazwie `1`.|  
|`(?<1>\S+)`|Przypisz co najmniej jeden z systemem innym niż biały znak do przechwytywania grupy o nazwie `1`.|  
  
## <a name="match-result-class"></a>Dopasuj wynik klasy  
 Wyniki wyszukiwania są przechowywane w <xref:System.Text.RegularExpressions.Match> klasy, która zapewnia dostęp do wszystkich podciągów wyodrębnione podczas wyszukiwania. On również pamięta przeszukiwany ciąg i wyrażenie regularne używane, dlatego może wywołać <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodę w celu których ostatnio zakończone innego początkowy wyszukiwania.  
  
## <a name="explicitly-named-captures"></a>Przechwytuje wyraźnie nazwane  
 W tradycyjnym wyrażeń regularnych nawiasów przechwytywania automatycznie numerowane kolejno. Prowadzi to do dwóch problemów. Najpierw Jeśli wyrażenie regularne jest modyfikowany przez wstawiania lub usuwania zestawu nawiasów, żadnego kodu, który odwołuje się do przechwytywania numerowane należy ponownie zapisać celu odzwierciedlenia nowych numerów. Po drugie ponieważ często różne zestawy nawiasów służą do zapewniania dwóch wyrażeń alternatywne dopasowania dopuszczalne, może być trudne do ustalenia, które z dwóch wyrażeń faktycznie zwrócił wynik.  
  
 Aby rozwiązać te problemy, <xref:System.Text.RegularExpressions.Regex> klasa obsługuje składnię `(?<name>…)` przechwytywania dopasowania do określonego miejsca (gniazdo może nosić przy użyciu ciąg lub liczba całkowita; liczby całkowite można odwołać szybciej). W związku z tym alternatywne dopasowania dla tych samych parametrach, którego wszystkie może zostać skierowany do tej samej lokalizacji. W przypadku konfliktu ostatni dopasowania upuścić na gnieździe jest pomyślne dopasowanie. (Jednak pełną listę wiele elementów zgodnych z jednego miejsca jest dostępne. Zobacz <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji, aby uzyskać więcej informacji.)  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
