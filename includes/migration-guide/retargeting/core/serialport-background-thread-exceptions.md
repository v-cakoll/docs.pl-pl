---
ms.openlocfilehash: 81b104d8e5a9ccc8e790c3b16e4837cfa0c0def5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804710"
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
