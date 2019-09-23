---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181969"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="b9432-101">EnvelopedCms domyślnie szyfrowanie AES-256</span><span class="sxs-lookup"><span data-stu-id="b9432-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="b9432-102">Domyślny algorytm szyfrowania symetrycznego używany przez `EnvelopedCms` program został zmieniony z TripleDES na AES-256.</span><span class="sxs-lookup"><span data-stu-id="b9432-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="details"></a><span data-ttu-id="b9432-103">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b9432-103">Details</span></span>

<span data-ttu-id="b9432-104">W programie .NET Core w wersji zapoznawczej 7 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> i starszych wersjach, gdy jest używany do szyfrowania danych bez określania algorytmu szyfrowania symetrycznego za pośrednictwem przeciążenia konstruktora, dane były szyfrowane przy użyciu algorytmu TripleDES/3DES/3DEA/DES3-Ede.</span><span class="sxs-lookup"><span data-stu-id="b9432-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="b9432-105">Począwszy od programu .NET Core 3,0 wersja zapoznawcza 8 (za pośrednictwem wersji 4.6.0 pliku [System. Security. Cryptography. PKCS](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), domyślny algorytm został zmieniony na AES-256 na potrzeby modernizacji algorytmu oraz poprawić zabezpieczenia opcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="b9432-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="b9432-106">Jeśli certyfikat odbiorcy wiadomości ma klucz publiczny (poza EC), operacja szyfrowania może zakończyć się niepowodzeniem z <xref:System.Security.Cryptography.CryptographicException> powodu ograniczeń na platformie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b9432-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="b9432-107">W poniższym przykładowym kodzie dane są szyfrowane przy użyciu TripleDES, jeśli uruchomiono w programie .NET Core 3,0 w wersji zapoznawczej 7 lub starszym.</span><span class="sxs-lookup"><span data-stu-id="b9432-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="b9432-108">W przypadku korzystania z programu .NET Core 3,0 w wersji zapoznawczej 8 lub nowszej jest on szyfrowany przy użyciu algorytmu AES-256.</span><span class="sxs-lookup"><span data-stu-id="b9432-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="b9432-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="b9432-109">Version introduced</span></span>

<span data-ttu-id="b9432-110">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="b9432-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9432-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b9432-111">Recommended action</span></span>

<span data-ttu-id="b9432-112">Jeśli zmiana ma negatywny wpływ na zmiany, można przywrócić szyfrowanie TripleDES przez jawne określenie identyfikatora algorytmu szyfrowania w <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> konstruktorze, który zawiera parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, taki jak:</span><span class="sxs-lookup"><span data-stu-id="b9432-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="b9432-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b9432-113">Category</span></span>

<span data-ttu-id="b9432-114">Cryptography</span><span class="sxs-lookup"><span data-stu-id="b9432-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9432-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b9432-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
