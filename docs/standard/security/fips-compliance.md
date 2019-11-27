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
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a>Zgodność z programem .NET Core Federal Information Processing Standard (FIPS)

Publikacja Federal Information Processing Standard (FIPS) 140-2 jest standardem rządowym USA, który definiuje minimalne wymagania dotyczące zabezpieczeń modułów kryptograficznych w produktach technologii informatycznych, zgodnie z definicją w sekcji 5131 informacji Czynność reform zarządzania technologią 1996.

.NET Core:

* Przekazuje wywołania pierwotnych elementów kryptograficznych do modułów standardowych dostępnych w systemie operacyjnym.
* Nie **wymusza użycia** zatwierdzonych algorytmów FIPS ani rozmiarów kluczy w aplikacjach .NET Core.

Administrator systemu jest odpowiedzialny za skonfigurowanie zgodności ze standardem FIPS dla systemu operacyjnego.

Jeśli kod jest pisany dla środowiska zgodnego ze standardem FIPS, deweloper jest odpowiedzialny za zapewnienie, że niezgodne algorytmy FIPS nie są używane.

Aby uzyskać więcej informacji na temat zgodności ze standardem FIPS, zobacz następujące artykuły:

* [Zgodność ze standardem FIPS systemu Windows](/windows/security/threat-protection/fips-140-validation)
* [Konfigurowanie zgodności systemu Windows pod kątem FIPS](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [10,2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
