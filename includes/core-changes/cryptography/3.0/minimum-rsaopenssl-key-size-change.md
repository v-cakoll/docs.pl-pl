---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275209"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Minimalny rozmiar generowania kluczy RSAOpenSsl wzrósł

Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowych do 512-bitowych.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0, minimalny `LegalKeySizes` rozmiar klucza prawnego <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>zgłoszony <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>przez <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> właściwość w wystąpieniach RSA z , a na Linuksie wzrósł z 384 do 512.

W rezultacie w .NET Core 2.2 i wcześniejszych wersjach wywołanie metody, takie jak `RSA.Create(384)` powiedzie się. W .NET Core 3.0 i nowszych wersjach wywołanie `RSA.Create(384)` metody zgłasza wyjątek wskazujący rozmiar jest zbyt mały.

Ta zmiana została wniesiona, ponieważ OpenSSL, który wykonuje operacje kryptograficzne w systemie Linux, podniósł swoje minimum między wersjami 1.0.2 i 1.1.0. .NET Core 3.0 preferuje OpenSSL 1.1.x do 1.0.x, a minimalna zgłoszona wersja została podniesiona w celu odzwierciedlenia tego nowego wyższego ograniczenia zależności.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wywołasz którykolwiek z interfejsów API, których dotyczy problem, upewnij się, że rozmiar wszystkich wygenerowanych kluczy jest nie mniejszy niż minimum dostawcy.

> [!NOTE]
> 384-bitowy RSA jest już uważany za niebezpieczny (podobnie jak 512-bitowy RSA). Nowoczesne zalecenia, takie jak [publikacja specjalna NIST 800-57 Część 1 Wersja 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerują 2048-bit jako minimalny rozmiar dla nowo wygenerowanych kluczy.

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
