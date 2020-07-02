---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622126"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Wywołanie elementu DataGrid. CommitEdit z obsługi CellEditEnding powoduje odrzucenie fokusu

#### <a name="details"></a>Szczegóły

Wywołanie <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednego z <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> programów obsługi zdarzeń powoduje <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> utratę fokusu.

#### <a name="suggestion"></a>Sugestia

Ta usterka została rozwiązana w .NET Framework 4.5.2, dlatego można ją uniknąć, uaktualniając .NET Framework. Alternatywnie można to uniknąć przez jawne ponowne wybranie polecenia <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> po wywołaniu <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
