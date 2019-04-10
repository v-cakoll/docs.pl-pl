---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235564"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Właściwość CheckForOverflowUnderflow WinForm firmy to teraz System.Drawing

|   |   |
|---|---|
|Szczegóły|Właściwość CheckForOverflowUnderflow dla zestawu System.Drawing.dll jest ustawiona na wartość true.|
|Sugestia|Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty. Teraz <xref:System.OverflowException?displayProperty=name> wyjątku.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
