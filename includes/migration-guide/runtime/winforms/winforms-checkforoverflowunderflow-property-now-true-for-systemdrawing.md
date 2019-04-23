---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804763"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Właściwość CheckForOverflowUnderflow WinForm firmy to teraz System.Drawing

|   |   |
|---|---|
|Szczegóły|Właściwość CheckForOverflowUnderflow dla zestawu System.Drawing.dll jest ustawiona na wartość true.|
|Sugestia|Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty. Teraz <xref:System.OverflowException?displayProperty=name> wyjątku.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
