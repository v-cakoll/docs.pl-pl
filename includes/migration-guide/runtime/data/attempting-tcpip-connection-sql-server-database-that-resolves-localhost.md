---
ms.openlocfilehash: a4b8a03661650a3ef1d96b656798c3c3d39a5705
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58467091"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Próba nawiązania połączenia protokołu TCP/IP w bazie danych SQL Server, który jest rozpoznawany jako `localhost` kończy się niepowodzeniem

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6 i 4.6.1 nawiązać połączenie TCP/IP z bazy danych programu SQL Server, który jest rozpoznawany jako <code>localhost</code> zakończy się niepowodzeniem z powodu błędu, &quot;wystąpił błąd związany z siecią lub wystąpieniem podczas nawiązywania połączenia z programem SQL Server. Serwer nie został znaleziony lub jest on niedostępny. Sprawdź, czy nazwa wystąpienia jest prawidłowa i że program SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: Interfejsy sieciowe programu SQL, błąd: 26 — błąd podczas znajdowania/podanego wystąpienia)&quot;|
|Sugestia|Ten problem został rozwiązany i przywrócić poprzednie zachowanie w programie .NET Framework 4.6.2. Aby nawiązać połączenie z bazą danych SQL Server, który jest rozpoznawany jako <code>localhost</code>Przeprowadź uaktualnienie do programu .NET Framework 4.6.2.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|

