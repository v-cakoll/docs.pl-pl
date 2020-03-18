---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936983"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Zduplikowane interfejsy API usunięte z formularzy systemu Windows

Liczba interfejsów API przypadkowo zduplikowanych w obszarze <xref:System.Windows.Forms?displayProperty=fullName> nazw, począwszy od .NET Core 3.0 Preview 4, została usunięta w .NET Core 3.0 RC1.

#### <a name="change-description"></a>Zmień opis

.NET Core 3.0 Preview 4 przypadkowo zduplikował liczbę typów w obszarze <xref:System.Windows.Forms?displayProperty=fullName> nazw, które już istniały w obszarze <xref:System.ComponentModel.Design?displayProperty=fullName> nazw. Począwszy od .NET Core 3.0 RC1, te zduplikowane typy nie są już dostępne. W poniższej tabeli przedstawiono oryginalny typ i jego zduplikowany typ:

> [!div class="mx-tdCol2BreakAll"]
> |Typ oryginalny|Zduplikowany typ|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Rc1

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj kod, aby odwoływać się do oryginalnego typu, jak pokazano w kolumnie **Typ oryginalny** tabeli.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Nie wykrywalne za pomocą analizy Interfejsu API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
