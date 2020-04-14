---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275209"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="f0be2-101">Minimalny rozmiar generowania kluczy RSAOpenSsl wzrósł</span><span class="sxs-lookup"><span data-stu-id="f0be2-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="f0be2-102">Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowych do 512-bitowych.</span><span class="sxs-lookup"><span data-stu-id="f0be2-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f0be2-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f0be2-103">Change description</span></span>

<span data-ttu-id="f0be2-104">Począwszy od .NET Core 3.0, minimalny `LegalKeySizes` rozmiar klucza prawnego <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>zgłoszony <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>przez <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> właściwość w wystąpieniach RSA z , a na Linuksie wzrósł z 384 do 512.</span><span class="sxs-lookup"><span data-stu-id="f0be2-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="f0be2-105">W rezultacie w .NET Core 2.2 i wcześniejszych wersjach wywołanie metody, takie jak `RSA.Create(384)` powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="f0be2-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="f0be2-106">W .NET Core 3.0 i nowszych wersjach wywołanie `RSA.Create(384)` metody zgłasza wyjątek wskazujący rozmiar jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="f0be2-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="f0be2-107">Ta zmiana została wniesiona, ponieważ OpenSSL, który wykonuje operacje kryptograficzne w systemie Linux, podniósł swoje minimum między wersjami 1.0.2 i 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="f0be2-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="f0be2-108">.NET Core 3.0 preferuje OpenSSL 1.1.x do 1.0.x, a minimalna zgłoszona wersja została podniesiona w celu odzwierciedlenia tego nowego wyższego ograniczenia zależności.</span><span class="sxs-lookup"><span data-stu-id="f0be2-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f0be2-109">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="f0be2-109">Version introduced</span></span>

<span data-ttu-id="f0be2-110">3.0</span><span class="sxs-lookup"><span data-stu-id="f0be2-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f0be2-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f0be2-111">Recommended action</span></span>

<span data-ttu-id="f0be2-112">Jeśli wywołasz którykolwiek z interfejsów API, których dotyczy problem, upewnij się, że rozmiar wszystkich wygenerowanych kluczy jest nie mniejszy niż minimum dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f0be2-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="f0be2-113">384-bitowy RSA jest już uważany za niebezpieczny (podobnie jak 512-bitowy RSA).</span><span class="sxs-lookup"><span data-stu-id="f0be2-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="f0be2-114">Nowoczesne zalecenia, takie jak [publikacja specjalna NIST 800-57 Część 1 Wersja 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)sugerują 2048-bit jako minimalny rozmiar dla nowo wygenerowanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="f0be2-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="f0be2-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f0be2-115">Category</span></span>

<span data-ttu-id="f0be2-116">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="f0be2-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f0be2-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f0be2-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
