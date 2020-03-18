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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138721"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Porady: wyodrębnianie protokółu i numeru portu z adresu URL
Poniższy przykład wyodrębnia protokół i numer portu z adresu URL.  
  
## <a name="example"></a>Przykład  
 W przykładzie <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> użyto metody do zwrócenia protokołu, po którym następuje dwukropek, po którym następuje numer portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Wzorzec `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` wyrażenia regularnego można interpretować w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu.|  
|`(?<proto>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwij `proto`tę grupę .|  
|`://`|Dopasuj dwukropek, po którym następują dwa znaki ukośnika.|  
|`[^/]+?`|Dopasuj jedno lub więcej wystąpień (ale jak najmniej) dowolnego znaku innego niż znak ukośnika.|  
|`(?<port>:\d+)?`|Dopasuj zero lub jedno wystąpienie dwukropka, po którym następuje jeden lub więcej znaków cyfr. Nazwij `port`tę grupę .|  
|`/`|Dopasuj znacznik ukośnika.|  
  
 Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> rozwija sekwencję `${proto}${port}` wymiany, która łączy wartość dwóch nazwanych grup przechwyconych we wzorcu wyrażenia regularnego. Jest wygodną alternatywą jawnie łączenie ciągów pobranych z obiektu kolekcji zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwość.  
  
 W przykładzie <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> użyto metody z dwoma podstawieniami `${proto}` i `${port}`, aby uwzględnić przechwycone grupy w ciągu danych wyjściowych. Przechwycone grupy można <xref:System.Text.RegularExpressions.GroupCollection> pobrać z obiektu dopasowania, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
