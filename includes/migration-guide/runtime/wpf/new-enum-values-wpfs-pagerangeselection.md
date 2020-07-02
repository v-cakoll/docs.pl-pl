---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620454"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a>Nowe wartości wyliczeniowe w PageRangeSelection WPF

#### <a name="details"></a>Szczegóły

Dodano dwóch nowych członków ( <xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> i <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName> ) do <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> wyliczenia.

#### <a name="suggestion"></a>Sugestia

W większości przypadków te zmiany nie wpłyną na kod użytkownika. Kod, który zależy od określonej liczby elementów istniejących w <xref:System.Enum.GetNames(System.Type)> lub <xref:System.Enum.GetValues(System.Type)> wywołania <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> typu należy zmodyfikować, chociaż.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
