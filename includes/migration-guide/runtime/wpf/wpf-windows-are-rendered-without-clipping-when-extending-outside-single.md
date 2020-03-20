---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858537"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Okna WPF są renderowane bez przycinania podczas rozciągania poza jednym monitorem

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6 działającym w systemie Windows 8 i wyższym całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z wieloma monitorami. Różni się to od poprzednich wersji programu .NET Framework, które przycinałyby okna WPF, które wykraczały poza jeden ekran.|
|Sugestia|To zachowanie (czy do klipu lub nie) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> można <code>&lt;appSettings&gt;</code> jawnie ustawić przy użyciu elementu <code>EnableMultiMonitorDisplayClipping</code> w pliku konfiguracyjnym aplikacji lub ustawiając właściwość podczas uruchamiania aplikacji.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
