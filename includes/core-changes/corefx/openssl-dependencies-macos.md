---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147454"
---
### <a name="openssl-versions-on-macos"></a>Wersje OpenSSL w systemie macOS

.NET Core 3.0 i nowsze wersje w systemie macOS preferują teraz wersje OpenSSL <xref:System.Security.Cryptography.AesCcm>1.1.x <xref:System.Security.Cryptography.RSAOpenSsl>od <xref:System.Security.Cryptography.SafeEvpPKeyHandle> wersji OpenSSL 1.0.x dla , <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, i typów.

Program .NET Core 2.1 działa teraz obsługuje wersje OpenSSL 1.1.x, ale nadal preferuje wersje OpenSSL 1.0.x.

#### <a name="change-description"></a>Zmień opis

Wcześniej w czasie wykonywania .NET Core używane OpenSSL 1.0.x wersje na macOS dla typów, które współdziałają z OpenSSL. Najnowsza wersja OpenSSL 1.0.x, OpenSSL 1.0.2, jest obecnie nieobsługiwana. Aby zachować typy, które używają OpenSSL w obsługiwanych wersjach OpenSSL, .NET Core 3.0 i nowsze uruchamianie teraz używać nowszych wersji OpenSSL w systemie macOS.

Dzięki tej zmianie zachowanie dla runii .NET Core w systemie macOS jest następujące:

- Programy .NET Core 3.0 i nowsze wersje używają openssl 1.1.x, jeśli są dostępne, i wracają do OpenSSL 1.0.x tylko wtedy, gdy nie ma dostępnej wersji 1.1.x.

  W przypadku obiektów wywołujących, które używają openssl typów współdziałania z <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w uwagach. Jeśli nie sprawdzisz <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> wartości, aplikacja może ulec awarii.

- Program .NET Core 2.1 używa openssl 1.0.x, jeśli jest dostępny, i powraca do OpenSSL 1.1.x, jeśli nie ma dostępnej wersji 1.0.x.

  Czas uruchomieniowy 2.1 preferuje wcześniejszą wersję OpenSSL, ponieważ <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> właściwość nie istnieje w .NET Core 2.1, więc nie można wiarygodnie określić wersji OpenSSL w czasie wykonywania.

#### <a name="version-introduced"></a>Wprowadzona wersja

- .NET Core 2.1.16
- .NET Core 3.0.3
- .NET Core 3.1.2

#### <a name="recommended-action"></a>Zalecana akcja

- Odinstaluj OpenSSL w wersji 1.0.2, jeśli nie jest już potrzebna.

- Zainstaluj OpenSSL 1.1.x, <xref:System.Security.Cryptography.AesCcm>jeśli <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>używasz <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , , lub typów.

- Jeśli używasz OpenSSL współdziałania typów z niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.

#### <a name="category"></a>Kategoria

CoreFx

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
