---
ms.openlocfilehash: 347b6ccb3e986d820514159179c824c28907fc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640084"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Ulepszenia ułatwień dostępu programu ASP.NET w programie .NET Framework 4.7.1

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1 ASP.NET uległa poprawie, jak działają kontrolki sieci Web platformy ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio klientom lepsze ASP.NET pomocy technicznej.  Obejmują one następujące zmiany:<ul><li>Zmiany do zaimplementowania Brak wzorce dostępności interfejsu użytkownika w kontrolkach, np. okno dialogowe Dodawanie pola w Kreatorze widoku szczegółów lub okno dialogowe Konfigurowanie ListView kreatora ListView.</li><li>Zmiany w celu zwiększenia wyświetlaną w trybie dużego kontrastu, takich jak edytor pola danych Pager.</li><li>Zmiany w celu polepszenia nawigacji klawiatury środowisk dla formantów, takich jak okna dialogowego pola w Kreatorze edytowania pola pagera kontrolka DataPager, okno dialogowe Konfigurowanie obiektu ObjectContext lub okno dialogowe Konfigurowanie wyboru danych kreatora Konfigurowanie źródła danych.</li></ul>|
|Sugestia|<strong>Sposób korzystania z opcji na lub poza te zmiany</strong>aby projektanta programu Visual Studio korzystać z tych zmian, należy uruchomić w środowisku .NET Framework 4.7.1 lub nowszej. Aplikacja sieci web mogą korzystać z tych zmian w jednej z następujących sposobów:<ul><li>Zainstaluj program Visual Studio 2017 15.3 lub później, który obsługuje nowe funkcje ułatwień dostępu za pomocą następującego przełącznika AppContext domyślnie.</li><li>Zrezygnować z zachowania dostępności starszej wersji, dodając <code>Switch.UseLegacyAccessibilityFeatures</code> przełącznik AppContext <code>&lt;runtime&gt;</code> sekcji w pliku devenv.exe.config i ustawieniem dla niego <code>false</code>, jak pokazano w poniższym przykładzie.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszej i chcesz zachować starsze zachowanie dostępności zgodzić się na korzystanie z funkcji ułatwień dostępu w starszej wersji przez jawne ustawienie tego parametru AppContext <code>true</code>.|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Przekierowanie|
