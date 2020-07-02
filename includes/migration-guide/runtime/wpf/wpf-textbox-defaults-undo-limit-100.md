---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620478"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Wartość pola tekstowego WPF jest domyślna dla limitu cofania 100

#### <a name="details"></a>Szczegóły

W .NET Framework 4,5 domyślny limit cofania dla pola tekstowego WPF to 100 (w przeciwieństwie do nieograniczonego w .NET Framework 4,0)

#### <a name="suggestion"></a>Sugestia

Jeśli limit cofania wynoszący 100 jest zbyt niski, limit może być jawnie ustawiony z<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
