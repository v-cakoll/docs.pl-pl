---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620442"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Właściwość CheckForOverflowUnderflow kontrolki WinForm jest teraz prawdziwa dla elementu System. Drawing

#### <a name="details"></a>Szczegóły

Właściwość CheckForOverflowUnderflow zestawu System.Drawing.dll ma wartość true.

#### <a name="suggestion"></a>Sugestia

Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty. Zostanie <xref:System.OverflowException?displayProperty=fullName> zgłoszony wyjątek.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
