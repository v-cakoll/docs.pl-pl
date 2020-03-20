---
title: 'Łagodzenie: Okres blokowania puli'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457847"
---
# <a name="mitigation-pool-blocking-period"></a>Łagodzenie: Okres blokowania puli
Okres blokowania puli połączeń został usunięty dla połączeń z bazami danych SQL platformy Azure.  
  
## <a name="additional-description"></a>Dodatkowy opis  
 W .NET Framework 4.6.1 i wcześniejszych wersjach, gdy aplikacja napotka przejściowy błąd połączenia podczas łączenia się z bazą danych, nie można szybko ponowić próbę połączenia, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go na 5 sekund do 1 min. Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). To zachowanie jest problematyczne dla połączeń z bazami danych SQL platformy Azure, które często nie z błędami przejściowymi, które są zwykle odzyskane w ciągu kilku sekund. Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna. To zachowanie jest szczególnie problematyczne dla aplikacji sieci web, które łączą się z bazami danych SQL platformy Azure i które muszą być renderowane w ciągu kilku sekund.  
  
 Począwszy od programu .NET Framework 4.6.2, dla otwartych żądań połączeń do \*znanych baz danych \*SQL platformy Azure \*(*.database.windows.net, .database.chinacloudapi.cn, .database.usgovcloudapi.net, .database.cloudapi.de), błędy otwierania połączenia nie są buforowane. W przypadku wszystkich innych prób połączenia okres blokowania puli połączeń jest nadal wymuszany.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana umożliwia natychmiastowe ponowienie próby ponownego ponawiania otwartej próby połączenia dla baz danych SQL platformy Azure, co zwiększa wydajność aplikacji z obsługą chmury.  
  
## <a name="mitigation"></a>Środki zaradcze  
 W przypadku aplikacji, na które ta zmiana ma negatywny wpływ, okres blokowania <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> puli połączeń można skonfigurować, ustawiając nową właściwość.  Wartość właściwości jest członkiem wyliczenia, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> które może przyjmować jedną z trzech wartości:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Poprzednie zachowanie można przywrócić, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> ustawiając <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>właściwość na .  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
