---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620398"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Kontrolki hostingu zarządzanej przeglądarki z .NET Framework 1,1 i 2,0 są blokowane

#### <a name="details"></a>Szczegóły

Obsługa tych formantów jest zablokowana w programie Internet Explorer.

#### <a name="suggestion"></a>Sugestia

Program Internet Explorer nie będzie mógł uruchomić aplikacji, która używa formantów zarządzanego hostingu w przeglądarce. Poprzednie zachowanie można przywrócić, ustawiając wartość EnableIEHosting podklucza rejestru dla <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> <code>1</code> systemów x86 i dla procesów 32-bitowych w systemach x64 oraz ustawiając <code>EnableIEHosting</code> wartość podklucza rejestru dla <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> <code>1</code> procesów 64-bitowych w systemach x64.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
