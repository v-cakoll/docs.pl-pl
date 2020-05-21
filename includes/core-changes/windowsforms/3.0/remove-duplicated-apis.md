---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721519"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Zduplikowane interfejsy API zostały usunięte z Windows Forms

Wiele interfejsów API przypadkowo zduplikowanych w <xref:System.Windows.Forms?displayProperty=fullName> przestrzeni nazw rozpoczynających się w programie .net core 3,0 Preview 4 zostały usunięte w programie .net core 3,0 RC1.

#### <a name="change-description"></a>Zmień opis

Program .NET Core 3,0 w wersji zapoznawczej 4 przypadkowo duplikuje kilka typów w <xref:System.Windows.Forms?displayProperty=fullName> przestrzeni nazw, które już istniały w <xref:System.ComponentModel.Design?displayProperty=fullName> przestrzeni nazw. Począwszy od platformy .NET Core 3,0 RC1, te zduplikowane typy nie są już dostępne. Poniższa tabela zawiera listę typów pierwotnych i duplikatów typów:

> [!div class="mx-tdCol2BreakAll"]
> |Typ oryginalny|Zduplikowany typ|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 RC1

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj kod, aby odwołać się do oryginalnego typu, jak pokazano w kolumnie **pierwotnego typu** tabeli.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak.

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
