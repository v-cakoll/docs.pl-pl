---
title: ToolBar — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186615"
---
# <a name="toolbar-overview"></a>ToolBar — Przegląd
<xref:System.Windows.Controls.ToolBar>formanty są kontenerami dla grupy poleceń lub formantów, które są zazwyczaj związane w ich funkcji. Zwykle <xref:System.Windows.Controls.ToolBar> zawiera przyciski, które wywołują polecenia.  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>ToolBar — Formant  
 Formant <xref:System.Windows.Controls.ToolBar> bierze swoją nazwę od paska jak rozmieszczenie przycisków lub innych formantów w jednym wierszu lub kolumnie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> formanty zapewniają mechanizm przepełnienia, który umieszcza wszystkie elementy, <xref:System.Windows.Controls.ToolBar> które nie mieszczą się naturalnie w rozmiarze ograniczone do specjalnego obszaru przepełnienia. Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> formanty są zwykle <xref:System.Windows.Controls.ToolBarTray> używane z powiązanym formantem, który zapewnia zachowanie specjalnego układu, a także obsługę zmiany rozmiaru inicjowanego przez użytkownika i organizowania pasków narzędzi.  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Określanie położenia pasków narzędzi w pasku narzędzi  
 Użyj <xref:System.Windows.Controls.ToolBar.Band%2A> właściwości <xref:System.Windows.Controls.ToolBar.BandIndex%2A> i, aby <xref:System.Windows.Controls.ToolBar> umieścić <xref:System.Windows.Controls.ToolBarTray>w pliku . <xref:System.Windows.Controls.ToolBar.Band%2A>wskazuje pozycję, w <xref:System.Windows.Controls.ToolBar> której znajduje się <xref:System.Windows.Controls.ToolBarTray>jego rodzic . <xref:System.Windows.Controls.ToolBar.BandIndex%2A>wskazuje kolejność, w <xref:System.Windows.Controls.ToolBar> jakiej znajduje się w jego paśmie. W poniższym przykładzie pokazano, <xref:System.Windows.Controls.ToolBar> jak <xref:System.Windows.Controls.ToolBarTray>używać tej właściwości do umieszczania formantów wewnątrz .  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>Paski narzędziowe z elementami przepełnienia  
 Często <xref:System.Windows.Controls.ToolBar> formanty zawierają więcej elementów, niż można zmieścić w rozmiarze paska narzędzi. W takim przypadku <xref:System.Windows.Controls.ToolBar> zostanie wyświetlony przycisk przepełnienia. Aby wyświetlić elementy przepełnienia, użytkownik kliknie przycisk przepełnienia, a elementy <xref:System.Windows.Controls.ToolBar>są wyświetlane w wyskakującym oknie pod przyciskiem . Na poniższej <xref:System.Windows.Controls.ToolBar> ilustracji przedstawiono elementy przepełnienia:  
  
 ![Zrzut ekranu przedstawiający pasek narzędzi z elementami przepełnienia.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Można określić, kiedy element na pasku narzędzi jest umieszczany na panelu przepełnienia, ustawiając <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> dołączoną właściwość na <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>lub <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Poniższy przykład określa, że ostatnie cztery przyciski na pasku narzędzi powinny zawsze znajdować się na panelu przepełnienia.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Zastosowania <xref:System.Windows.Controls.ToolBar> a <xref:System.Windows.Controls.Primitives.ToolBarPanel> i <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> a <xref:System.Windows.Controls.ControlTemplate>w jego .  Jest <xref:System.Windows.Controls.Primitives.ToolBarPanel> odpowiedzialny za układ elementów na pasku narzędzi.  Jest <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> odpowiedzialny za układ elementów, które nie <xref:System.Windows.Controls.ToolBar>mieszczą się w pliku . Na przykład for <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.ToolBar>, zobacz  
  
 [Style i szablony paska narzędzi](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Kontrolki stylu na pasku ToolBar](how-to-style-controls-on-a-toolbar.md)
- [Przykład galerii kontrolek WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
