---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147454"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="d8315-101">Wersje OpenSSL w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="d8315-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="d8315-102">.NET Core 3.0 i nowsze wersje w systemie macOS preferują teraz wersje OpenSSL <xref:System.Security.Cryptography.AesCcm>1.1.x <xref:System.Security.Cryptography.RSAOpenSsl>od <xref:System.Security.Cryptography.SafeEvpPKeyHandle> wersji OpenSSL 1.0.x dla , <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, i typów.</span><span class="sxs-lookup"><span data-stu-id="d8315-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="d8315-103">Program .NET Core 2.1 działa teraz obsługuje wersje OpenSSL 1.1.x, ale nadal preferuje wersje OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="d8315-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d8315-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d8315-104">Change description</span></span>

<span data-ttu-id="d8315-105">Wcześniej w czasie wykonywania .NET Core używane OpenSSL 1.0.x wersje na macOS dla typów, które współdziałają z OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="d8315-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="d8315-106">Najnowsza wersja OpenSSL 1.0.x, OpenSSL 1.0.2, jest obecnie nieobsługiwana.</span><span class="sxs-lookup"><span data-stu-id="d8315-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="d8315-107">Aby zachować typy, które używają OpenSSL w obsługiwanych wersjach OpenSSL, .NET Core 3.0 i nowsze uruchamianie teraz używać nowszych wersji OpenSSL w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="d8315-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="d8315-108">Dzięki tej zmianie zachowanie dla runii .NET Core w systemie macOS jest następujące:</span><span class="sxs-lookup"><span data-stu-id="d8315-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="d8315-109">Programy .NET Core 3.0 i nowsze wersje używają openssl 1.1.x, jeśli są dostępne, i wracają do OpenSSL 1.0.x tylko wtedy, gdy nie ma dostępnej wersji 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="d8315-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="d8315-110">W przypadku obiektów wywołujących, które używają openssl typów współdziałania z <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w uwagach.</span><span class="sxs-lookup"><span data-stu-id="d8315-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="d8315-111">Jeśli nie sprawdzisz <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> wartości, aplikacja może ulec awarii.</span><span class="sxs-lookup"><span data-stu-id="d8315-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="d8315-112">Program .NET Core 2.1 używa openssl 1.0.x, jeśli jest dostępny, i powraca do OpenSSL 1.1.x, jeśli nie ma dostępnej wersji 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="d8315-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="d8315-113">Czas uruchomieniowy 2.1 preferuje wcześniejszą wersję OpenSSL, ponieważ <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> właściwość nie istnieje w .NET Core 2.1, więc nie można wiarygodnie określić wersji OpenSSL w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d8315-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d8315-114">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d8315-114">Version introduced</span></span>

- <span data-ttu-id="d8315-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="d8315-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="d8315-116">.NET Core 3.0.3</span><span class="sxs-lookup"><span data-stu-id="d8315-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="d8315-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="d8315-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d8315-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d8315-118">Recommended action</span></span>

- <span data-ttu-id="d8315-119">Odinstaluj OpenSSL w wersji 1.0.2, jeśli nie jest już potrzebna.</span><span class="sxs-lookup"><span data-stu-id="d8315-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="d8315-120">Zainstaluj OpenSSL 1.1.x, <xref:System.Security.Cryptography.AesCcm>jeśli <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>używasz <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , , lub typów.</span><span class="sxs-lookup"><span data-stu-id="d8315-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="d8315-121">Jeśli używasz OpenSSL współdziałania typów z niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.</span><span class="sxs-lookup"><span data-stu-id="d8315-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="d8315-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d8315-122">Category</span></span>

<span data-ttu-id="d8315-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="d8315-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d8315-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d8315-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
