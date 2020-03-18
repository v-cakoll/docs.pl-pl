---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567970"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="bb4e6-101">Minimalny rozmiar generowania kluczy RSAOpenSsl wzrósł</span><span class="sxs-lookup"><span data-stu-id="bb4e6-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="bb4e6-102">Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowego do 512-bitowego.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bb4e6-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="bb4e6-103">Change description</span></span>

<span data-ttu-id="bb4e6-104">Począwszy od .NET Core 3.0, minimalny `LegalKeySizes` rozmiar klucza prawnego <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>zgłoszony <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>przez <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> właściwość w wystąpieniach RSA z , i na Linuksie wzrosła z 384 do 512.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="bb4e6-105">W rezultacie w .NET Core 2.2 i wcześniejszych `RSA.Create(384)` wersjach wywołanie metody, takie jak powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="bb4e6-106">W .NET Core 3.0 i nowszych wersjach wywołanie `RSA.Create(384)` metody zgłasza wyjątek wskazujący rozmiar jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="bb4e6-107">Ta zmiana została winna, ponieważ OpenSSL, który wykonuje operacje kryptograficzne w systemie Linux, podniósł swoje minimum między wersjami 1.0.2 i 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="bb4e6-108">.NET Core 3.0 preferuje OpenSSL 1.1.x do 1.0.x, a minimalna zgłoszona wersja została podniesiona w celu odzwierciedlenia tego nowego wyższego ograniczenia zależności.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb4e6-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="bb4e6-109">Version introduced</span></span>

<span data-ttu-id="bb4e6-110">3.0</span><span class="sxs-lookup"><span data-stu-id="bb4e6-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb4e6-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="bb4e6-111">Recommended action</span></span>

<span data-ttu-id="bb4e6-112">Jeśli wywołasz którykolwiek z dotkniętych interfejsów API, upewnij się, że rozmiar wszystkich wygenerowanych kluczy jest nie mniejsza niż minimalne dostawcy.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="bb4e6-113">384-bitowy rsa jest już uważany za niepewny (podobnie jak 512-bitowy RSA).</span><span class="sxs-lookup"><span data-stu-id="bb4e6-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="bb4e6-114">Nowoczesne zalecenia, takie jak [NIST Special Publication 800-57 Część 1 Wersja 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerują 2048-bitowy rozmiar jako minimalny rozmiar dla nowo wygenerowanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="bb4e6-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="bb4e6-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="bb4e6-115">Category</span></span>

<span data-ttu-id="bb4e6-116">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="bb4e6-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb4e6-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bb4e6-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
