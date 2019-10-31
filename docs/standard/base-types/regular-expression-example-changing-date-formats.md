---
title: 'Przykładowe wyrażenie regularne: zmienianie formatów daty'
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
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 358e26957747073fec9dfe9eb0d404cb438afaf9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084181"
---
# <a name="regular-expression-example-changing-date-formats"></a>Przykładowe wyrażenie regularne: zmienianie formatów daty
Poniższy przykład kodu używa metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>, aby zastąpić daty, które mają postać *mm*/*DD*/*yy* z datami, które mają postać *DD*-*mm*-*RR*.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Poniższy kod pokazuje, jak Metoda `MDYToDMY` może być wywoływana w aplikacji.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentarze  
 `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?<month>\d{1,2})`|Dopasowuje jedną lub dwie cyfry dziesiętne. To jest Grupa przechwycona `month`.|  
|`/`|Dopasowuje znak ukośnika.|  
|`(?<day>\d{1,2})`|Dopasowuje jedną lub dwie cyfry dziesiętne. To jest Grupa przechwycona `day`.|  
|`/`|Dopasowuje znak ukośnika.|  
|`(?<year>\d{2,4})`|Dopasowuje od dwóch do czterech cyfr dziesiętnych. To jest Grupa przechwycona `year`.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec `${day}-${month}-${year}` definiuje ciąg zamienny, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`$(day)`|Dodaj ciąg przechwytywany przez grupę przechwytywania `day`.|  
|`-`|Dodaj łącznik.|  
|`$(month)`|Dodaj ciąg przechwytywany przez grupę przechwytywania `month`.|  
|`-`|Dodaj łącznik.|  
|`$(year)`|Dodaj ciąg przechwytywany przez grupę przechwytywania `year`.|  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
