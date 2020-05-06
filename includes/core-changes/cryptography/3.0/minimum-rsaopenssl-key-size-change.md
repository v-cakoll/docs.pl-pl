---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275209"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Zwiększono minimalny rozmiar generowania klucza RSAOpenSsl

Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowego do 512-bitowego.

#### <a name="change-description"></a>Zmień opis

Począwszy od platformy .NET Core 3,0, minimalny rozmiar klucza prawnego raportowany przez `LegalKeySizes` właściwość w wystąpieniach RSA <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>z <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, i <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> w systemie Linux wzrósł od 384 do 512.

W związku z tym w programie .NET Core 2,2 i starszych wersjach metoda wywołuje takie jak `RSA.Create(384)` pomyślne. W programie .NET Core 3,0 i jego nowszych wersjach wywołanie `RSA.Create(384)` metody zgłasza wyjątek wskazujący, że rozmiar jest zbyt mały.

Ta zmiana została wprowadzona, ponieważ OpenSSL, która wykonuje operacje kryptograficzne w systemie Linux, wygenerowała jej minimum między wersjami 1.0.2 i 1.1.0. Platforma .NET Core 3,0 preferuje OpenSSL 1.1. x do 1.0. x, a zgłoszono minimalną wersję raportowaną w celu odzwierciedlenia tego nowego ograniczenia zależności.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wywołasz dowolne z tych interfejsów API, upewnij się, że rozmiar wszystkich wygenerowanych kluczy nie jest mniejszy niż minimalny dostawca.

> [!NOTE]
> 384-bitowy klucz RSA jest już uznawany za niezabezpieczony (AS 512-bitowy klucz RSA). Nowoczesne zalecenia, takie jak [Publikacje specjalne NIST 800-57 część 1 Poprawka 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), Sugeruj 2048-bitowy jako minimalny rozmiar nowo wygenerowanych kluczy.

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
