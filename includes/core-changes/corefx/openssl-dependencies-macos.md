---
ms.openlocfilehash: 8790637c31d503455eb8ba722cca827c2a24b7c9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021455"
---
### <a name="openssl-versions-on-macos"></a>Wersje OpenSSL w systemie macOS

Środowiska wykonawcze .NET Core 3.0 i nowsze w systemie macOS preferują teraz wersje OpenSSL 1.1.x <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>niż <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl>wersje <xref:System.Security.Cryptography.SafeEvpPKeyHandle> OpenSSL 1.0.x dla <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm>, , , , i typów.

Środowisko uruchomieniowe .NET Core 2.1 obsługuje teraz wersje OpenSSL 1.1.x, ale nadal preferuje wersje OpenSSL 1.0.x.

#### <a name="change-description"></a>Zmień opis

Wcześniej środowisko uruchomieniowe .NET Core używało wersji OpenSSL 1.0.x w systemie macOS dla typów, które wchodzą w interakcję z openssl. Najnowsza wersja OpenSSL 1.0.x, OpenSSL 1.0.2, jest teraz niesprymaśni. Aby zachować typy, które używają OpenSSL w obsługiwanych wersjach OpenSSL, środowiska uruchomieniowe .NET Core 3.0 i nowsze używają teraz nowszych wersji OpenSSL w systemie macOS.

Dzięki tej zmianie zachowanie środowiska uruchomień .NET Core w systemie macOS jest następujące:

- Środowiska wykonawcze .NET Core 3.0 i nowszej wersji używają OpenSSL 1.1.x, jeśli jest dostępna, i wracają do OpenSSL 1.0.x tylko wtedy, gdy nie ma dostępnej wersji 1.1.x.

  Dla osób wywołujących, które używają openssl typów interop z niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach. Aplikacja może ulec awarii, jeśli <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> nie sprawdzisz wartości.

- Środowisko uruchomieniowe .NET Core 2.1 używa openssl 1.0.x, jeśli jest dostępny, i powraca do OpenSSL 1.1.x, jeśli nie ma dostępnej wersji 1.0.x.

  Środowisko uruchomieniowe 2.1 preferuje wcześniejszą wersję <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> OpenSSL, ponieważ właściwość nie istnieje w .NET Core 2.1, więc nie można niezawodnie określić wersji OpenSSL w czasie wykonywania.

#### <a name="version-introduced"></a>Wprowadzono wersję

- .NET Rdzeń 2.1.16
- .NET Rdzeń 3.0.3
- .NET Rdzeń 3.1.2

#### <a name="recommended-action"></a>Zalecana akcja

- Odinstaluj OpenSSL w wersji 1.0.2, jeśli nie jest już potrzebna.

- Zainstaluj OpenSSL 1.1.x, <xref:System.Security.Cryptography.AesCcm>jeśli <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>używasz <xref:System.Security.Cryptography.RSAOpenSsl>, <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, , lub typów.

- Jeśli używasz OpenSSL interop typów z niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
