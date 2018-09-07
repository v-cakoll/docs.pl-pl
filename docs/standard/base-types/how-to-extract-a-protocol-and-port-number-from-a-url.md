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
ms.openlocfilehash: a08e97b02e2f60422132e97e2f3f7d4d2d5b8ec4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061666"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Porady: wyodrębnianie protokółu i numeru portu z adresu URL
Poniższy przykład wyodrębnia protokół i numer portu z adresu URL.  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę, aby zwrócić protokołu następuje dwukropek i numer portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` mogą być interpretowane, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu.|  
|`(?<proto>\w+)`|Dopasowuje co najmniej jeden znak słowa. Określ nazwę tej grupy `proto`.|  
|`://`|Dopasowuje dwukropek następuje dwóch znaków ukośnika.|  
|`[^/]+?`|Dopasowuje jedno lub więcej wystąpień (ale możliwie) dowolny znak inny niż znak ukośnika.|  
|`(?<port>:\d+)?`|Dopasowuje zero lub jeden wystąpienie średnikami, na którym następuje co najmniej jeden znak cyfry. Określ nazwę tej grupy `port`.|  
|`/`|Dopasowuje znak ukośnika.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Rozszerza metoda `${proto}${port}` sekwencji zastąpienie łączy wartości z dwóch grup o nazwie przechwycone we wzorcu wyrażenia regularnego. Jest wygodne alternatywa jawnie łączenia ciągów pobierana z obiektu kolekcji zwrócony przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości.  
  
 W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody za pomocą dwóch podstawienia `${proto}` i `${port}`, aby uwzględnić przechwyconych grupach w ciągu wyjściowym. Możesz pobrać przechwyconych grupach z dopasowania <xref:System.Text.RegularExpressions.GroupCollection> zamiast tego, co ilustruje poniższy kod obiektu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
