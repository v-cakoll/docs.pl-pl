---
ms.openlocfilehash: 0b087fca59d60a086a9ea8b2bb19c09f646c3dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858976"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Ulepszona dostępność niektórych narzędzi zestawu SDK platformy .NET

|   |   |
|---|---|
|Szczegóły|W .NET Framework SDK 4.7.1 narzędzia SvcConfigEditor.exe i SvcTraceViewer.exe zostały ulepszone przez naprawienie różnych problemów z dostępnością. Większość z nich były małe problemy, takie jak nazwa nie jest zdefiniowana lub niektórych wzorców automatyzacji interfejsu użytkownika nie są implementowane poprawnie. Podczas gdy wielu użytkowników nie będzie świadomy tych niepoprawnych wartości, klienci, którzy korzystają z technologii ułatwień dostępu, takich jak czytniki ekranu, znajdą te narzędzia zestawu SDK bardziej dostępne. Z pewnością te poprawki zmieniają niektóre poprzednie zachowania, takie jak kolejność ustawiania ostrości klawiatury. Aby uzyskać wszystkie poprawki ułatwień dostępu w tych narzędziach, można wykonać następujące pliki do pliku app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7.1|
|Typ|Przekierowanie|
