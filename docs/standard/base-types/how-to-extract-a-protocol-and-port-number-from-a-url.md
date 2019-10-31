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
ms.openlocfilehash: f2704e3fb5ceb68609a475d52e11030177ad760b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138721"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Porady: wyodrębnianie protokółu i numeru portu z adresu URL
Poniższy przykład wyodrębnia protokołu i numeru portu z adresu URL.  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto metody <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> do zwrócenia protokołu, po którym następuje dwukropek i numer portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Wzorzec wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` można interpretować, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu.|  
|`(?<proto>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nadaj tej grupie nazwę `proto`.|  
|`://`|Dopasowuje dwukropek, po którym następuje dwa znaki ukośnika.|  
|`[^/]+?`|Dopasowuje jedno lub więcej wystąpień (ale jak najszybciej) dowolnego znaku, który jest inny niż znak kreski ułamkowej.|  
|`(?<port>:\d+)?`|Dopasowanie do zera lub jednego wystąpienia dwukropka, po którym następuje jeden lub więcej znaków cyfrowych. Nadaj tej grupie nazwę `port`.|  
|`/`|Dopasowuje znak ukośnika.|  
  
 Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> rozszerza `${proto}${port}` sekwencję zastępowania, która łączy wartość dwóch nazwanych grup przechwyconych we wzorcu wyrażenia regularnego. Jest to wygodna alternatywa do jawnego łączenia ciągów pobranych z obiektu kolekcji zwróconego przez właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>.  
  
 W przykładzie zastosowano metodę <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> z dwoma podstawiami, `${proto}` i `${port}`, aby uwzględnić przechwycone grupy w ciągu danych wyjściowych. Przechwycone grupy można pobrać z obiektu <xref:System.Text.RegularExpressions.GroupCollection> dopasowania zamiast tego, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
