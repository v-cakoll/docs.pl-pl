---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858425"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Sprawdzanie pisowni WPF w formantach z włączoną funkcją tekstową nie będzie działać w systemie Windows 10 dla języków, które nie znajdują się na liście języków wejściowych systemu operacyjnego

|   |   |
|---|---|
|Szczegóły|Podczas uruchamiania w systemie Windows 10 moduł sprawdzania pisowni może nie działać dla formantów z włączoną funkcją tekstową WPF, ponieważ funkcje sprawdzania pisowni platformy są dostępne tylko dla języków znajdujących się na liście języków wejściowych. W systemie Windows 10 po dodaniu języka do listy dostępnych klawiatur system Windows automatycznie pobiera i instaluje odpowiedni pakiet funkcji na żądanie (FOD), który zapewnia funkcje sprawdzania pisowni. Dodając język do listy języków wejściowych, moduł sprawdzania pisowni będzie obsługiwany.|
|Sugestia|Należy pamiętać, że język lub tekst, który ma być sprawdzany pisownią, musi zostać dodany jako język wprowadzania do sprawdzania pisowni, aby działał w systemie Windows 10.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
