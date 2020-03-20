---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804564"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>Zmieniono zaokrąglanie marginesów w układzie WPF

|   |   |
|---|---|
|Szczegóły|Zmienił się sposób, w jaki marginesy są zaokrąglane, a granice oraz tło wewnątrz nich uległy zmianie. W wyniku tej zmiany:<ul><li>Szerokość lub wysokość elementów może rosnąć lub zmniejszać się o co najwyżej jeden piksel.</li><li>Położenie obiektu może poruszać się o co najwyżej jeden piksel.</li><li>Wyśrodkowane elementy mogą być pionowo lub poziomo wyłączone do środka o co najwyżej jeden piksel.</li></ul>Domyślnie ten nowy układ jest włączony tylko dla aplikacji, które są przeznaczone dla programu .NET Framework 4.6.|
|Sugestia|Ponieważ ta modyfikacja ma tendencję do wyeliminowania przycinania prawego lub dolnego poziomu formantów WPF w wysokich dpis, aplikacje, które są przeznaczone dla wcześniejszych wersji <code>&lt;runtime&gt;</code> programu .NET Framework, ale są uruchomione w programie .NET Framework 4.6, mogą zdecydować się na to nowe zachowanie, dodając następujący wiersz do sekcji pliku app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Aplikacje, które są przeznaczone dla programu .NET Framework 4.6, ale chcesz, aby formanty WPF renderowane przy użyciu poprzedniego algorytmu układu można to zrobić, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
