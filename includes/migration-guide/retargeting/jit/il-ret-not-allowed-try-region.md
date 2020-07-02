---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615671"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Element IL RET nie jest dozwolony w regionie try

#### <a name="details"></a>Szczegóły

W przeciwieństwie do kompilatora JIT64 just in Time RyuJIT (używany w .NET Framework 4,6) nie zezwala na instrukcje języka IL RET w regionie try. Powrót z regionu try jest niedozwolony w specyfikacji ECMA-335, a żaden znany kompilator zarządzany nie generuje takiego IL. Jednak kompilator JIT64 wykona takie IL, jeśli zostanie wygenerowany przy użyciu emisji odbicia.

#### <a name="suggestion"></a>Sugestia

Jeśli aplikacja generuje IL, która zawiera kod operacji RET w regionie try, aplikacja może kierować .NET Framework 4,5, aby użyć starego JIT i uniknąć tego przerwy. Alternatywnie wygenerowany kod IL może zostać zaktualizowany w celu powrotu po regionie try.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6         |
| Typ    | Przekierowanie |
