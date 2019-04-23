---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804667"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Kontrolki hostingu programu Managed browser z .NET Framework 1.1 i 2.0 są zablokowane.

|   |   |
|---|---|
|Szczegóły|Obsługa tych formantów jest zablokowana w programie Internet Explorer.|
|Sugestia|Program Internet Explorer nie będzie mógł uruchomić aplikacji, która używa formantów zarządzanego hostingu w przeglądarce. Poprzednie zachowanie można przywrócić, ustawiając wartość EnableIEHosting podklucza rejestru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> do <code>1</code> dla x86 systemów i procesów 32-bitowych w x64 systemów i ustawiając <code>EnableIEHosting</code> wartość podklucza rejestru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>do <code>1</code> dla procesów 64-bitowego na x64 systemów.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
