---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774212"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>WPF sprawdzanie pisowni w włączona tekst kontrolki nie będzie działać w systemie Windows 10 dla języków nie ma na liście język systemu operacyjnego

|   |   |
|---|---|
|Szczegóły|Moduł sprawdzania pisowni uruchomiony w systemie Windows 10, mogą nie działać dla kontrolek WPF z komputerów z obsługą tekstu możliwości sprawdzania pisowni platformy nie są dostępne tylko dla języków występuje na liście języków. W systemie Windows 10 gdy język jest dodawany do listy dostępnych klawiatury Windows automatycznie pobiorą i zainstalują odpowiedniej funkcji pakietu żądanie (FDZ), która oferuje możliwości sprawdzania pisowni. Dodając język do listy języków, będzie objęta sprawdzania pisowni.|
|Sugestia|Należy pamiętać, że język lub tekst ma być sprawdzana pisownia należy dodać język do sprawdzania pisowni do pracy w systemie Windows 10.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
