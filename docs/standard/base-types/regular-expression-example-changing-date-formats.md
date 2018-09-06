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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039637"
---
# <a name="regular-expression-example-changing-date-formats"></a>Przykładowe wyrażenie regularne: zmienianie formatów daty
Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, aby zastąpić dat, które mają następującą formę *mm*/*dd*/*rr* z daty mają następującą formę *dd*-*mm*-*rr*.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Poniższy kod przedstawia sposób, w jaki `MDYToDMY` metodę można wywołać w aplikacji.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Komentarze  
 Definicję wzorca wyrażenia regularnego `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?<month>\d{1,2})`|Dopasowuje co najmniej dwie cyfry dziesiętne. Jest to `month` przechwyconą grupę.|  
|`/`|Dopasowuje znak ukośnika.|  
|`(?<day>\d{1,2})`|Dopasowuje co najmniej dwie cyfry dziesiętne. Jest to `day` przechwyconą grupę.|  
|`/`|Dopasowuje znak ukośnika.|  
|`(?<year>\d{2,4})`|Dopasowuje od dwóch do czterech cyfr dziesiętnych. Jest to `year` przechwyconą grupę.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec `${day}-${month}-${year}` definiuje ciąg zastępujący, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`$(day)`|Dodaj parametry przechwycone przez `day` grupa przechwytywania.|  
|`-`|Dodaj łącznik.|  
|`$(month)`|Dodaj parametry przechwycone przez `month` grupa przechwytywania.|  
|`-`|Dodaj łącznik.|  
|`$(year)`|Dodaj parametry przechwycone przez `year` grupa przechwytywania.|  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
