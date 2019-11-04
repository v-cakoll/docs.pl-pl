---
title: 'Środki zaradcze: okres blokowania puli'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457847"
---
# <a name="mitigation-pool-blocking-period"></a>Środki zaradcze: okres blokowania puli
Okres blokowania puli połączeń został usunięty z połączeń z bazami danych Azure SQL Database.  
  
## <a name="additional-description"></a>Dodatkowy opis  
 W .NET Framework 4.6.1 i starszych wersjach, gdy podczas nawiązywania połączenia z bazą danych wystąpi błąd przejściowy, próba połączenia nie może zostać wznowiona szybko, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 długości. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). To zachowanie jest przyczyną problemów z połączeniami z bazami danych Azure SQL, co często kończy się niepowodzeniem z błędami przejściowymi, które zwykle są odzyskiwane z ciągu kilku sekund. Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna. To zachowanie jest szczególnie problematyczne w przypadku aplikacji sieci Web, które łączą się z bazami danych SQL Azure i które muszą być renderowane w ciągu kilku sekund.  
  
 Począwszy od .NET Framework 4.6.2, w przypadku żądań otwartych dla połączenia z znanymi bazami danych Azure SQL Database (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), połączenie Błędy otwierania nie są buforowane. W przypadku wszystkich innych prób połączenia będzie wymuszany okres blokowania puli połączeń.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana umożliwia natychmiastowe ponawianie próby nawiązania połączenia z bazami danych Azure SQL, co poprawia wydajność aplikacji obsługujących chmurę.  
  
## <a name="mitigation"></a>Ograniczenie  
 W przypadku aplikacji, które mają niekorzystnie wpływać na tę zmianę, można skonfigurować okres blokowania puli połączeń, ustawiając nową właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.  Wartość właściwości jest składową wyliczenia <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType>, która może przyjmować jedną z trzech wartości:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Poprzednie zachowanie można przywrócić, ustawiając właściwość <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
