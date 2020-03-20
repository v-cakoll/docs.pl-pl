---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887813"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>ASP.NET ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1, ASP.NET poprawiła sposób pracy ASP.NET formantów sieci Web z technologią ułatwień dostępu w programie Visual Studio w celu lepszej obsługi klientów ASP.NET.  Należą do nich następujące zmiany:<ul><li>Zmiany implementujące brakujące wzorce ułatwień dostępu interfejsu użytkownika w formantych, takie jak okno dialogowe Dodawanie pola w kreatorze widoku szczegółów lub okno dialogowe Konfigurowanie widoku listy kreatora ListView.</li><li>Zmiany w celu poprawy wyświetlania w trybie wysokiego kontrastu, takie jak Edytor pól pagera danych.</li><li>Zmiany ułatwiające nawigację za pomocą klawiatury dla kontrolek, takie jak okno dialogowe Pola w kreatorze Edytowanie pól pagera formantu DataPager, okno dialogowe Konfigurowanie obiektu ObjectContext lub Okno dialogowe Konfigurowanie selction danych kreatora Konfigurowanie źródła danych.</li></ul>|
|Sugestia|**Jak zgłosić się lub zrezygnować z tych zmian**<br>Aby projektant programu Visual Studio korzystać z tych zmian, należy uruchomić w programie .NET Framework 4.7.1 lub nowszych. Aplikacja internetowa może korzystać z tych zmian w jeden z następujących sposobów:<ul><li>Zainstaluj program Visual Studio 2017 15.3 lub nowszy, który domyślnie obsługuje nowe funkcje ułatwień dostępu z następującym przełącznikiem AppContext.</li><li>Zrezygnuj ze starszych <code>Switch.UseLegacyAccessibilityFeatures</code> zachowań ułatwień <code>&lt;runtime&gt;</code> dostępu, dodając przełącznik AppContext do sekcji w <code>false</code>pliku devenv.exe.config i ustawiając go na , jak pokazano w poniższym przykładzie.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikacje przeznaczone dla programu .NET Framework 4.7.1 lub nowszego i chcą zachować starsze zachowanie ułatwień dostępu, <code>true</code>mogą zdecydować się na korzystanie ze starszych funkcji ułatwień dostępu, wyraźnie ustawiając przełącznik AppContext .|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
