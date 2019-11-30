---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567970"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Zwiększono minimalny rozmiar generowania klucza RSAOpenSsl

Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowego do 512-bitowego.

#### <a name="change-description"></a>Zmień opis

Począwszy od platformy .NET Core 3,0, minimalny rozmiar klucza prawnego raportowany przez właściwość `LegalKeySizes` w wystąpieniach RSA z <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>i <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> w systemie Linux wzrósł z 384 do 512.

W związku z tym w programie .NET Core 2,2 i wcześniejszych wersjach wywołanie metody, takie jak `RSA.Create(384)` powiodło się. W programie .NET Core 3,0 i nowszych wersjach metoda wywołania `RSA.Create(384)` zgłasza wyjątek wskazujący, że rozmiar jest zbyt mały.

Ta zmiana została wprowadzona, ponieważ OpenSSL, która wykonuje operacje kryptograficzne w systemie Linux, wygenerowała jej minimum między wersjami 1.0.2 i 1.1.0. Platforma .NET Core 3,0 preferuje OpenSSL 1.1. x do 1.0. x, a zgłoszono minimalną wersję raportowaną w celu odzwierciedlenia tego nowego ograniczenia zależności.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli wywołasz dowolne z tych interfejsów API, upewnij się, że rozmiar wszystkich wygenerowanych kluczy nie jest mniejszy niż minimalny dostawca.

> [!NOTE]
> 384-bitowy klucz RSA jest już uznawany za niezabezpieczony (AS 512-bitowy klucz RSA). Nowoczesne zalecenia, takie jak [Publikacje specjalne NIST 800-57 część 1 Poprawka 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), Sugeruj 2048-bitowy jako minimalny rozmiar nowo wygenerowanych kluczy.

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
