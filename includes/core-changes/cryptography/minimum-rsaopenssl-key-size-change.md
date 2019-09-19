---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117200"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="6b337-101">Zwiększono minimalny rozmiar generowania klucza RSAOpenSsl</span><span class="sxs-lookup"><span data-stu-id="6b337-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="6b337-102">Minimalny rozmiar generowania nowych kluczy RSA w systemie Linux wzrósł z 384-bitowego do 512-bitowego.</span><span class="sxs-lookup"><span data-stu-id="6b337-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6b337-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="6b337-103">Change description</span></span>

<span data-ttu-id="6b337-104">Począwszy od platformy .NET Core 3,0, minimalny rozmiar klucza prawnego raportowany przez `LegalKeySizes` Właściwość wystąpień RSA z < System. Security. Cryptography. RSA. Create% 2a? displayProperty = nameWithType >, < System. Security. Cryptography. RSAOpenSsl.% 23ctor% 2A? displayPropertyd = nameWithType > i < System. Security. Cryptography. RSACryptoServicePlatform.% 23ctor% 2A? displayProperty = nameWithType > w systemie Linux zwiększył się z 384 do 512.</span><span class="sxs-lookup"><span data-stu-id="6b337-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <System.Security.Cryptography.RSACryptoServicePlatform.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="6b337-105">W związku z tym w programie .NET Core 2,2 i starszych wersjach metoda wywołuje takie jak `RSA.Create(384)` pomyślne.</span><span class="sxs-lookup"><span data-stu-id="6b337-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="6b337-106">W programie .NET Core 3,0 i jego nowszych wersjach wywołanie `RSA.Create(384)` metody zgłasza wyjątek wskazujący, że rozmiar jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="6b337-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="6b337-107">Wprowadzono te zmiany, ponieważ OpenSSL, które wykonują operacje kryptograficzne w systemie Linux, wywołały swój minimum między wersjami 1.0.2 i 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="6b337-107">This changes was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span>  <span data-ttu-id="6b337-108">Platforma .NET Core 3,0 preferuje OpenSSL 1.1. x do 1.0. x, a zgłoszono minimalną wersję raportowaną w celu odzwierciedlenia tego nowego ograniczenia zależności.</span><span class="sxs-lookup"><span data-stu-id="6b337-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b337-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6b337-109">Version introduced</span></span>

<span data-ttu-id="6b337-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6b337-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b337-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6b337-111">Recommended action</span></span>

<span data-ttu-id="6b337-112">Jeśli wywołasz dowolne z tych interfejsów API, upewnij się, że rozmiar wszystkich wygenerowanych kluczy nie jest mniejszy niż minimalny dostawca.</span><span class="sxs-lookup"><span data-stu-id="6b337-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="6b337-113">384-bitowy klucz RSA jest już uznawany za niezabezpieczony (AS 512-bitowy klucz RSA).</span><span class="sxs-lookup"><span data-stu-id="6b337-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="6b337-114">Nowoczesne zalecenia, takie jak [Publikacje specjalne NIST 800-57 część 1 Poprawka 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), Sugeruj 2048-bitowy jako minimalny rozmiar nowo wygenerowanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="6b337-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="6b337-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6b337-115">Category</span></span>

<span data-ttu-id="6b337-116">Cryptography</span><span class="sxs-lookup"><span data-stu-id="6b337-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b337-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6b337-117">Affected APIs</span></span>

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
