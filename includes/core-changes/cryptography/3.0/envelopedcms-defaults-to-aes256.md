---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275181"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>Domyślnie 256: 000 000 000 000 000 000 000 000 000 000

Domyślny algorytm szyfrowania symetrycznego używany przez `EnvelopedCms` został zmieniony z TripleDES na AES-256.

#### <a name="change-description"></a>Zmień opis

W wersji .NET Core Preview 7 i wcześniejszych wersjach, gdy <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> jest używany do szyfrowania danych bez określania algorytmu szyfrowania symetrycznego za pomocą przeciążenia konstruktora, dane zostały zaszyfrowane za pomocą algorytmu TripleDES/3DES/3DEA/DES3-EDE.

Począwszy od pakietu .NET Core 3.0 Preview 8 (w wersji 4.6.0 pakietu [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), domyślny algorytm został zmieniony na AES-256 w celu modernizacji algorytmu i poprawy bezpieczeństwa opcji domyślnych. Jeśli certyfikat adresata wiadomości ma klucz publiczny Diffie-Hellman (nie-WE), <xref:System.Security.Cryptography.CryptographicException> operacja szyfrowania może zakończyć się niepowodzeniem z powodu ograniczeń na podstawowej platformie.

W poniższym przykładowym kodzie dane są szyfrowane za pomocą TripleDES, jeśli jest uruchomiony w programie .NET Core 3.0 Preview 7 lub starszym. Jeśli jest uruchomiony w programie .NET Core 3.0 Preview 8 lub nowszym, jest szyfrowany za pomocą aes-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0 Podgląd 8

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli zmiana negatywnie wpłynęła na Ciebie, możesz przywrócić szyfrowanie TripleDES, wyraźnie określając <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> identyfikator algorytmu szyfrowania <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>w konstruktorze, który zawiera parametr typu, taki jak:

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

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
