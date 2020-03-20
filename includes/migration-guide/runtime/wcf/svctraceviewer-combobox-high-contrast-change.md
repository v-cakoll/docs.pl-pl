---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802677"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox zmiana wysokiego kontrastu

|   |   |
|---|---|
|Szczegóły|W [narzędziu Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)formanty ComboBox nie były wyświetlane we właściwym kolorze w niektórych motywach o wysokim kontraście. Problem został rozwiązany w .NET Framework 4.7.2. Jednak ze względu na wymagania zgodności sdk .NET Framework zgodności wstecznej, poprawka nie była domyślnie widoczna dla klientów. .NET 4.8 powierzchni tej zmiany przez dodanie następujących [appcontext przełączniki konfiguracji](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Sugestia|<ul><li>Jak zrezygnować ze zmiany Jeśli nie chcesz, aby zmiana zachowania wysokiego kontrastu, można go wyłączyć, usuwając następującą sekcję z pliku svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
