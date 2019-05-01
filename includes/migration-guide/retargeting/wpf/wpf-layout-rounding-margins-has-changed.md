---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091680"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF układ zaokrąglania marginesów został zmieniony

|   |   |
|---|---|
|Szczegóły|Sposobu marginesy są zaokrąglane i obramowań i tła wewnątrz nich został zmieniony. W wyniku tej zmiany:<ul><li>Szerokość lub wysokość elementów może zwiększać i zmniejszać co najwyżej jeden piksel.</li><li>Położenie obiektu można przenieść co najwyżej jeden piksel.</li><li>Wyśrodkowany elementy mogą być w pionie lub w poziomie, od środka co najwyżej jeden piksel.</li></ul>Domyślnie ten nowy układ jest włączona tylko dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.|
|Sugestia|Ponieważ ta modyfikacja zwykle wyeliminować wycinka elementu po prawej stronie lub u dołu okna kontrolki WPF w dużych wysokiej, aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na platformie .NET Framework 4.6 mogą wyrazić zgodę to nowe zachowanie, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Aplikacje, które docelowych programu .NET Framework 4.6, ale chcesz kontrolek WPF do renderowania przy użyciu poprzednich algorytmu układu można to zrobić, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
