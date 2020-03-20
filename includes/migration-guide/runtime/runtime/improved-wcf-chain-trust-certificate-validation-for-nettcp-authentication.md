---
ms.openlocfilehash: e69ed64390504af872fa6785aa0b7d6c4db84ef0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "69671037"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Ulepszona sprawdzanie poprawności certyfikatu zaufania łańcucha WCF dla uwierzytelniania certyfikatów Net.Tcp

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.2 poprawia sprawdzanie poprawności certyfikatu zaufania łańcucha podczas korzystania z uwierzytelniania certyfikatów z zabezpieczeniami transportu z WCF. Dzięki temu udoskonaleniu certyfikaty klienta używane do uwierzytelniania na serwerze muszą być skonfigurowane do uwierzytelniania klienta.  Podobnie certyfikaty serwera przeznaczone do uwierzytelniania serwera muszą być skonfigurowane do uwierzytelniania serwera. Po tej zmianie certyfikat główny jest wyłączony, sprawdzanie poprawności łańcucha certyfikatów kończy się niepowodzeniem. Ta sama zmiana została również wniesiena do platformy .NET Framework 3.5 i nowszych wersji za pośrednictwem zbiorczego okna zabezpieczeń. Więcej informacji można znaleźć [tutaj](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Ta zmiana jest domyślnie włączona i może być wyłączona przez ustawienie konfiguracji.|
|Sugestia|<ul><li>Sprawdź, czy certyfikat serwera i klienta ma wymagany identyfikator EKU OID. Jeśli nie, zaktualizuj certyfikat.</li><li>Sprawdź poprawność, czy certyfikat główny jest nieprawidłowy. Jeśli tak, zaktualizuj certyfikat główny.</li><li>Jak zrezygnować ze zmiany: Jeśli nie możesz zaktualizować certyfikatu, możesz tymczasowo obejść zmianę z następującym ustawieniem konfiguracji, Jednak rezygnacja ze zmiany spowoduje, że system będzie narażony na problem z zabezpieczeniami.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
