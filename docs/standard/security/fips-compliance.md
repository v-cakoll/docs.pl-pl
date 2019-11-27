---
title: Zgodność ze standardem FIPS — .NET Core
description: Objaśnia zgodność architektury .NET Core Federal Information Processing Standard (FIPS).
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205067"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="92d54-103">Zgodność z programem .NET Core Federal Information Processing Standard (FIPS)</span><span class="sxs-lookup"><span data-stu-id="92d54-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="92d54-104">Publikacja Federal Information Processing Standard (FIPS) 140-2 jest standardem rządowym USA, który definiuje minimalne wymagania dotyczące zabezpieczeń modułów kryptograficznych w produktach technologii informatycznych, zgodnie z definicją w sekcji 5131 informacji Czynność reform zarządzania technologią 1996.</span><span class="sxs-lookup"><span data-stu-id="92d54-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="92d54-105">.NET Core:</span><span class="sxs-lookup"><span data-stu-id="92d54-105">.NET Core:</span></span>

* <span data-ttu-id="92d54-106">Przekazuje wywołania pierwotnych elementów kryptograficznych do modułów standardowych dostępnych w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="92d54-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="92d54-107">Nie **wymusza użycia** zatwierdzonych algorytmów FIPS ani rozmiarów kluczy w aplikacjach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="92d54-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="92d54-108">Administrator systemu jest odpowiedzialny za skonfigurowanie zgodności ze standardem FIPS dla systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="92d54-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="92d54-109">Jeśli kod jest pisany dla środowiska zgodnego ze standardem FIPS, deweloper jest odpowiedzialny za zapewnienie, że niezgodne algorytmy FIPS nie są używane.</span><span class="sxs-lookup"><span data-stu-id="92d54-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="92d54-110">Aby uzyskać więcej informacji na temat zgodności ze standardem FIPS, zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="92d54-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="92d54-111">Zgodność ze standardem FIPS systemu Windows</span><span class="sxs-lookup"><span data-stu-id="92d54-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="92d54-112">Konfigurowanie zgodności systemu Windows pod kątem FIPS</span><span class="sxs-lookup"><span data-stu-id="92d54-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="92d54-113">10,2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span><span class="sxs-lookup"><span data-stu-id="92d54-113">10.2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span></span>](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
