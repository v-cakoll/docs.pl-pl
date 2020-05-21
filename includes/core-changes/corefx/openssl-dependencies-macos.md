---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721304"
---
### <a name="openssl-versions-on-macos"></a>Wersje OpenSSL na macOS

Środowiska uruchomieniowe platformy .NET Core 3,0 i nowszego w systemie macOS teraz preferują wersje OpenSSL 1.0. x dla <xref:System.Security.Cryptography.AesCcm> typów,,, <xref:System.Security.Cryptography.AesGcm> , <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> i <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .

Środowisko uruchomieniowe programu .NET Core 2,1 obsługuje teraz wersje OpenSSL 1.1. x, ale nadal preferują wersje OpenSSL 1.0. x.

#### <a name="change-description"></a>Zmień opis

Wcześniej środowisko uruchomieniowe platformy .NET Core używało wersji OpenSSL 1.0. x w macOS dla typów, które współdziałają z OpenSSL. Najnowsza wersja OpenSSL 1.0. x, OpenSSL 1.0.2, już nie jest obsługiwana. Aby zachować typy korzystające z OpenSSL na obsługiwanych wersjach OpenSSL, środowisko uruchomieniowe programu .NET Core 3,0 i nowszych wersji już teraz używa nowszych wersjach OpenSSL na macOS.

W przypadku tej zmiany zachowanie środowiska uruchomieniowego .NET Core w systemie macOS jest następujące:

- Środowisko uruchomieniowe programu .NET Core 3,0 i nowszych wersji używa OpenSSL 1.1. x, jeśli jest dostępny, i wraca do OpenSSL 1.0. x tylko wtedy, gdy nie jest dostępna wersja 1.1. x.

  W przypadku wywołujących, które używają typów międzyoperacyjnych OpenSSL z niestandardowym P/Invoke, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach. Jeśli wartość nie zostanie sprawdzona, może wystąpić awaria aplikacji <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> .

- Środowisko uruchomieniowe programu .NET Core 2,1 korzysta z OpenSSL 1.0. x, jeśli jest dostępne, i wraca do OpenSSL 1.1. x, jeśli nie jest dostępna wersja 1.0. x.

  Środowisko uruchomieniowe 2,1 preferuje wcześniejszą wersję programu OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> , ponieważ właściwość nie istnieje w programie .NET Core 2,1, więc nie można w sposób niezawodny określić wersji OpenSSL w czasie wykonywania.

#### <a name="version-introduced"></a>Wprowadzona wersja

- 2.1.16 .NET Core
- 3.0.3 .NET Core
- .NET Core 3.1.2

#### <a name="recommended-action"></a>Zalecana akcja

- Odinstaluj program OpenSSL w wersji 1.0.2, jeśli nie jest już wymagany.

- Zainstaluj OpenSSL 1.1. x, jeśli używasz <xref:System.Security.Cryptography.AesCcm> , <xref:System.Security.Cryptography.AesGcm> ,,,, <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> lub <xref:System.Security.Cryptography.SafeEvpPKeyHandle> typów.

- Jeśli używasz typów międzyoperacyjnych OpenSSL z niestandardowym P/Invoke, postępuj zgodnie ze wskazówkami zawartymi w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
