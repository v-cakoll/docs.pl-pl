---
ms.openlocfilehash: d23c6cc9f8ee9c912ce5c9509d157692d1a18f90
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721622"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms domyślnie szyfrowanie AES-256

Domyślny algorytm szyfrowania symetrycznego używany przez program `EnvelopedCms` został zmieniony z TripleDES na AES-256.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core w wersji zapoznawczej 7 i starszych wersjach, gdy <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> jest używany do szyfrowania danych bez określania algorytmu szyfrowania symetrycznego za pośrednictwem przeciążenia konstruktora, dane były szyfrowane przy użyciu algorytmu TripleDES/3DES/3DEA/DES3-Ede.

Począwszy od programu .NET Core 3,0 wersja zapoznawcza 8 (za pośrednictwem wersji 4.6.0 pliku [System. Security. Cryptography. PKCS](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), domyślny algorytm został zmieniony na AES-256 na potrzeby modernizacji algorytmu oraz poprawić zabezpieczenia opcji domyślnych. Jeśli certyfikat odbiorcy wiadomości ma klucz publiczny (poza EC), operacja szyfrowania może zakończyć się niepowodzeniem z <xref:System.Security.Cryptography.CryptographicException> powodu ograniczeń na platformie podstawowej.

W poniższym przykładowym kodzie dane są szyfrowane przy użyciu TripleDES, jeśli uruchomiono w programie .NET Core 3,0 w wersji zapoznawczej 7 lub starszym. W przypadku korzystania z programu .NET Core 3,0 w wersji zapoznawczej 8 lub nowszej jest on szyfrowany przy użyciu algorytmu AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 8

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli zmiana ma negatywny wpływ na zmiany, można przywrócić szyfrowanie TripleDES przez jawne określenie identyfikatora algorytmu szyfrowania w <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> konstruktorze, który zawiera parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> , taki jak:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
