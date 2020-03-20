---
ms.openlocfilehash: 81b104d8e5a9ccc8e790c3b16e4837cfa0c0def5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859053"
---
### <a name="serialport-background-thread-exceptions"></a>Wyjątki wątku w tle SerialPort

|   |   |
|---|---|
|Szczegóły|Wątki w <xref:System.IO.Ports.SerialPort> tle utworzone za pomocą strumieni nie kończą już procesu po wyświetleniu wyjątków systemu operacyjnego. <br/>W aplikacjach, które są przeznaczone dla .NET Framework 4.7 i wcześniejszych wersji, proces jest <xref:System.IO.Ports.SerialPort> zakończony, gdy wyjątek systemu operacyjnego jest zgłaszany w wątku w tle utworzone za pomocą strumienia. <br/>W aplikacjach przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszej wersji wątki w tle czekają na zdarzenia systemu operacyjnego związane z aktywnym portem szeregowym i mogą ulec awarii w niektórych przypadkach, na przykład nagłe usunięcie portu szeregowego.|
|Sugestia|W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.7.1 można zrezygnować z obsługi wyjątków, jeśli nie jest to pożądane, dodając do <code>&lt;runtime&gt;</code> sekcji <code>app.config</code> pliku następujące elementy:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>W przypadku aplikacji przeznaczonych dla starszych wersji programu .NET Framework, ale uruchamianych w programie .NET Framework 4.7.1 lub nowszym, można zdecydować się na obsługę wyjątków, dodając następujące <code>&lt;runtime&gt;</code> elementy do sekcji <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|
