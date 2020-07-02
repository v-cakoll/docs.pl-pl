---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622129"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilowanie aplikacji ASP.Net MVC4 może prowadzić do błędu aparatu wykonywania krytycznych

#### <a name="details"></a>Szczegóły

Moduły plików używające narzędzia NGEN/profile mogą ulec awarii w profilowanych aplikacjach ASP.NET MVC4 podczas uruchamiania przy użyciu "wyjątku aparatu wykonywania krytycznego"

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4.5.2. Alternatywnie profiler może uniknąć tego problemu przez określenie <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego masce zdarzeń.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
