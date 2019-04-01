---
ms.openlocfilehash: 448a6160bd64143000c00d21a9ddecdc61b53475
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760375"
---
### <a name="serialport-background-thread-exceptions"></a>Wyjątki wątku tła portu SerialPort

|   |   |
|---|---|
|Szczegóły|Utworzone za pomocą wątków w tle <xref:System.IO.Ports.SerialPort> strumieni nie jest już zakończyć proces, gdy są zgłaszane wyjątki systemu operacyjnego. <br/>W aplikacjach przeznaczonych dla platformy .NET Framework 4.7 i wcześniejszych wersjach, proces zostanie zakończony, gdy system operacyjny jest wyjątek w wątku w tle utworzonych za pomocą <xref:System.IO.Ports.SerialPort> strumienia. <br/>W aplikacjach, dla środowiska .NET Framework 4.7.1 lub nowszej wersji, wątków w tle poczekaj zdarzenia systemu operacyjnego związane z portu szeregowego active i może ulec awarii w niektórych przypadkach, takich jak nagłe usunięcia portu szeregowego.|
|Sugestia|W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 można zrezygnować z obsługi wyjątków, jeśli nie jest pożądane, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojej <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Dla aplikacji przeznaczonych dla wcześniejszych wersji programu .NET Framework jednak uruchomić w środowisku .NET Framework 4.7.1 lub później, można włączyć do obsługi, dodając następujące polecenie, aby wyjątków <code>&lt;runtime&gt;</code> części Twojej <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

