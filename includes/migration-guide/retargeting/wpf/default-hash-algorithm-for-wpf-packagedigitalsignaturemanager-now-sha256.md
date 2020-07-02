---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614917"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Domyślny algorytm wyznaczania wartości skrótu dla programu WPF PackageDigitalSignatureManager jest teraz SHA256

#### <a name="details"></a>Szczegóły

`System.IO.Packaging.PackageDigitalSignatureManager`Oferuje funkcje dla podpisów cyfrowych w odniesieniu do pakietów WPF.  W .NET Framework 4,7 i starszych wersjach algorytm domyślny ( <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType> ) używany do podpisywania części pakietu był SHA1.  Z powodu niedawnych problemów z zabezpieczeniami algorytmem SHA1 ta wartość domyślna została zmieniona na SHA256, począwszy od .NET Framework 4.7.1.  Ta zmiana ma wpływ na wszystkie podpisywanie pakietów, w tym dokumenty XPS.

#### <a name="suggestion"></a>Sugestia

Deweloperzy, którzy chcą korzystać z tej zmiany podczas określania wersji platformy poniżej, .NET Framework 4.7.1 lub deweloper, który wymaga poprzedniej funkcjonalności podczas określania wartości docelowej .NET Framework 4.7.1 lub nowszy, może odpowiednio ustawić następującą flagę AppContext.  Wartość true spowoduje użycie SHA1 jako algorytmu domyślnego; wartość false w SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
