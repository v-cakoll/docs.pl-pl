---
ms.openlocfilehash: c4b293cf7db3762831be7f3a7a355748ff5758c5
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760262"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase — nie Propagacja wyjątków dla metody OnStart

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7 i w wersjach wcześniejszych wyjątków zgłaszanych na uruchamianie usługi nie są propagowane do obiektu wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.7.1, środowisko uruchomieniowe propaguje wyjątki <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> dla usług, których nie udało się uruchomić.|
|Sugestia|W menu start usługi Jeśli występuje wyjątek, ten wyjątek będą propagowane. Powinno to pomóc zdiagnozować przypadki, w którym można uruchomić usługi. <br/>Jeśli to zachowanie jest niepożądany, można zrezygnować z jej przez dodanie poniższego &lt;AppContextSwitchOverrides&gt; elementu &lt;środowiska uruchomieniowego&gt; sekcji w pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Jeśli aplikacja jest przeznaczony dla starszej wersji niż 4.7.1, ale chcesz mieć to zachowanie, Dodaj następujący kod &lt;AppContextSwitchOverrides&gt; elementu &lt;środowiska uruchomieniowego&gt; części aplikacji plik konfiguracji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

