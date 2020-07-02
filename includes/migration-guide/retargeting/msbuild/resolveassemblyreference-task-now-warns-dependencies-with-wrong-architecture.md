---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616102"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Zadanie ResolveAssemblyReference — teraz ostrzega o zależnościach z niewłaściwą architekturą

#### <a name="details"></a>Szczegóły

Zadanie emituje ostrzeżenie, MSB3270, co oznacza, że odwołanie lub jego zależności nie są zgodne z architekturą aplikacji. Na przykład dzieje się tak, jeśli aplikacja, która została skompilowana przy użyciu `AnyCPU` opcji zawiera odwołanie do platformy x86. Taki scenariusz może spowodować awarię aplikacji w czasie wykonywania (w tym przypadku, jeśli aplikacja jest wdrażana jako proces x64).

#### <a name="suggestion"></a>Sugestia

Istnieją dwa obszary wpływu:

- Ponowna kompilacja generuje ostrzeżenia, które nie były wyświetlane, gdy aplikacja została skompilowana w poprzedniej wersji programu MSBuild. Jednak ze względu na to, że ostrzeżenie identyfikuje możliwe Źródło błędu czasu wykonywania, należy zbadać i rozwiązać ten problem.
- Jeśli ostrzeżenia są traktowane jako błędy, kompilacja nie powiedzie się.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5.1       |
| Typ    | Przekierowanie |
