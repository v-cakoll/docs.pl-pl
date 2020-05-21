---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721304"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="6d6e6-101">Wersje OpenSSL na macOS</span><span class="sxs-lookup"><span data-stu-id="6d6e6-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="6d6e6-102">Środowiska uruchomieniowe platformy .NET Core 3,0 i nowszego w systemie macOS teraz preferują wersje OpenSSL 1.0. x dla <xref:System.Security.Cryptography.AesCcm> typów,,, <xref:System.Security.Cryptography.AesGcm> , <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> i <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .</span><span class="sxs-lookup"><span data-stu-id="6d6e6-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="6d6e6-103">Środowisko uruchomieniowe programu .NET Core 2,1 obsługuje teraz wersje OpenSSL 1.1. x, ale nadal preferują wersje OpenSSL 1.0. x.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6d6e6-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="6d6e6-104">Change description</span></span>

<span data-ttu-id="6d6e6-105">Wcześniej środowisko uruchomieniowe platformy .NET Core używało wersji OpenSSL 1.0. x w macOS dla typów, które współdziałają z OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="6d6e6-106">Najnowsza wersja OpenSSL 1.0. x, OpenSSL 1.0.2, już nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="6d6e6-107">Aby zachować typy korzystające z OpenSSL na obsługiwanych wersjach OpenSSL, środowisko uruchomieniowe programu .NET Core 3,0 i nowszych wersji już teraz używa nowszych wersjach OpenSSL na macOS.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="6d6e6-108">W przypadku tej zmiany zachowanie środowiska uruchomieniowego .NET Core w systemie macOS jest następujące:</span><span class="sxs-lookup"><span data-stu-id="6d6e6-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="6d6e6-109">Środowisko uruchomieniowe programu .NET Core 3,0 i nowszych wersji używa OpenSSL 1.1. x, jeśli jest dostępny, i wraca do OpenSSL 1.0. x tylko wtedy, gdy nie jest dostępna wersja 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="6d6e6-110">W przypadku wywołujących, które używają typów międzyoperacyjnych OpenSSL z niestandardowym P/Invoke, postępuj zgodnie ze wskazówkami w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="6d6e6-111">Jeśli wartość nie zostanie sprawdzona, może wystąpić awaria aplikacji <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> .</span><span class="sxs-lookup"><span data-stu-id="6d6e6-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="6d6e6-112">Środowisko uruchomieniowe programu .NET Core 2,1 korzysta z OpenSSL 1.0. x, jeśli jest dostępne, i wraca do OpenSSL 1.1. x, jeśli nie jest dostępna wersja 1.0. x.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="6d6e6-113">Środowisko uruchomieniowe 2,1 preferuje wcześniejszą wersję programu OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> , ponieważ właściwość nie istnieje w programie .NET Core 2,1, więc nie można w sposób niezawodny określić wersji OpenSSL w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6d6e6-114">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6d6e6-114">Version introduced</span></span>

- <span data-ttu-id="6d6e6-115">2.1.16 .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d6e6-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="6d6e6-116">3.0.3 .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d6e6-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="6d6e6-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="6d6e6-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6d6e6-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6d6e6-118">Recommended action</span></span>

- <span data-ttu-id="6d6e6-119">Odinstaluj program OpenSSL w wersji 1.0.2, jeśli nie jest już wymagany.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="6d6e6-120">Zainstaluj OpenSSL 1.1. x, jeśli używasz <xref:System.Security.Cryptography.AesCcm> , <xref:System.Security.Cryptography.AesGcm> ,,,, <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> lub <xref:System.Security.Cryptography.SafeEvpPKeyHandle> typów.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="6d6e6-121">Jeśli używasz typów międzyoperacyjnych OpenSSL z niestandardowym P/Invoke, postępuj zgodnie ze wskazówkami zawartymi w <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uwagach.</span><span class="sxs-lookup"><span data-stu-id="6d6e6-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="6d6e6-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6d6e6-122">Category</span></span>

<span data-ttu-id="6d6e6-123">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6d6e6-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6d6e6-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6d6e6-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
