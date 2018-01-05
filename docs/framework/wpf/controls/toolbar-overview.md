---
title: "ToolBar — Przegląd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f00597d48ff100325c1fb2884f64169164415a50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-overview"></a>ToolBar — Przegląd
<xref:System.Windows.Controls.ToolBar>Formanty są kontenerami dla grupy poleceń lub kontrolek, które zwykle są związane z ich funkcji. A <xref:System.Windows.Controls.ToolBar> zwykle zawiera przyciski, które wywołują polecenia.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar — Formant  
 <xref:System.Windows.Controls.ToolBar> Kontroli przyjmuje nazwy rozmieszczenie przypominającej paska przycisków lub inne formanty na jeden wiersz lub kolumnę. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> elementy sterujące udostępniają mechanizm przepełnienia, który umieszcza wszystkie elementy, które nie mieszczą się naturalnie rozmiar ograniczony <xref:System.Windows.Controls.ToolBar> w obszarze specjalne przepełnienia. Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> formanty są zazwyczaj używane z odnośnych <xref:System.Windows.Controls.ToolBarTray> kontroli, która zapewnia zachowanie specjalne układ, a także zapewnia obsługę zainicjowane przez użytkownika zmiany rozmiaru i rozmieszczanie pasków narzędzi.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Określanie w kontrolki ToolBarTray pozycji pasków narzędzi  
 Użyj <xref:System.Windows.Controls.ToolBar.Band%2A> i <xref:System.Windows.Controls.ToolBar.BandIndex%2A> właściwości, aby umieścić <xref:System.Windows.Controls.ToolBar> w <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A>Określa położenie, w którym <xref:System.Windows.Controls.ToolBar> znajduje się w ramach jego elementu nadrzędnego <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A>Określa kolejność, w którym <xref:System.Windows.Controls.ToolBar> znajduje się w jego poza pasmem. W poniższym przykładzie przedstawiono sposób używać tej właściwości można umieścić <xref:System.Windows.Controls.ToolBar> kontrolki wewnątrz <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Paski narzędzi z elementami przepełnienia  
 Często <xref:System.Windows.Controls.ToolBar> formanty zawiera więcej elementów niż można zmieścić w pasku narzędzi rozmiar. W takim przypadku <xref:System.Windows.Controls.ToolBar> Wyświetla przycisku przeciążenia. Aby wyświetlić elementy przepełnienia, użytkownik kliknie przycisk przepełnienie i elementy są wyświetlane w oknie podręcznym poniżej <xref:System.Windows.Controls.ToolBar>. Poniżej przedstawiono graficzne <xref:System.Windows.Controls.ToolBar> z elementami przepełnienia.  
  
 ![Pasek narzędzi z przepełnienie](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
Pasek narzędzi z elementami przepełnienia  
  
 Można określić, kiedy element na pasku narzędzi jest umieszczony na panelu przepełnienia przez ustawienie <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> dołączona właściwość do <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, lub <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. W poniższym przykładzie określono, że cztery ostatnie przycisków na pasku narzędzi zawsze powinna znajdować się na panelu przepełnienia.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> Używa <xref:System.Windows.Controls.Primitives.ToolBarPanel> i <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> w jego <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> Jest odpowiedzialny za układ elementów na pasku narzędzi.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> Jest odpowiedzialny za układ elementów, które nie mieszczą się na <xref:System.Windows.Controls.ToolBar>. Przykład <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ToolBar>, zobacz  
  
 [Style paska narzędzi i szablony](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [Kontrolki stylu na pasku ToolBar](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [Przykładu z galerii formantów WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
