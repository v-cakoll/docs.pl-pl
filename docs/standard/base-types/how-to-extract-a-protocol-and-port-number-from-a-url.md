---
title: 'Instrukcje: Wyodrębnianie protokołu i numeru portu z adresu URL'
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
ms.openlocfilehash: 48f2bf5c0d9af0a3fc286561ba978f86d1f11ac8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290490"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Instrukcje: Wyodrębnianie protokołu i numeru portu z adresu URL
Poniższy przykład wyodrębnia protokołu i numeru portu z adresu URL.  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody do zwrócenia protokołu, po którym następuje dwukropek i numer portu.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Wzorzec wyrażenia regularnego `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` może być interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu.|  
|`(?<proto>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nadaj nazwę tej grupie `proto` .|  
|`://`|Dopasowuje dwukropek, po którym następuje dwa znaki ukośnika.|  
|`[^/]+?`|Dopasowuje jedno lub więcej wystąpień (ale jak najszybciej) dowolnego znaku, który jest inny niż znak kreski ułamkowej.|  
|`(?<port>:\d+)?`|Dopasowanie do zera lub jednego wystąpienia dwukropka, po którym następuje jeden lub więcej znaków cyfrowych. Nadaj nazwę tej grupie `port` .|  
|`/`|Dopasowuje znak ukośnika.|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Metoda rozszerza `${proto}${port}` sekwencję zamiany, która łączy wartość dwóch nazwanych grup przechwytywanych we wzorcu wyrażenia regularnego. Jest to wygodna alternatywa do jawnego łączenia ciągów pobranych z obiektu kolekcji zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość.  
  
 W przykładzie zastosowano <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę z dwoma podstawiami, `${proto}` a w `${port}` celu uwzględnienia przechwyconych grup w ciągu danych wyjściowych. Przechwycone grupy można pobrać z <xref:System.Text.RegularExpressions.GroupCollection> obiektu dopasowania zamiast tego, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](regular-expressions.md)
