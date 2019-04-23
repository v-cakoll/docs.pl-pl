---
ms.openlocfilehash: 0b087fca59d60a086a9ea8b2bb19c09f646c3dfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804737"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Ulepszone ułatwienia dostępu dla niektórych narzędzi zestawu SDK platformy .NET

|   |   |
|---|---|
|Szczegóły|W .NET Framework SDK 4.7.1 zostały ulepszone narzędzia SvcConfigEditor.exe i SvcTraceViewer.exe napraw problemy zależeć od dostępności. Większość z nich zostały niewielkie problemy, takie jak nazwy, nie zostały zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie. Gdy wielu użytkowników w takich sytuacjach przydałaby należy pamiętać o tych niepoprawne wartości, klienci korzystający z technologiami pomocniczymi, takich jak czytniki zawartości ekranu znajduje się tych narzędzi zestawu SDK łatwiej dostępne. Bez obaw poprawki te zmiany niektórych poprzednich zachowań, takich jak kolejność fokus klawiatury. Aby uzyskać wszystko, czego Dostępność poprawki w tych narzędziach, można poniższy kod do pliku app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.1|
|Typ|Przekierowanie|
