---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567982"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 preferuje OpenSSL 1.1.x do OpenSSL 1.0.x

.NET Core for Linux, który działa w wielu dystrybucjach Linuksa, może obsługiwać zarówno OpenSSL 1.0.x, jak i OpenSSL 1.1.x.  .NET Core 2.1 i .NET Core 2.2 najpierw szukają 1.0.x, a następnie wracają do 1.1.x; .NET Core 3.0 najpierw szuka 1.1.x. Ta zmiana została wmazana w celu dodania obsługi nowych standardów kryptograficznych.

Ta zmiana może mieć wpływ na biblioteki lub aplikacje, które współdziałają z typami współzależności specyficznymi dla OpenSSL w .NET Core.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i wcześniejszych wersjach program runtime preferuje ładowanie OpenSSL 1.0.x ponad 1.1.x. Oznacza to, <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> że i typy interop z OpenSSL są używane z libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 według preferencji.

Począwszy od .NET Core 3.0, czas wykonywania preferuje ładowanie OpenSSL 1.1.x nad <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> OpenSSL 1.0.x, więc i typy interop z OpenSSL są używane z libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.11 / libcrypto.so.1 / libcrypto.so.1 / libcrypto.so.1 przez preferencje. W rezultacie biblioteki i aplikacje, które współdziałają bezpośrednio z OpenSSL bezpośrednio może mieć niezgodne wskaźniki z .NET Core-exposed wartości podczas uaktualniania z .NET Core 2.1 lub .NET Core 2.2.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Biblioteki i aplikacje, które wykonują bezpośrednie operacje z OpenSSL należy uważać, aby upewnić się, że używają tej samej wersji OpenSSL jako .NET Core runtime.

Wszystkie biblioteki lub aplikacje, które używają <xref:System.IntPtr> lub <xref:System.Runtime.InteropServices.SafeHandle> wartości z .NET Core typów kryptograficznych bezpośrednio z OpenSSL należy porównać wersję biblioteki, których używają z nową <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> właściwością, aby upewnić się, że wskaźniki są zgodne.

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
