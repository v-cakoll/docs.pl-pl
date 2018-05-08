---
title: 'Porady: wyodrębnianie protokółu i numeru portu z adresu URL'
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
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffb31030a2e29458165ae6615a51685ed163fbac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Porady: wyodrębnianie protokółu i numeru portu z adresu URL
Poniższy przykład wyodrębnia protokołem i numerem portu z adresu URL.  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę, aby zwrócić protokołu wprowadź dwukropek i numer portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Wzorzec wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` może zostać zinterpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowania na początku ciąg.|  
|`(?<proto>\w+)`|Dopasowuje co najmniej jeden znak słowa. Określ nazwę tej grupy `proto`.|  
|`://`|Zgodne dwukropkiem następuje dwóch ukośnikami.|  
|`[^/]+?`|Odpowiada jedno lub więcej wystąpień (ale jak najmniejszej liczby możliwie) dowolny znak inny niż znak ukośnika.|  
|`(?<port>:\d+)?`|Zgodne wystąpienie zero lub jeden dwukropek następuje co najmniej jeden znak cyfr. Określ nazwę tej grupy `port`.|  
|`/`|Zgodne znaku ukośnika.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Rozszerza metodę `${proto}${port}` sekwencji zastępczy łączy wartość dwie grupy o nazwie przechwytywane wzorzec wyrażenia regularnego. Jest wygodnym sposobem jawnie łączenie ciągów, pobierana z obiektu kolekcji zwrócony przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości.  
  
 W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody za pomocą dwóch podstawienia `${proto}` i `${port}`, aby uwzględnić przechwyconej grupy w ciągu wyjściowego. Przechwycony grup można pobrać z dopasowania <xref:System.Text.RegularExpressions.GroupCollection> obiekt zamiast tego, jak przedstawiono na poniższym kodem.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
