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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084223"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Przykład wyrażenia regularnego: wyszukiwanie wartości HREF
Poniższy przykład przeszukuje ciąg wejściowy i wyświetla wszystkie href="..." wartości i ich lokalizacji w ciągu.  
  
## <a name="the-regex-object"></a>Obiekt Regex  
 Ponieważ `DumpHRefs` metoda może być wywoływana wiele razy `static` z`Shared` kodu użytkownika, używa (w języku Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda. Dzięki temu aparat wyrażeń regularnych do buforowania wyrażenia regularnego i <xref:System.Text.RegularExpressions.Regex> pozwala uniknąć narzutów tworzenia wystąpienia nowego obiektu za każdym razem, gdy wywoływana jest metoda. Obiekt <xref:System.Text.RegularExpressions.Match> jest następnie używany do iterate przez wszystkie dopasowania w ciągu.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 Poniższy przykład następnie ilustruje `DumpHRefs` wywołanie metody.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Wzorzec `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`href`|Dopasuj dosłowny ciąg "href". W meczu nie uwzględnia się wielkości liter.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`=`|Dopasuj znak równości.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|Dopasuj jedną z następujących elementów bez przypisywania wyniku do przechwyconej grupy:<br /> <ul><li><p>Cudzysłów lub apostrof, po którym następuje zero lub więcej wystąpień jakiegokolwiek znaku innego niż cudzysłów lub apostrof, po którym następuje cudzysłów lub apostrof. Nazwana `1` grupa znajduje się w tym wzorcu.</p></li><li><p>Jeden lub więcej znaków innych niż białe. Nazwana `1` grupa znajduje się w tym wzorcu.</p></li></ul>|  
|`(?<1>[^"']*)`|Przypisz zero lub więcej wystąpień dowolnego znaku innego niż cudzysłów `1`lub apostrof do grupy przechwytywania o nazwie .|  
|`(?<1>\S+)`|Przypisz jeden lub więcej znaków innych niż białe `1`do grupy przechwytywania o nazwie .|  
  
## <a name="match-result-class"></a>Dopasuj wynik klasy  
 Wyniki wyszukiwania są przechowywane w <xref:System.Text.RegularExpressions.Match> klasie, która zapewnia dostęp do wszystkich podciągów wyodrębnionych przez wyszukiwanie. Zapamiętuje również przeszukiwany ciąg i używane wyrażenie regularne, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> dzięki czemu można wywołać metodę do wykonania innego wyszukiwania, zaczynając od miejsca zakończenia ostatniego.  
  
## <a name="explicitly-named-captures"></a>Przechwytuje wyraźnie nazwane  
 W tradycyjnych wyrażeniach regularnych przechwytywanie nawiasów jest automatycznie numerowane sekwencyjnie. Prowadzi to do dwóch problemów. Po pierwsze, jeśli wyrażenie regularne jest modyfikowane przez wstawienie lub usunięcie zestawu nawiasów, cały kod, który odwołuje się do ponumerowanych ujęć, musi zostać przepisany w celu odzwierciedlenia nowej numeracji. Po drugie, ponieważ różne zestawy nawiasów często są używane do zapewnienia dwóch alternatywnych wyrażeń dla akceptowalnego dopasowania, może być trudne do określenia, które z dwóch wyrażeń faktycznie zwrócił wynik.  
  
 Aby rozwiązać te <xref:System.Text.RegularExpressions.Regex> problemy, klasa `(?<name>…)` obsługuje składnię przechwytywania dopasowania do określonego gniazda (gniazdo można nazwać za pomocą ciągu lub liczby całkowitej; liczby całkowite można przypomnieć szybciej). W związku z tym alternatywne dopasowania dla tego samego ciągu wszystkie mogą być kierowane do tego samego miejsca. W przypadku konfliktu, ostatni mecz spadł do gniazda jest udane dopasowanie. (Dostępna jest jednak pełna lista wielu dopasowań dla jednego gniazda. Zobacz <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcję, aby uzyskać szczegółowe informacje.)  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
