---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857515"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="0d437-101">Jakiekolwiek niepowodzenie weryfikacji RSACng.VerifyHash teraz zwraca wartość False</span><span class="sxs-lookup"><span data-stu-id="0d437-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0d437-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0d437-102">Details</span></span>|<span data-ttu-id="0d437-103">Począwszy od programu .NET Framework 4.6.2, Metoda ta zwraca <strong>False</strong> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="0d437-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="0d437-104">Obecnie zwraca wartość false dla jakiekolwiek niepowodzenie weryfikacji. W .NET Framework 4.6 i 4.6.1, metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> jeśli sam podpis jest źle sformatowany.</span><span class="sxs-lookup"><span data-stu-id="0d437-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="0d437-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0d437-105">Suggestion</span></span>|<span data-ttu-id="0d437-106">Jakiegokolwiek kodu, których wykonanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zamiast tego powinien zostać wykonany, jeśli weryfikacja zakończy się niepowodzeniem i metoda zwraca <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="0d437-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="0d437-107">Scope</span><span class="sxs-lookup"><span data-stu-id="0d437-107">Scope</span></span>|<span data-ttu-id="0d437-108">Mały</span><span class="sxs-lookup"><span data-stu-id="0d437-108">Minor</span></span>|
|<span data-ttu-id="0d437-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="0d437-109">Version</span></span>|<span data-ttu-id="0d437-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="0d437-110">4.6.2</span></span>|
|<span data-ttu-id="0d437-111">Typ</span><span class="sxs-lookup"><span data-stu-id="0d437-111">Type</span></span>|<span data-ttu-id="0d437-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0d437-112">Runtime</span></span>|
|<span data-ttu-id="0d437-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0d437-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

