---
ms.openlocfilehash: 6cdd410cc818c2c0a993a364e550f5f92ed6a821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762650"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>ResGen odmawia do załadowania zawartości z sieci web

|   |   |
|---|---|
|Szczegóły|pliki resx mogą zawierać binarne sformatowane dane wejściowe. Jeśli spróbujesz użyć resgen można załadować pliku, który został pobrany z lokalizacji niezaufanych, zakończy się niepowodzeniem do ładowania danych wejściowych domyślnie.|
|Sugestia|ResGen użytkowników, którzy potrzebują ładowanie binarne sformatowane dane wejściowe z niezaufanych lokalizacji można usunąć znacznik sieci Web z pliku wejściowego lub niedoskonałość rezygnacji z zastosowania. Dodaj następujące ustawienie rejestru, aby zastosować niedoskonałość szeroki rezygnacji maszyny: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowanie|
