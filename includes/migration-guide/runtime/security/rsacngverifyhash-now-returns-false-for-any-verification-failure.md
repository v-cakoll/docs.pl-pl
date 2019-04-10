---
ms.openlocfilehash: acf4e8df2cef3d9ec5d123a14cc7bfcd6f1bfb8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236083"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="e040f-101">Jakiekolwiek niepowodzenie weryfikacji RSACng.VerifyHash teraz zwraca wartość False</span><span class="sxs-lookup"><span data-stu-id="e040f-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e040f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e040f-102">Details</span></span>|<span data-ttu-id="e040f-103">Począwszy od programu .NET Framework 4.6.2, Metoda ta zwraca <strong>False</strong> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="e040f-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="e040f-104">Obecnie zwraca wartość false dla jakiekolwiek niepowodzenie weryfikacji. W .NET Framework 4.6 i 4.6.1, metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="e040f-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="e040f-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e040f-105">Suggestion</span></span>|<span data-ttu-id="e040f-106">Jakiegokolwiek kodu, których wykonanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zamiast tego powinien zostać wykonany, jeśli weryfikacja zakończy się niepowodzeniem i metoda zwraca <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="e040f-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="e040f-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="e040f-107">Scope</span></span>|<span data-ttu-id="e040f-108">Mały</span><span class="sxs-lookup"><span data-stu-id="e040f-108">Minor</span></span>|
|<span data-ttu-id="e040f-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="e040f-109">Version</span></span>|<span data-ttu-id="e040f-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e040f-110">4.6.2</span></span>|
|<span data-ttu-id="e040f-111">Typ</span><span class="sxs-lookup"><span data-stu-id="e040f-111">Type</span></span>|<span data-ttu-id="e040f-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e040f-112">Runtime</span></span>|
|<span data-ttu-id="e040f-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e040f-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
