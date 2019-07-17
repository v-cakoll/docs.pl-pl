---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237837"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Próba nawiązania połączenia protokołu TCP/IP w bazie danych SQL Server, który jest rozpoznawany jako `localhost` kończy się niepowodzeniem

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6 i 4.6.1 nawiązać połączenie TCP/IP z bazy danych programu SQL Server, który jest rozpoznawany jako <code>localhost</code> zakończy się niepowodzeniem z powodu błędu, &quot;wystąpił błąd związany z siecią lub wystąpieniem podczas nawiązywania połączenia z programem SQL Server. Serwer nie został znaleziony lub jest on niedostępny. Sprawdź, czy nazwa wystąpienia jest prawidłowa i że program SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: Interfejsy sieciowe programu SQL, błąd: 26 — błąd podczas znajdowania/podanego wystąpienia)&quot;|
|Sugestia|Ten problem został rozwiązany i przywrócić poprzednie zachowanie w programie .NET Framework 4.6.2. Połączyć się z opcjami programu SQL Server, który jest rozpoznawany jako <code>localhost</code>Przeprowadź uaktualnienie do programu .NET Framework 4.6.2.|
|Scope|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
