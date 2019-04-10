---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235419"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Domyślnie pole tekstowe WPF Cofnij granicę równą 100

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 domyślny limit cofania WPF textbox wynosi 100 (w przeciwieństwie do zwrócenia w .NET Framework 4.0)|
|Sugestia|Jeśli limit 100 cofania jest zbyt niska, limit można jawnie ustawić za pomocą <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
