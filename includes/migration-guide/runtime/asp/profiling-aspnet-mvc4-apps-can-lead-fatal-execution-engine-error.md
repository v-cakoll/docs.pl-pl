---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803157"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilowanie ASP.Net aplikacjami MVC4 może prowadzić do błędu silnika wykonanie fatalne

|   |   |
|---|---|
|Szczegóły|Profilerzy używający zestawów NGEN /Profile mogą ulegać awarii w profilowaniu aplikacji MVC4 ASP.NET podczas uruchamiania z "Fatal Execution Engine Exception"|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.5.2. Alternatywnie profiler może uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.|
|Zakres|Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
