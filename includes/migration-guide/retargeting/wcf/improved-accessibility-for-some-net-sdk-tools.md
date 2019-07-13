---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858976"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Ulepszone ułatwienia dostępu dla niektórych narzędzi zestawu SDK platformy .NET

|   |   |
|---|---|
|Szczegóły|W .NET Framework SDK 4.7.1 zostały ulepszone narzędzia SvcConfigEditor.exe i SvcTraceViewer.exe napraw problemy zależeć od dostępności. Większość z nich zostały niewielkie problemy, takie jak nazwy, nie zostały zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie. Gdy wielu użytkowników w takich sytuacjach przydałaby należy pamiętać o tych niepoprawne wartości, klienci korzystający z technologiami pomocniczymi, takich jak czytniki zawartości ekranu znajduje się tych narzędzi zestawu SDK łatwiej dostępne. Bez obaw poprawki te zmiany niektórych poprzednich zachowań, takich jak kolejność fokus klawiatury. Aby uzyskać wszystko, czego Dostępność poprawki w tych narzędziach, można poniższy kod do pliku app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.7.1|
|Typ|Przekierowanie|

