---
title: Przegląd Menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124653"
---
# <a name="menu-overview"></a>Przegląd Menu
Klasa <xref:System.Windows.Controls.Menu> umożliwia organizowanie elementów skojarzonych z poleceniami i programami obsługi zdarzeń w kolejności hierarchicznej. Każdy element <xref:System.Windows.Controls.Menu> zawiera kolekcję elementów <xref:System.Windows.Controls.MenuItem>.  

<a name="menu_control"></a>   
## <a name="menu-control"></a>Kontrolka menu  
 Formant <xref:System.Windows.Controls.Menu> przedstawia listę elementów, które określają polecenia lub opcje dla aplikacji. Zazwyczaj kliknięcie <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja wykonuje polecenie.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Tworzenie menu  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> do manipulowania tekstem w <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> zawiera <xref:System.Windows.Controls.MenuItem> obiektów, które używają właściwości <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>i <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> oraz zdarzeń <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>i <xref:System.Windows.Controls.MenuItem.Click>.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Elementy MenuItems ze skrótami klawiaturowymi  
 Skróty klawiaturowe to kombinacje znaków, które można wprowadzić przy użyciu klawiatury, aby wywołać polecenia <xref:System.Windows.Controls.Menu>. Na przykład skrót do **kopii** to CTRL + C. Istnieją dwie właściwości do użycia ze skrótami klawiaturowymi i elementami menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> lub <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Poniższy przykład pokazuje, jak używać właściwości <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> do przypisywania tekstu skrótu klawiaturowego do kontrolek <xref:System.Windows.Controls.MenuItem>. Spowoduje to jedynie umieszczenie skrótu klawiaturowego w elemencie menu.  Nie kojarzy polecenia z <xref:System.Windows.Controls.MenuItem>. Aplikacja musi obsłużyć dane wejściowe użytkownika w celu wykonania akcji.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Polecenie  
 W poniższym przykładzie pokazano, jak za pomocą właściwości <xref:System.Windows.Controls.MenuItem.Command%2A> skojarzyć polecenia **Otwórz** i **Zapisz** z kontrolkami <xref:System.Windows.Controls.MenuItem>. Właściwość Command kojarzy polecenie z <xref:System.Windows.Controls.MenuItem>, ale udostępnia również tekst gestu wejściowego, który ma być używany jako skrót.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 Klasa <xref:System.Windows.Controls.MenuItem> ma również właściwość <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>, która określa element, w którym występuje polecenie. Jeśli <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiona, element, który ma fokus klawiatury otrzymuje polecenie. Aby uzyskać więcej informacji na temat poleceń, zobacz [Omówienie poleceń](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Style menu  
 Za pomocą stylów kontrolek można znacząco zmienić wygląd i zachowanie formantów <xref:System.Windows.Controls.Menu> bez konieczności pisania kontrolki niestandardowej. Oprócz ustawiania właściwości wizualnych, można również zastosować <xref:System.Windows.Style> do poszczególnych części kontrolki, zmienić zachowanie części kontrolki za pomocą właściwości lub dodać dodatkowe części albo zmienić układ formantu. W poniższych przykładach pokazano kilka sposobów dodawania <xref:System.Windows.Style> do kontrolki <xref:System.Windows.Controls.Menu>.  
  
 Pierwszy przykład kodu definiuje <xref:System.Windows.Style> o nazwie `Simple`, który pokazuje, jak używać bieżących ustawień systemu w stylu. Kod przypisuje kolor `MenuHighlightBrush` jako kolor tła menu i `MenuTextBrush` jako kolor pierwszego planu menu. Zwróć uwagę, że za pomocą kluczy zasobów można przypisać pędzle.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Poniższy przykład używa elementów <xref:System.Windows.Trigger>, które umożliwiają zmianę wyglądu <xref:System.Windows.Controls.MenuItem> w odpowiedzi na zdarzenia występujące w <xref:System.Windows.Controls.Menu>. Po przesunięciu wskaźnika myszy nad <xref:System.Windows.Controls.Menu>, kolor pierwszego planu i charakterystyka czcionki elementów menu.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Przykład galerii formantów WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
