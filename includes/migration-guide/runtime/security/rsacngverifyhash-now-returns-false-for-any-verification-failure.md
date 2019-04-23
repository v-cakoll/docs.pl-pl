---
ms.openlocfilehash: acf4e8df2cef3d9ec5d123a14cc7bfcd6f1bfb8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804697"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="3c3fc-101">Jakiekolwiek niepowodzenie weryfikacji RSACng.VerifyHash teraz zwraca wartość False</span><span class="sxs-lookup"><span data-stu-id="3c3fc-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3c3fc-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3c3fc-102">Details</span></span>|<span data-ttu-id="3c3fc-103">Począwszy od programu .NET Framework 4.6.2, Metoda ta zwraca <strong>False</strong> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="3c3fc-104">Obecnie zwraca wartość false dla jakiekolwiek niepowodzenie weryfikacji. W .NET Framework 4.6 i 4.6.1, metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="3c3fc-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3c3fc-105">Suggestion</span></span>|<span data-ttu-id="3c3fc-106">Jakiegokolwiek kodu, których wykonanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zamiast tego powinien zostać wykonany, jeśli weryfikacja zakończy się niepowodzeniem i metoda zwraca <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="3c3fc-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="3c3fc-107">Scope</span></span>|<span data-ttu-id="3c3fc-108">Mały</span><span class="sxs-lookup"><span data-stu-id="3c3fc-108">Minor</span></span>|
|<span data-ttu-id="3c3fc-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="3c3fc-109">Version</span></span>|<span data-ttu-id="3c3fc-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3c3fc-110">4.6.2</span></span>|
|<span data-ttu-id="3c3fc-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3c3fc-111">Type</span></span>|<span data-ttu-id="3c3fc-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3c3fc-112">Runtime</span></span>|
|<span data-ttu-id="3c3fc-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3c3fc-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
