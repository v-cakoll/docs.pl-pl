---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888139"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Zduplikowane interfejsy API usunięte z formularzy systemu Windows

Liczba interfejsów API przypadkowo zduplikowane w obszarze <xref:System.Windows.Forms?displayProperty=fullName> nazw, począwszy od .NET Core 3.0 Preview 4 zostały usunięte w .NET Core 3.0 RC1.

#### <a name="change-description"></a>Zmień opis

Program .NET Core 3.0 Preview 4 przypadkowo zduplikował wiele typów w obszarze <xref:System.Windows.Forms?displayProperty=fullName> nazw, które już istniały w obszarze <xref:System.ComponentModel.Design?displayProperty=fullName> nazw. Począwszy od .NET Core 3.0 RC1, te zduplikowane typy nie są już dostępne. W poniższej tabeli przedstawiono oryginalny typ i jego zduplikowany typ:

> [!div class="mx-tdCol2BreakAll"]
> |Typ oryginalny|Zduplikowany typ|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0 RC1

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj kod, aby odwoływać się do oryginalnego typu, jak pokazano w kolumnie **Typ oryginalny** tabeli.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
