---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622116"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a>Naprawiono zawieszenie, gdy pole listy zawiera zduplikowane typy wartości

#### <a name="details"></a>Szczegóły

Rozwiązano problem polegający na tym, że wirtualizacja <xref:System.Windows.Controls.ItemsControl> może się zawiesić podczas przewijania, gdy kolekcja elementów zawiera zduplikowane obiekty z typem wartości.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4,8|
|Typ|Środowisko uruchomieniowe|
