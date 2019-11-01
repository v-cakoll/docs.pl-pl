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
ms.openlocfilehash: d8546980dd0cf58ca7c095750f2749d5a6bc7723
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084223"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Przykład wyrażenia regularnego: wyszukiwanie wartości HREF
Poniższy przykład wyszukuje ciąg wejściowy i wyświetla wszystkie odwołania href = "..." wartości i ich lokalizacje w ciągu.  
  
## <a name="the-regex-object"></a>Obiekt Regex  
 Ponieważ metoda `DumpHRefs` może być wywoływana wiele razy z kodu użytkownika, używa metody <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> `static` (`Shared` w Visual Basic). Dzięki temu aparat wyrażeń regularnych może buforować wyrażenie regularne i pozwala uniknąć obciążenia wystąpienia nowego obiektu <xref:System.Text.RegularExpressions.Regex> przy każdym wywołaniu metody. Obiekt <xref:System.Text.RegularExpressions.Match> jest następnie używany do iteracji we wszystkich dopasowaniach w ciągu.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Poniższy przykład ilustruje wywołanie metody `DumpHRefs`.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`href`|Dopasowuje ciąg literału "href". W dopasowaniu nie jest rozróżniana wielkość liter.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`=`|Dopasowuje znak równości.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Dopasowanie jednego z następujących elementów bez przypisywania wyniku do przechwyconej grupy:<br /> <ul><li><p>Znak cudzysłowu lub apostrofu, po którym następuje zero lub więcej wystąpień dowolnego znaku innego niż znak cudzysłowu lub apostrofu, po którym następuje znak cudzysłowu lub apostrof. Grupa o nazwie `1` jest zawarta w tym wzorcu.</p></li><li><p>Co najmniej jeden znak niebędący odstępem. Grupa o nazwie `1` jest zawarta w tym wzorcu.</p></li></ul>|  
|`(?<1>[^"']*)`|Przypisz zero lub więcej wystąpień dowolnego znaku innego niż znak cudzysłowu lub apostrofu do grupy przechwytywania o nazwie `1`.|  
|`(?<1>\S+)`|Przypisz co najmniej jeden znak niebędący odstępem do grupy przechwytywania o nazwie `1`.|  
  
## <a name="match-result-class"></a>Dopasuj wynik klasy  
 Wyniki wyszukiwania są przechowywane w klasie <xref:System.Text.RegularExpressions.Match>, która zapewnia dostęp do wszystkich podciągów wyodrębnionych przez wyszukiwanie. Odwołuje się również do wyszukiwanego ciągu i używanego wyrażenia regularnego, dzięki czemu można wywołać metodę <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>, aby wykonać kolejne wyszukiwanie, rozpoczynając od ostatniego zakończono.  
  
## <a name="explicitly-named-captures"></a>Przechwytuje wyraźnie nazwane  
 W tradycyjnych wyrażeniach regularnych przechwytywanie nawiasów jest numerowane kolejno automatycznie. Prowadzi to do dwóch problemów. Po pierwsze, jeśli wyrażenie regularne jest modyfikowane przez wstawianie lub usuwanie zestawu nawiasów, cały kod, który odwołuje się do numerowanych przechwytywania, musi zostać ponownie zapisany w celu odzwierciedlenia nowej numeracji. Drugi, ponieważ różne zestawy nawiasów często są używane do zapewnienia dwóch alternatywnych wyrażeń dla akceptowalnego dopasowania, może być trudne do ustalenia, które z dwóch wyrażeń faktycznie zwracają wynik.  
  
 Aby rozwiązać te problemy, Klasa <xref:System.Text.RegularExpressions.Regex> obsługuje składnię `(?<name>…)` do przechwytywania dopasowania do określonego miejsca (miejsce może być nazwane przy użyciu ciągu lub liczby całkowitej; liczby całkowite można wielokrotnie odwoływać). W rezultacie alternatywne dopasowania dla tego samego ciągu All można skierować do tego samego miejsca. W przypadku konfliktu ostatnie dopasowanie opuszczone w gnieździe to pomyślne dopasowanie. (Jednak kompletna lista wielu dopasowań dla jednego gniazda jest dostępna. Szczegółowe informacje znajdują się w kolekcji <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.)  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
