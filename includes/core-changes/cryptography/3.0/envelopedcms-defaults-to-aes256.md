---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275181"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="20168-101">Domyślnie 256: 000 000 000 000 000 000 000 000 000 000</span><span class="sxs-lookup"><span data-stu-id="20168-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="20168-102">Domyślny algorytm szyfrowania symetrycznego używany przez `EnvelopedCms` został zmieniony z TripleDES na AES-256.</span><span class="sxs-lookup"><span data-stu-id="20168-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="20168-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="20168-103">Change description</span></span>

<span data-ttu-id="20168-104">W wersji .NET Core Preview 7 i wcześniejszych wersjach, gdy <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> jest używany do szyfrowania danych bez określania algorytmu szyfrowania symetrycznego za pomocą przeciążenia konstruktora, dane zostały zaszyfrowane za pomocą algorytmu TripleDES/3DES/3DEA/DES3-EDE.</span><span class="sxs-lookup"><span data-stu-id="20168-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="20168-105">Począwszy od pakietu .NET Core 3.0 Preview 8 (w wersji 4.6.0 pakietu [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), domyślny algorytm został zmieniony na AES-256 w celu modernizacji algorytmu i poprawy bezpieczeństwa opcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="20168-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="20168-106">Jeśli certyfikat adresata wiadomości ma klucz publiczny Diffie-Hellman (nie-WE), <xref:System.Security.Cryptography.CryptographicException> operacja szyfrowania może zakończyć się niepowodzeniem z powodu ograniczeń na podstawowej platformie.</span><span class="sxs-lookup"><span data-stu-id="20168-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="20168-107">W poniższym przykładowym kodzie dane są szyfrowane za pomocą TripleDES, jeśli jest uruchomiony w programie .NET Core 3.0 Preview 7 lub starszym.</span><span class="sxs-lookup"><span data-stu-id="20168-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="20168-108">Jeśli jest uruchomiony w programie .NET Core 3.0 Preview 8 lub nowszym, jest szyfrowany za pomocą aes-256.</span><span class="sxs-lookup"><span data-stu-id="20168-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="20168-109">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="20168-109">Version introduced</span></span>

<span data-ttu-id="20168-110">3.0 Podgląd 8</span><span class="sxs-lookup"><span data-stu-id="20168-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="20168-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="20168-111">Recommended action</span></span>

<span data-ttu-id="20168-112">Jeśli zmiana negatywnie wpłynęła na Ciebie, możesz przywrócić szyfrowanie TripleDES, wyraźnie określając <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> identyfikator algorytmu szyfrowania <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>w konstruktorze, który zawiera parametr typu, taki jak:</span><span class="sxs-lookup"><span data-stu-id="20168-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="20168-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="20168-113">Category</span></span>

<span data-ttu-id="20168-114">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="20168-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="20168-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="20168-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
