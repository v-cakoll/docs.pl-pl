---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614651"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng teraz prawidłowo ładuje klucze RSA o niestandardowym rozmiarze klucza

#### <a name="details"></a>Szczegóły

W wersjach .NET Framework wcześniejszych niż 4.6.2 klienci z niestandardowymi rozmiarami kluczy dla certyfikatów RSA nie mogą uzyskać dostępu do tych kluczy za <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> pomocą <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> metod rozszerzenia i.  <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>Komunikat o błędzie &quot; , którego żądany rozmiar klucza nie jest obsługiwany &quot; . W .NET Framework 4.6.2 ten problem został rozwiązany. Podobnie <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> i <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> teraz pracujesz z niestandardowymi rozmiarami kluczy bez wyrzucania <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> .

#### <a name="suggestion"></a>Sugestia

Jeśli występuje jakakolwiek logika obsługi wyjątków, która opiera się na poprzednim zachowaniu, gdy <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> jest zgłaszany, gdy używane są rozmiary kluczy niestandardowych, należy rozważyć usunięcie logiki.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
