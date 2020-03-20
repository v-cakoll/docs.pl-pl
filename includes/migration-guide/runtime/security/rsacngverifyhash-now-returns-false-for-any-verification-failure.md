---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887816"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="7be59-101">RSACng.VerifyHash zwraca teraz False dla każdego błędu weryfikacji</span><span class="sxs-lookup"><span data-stu-id="7be59-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7be59-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7be59-102">Details</span></span>|<span data-ttu-id="7be59-103">Począwszy od programu .NET Framework 4.6.2, ta metoda zwraca **False,** jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="7be59-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="7be59-104">Teraz zwraca false dla każdego błędu weryfikacji. W .NET Framework 4.6 i 4.6.1 metoda <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zgłasza, jeśli podpis sam jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="7be59-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="7be59-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7be59-105">Suggestion</span></span>|<span data-ttu-id="7be59-106">Każdy kod, którego wykonanie <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zależy od obsługi należy wykonać zamiast tego, jeśli sprawdzanie poprawności nie powiedzie się, a metoda zwraca **False**.</span><span class="sxs-lookup"><span data-stu-id="7be59-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="7be59-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="7be59-107">Scope</span></span>|<span data-ttu-id="7be59-108">Mały</span><span class="sxs-lookup"><span data-stu-id="7be59-108">Minor</span></span>|
|<span data-ttu-id="7be59-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="7be59-109">Version</span></span>|<span data-ttu-id="7be59-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="7be59-110">4.6.2</span></span>|
|<span data-ttu-id="7be59-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7be59-111">Type</span></span>|<span data-ttu-id="7be59-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7be59-112">Runtime</span></span>|
|<span data-ttu-id="7be59-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7be59-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
