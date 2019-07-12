---
ms.openlocfilehash: 5a45d616001be5a2a2bdf2c654c10526125d7d86
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802677"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Zmiana o wysokim kontraście ComboBox svcTraceViewer

|   |   |
|---|---|
|Szczegóły|W [narzędzia przeglądarki danych śledzenia usługi Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), kontrolki ComboBox nie były wyświetlane w prawidłowy kolor w niektórych motywy o wysokim kontraście. Problem został rozwiązany w programie .NET Framework 4.7.2. Jednak ze względu na wymagania zgodności z poprzednimi wersjami .NET Framework SDK poprawki nie jest widoczne dla klientów, domyślnie. .NET 4.8 wydobywa informacje dotyczące tej zmiany przez dodanie poniższego [AppContext konfiguracji przełączników](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) pliku svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Sugestia|<ul><li>W jaki sposób można wycofać się zmiany, jeśli nie chcesz mieć duży kontrast zmienić zachowanie, można ją wyłączyć, usuwając w poniższej sekcji z pliku svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|

