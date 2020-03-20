---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804531"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret nie jest dozwolony w regionie try

|   |   |
|---|---|
|Szczegóły|W przeciwieństwie do kompilatora just-in-time JIT64 RyuJIT (używany w .NET Framework 4.6) nie zezwala na instrukcję IL ret w regionie try. Powrót z regionu try jest niedozwolony przez specyfikację ECMA-335 i żaden znany kompilator zarządzany nie generuje takiego identyfikatora IL. Jednak kompilator JIT64 wykona takie IL, jeśli jest generowany przy użyciu emisji odbicia.|
|Sugestia|Jeśli aplikacja generuje IL, który zawiera kod opcode ret w regionie try, aplikacja może kierować .NET Framework 4.5 do korzystania ze starego JIT i uniknąć tej przerwy. Alternatywnie wygenerowany IL może zostać zaktualizowany, aby powrócić po regionie try.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Przekierowanie|
