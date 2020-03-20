---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858411"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nie są wyliczane przez profilerzy

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework w wersji 4.5.1 interfejs <code>RootReferences2()</code> <code>COR_PRF_GC_ROOT_HANDLE</code> API profilowania <code>COR_PRF_GC_ROOT_OTHER</code> niepoprawnie nigdy nie zwraca (są one zwracane jako zamiast tego). Ten problem został rozwiązany począwszy od .NET Framework 4.6.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
