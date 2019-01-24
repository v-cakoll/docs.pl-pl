---
title: ToolBar — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 913c7a9f1b5cf891f3e19c4f3126596bad49f79d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695857"
---
# <a name="toolbar-overview"></a>ToolBar — Przegląd
<xref:System.Windows.Controls.ToolBar> Formanty są kontenerami dla grupy poleceń lub kontrolek, które są zazwyczaj powiązane w ich funkcji. A <xref:System.Windows.Controls.ToolBar> zwykle zawiera przyciski, które wywołują polecenia.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar — Formant  
 <xref:System.Windows.Controls.ToolBar> Kontrolka uzyskuje jego nazwę rozmieszczenie słupkowy przypominających przycisków lub innych kontrolek w pojedynczym wierszu lub kolumnie. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> elementy sterujące udostępniają mechanizm przepełnienia, który umieszcza wszystkie elementy, które nie mieszczą się naturalnie ograniczony rozmiar <xref:System.Windows.Controls.ToolBar> w obszarze specjalne przepełnienia. Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> formanty są zwykle używane z powiązane <xref:System.Windows.Controls.ToolBarTray> formant, który zapewnia zachowanie specjalnego układu, a także obsługę zainicjowanego przez użytkownika rozmiaru i rozmieszczanie pasków narzędzi.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Określanie pozycja paski narzędzi w ToolBarTray  
 Użyj <xref:System.Windows.Controls.ToolBar.Band%2A> i <xref:System.Windows.Controls.ToolBar.BandIndex%2A> właściwości, aby umieścić <xref:System.Windows.Controls.ToolBar> w <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> Określa położenie, w którym <xref:System.Windows.Controls.ToolBar> znajduje się w ramach jego elementu nadrzędnego <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> Określa kolejność, w którym <xref:System.Windows.Controls.ToolBar> znajduje się w jego poza pasmem. W poniższym przykładzie pokazano jak używać tej właściwości można umieścić <xref:System.Windows.Controls.ToolBar> kontroluje wewnątrz <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Paski narzędzi z elementami przepełnienia  
 Często <xref:System.Windows.Controls.ToolBar> kontrolki zawiera więcej elementów niż można zmieścić na pasku narzędzi rozmiar. W takim przypadku <xref:System.Windows.Controls.ToolBar> powoduje wyświetlenie przycisku przepełnienia. Aby wyświetlić elementy przepełnienia, użytkownik klika przycisk przepełnienie i elementy są wyświetlane w oknie podręcznym poniżej <xref:System.Windows.Controls.ToolBar>. Pokazano grafiki <xref:System.Windows.Controls.ToolBar> z elementami przepełnienia.  
  
 ![Pasek narzędzi z przepełnienia](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
Pasek narzędzi z elementami przepełnienia  
  
 Można określić, gdy element na pasku narzędzi jest umieszczony na panelu przepełnienia, ustawiając <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> dołączonych właściwości <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, lub <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. W poniższym przykładzie określono, że ostatnie cztery przyciski na pasku narzędzi powinny zawsze być na panelu przepełnienia.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> Używa <xref:System.Windows.Controls.Primitives.ToolBarPanel> i <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> w jego <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> Jest odpowiedzialny za układ elementów na pasku narzędzi.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> Jest odpowiedzialny za układu elementów, które nie mieszczą się na <xref:System.Windows.Controls.ToolBar>. Na przykład <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolBar>, zobacz  
  
 [ToolBar — style i szablony](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Kontrolki stylu na pasku ToolBar](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)
- [Przykładu z galerii kontrolki WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
