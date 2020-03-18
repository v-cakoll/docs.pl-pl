---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567970"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Minimalny rozmiar generowania kluczy RSAOpenSsl wzrósł

Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowego do 512-bitowego.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0, minimalny `LegalKeySizes` rozmiar klucza prawnego <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>zgłoszony <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>przez <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> właściwość w wystąpieniach RSA z , i na Linuksie wzrosła z 384 do 512.

W rezultacie w .NET Core 2.2 i wcześniejszych `RSA.Create(384)` wersjach wywołanie metody, takie jak powiedzie się. W .NET Core 3.0 i nowszych wersjach wywołanie `RSA.Create(384)` metody zgłasza wyjątek wskazujący rozmiar jest zbyt mały.

Ta zmiana została winna, ponieważ OpenSSL, który wykonuje operacje kryptograficzne w systemie Linux, podniósł swoje minimum między wersjami 1.0.2 i 1.1.0. .NET Core 3.0 preferuje OpenSSL 1.1.x do 1.0.x, a minimalna zgłoszona wersja została podniesiona w celu odzwierciedlenia tego nowego wyższego ograniczenia zależności.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wywołasz którykolwiek z dotkniętych interfejsów API, upewnij się, że rozmiar wszystkich wygenerowanych kluczy jest nie mniejsza niż minimalne dostawcy.

> [!NOTE]
> 384-bitowy rsa jest już uważany za niepewny (podobnie jak 512-bitowy RSA). Nowoczesne zalecenia, takie jak [NIST Special Publication 800-57 Część 1 Wersja 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerują 2048-bitowy rozmiar jako minimalny rozmiar dla nowo wygenerowanych kluczy.

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
