---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859267"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng teraz poprawnie ładuje klawisze RSA niestandardowego rozmiaru klucza

|   |   |
|---|---|
|Szczegóły|W wersjach programu .NET Framework przed wersją 4.6.2 klienci o niestandardowych rozmiarach kluczy dla certyfikatów RSA nie mogą uzyskać dostępu do tych kluczy za pośrednictwem metod <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> rozszerzenia i. <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name>  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> z &quot;komunikatem Żądany rozmiar klucza nie jest obsługiwany.&quot; W .NET Framework 4.6.2 ten problem został rozwiązany. Podobnie i <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> teraz działają z niestandardowymi rozmiarami kluczy bez rzucania <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Sugestia|Jeśli istnieje jakaś logika obsługi wyjątków, która opiera się na poprzednim zachowaniu, <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> gdzie jest generowany, gdy używane są niestandardowe rozmiary kluczy, należy rozważyć usunięcie logiki.|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
