---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887813"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Udoskonalenia ułatwień dostępu ASP.NET w programie .NET Framework 4.7.1

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.7.1, ASP.NET ulepszono sposób, w jaki formanty sieci Web ASP.NET współpracują z technologią ułatwień dostępu w programie Visual Studio, aby lepiej obsługiwać klientów ASP.NET.  Należą do nich następujące zmiany:<ul><li>Zmiany w celu zaimplementowania brakujących wzorców dostępności interfejsu użytkownika w kontrolkach, takich jak okno dialogowe Dodawanie pola w Kreatorze widoku szczegółów lub okno dialogowe Konfiguruj widok ListView kreatora ListView.</li><li>Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast, takie jak edytor pól modułu stronicowania danych.</li><li>Zmiany w celu ulepszenia środowiska nawigacji klawiaturowej dla kontrolek, takich jak okno dialogowe pola w Kreatorze Edytuj pola modułu stronicowania kontrolki formantu DataPager, okno dialogowe Konfigurowanie obiektu ObjectContext lub okno dialogowe Konfigurowanie danych Selction Kreatora konfiguracji źródła danych.</li></ul>|
|Sugestia|**Jak wybrać lub wycofać te zmiany**<br>Aby projektant programu Visual Studio mógł korzystać z tych zmian, musi on działać na .NET Framework 4.7.1 lub nowszym. Aplikacja sieci Web może korzystać z tych zmian w jeden z następujących sposobów:<ul><li>Zainstaluj program Visual Studio 2017 15,3 lub nowszy, który obsługuje nowe funkcje ułatwień dostępu domyślnie z następującym przełącznikiem AppContext.</li><li>Zrezygnuj ze starszych zachowań ułatwień dostępu, dodając przełącznik <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext do sekcji <code>&lt;runtime&gt;</code> w pliku devenv. exe. config i ustawiając go na <code>false</code>, jak pokazano w poniższym przykładzie.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikacje ukierunkowane na .NET Framework 4.7.1 lub nowsze i chcą zachować starsze zachowanie ułatwień dostępu mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na <code>true</code>.|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
