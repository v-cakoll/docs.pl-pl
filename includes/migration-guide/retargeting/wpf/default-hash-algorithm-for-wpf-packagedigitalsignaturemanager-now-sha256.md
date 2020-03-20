---
ms.openlocfilehash: 141e906077748795e0360cec450a54a9fd170dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858983"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Domyślny algorytm mieszania dla WPF PackageDigitalSignatureManager jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|Zapewnia <code>System.IO.Packaging.PackageDigitalSignatureManager</code> funkcje podpisów cyfrowych w odniesieniu do pakietów WPF.  W .NET Framework 4.7 i wcześniejszych wersjach domyślnym algorytmem (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) używanym do podpisywania części pakietu był SHA1.  Ze względu na ostatnie problemy z zabezpieczeniami z SHA1 ta wartość domyślna została zmieniona na SHA256, począwszy od programu .NET Framework 4.7.1.  Ta zmiana dotyczy wszystkich podpisywania pakietów, w tym dokumentów XPS.|
|Sugestia|Deweloper, który chce korzystać z tej zmiany podczas kierowania wersji struktury poniżej .NET Framework 4.7.1 lub dewelopera, który wymaga poprzedniej funkcji podczas kierowania .NET Framework 4.7.1 lub nowszej można odpowiednio ustawić następującą flagę AppContext.  Wartość true spowoduje SHA1 jest używany jako domyślny algorytm; fałszywych wyników w SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|
