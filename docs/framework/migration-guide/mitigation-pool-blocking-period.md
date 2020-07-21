---
title: 'Środki zaradcze: okres blokowania puli'
description: Dowiedz się, jak uniknąć problemów spowodowanych przez okres blokowania puli połączeń, który jest usuwany dla połączeń z bazami danych Azure SQL.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: be60fe87952697d964571176743a4e6f839c4894
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475414"
---
# <a name="mitigation-pool-blocking-period"></a>Środki zaradcze: okres blokowania puli
Okres blokowania puli połączeń został usunięty z połączeń z bazami danych Azure SQL Database.  
  
## <a name="additional-description"></a>Dodatkowy opis  
 W .NET Framework 4.6.1 i starszych wersjach, gdy podczas łączenia się z bazą danych w aplikacji wystąpi przejściowy błąd połączenia, próba połączenia nie może być podejmowana szybko, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 minuty. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). To zachowanie jest przyczyną problemów z połączeniami z bazami danych Azure SQL, co często kończy się niepowodzeniem z błędami przejściowymi, które zwykle są odzyskiwane z ciągu kilku sekund. Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna. To zachowanie jest szczególnie problematyczne w przypadku aplikacji sieci Web, które łączą się z bazami danych SQL Azure i które muszą być renderowane w ciągu kilku sekund.  
  
 Począwszy od .NET Framework 4.6.2, w przypadku żądań otwartych dla połączenia z znanymi bazami danych Azure SQL Database (*. database.windows.net, \* . Database.chinacloudapi.CN, \* . Database.usgovcloudapi.NET, \* . Database.cloudapi.de), błędy otwarcia połączenia nie są buforowane. W przypadku wszystkich innych prób połączenia będzie wymuszany okres blokowania puli połączeń.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana umożliwia natychmiastowe ponawianie próby nawiązania połączenia z bazami danych Azure SQL, co poprawia wydajność aplikacji obsługujących chmurę.  
  
## <a name="mitigation"></a>Ograniczanie ryzyka  
 W przypadku aplikacji, które mają niekorzystnie wpływać na tę zmianę, można skonfigurować okres blokowania puli połączeń, ustawiając nową <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> Właściwość.  Wartość właściwości jest składową <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> wyliczenia, która może przyjmować jedną z trzech wartości:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Poprzednie zachowanie można przywrócić, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> Właściwość na <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
