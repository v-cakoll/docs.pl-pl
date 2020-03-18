---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567956"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>Domyślnie moduły szyfrowania EnvelopedCms

Domyślny algorytm szyfrowania symetrycznego używany `EnvelopedCms` przez został zmieniony z TripleDES na AES-256.

#### <a name="change-description"></a>Zmień opis

W .NET Core Preview 7 i <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> wcześniejszych wersjach, gdy jest używany do szyfrowania danych bez określania algorytmu szyfrowania symetrycznego za pomocą przeciążenia konstruktora, dane zostały zaszyfrowane za pomocą algorytmu TripleDES/3DES/3DEA/DES3-EDE.

Począwszy od .NET Core 3.0 Preview 8 (za pośrednictwem wersji 4.6.0 [pakietu System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), domyślny algorytm został zmieniony na AES-256 w celu modernizacji algorytmów i poprawy bezpieczeństwa opcji domyślnych. Jeśli certyfikat adresata wiadomości ma (non-EC) Diffie-Hellman klucz publiczny, operacja szyfrowania może zakończyć się niepowodzeniem z <xref:System.Security.Cryptography.CryptographicException> powodu ograniczeń w platformie źródłowej.

W poniższym przykładowym kodzie dane są szyfrowane za pomocą programu TripleDES, jeśli są uruchomione w wersji .NET Core 3.0 Preview 7 lub wcześniejszej. Jeśli jest uruchomiona na .NET Core 3.0 Preview 8 lub nowszy, jest szyfrowana za pomocą AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 8

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli zmiana ma negatywny wpływ, możesz przywrócić szyfrowanie TripleDES, jawnie określając identyfikator <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> algorytmu szyfrowania w konstruktorze zawierającym parametr typu, <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>na przykład:

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

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
