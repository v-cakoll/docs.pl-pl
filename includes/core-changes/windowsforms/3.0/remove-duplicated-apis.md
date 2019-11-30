---
ms.openlocfilehash: 3d0a90a57c2b1c2759b8420e74c284668d54e9cb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644041"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Zduplikowane interfejsy API zostały usunięte z Windows Forms

Wiele interfejsów API przypadkowo zduplikowanych w przestrzeni nazw <xref:System.Windows.Forms?displayProperty=fullName>, począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 4, zostało usuniętych w programie .NET Core 3,0 RC1.

#### <a name="change-description"></a>Zmień opis

Program .NET Core 3,0 w wersji zapoznawczej 4 przypadkowo duplikuje kilka typów w przestrzeni nazw <xref:System.Windows.Forms?displayProperty=fullName>, które już istniały w przestrzeni nazw <xref:System.ComponentModel.Design?displayProperty=fullName>. Począwszy od platformy .NET Core 3,0 RC1, te zduplikowane typy nie są już dostępne. Poniższa tabela zawiera listę typów pierwotnych i duplikatów typów:

|Typ oryginalny|Zduplikowany typ|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 RC1

#### <a name="recommended-action"></a>Zalecane działanie

Zaktualizuj kod, aby odwołać się do oryginalnego typu, jak pokazano w kolumnie **pierwotnego typu** tabeli.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Nie wykrywalne za pośrednictwem analizy interfejsu API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
