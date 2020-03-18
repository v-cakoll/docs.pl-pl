---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937119"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.EnableVisualStyleValidation` zgodności nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

W programie .NET `Switch.System.Windows.Forms.EnableVisualStyleValidation` Framework przełącznik zgodności umożliwił aplikacji rezygnację z sprawdzania poprawności stylów wizualnych dostarczanych w formie liczbowej.

W .NET Core `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
