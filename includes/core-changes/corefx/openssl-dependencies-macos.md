---
ms.openlocfilehash: 8790637c31d503455eb8ba722cca827c2a24b7c9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021455"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="244ab-101">Wersje OpenSSL w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="244ab-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="244ab-102">Środowiska wykonawcze .NET Core 3.0 i nowsze w systemie macOS preferują teraz wersje OpenSSL 1.1.x <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>niż <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl>wersje <xref:System.Security.Cryptography.SafeEvpPKeyHandle> OpenSSL 1.0.x dla <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm>, , , , i typów.</span><span class="sxs-lookup"><span data-stu-id="244ab-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="244ab-103">Środowisko uruchomieniowe .NET Core 2.1 obsługuje teraz wersje OpenSSL 1.1.x, ale nadal preferuje wersje OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="244ab-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="244ab-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="244ab-104">Change description</span></span>

<span data-ttu-id="244ab-105">Wcześniej środowisko uruchomieniowe .NET Core używało wersji OpenSSL 1.0.x w systemie macOS dla typów, które wchodzą w interakcję z openssl.</span><span class="sxs-lookup"><span data-stu-id="244ab-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="244ab-106">Najnowsza wersja OpenSSL 1.0.x, OpenSSL 1.0.2, jest teraz niesprymaśni.</span><span class="sxs-lookup"><span data-stu-id="244ab-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="244ab-107">Aby zachować typy, które używają OpenSSL w obsługiwanych wersjach OpenSSL, środowiska uruchomieniowe .NET Core 3.0 i nowsze używają teraz nowszych wersji OpenSSL w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="244ab-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="244ab-108">Dzięki tej zmianie zachowanie środowiska uruchomień .NET Core w systemie macOS jest następujące:</span><span class="sxs-lookup"><span data-stu-id="244ab-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="244ab-109">Środowiska wykonawcze .NET Core 3.0 i nowszej wersji używają OpenSSL 1.1.x, jeśli jest dostępna, i wracają do OpenSSL 1.0.x tylko wtedy, gdy nie ma dostępnej wersji 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="244ab-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="244ab-110">Dla osób wywołujących, które używają openssl typów interop z niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.</span><span class="sxs-lookup"><span data-stu-id="244ab-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="244ab-111">Aplikacja może ulec awarii, jeśli <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> nie sprawdzisz wartości.</span><span class="sxs-lookup"><span data-stu-id="244ab-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="244ab-112">Środowisko uruchomieniowe .NET Core 2.1 używa openssl 1.0.x, jeśli jest dostępny, i powraca do OpenSSL 1.1.x, jeśli nie ma dostępnej wersji 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="244ab-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="244ab-113">Środowisko uruchomieniowe 2.1 preferuje wcześniejszą wersję <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> OpenSSL, ponieważ właściwość nie istnieje w .NET Core 2.1, więc nie można niezawodnie określić wersji OpenSSL w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="244ab-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="244ab-114">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="244ab-114">Version introduced</span></span>

- <span data-ttu-id="244ab-115">.NET Rdzeń 2.1.16</span><span class="sxs-lookup"><span data-stu-id="244ab-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="244ab-116">.NET Rdzeń 3.0.3</span><span class="sxs-lookup"><span data-stu-id="244ab-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="244ab-117">.NET Rdzeń 3.1.2</span><span class="sxs-lookup"><span data-stu-id="244ab-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="244ab-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="244ab-118">Recommended action</span></span>

- <span data-ttu-id="244ab-119">Odinstaluj OpenSSL w wersji 1.0.2, jeśli nie jest już potrzebna.</span><span class="sxs-lookup"><span data-stu-id="244ab-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="244ab-120">Zainstaluj OpenSSL 1.1.x, <xref:System.Security.Cryptography.AesCcm>jeśli <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>używasz <xref:System.Security.Cryptography.RSAOpenSsl>, <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, , lub typów.</span><span class="sxs-lookup"><span data-stu-id="244ab-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="244ab-121">Jeśli używasz OpenSSL interop typów z niestandardowych P/Invokes, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.</span><span class="sxs-lookup"><span data-stu-id="244ab-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="244ab-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="244ab-122">Category</span></span>

<span data-ttu-id="244ab-123">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="244ab-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="244ab-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="244ab-124">Affected APIs</span></span>

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
