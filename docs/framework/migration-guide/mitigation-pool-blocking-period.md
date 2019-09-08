---
title: Środki zaradcze Okres blokowania puli
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71f1b06e53b3851ca3f65edc1755527779b42a67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789959"
---
# <a name="mitigation-pool-blocking-period"></a>Środki zaradcze Okres blokowania puli
Okres blokowania puli połączeń został usunięty z połączeń z bazami danych Azure SQL Database.  
  
## <a name="additional-description"></a>Dodatkowy opis  
 W .NET Framework 4.6.1 i starszych wersjach, gdy podczas nawiązywania połączenia z bazą danych wystąpi błąd przejściowy, próba połączenia nie może zostać wznowiona szybko, ponieważ pula połączeń buforuje błąd i ponownie zgłasza go przez 5 sekund do 1 długości. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). To zachowanie jest przyczyną problemów z połączeniami z bazami danych Azure SQL, co często kończy się niepowodzeniem z błędami przejściowymi, które zwykle są odzyskiwane z ciągu kilku sekund. Funkcja blokowania puli połączeń oznacza, że aplikacja nie może połączyć się z bazą danych przez dłuższy czas, nawet jeśli baza danych jest dostępna. To zachowanie jest szczególnie problematyczne w przypadku aplikacji sieci Web, które łączą się z bazami danych SQL Azure i które muszą być renderowane w ciągu kilku sekund.  
  
 Począwszy od .NET Framework 4.6.2, w przypadku żądań otwartych dla połączenia z znanymi bazami danych Azure SQL Database ( \**. Database.Windows.NET \*,. Database.chinacloudapi.CN \*,. Database.usgovcloudapi.NET,. Database.cloudapi.de ), błędy otwarcia połączenia nie są buforowane. W przypadku wszystkich innych prób połączenia będzie wymuszany okres blokowania puli połączeń.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana umożliwia natychmiastowe ponawianie próby nawiązania połączenia z bazami danych Azure SQL, co poprawia wydajność aplikacji obsługujących chmurę.  
  
## <a name="mitigation"></a>Ograniczenie  
 W przypadku aplikacji, które mają niekorzystnie wpływać na tę zmianę, można skonfigurować okres blokowania puli połączeń, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> nową właściwość.  Wartość właściwości jest składową <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> wyliczenia, która może przyjmować jedną z trzech wartości:  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Poprzednie zachowanie można przywrócić, ustawiając <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> właściwość na. <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](runtime-changes-in-the-net-framework-4-6-2.md)
