---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617196"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Wersja Entity Framework musi być zgodna z wersją .NET Framework

#### <a name="details"></a>Szczegóły

Wersja Entity Framework (EF) powinna być zgodna z wersją .NET Framework. Entity Framework 5 jest zalecana dla .NET Framework 4,5. Istnieją znane problemy z programem EF 4. x w projekcie .NET Framework 4,5 <xref:System.ComponentModel.DataAnnotations> . W .NET Framework 4,5 te zostały przeniesione do innego zestawu, dlatego występują problemy z ustaleniem adnotacji do użycia.

#### <a name="suggestion"></a>Sugestia

Uaktualnij do wersji Entity Framework 5 dla .NET Framework 4,5

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.5         |
| Typ    | Przekierowanie |
