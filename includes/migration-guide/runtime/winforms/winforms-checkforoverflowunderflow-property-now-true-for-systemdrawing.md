---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379701"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Właściwość CheckForOverflowUnderflow WinForm firmy to teraz System.Drawing

|   |   |
|---|---|
|Szczegóły|Właściwość CheckForOverflowUnderflow dla zestawu System.Drawing.dll jest ustawiona na wartość true.|
|Sugestia|Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty. Teraz <xref:System.OverflowException?displayProperty=name> wyjątku.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
