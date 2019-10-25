---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887816"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="f2708-101">RSACng. VerifyHash teraz zwraca wartość false dla dowolnego błędu weryfikacji</span><span class="sxs-lookup"><span data-stu-id="f2708-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f2708-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f2708-102">Details</span></span>|<span data-ttu-id="f2708-103">Rozpoczynając od .NET Framework 4.6.2, ta metoda zwraca **wartość false** , jeśli podpis jest nieprawidłowo sformatowany.</span><span class="sxs-lookup"><span data-stu-id="f2708-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="f2708-104">Teraz zwraca wartość false dla dowolnego błędu weryfikacji. W .NET Framework 4,6 i 4.6.1 Metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>, jeśli podpis jest nieprawidłowo sformatowany.</span><span class="sxs-lookup"><span data-stu-id="f2708-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="f2708-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f2708-105">Suggestion</span></span>|<span data-ttu-id="f2708-106">Każdy kod, którego wykonywanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> należy zamiast tego wykonać, jeśli Walidacja nie powiedzie się, a metoda zwróci **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="f2708-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="f2708-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="f2708-107">Scope</span></span>|<span data-ttu-id="f2708-108">Mały</span><span class="sxs-lookup"><span data-stu-id="f2708-108">Minor</span></span>|
|<span data-ttu-id="f2708-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="f2708-109">Version</span></span>|<span data-ttu-id="f2708-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f2708-110">4.6.2</span></span>|
|<span data-ttu-id="f2708-111">Typ</span><span class="sxs-lookup"><span data-stu-id="f2708-111">Type</span></span>|<span data-ttu-id="f2708-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f2708-112">Runtime</span></span>|
|<span data-ttu-id="f2708-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f2708-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
