---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622089"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Zmiana wysokiego kontrastu ComboBox svcTraceViewer

#### <a name="details"></a>Szczegóły

W [narzędziu Podgląd śledzenia usług firmy Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kontrolki ComboBox nie były wyświetlane w prawidłowym kolorze w niektórych motywach o dużym kontraście. Problem został rozwiązany w .NET Framework 4.7.2. Jednak ze względu na wymagania zgodności z zestawem SDK .NET Framework, poprawka nie była domyślnie widoczna dla klientów. Program .NET 4,8 wyświetla tę zmianę, dodając następujące [przełączniki konfiguracji AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a>Sugestia

<ul><li>Jak zrezygnować z zmiany, jeśli nie chcesz mieć zmiany zachowania dużego kontrastu, możesz ją wyłączyć, usuwając następującą sekcję z pliku svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4,8|
|Typ|Środowisko uruchomieniowe|
