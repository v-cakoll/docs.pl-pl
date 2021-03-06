---
ms.openlocfilehash: c9720f51e40ada4cd2cf6997ba7006a232893553
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702466"
---
### <a name="removed-status-bar-controls"></a>Usunięto kontrolki paska stanu

Począwszy od programu .NET 5,0 w wersji zapoznawczej 1, niektóre kontrolki Windows Forms nie są już dostępne.

#### <a name="change-description"></a>Zmień opis

Począwszy od programu .NET 5,0 w wersji zapoznawczej 1, niektóre kontrolki Windows Forms powiązane z paskiem stanu nie są już dostępne. Kontrolki zamiany, które mają lepszy projekt i pomoc techniczną, zostały wprowadzone w .NET Framework 2,0. Przestarzałe formanty zostały wcześniej usunięte z przyborników projektanta, ale były nadal dostępne do użycia. Teraz zostały całkowicie usunięte.

Następujące typy nie są już dostępne:

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 1

#### <a name="recommended-action"></a>Zalecana akcja

Przejdź do zastępczych interfejsów API dla tych formantów i ich scenariuszy:

| Stara kontrolka (API) | Zalecane zastąpienie                          |
|-------------------|--------------------------------------------------|
| StatusBar         | <xref:System.Windows.Forms.StatusStrip>          |
| StatusBarPanel    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
