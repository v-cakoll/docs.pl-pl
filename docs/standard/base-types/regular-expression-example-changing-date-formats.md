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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084181"
---
# <a name="regular-expression-example-changing-date-formats"></a>Przykładowe wyrażenie regularne: zmienianie formatów daty
Poniższy przykład kodu <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> używa metody do zastąpienia dat, które mają formularz *mm*/*dd*/*yy* z datami, które mają formularz *dd*-*mm*-*yy*.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Poniższy kod pokazuje, `MDYToDMY` jak można wywołać metodę w aplikacji.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentarze  
 Wzorzec `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?<month>\d{1,2})`|Dopasuj jedną lub dwie cyfry dziesiętne. Jest to `month` przechwycona grupa.|  
|`/`|Dopasuj znacznik ukośnika.|  
|`(?<day>\d{1,2})`|Dopasuj jedną lub dwie cyfry dziesiętne. Jest to `day` przechwycona grupa.|  
|`/`|Dopasuj znacznik ukośnika.|  
|`(?<year>\d{2,4})`|Dopasuj od dwóch do czterech cyfr dziesiętnych. Jest to `year` przechwycona grupa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Deseń `${day}-${month}-${year}` definiuje ciąg zastępczy, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`$(day)`|Dodaj ciąg przechwycony `day` przez grupę przechwytywania.|  
|`-`|Dodaj łącznik.|  
|`$(month)`|Dodaj ciąg przechwycony `month` przez grupę przechwytywania.|  
|`-`|Dodaj łącznik.|  
|`$(year)`|Dodaj ciąg przechwycony `year` przez grupę przechwytywania.|  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
