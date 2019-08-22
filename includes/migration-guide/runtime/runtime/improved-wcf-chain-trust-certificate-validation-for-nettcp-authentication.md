---
ms.openlocfilehash: e69ed64390504af872fa6785aa0b7d6c4db84ef0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69671037"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Ulepszono weryfikację certyfikatu zaufania łańcucha WCF dla uwierzytelniania certyfikatu net. TCP

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.2 ulepsza weryfikację certyfikatu zaufania łańcucha podczas korzystania z uwierzytelniania przy użyciu certyfikatu z zabezpieczeniami transportu za pomocą usługi WCF. W wyniku tego ulepszenia certyfikaty klienta, które są używane do uwierzytelniania na serwerze programu, muszą być skonfigurowane do uwierzytelniania klientów.  Podobne certyfikaty serwera, które są używane do uwierzytelniania serwera, muszą być skonfigurowane do uwierzytelniania serwera. W przypadku tej zmiany, jeśli certyfikat główny jest wyłączony, walidacja łańcucha certyfikatów kończy się niepowodzeniem. Ta sama zmiana została również wprowadzona w .NET Framework 3,5 i nowszych wersjach za pośrednictwem zabezpieczeń systemu Windows. Więcej informacji można znaleźć [tutaj](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Ta zmiana jest domyślnie włączona i można ją wyłączyć przy użyciu ustawienia konfiguracji.|
|Sugestia|<ul><li>Sprawdź, czy certyfikat serwera i klienta ma wymagany identyfikator OID EKU. W przeciwnym razie zaktualizuj certyfikat.</li><li>Sprawdź, czy certyfikat główny jest nieprawidłowy. W takim przypadku należy zaktualizować certyfikat główny.</li><li>Jak zrezygnować z zmiany: Jeśli aktualizacja certyfikatu nie jest możliwa, można obejść chwilową zmianę w sposób tymczasowy przy użyciu poniższego ustawienia konfiguracji, jednak rezygnacja z zmiany spowoduje, że system będzie narażony na problem z zabezpieczeniami.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
