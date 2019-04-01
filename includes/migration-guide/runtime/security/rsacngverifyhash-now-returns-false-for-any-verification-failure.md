---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760659"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="78043-101">Jakiekolwiek niepowodzenie weryfikacji RSACng.VerifyHash teraz zwraca wartość False</span><span class="sxs-lookup"><span data-stu-id="78043-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="78043-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="78043-102">Details</span></span>|<span data-ttu-id="78043-103">Począwszy od programu .NET Framework 4.6.2, Metoda ta zwraca <strong>False</strong> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="78043-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="78043-104">Obecnie zwraca wartość false dla jakiekolwiek niepowodzenie weryfikacji. W .NET Framework 4.6 i 4.6.1, metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="78043-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="78043-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="78043-105">Suggestion</span></span>|<span data-ttu-id="78043-106">Jakiegokolwiek kodu, których wykonanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zamiast tego powinien zostać wykonany, jeśli weryfikacja zakończy się niepowodzeniem i metoda zwraca <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="78043-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="78043-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="78043-107">Scope</span></span>|<span data-ttu-id="78043-108">Mały</span><span class="sxs-lookup"><span data-stu-id="78043-108">Minor</span></span>|
|<span data-ttu-id="78043-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="78043-109">Version</span></span>|<span data-ttu-id="78043-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="78043-110">4.6.2</span></span>|
|<span data-ttu-id="78043-111">Typ</span><span class="sxs-lookup"><span data-stu-id="78043-111">Type</span></span>|<span data-ttu-id="78043-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="78043-112">Runtime</span></span>|
|<span data-ttu-id="78043-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="78043-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

