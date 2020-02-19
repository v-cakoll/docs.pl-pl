---
title: ToolBar — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 460d4420d5faf849a8d05a94e0170aea384f69b4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452698"
---
# <a name="toolbar-overview"></a>ToolBar — Przegląd
formanty <xref:System.Windows.Controls.ToolBar> są kontenerami dla grupy poleceń lub kontrolek, które są zwykle powiązane z ich funkcją. <xref:System.Windows.Controls.ToolBar> zazwyczaj zawiera przyciski, które wywołują polecenia.  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar — Formant  
 Kontrolka <xref:System.Windows.Controls.ToolBar> przyjmuje swoją nazwę od układu przycisków lub innych kontrolek podobne do paska. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> kontrolki zapewniają mechanizm przepełnienia, który umieszcza elementy, które nie mieszczą się naturalnie w nieograniczonej <xref:System.Windows.Controls.ToolBar> rozmiarze w specjalnym obszarze przepełnienia. Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki <xref:System.Windows.Controls.ToolBar> są zwykle używane z powiązaną kontrolką <xref:System.Windows.Controls.ToolBarTray>, która zapewnia specjalne zachowanie układu, a także obsługę ustalania rozmiarów i układu pasków narzędzi inicjowanych przez użytkownika.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Określanie położenia pasków narzędzi w ToolBarTray  
 Użyj właściwości <xref:System.Windows.Controls.ToolBar.Band%2A> i <xref:System.Windows.Controls.ToolBar.BandIndex%2A>, aby ustawić <xref:System.Windows.Controls.ToolBar> w <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> wskazuje położenie, w którym <xref:System.Windows.Controls.ToolBar> jest umieszczane w <xref:System.Windows.Controls.ToolBarTray>nadrzędnym. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> wskazuje kolejność, w której <xref:System.Windows.Controls.ToolBar> jest umieszczony w obrębie pasma. Poniższy przykład pokazuje, jak używać tej właściwości do umieszczania formantów <xref:System.Windows.Controls.ToolBar> w <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Paski narzędzi z przepełnieniem elementów  
 Często formanty <xref:System.Windows.Controls.ToolBar> zawierają więcej elementów niż można dopasować do rozmiaru paska narzędzi. W takim przypadku <xref:System.Windows.Controls.ToolBar> wyświetla przycisk przepełnienie. Aby wyświetlić przepełnione elementy, użytkownik klika przycisk przeciążenia, a elementy są wyświetlane w oknie podręcznym poniżej <xref:System.Windows.Controls.ToolBar>. Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.ToolBar> z przepełnieniem elementów:  
  
 ![Zrzut ekranu pokazujący pasek narzędzi z przepełnieniem elementów.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Możesz określić, kiedy element na pasku narzędzi ma być umieszczony na panelu przepełnienia, ustawiając właściwość <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> dołączone do <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>lub <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. W poniższym przykładzie określono, że ostatnie cztery przyciski na pasku narzędzi powinny zawsze znajdować się na panelu przepełnienia.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> używa <xref:System.Windows.Controls.Primitives.ToolBarPanel> i <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> w <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> jest odpowiedzialna za układ elementów na pasku narzędzi.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> jest odpowiedzialna za układ elementów, które nie mieszczą się w <xref:System.Windows.Controls.ToolBar>. Przykład <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolBar>, zobacz  
  
 [Paski narzędzi i szablony](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Kontrolki stylu na pasku ToolBar](how-to-style-controls-on-a-toolbar.md)
- [Przykład galerii formantów WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
