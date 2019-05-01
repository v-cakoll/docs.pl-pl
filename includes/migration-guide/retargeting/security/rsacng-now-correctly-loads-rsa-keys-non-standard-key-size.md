---
ms.openlocfilehash: 4892f75e4ae673d9d9cc7e9eeb6fb9b1a73f572e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758437"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng poprawnie ładowana klucze niestandardowe rozmiar klucza RSA

|   |   |
|---|---|
|Szczegóły|W .NET Framework w wersjach wcześniejszych niż 4.6.2, klientów przy użyciu niestandardowych rozmiarów klucza dla certyfikatów RSA są w stanie uzyskać dostęp do tych kluczy za pośrednictwem <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> i <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> metody rozszerzenia.  A <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> z komunikatem &quot;żądany rozmiar klucza nie jest obsługiwany&quot; zgłaszany. W programie .NET Framework 4.6.2 ten problem został rozwiązany. Podobnie <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> i <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> obecnie pracować przy użyciu niestandardowych rozmiarów klucza bez niepotrzebnego <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Sugestia|W przypadku obsługi logiki, która opiera się na poprzednim zachowaniu wszelkich wyjątków gdzie <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> jest zgłaszany, gdy używane są niestandardowe rozmiarów klucza, rozważ usunięcie logiki.|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|
