---
title: Zgodność ze standardem FIPS — .NET Core
description: Objaśnia zgodność architektury .NET Core Federal Information Processing Standard (FIPS).
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626961"
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
* [Rozdział 8. Federalne standardy i regulacje Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
