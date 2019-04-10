---
ms.openlocfilehash: 2ec5224b1ab16c05f6f942f6084f1ab105b71b0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233989"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>Upewnij się, że System.Uri używa zestawu znaków zarezerwowanych spójne

|   |   |
|---|---|
|Szczegóły|W <xref:System.Uri?displayProperty=fullName>, niektóre teraz stale lewej kodowania znaków zakodowane w formacie procent, które zostały czasami zdekodowane. Dzieje się we właściwości i metod, uzyskujących dostęp do składników ścieżki, query, fragment lub informacje o użytkowniku identyfikatora URI. Spowoduje to zmianę działania tylko wtedy, gdy obie następujące czynności są spełnione:<ul><li>Identyfikator URI zawiera formie zakodowanej w dowolnej z następujących znaków zarezerwowanych: <code>:</code>, <code>'</code>, <code>(</code>, <code>)</code>, <code>!</code> lub <code>*</code>.</li><li>Identyfikator URI zawiera Unicode lub zakodowane niezarezerwowanych znaków. Jeśli powyższe są spełnione oba, zakodowanych znaków zastrzeżonych lewej są zakodowane. W poprzednich wersjach programu .NET Framework są odczytany.</li></ul>|
|Sugestia|W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.2 nowe zachowanie dekodowania jest domyślnie włączona. Jeśli ta zmiana jest niepożądany, można ją wyłączyć, dodając następujące [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączyć się do <code>&lt;runtime&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>W przypadku aplikacji docelowych z wcześniejszych wersji programu .NET Framework, które działają w wersjach, począwszy od .NET Framework 4.7.2 nowe zachowanie dekodowania jest domyślnie wyłączona. Możesz je włączyć przez dodanie poniższego [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączyć się do <code>&lt;runtime&gt;</code> części pliku konfiguracyjnego aplikacji::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
