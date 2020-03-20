---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237837"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Próba połączenia TCP/IP z bazą danych programu `localhost` SQL Server, która jest rozpoznawana pod w rozpoznawaniu awarii

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6 i 4.6.1 podczas próby połączenia TCP/IP <code>localhost</code> z bazą &quot;danych programu SQL Server, która rozwiązuje problem z błędem, wystąpił błąd związany z siecią lub wystąpieniem podczas ustanawiania połączenia z programem SQL Server. Serwer nie został znaleziony lub był niedostępny. Sprawdź, czy nazwa wystąpienia jest poprawna i czy program SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (dostawca: interfejsy sieciowe SQL, błąd: 26 - Określono błąd lokalizowania serwera/wystąpienia)&quot;|
|Sugestia|Ten problem został rozwiązany i poprzednie zachowanie przywrócone w .NET Framework 4.6.2. Aby połączyć się z databsae <code>localhost</code>programu SQL Server, który jest rozpoznawany do , uaktualnienie do programu .NET Framework 4.6.2.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
