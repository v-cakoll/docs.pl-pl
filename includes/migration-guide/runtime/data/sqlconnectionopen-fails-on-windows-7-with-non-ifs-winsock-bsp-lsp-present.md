---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235557"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open Windows 7 kończy się niepowodzeniem bez IFS Winsock BSP lub LSP obecne

|   |   |
|---|---|
|Szczegóły|<xref:System.Data.SqlClient.SqlConnection.Open> i <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> się niepowodzeniem w .NET Framework 4.5, jeśli działająca na maszynie Windows 7 przy użyciu innego niż IFS Winsock BSP lub dostawcą rozwiązań Licencjonowania są dostępne na komputerze. Aby określić, czy zainstalowano BSP bez IFS lub dostawcą rozwiązań Licencjonowania, użyj <code>netsh WinSock Show Catalog</code> polecenie i zbadaj co <code>Winsock Catalog Provider Entry</code> elementu, który jest zwracany. Jeśli ma wartość flagi usługi <code>0x20000</code> ustawiony bit, dostawca używa IFS obsługuje i będzie działać poprawnie. Jeśli <code>0x20000</code> bit jest jasne (nie ustawiono), jest inne niż IFS BSP lub dostawcą rozwiązań Licencjonowania.|
|Sugestia|Ten błąd został naprawiony w programie .NET Framework 4.5.2, dzięki czemu można uniknąć przez uaktualnienie programu .NET Framework. Alternatywnie można uniknąć, usuwając wszystkie zainstalowane bez - IFS Winsock nazywani.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
