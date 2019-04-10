---
ms.openlocfilehash: 141e906077748795e0360cec450a54a9fd170dc9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236423"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Domyślny algorytm skrótu dla WPF PackageDigitalSignatureManager jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> Oferuje funkcję dla podpisów cyfrowych w odniesieniu do pakietów programu WPF.  W .NET Framework 4.7 i wcześniejszymi wersjami, domyślny algorytm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) używany do podpisywania części pakietu zostało SHA1.  Ze względu na ostatnie obawy związane z bezpieczeństwem z SHA1, to ustawienie domyślne zostało zmienione na SHA256 począwszy od programu .NET Framework 4.7.1.  Ta zmiana ma wpływ na wszystkie podpisywanie pakietów, łącznie z dokumenty XPS.|
|Sugestia|Deweloper, który chce korzystać z tej zmiany podczas określania wartości docelowej framework w wersji starszej niż .NET Framework 4.7.1 lub deweloper, który wymaga poprzedniej funkcji, a przeznaczonych dla platformy .NET Framework 4.7.1 lub większą może ustawić następujące flagi AppContext odpowiednio.  Wartość true, wynikiem będzie SHA1 używany jako domyślny algorytm; FALSE powoduje SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|
