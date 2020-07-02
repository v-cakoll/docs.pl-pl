---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620208"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nie są wyliczane przez program do plików

#### <a name="details"></a>Szczegóły

W .NET Framework v 4.5.1 interfejs API profilowania <code>RootReferences2()</code> jest niepoprawnie nigdy nie zwraca <code>COR_PRF_GC_ROOT_HANDLE</code> (są zwracane jako <code>COR_PRF_GC_ROOT_OTHER</code> zamiast). Ten problem został rozwiązany, rozpoczynając od .NET Framework 4,6.

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
