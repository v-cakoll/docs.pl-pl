---
ms.openlocfilehash: 1148d040aa3b292d5c37eb50224413b6ddd202e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859044"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase nie propaguje wyjątków OnStart

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7 i wcześniejszych wersjach wyjątki zgłaszane podczas uruchamiania <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>usługi nie są propagowane do wywołującego .<br/>Począwszy od aplikacji, które są przeznaczone <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> dla programu .NET Framework 4.7.1, środowisko wykonawcze propaguje wyjątki dla usług, które nie można uruchomić.|
|Sugestia|Przy uruchomieniu usługi, jeśli istnieje wyjątek, ten wyjątek będzie propagowany. Powinno to pomóc w diagnozowaniu przypadków, w których usługi nie można uruchomić. <br/>Jeśli to zachowanie jest niepożądane, można zrezygnować z &lt;niego, dodając następujący AppContextSwitchOverrides&gt; element do sekcji środowiska &lt;wykonawczego&gt; pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Jeśli aplikacja jest przeznaczona dla starszej wersji niż 4.7.1, &lt;ale chcesz mieć to&gt; zachowanie, &lt;dodaj&gt; następujący AppContextSwitchOverrides element do sekcji środowiska wykonawczego pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|
