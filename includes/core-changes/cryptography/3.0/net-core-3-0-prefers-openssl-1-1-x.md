---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275482"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 preferuje OpenSSL 1.1.x od OpenSSL 1.0.x

.NET Core dla systemu Linux, który działa w wielu dystrybucjach Linuksa, może obsługiwać zarówno OpenSSL 1.0.x, jak i OpenSSL 1.1.x.  .NET Core 2.1 i .NET Core 2.2 najpierw wyglądają na 1.0.x, a następnie wracają do 1.1.x; .NET Core 3.0 najpierw szuka 1.1.x. Ta zmiana została wyekspowała nowe standardy kryptograficzne.

Ta zmiana może mieć wpływ na biblioteki lub aplikacje, które do platformy interop z OpenSSL specyficzne międzyop typów w .NET Core.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i wcześniejszych wersjach środowisko wykonawcze preferuje ładowanie OpenSSL 1.0.x przez 1.1.x. Oznacza to, <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> że i typy dla interop z OpenSSL są używane z libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 przez preferencje.

Począwszy od .NET Core 3.0, środowisko wykonawcze preferuje ładowanie OpenSSL 1.1.x przez OpenSSL 1.0.x, więc <xref:System.IntPtr> i <xref:System.Runtime.InteropServices.SafeHandle> typy dla interop z OpenSSL są używane z libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.0 / libcrypto.so.1 według preferencji. W rezultacie biblioteki i aplikacje, które współdziałają bezpośrednio z OpenSSL, mogą mieć niezgodne wskaźniki z wartościami udostępnianymi przez .NET Core podczas uaktualniania z platformy .NET Core 2.1 lub .NET Core 2.2.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Biblioteki i aplikacje, które wykonują bezpośrednie operacje za pomocą OpenSSL, muszą być ostrożne, aby upewnić się, że używają tej samej wersji OpenSSL jako środowiska uruchomieniowego .NET Core.

Wszystkie biblioteki lub <xref:System.IntPtr> aplikacje, które używają lub <xref:System.Runtime.InteropServices.SafeHandle> wartości z .NET Core kryptograficznych typów bezpośrednio z <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> OpenSSL należy porównać wersję biblioteki, których używają z nową właściwość, aby upewnić się, że wskaźniki są zgodne.

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
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
