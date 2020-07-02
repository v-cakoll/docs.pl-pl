---
title: 'Przykładowe wyrażenie regularne: zmienianie formatów daty'
ms.date: 06/30/2020
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
ms.openlocfilehash: 3b657ac6c88a1ee846f7f1d2156a18fd34621808
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803953"
---
# <a name="regular-expression-example-changing-date-formats"></a>Przykładowe wyrażenie regularne: zmienianie formatów daty
Poniższy przykład kodu używa <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody, aby zastąpić daty, które mają postać *mm* / *DD* / *yy* z datami, które mają postać *DD* - *mm* - *RR*.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Przykład  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Poniższy kod pokazuje, jak `MDYToDMY` Metoda może być wywoływana w aplikacji.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentarze  
 Wzorzec wyrażenia regularnego `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?<month>\d{1,2})`|Dopasowuje jedną lub dwie cyfry dziesiętne. To jest `month` Grupa przechwycona.|  
|`/`|Dopasowuje znak ukośnika.|  
|`(?<day>\d{1,2})`|Dopasowuje jedną lub dwie cyfry dziesiętne. To jest `day` Grupa przechwycona.|  
|`/`|Dopasowuje znak ukośnika.|  
|`(?<year>\d{2,4})`|Dopasowuje od dwóch do czterech cyfr dziesiętnych. To jest `year` Grupa przechwycona.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec `${day}-${month}-${year}` definiuje ciąg zamienny, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`$(day)`|Dodaj ciąg przechwytywany przez `day` grupę przechwytywania.|  
|`-`|Dodaj łącznik.|  
|`$(month)`|Dodaj ciąg przechwytywany przez `month` grupę przechwytywania.|  
|`-`|Dodaj łącznik.|  
|`$(year)`|Dodaj ciąg przechwytywany przez `year` grupę przechwytywania.|  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](regular-expressions.md)
