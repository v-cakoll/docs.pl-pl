---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803257"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open kończy się niepowodzeniem w systemie Windows 7 z non-IFS Winsock BSP lub LSP obecny

|   |   |
|---|---|
|Szczegóły|<xref:System.Data.SqlClient.SqlConnection.Open>i <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> zakończyć się niepowodzeniem w programie .NET Framework 4.5, jeśli działa na komputerze z systemem Windows 7 z systemem BSP lub LSP innego niż IFS Winsock są obecne na komputerze. Aby ustalić, czy jest zainstalowany bsp lub LSP <code>netsh WinSock Show Catalog</code> nieobjęty IFS, użyj polecenia i sprawdź każdy <code>Winsock Catalog Provider Entry</code> zwracany element. Jeśli service flags wartość <code>0x20000</code> ma bit ustawiony, dostawca używa uchwytów IFS i będzie działać poprawnie. Jeśli <code>0x20000</code> bit jest czysty (nie ustawiony), jest to bsp lub LSP innego niż IFS.|
|Sugestia|Ten błąd został naprawiony w .NET Framework 4.5.2, dzięki czemu można go uniknąć, uaktualniając program .NET Framework. Alternatywnie można tego uniknąć, usuwając wszystkie zainstalowane lspy winsocka spoza ifs.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
