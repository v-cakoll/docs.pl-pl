---
title: Przegląd Menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 4c3e8398ad058c50df535fea88dd9f366b7f24ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557605"
---
# <a name="menu-overview"></a>Przegląd Menu
<xref:System.Windows.Controls.Menu> Klasa umożliwia organizowanie elementów, skojarzonego z poleceniami i obsługi zdarzeń w porządku hierarchicznym. Każdy <xref:System.Windows.Controls.Menu> element zawiera kolekcję <xref:System.Windows.Controls.MenuItem> elementów.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Formant menu  
 <xref:System.Windows.Controls.Menu> Kontroli Wyświetla listę elementów, które Określ opcje dla aplikacji lub polecenia. Zwykle, klikając pozycję <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja do wykonania polecenia.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Tworzenie menu  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> do manipulowania tekstu w <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> Zawiera <xref:System.Windows.Controls.MenuItem> obiekty używające <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, i <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości i <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, i <xref:System.Windows.Controls.MenuItem.Click> zdarzenia.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Elementy MenuItem za pomocą skrótów klawiaturowych  
 Skróty klawiaturowe są kombinacji znaków, które mogą być wprowadzane z klawiatury do wywołania <xref:System.Windows.Controls.Menu> poleceń. Na przykład skrót **kopiowania** jest klawisze CTRL + C. Istnieją dwie właściwości do użycia z skróty klawiaturowe i elementy menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> lub <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> właściwość do przypisania tekst skrótów klawiaturowych do <xref:System.Windows.Controls.MenuItem> kontrolki. Skrót klawiaturowy zostanie tylko umieszczone w elemencie menu.  Kojarzy polecenie z <xref:System.Windows.Controls.MenuItem>. Aplikacja musi obsługiwać danych wejściowych użytkownika do wykonania akcji.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Polecenie  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.MenuItem.Command%2A> właściwość do skojarzenia **Otwórz** i **zapisać** poleceń z <xref:System.Windows.Controls.MenuItem> formantów. Nie tylko właściwość polecenia skojarzyć polecenie ze <xref:System.Windows.Controls.MenuItem>, ale zawiera także tekst wejściowy gestu do użycia jako skrót.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> Klasa ma również <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> właściwość, która określa, gdzie występuje polecenie elementu. Jeśli <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiona, element, który ma fokus klawiatury odbierze polecenie. Aby uzyskać więcej informacji na temat poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Style menu  
 Z stylów formantu, można znacznie zmienić wygląd i zachowanie <xref:System.Windows.Controls.Menu> formanty bez konieczności pisania kontrolkę niestandardową. Poza ustawieniem właściwości wizualnego, można także zastosować <xref:System.Windows.Style> do poszczególnych części kontrolki, zmianę zachowania części sterowanie za pośrednictwem właściwości, lub Dodaj dodatkowe części lub zmienianie układu formantu. W poniższych przykładach pokazano kilka sposobów, aby dodać <xref:System.Windows.Style> do <xref:System.Windows.Controls.Menu> formantu.  
  
 W pierwszym przykładzie kodu definiuje <xref:System.Windows.Style> o nazwie `Simple` który przedstawia sposób użycia bieżące ustawienia systemu swojego stylu. Kod przypisuje kolor `MenuHighlightBrush` jako kolor tła menu i `MenuTextBrush` jako menu Kolor pierwszego planu. Zwróć uwagę, użyj klawiszy zasobów można przypisać Pędzle.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Następujące przykładowe używa <xref:System.Windows.Trigger> elementy, które pozwalają zmienić wygląd <xref:System.Windows.Controls.MenuItem> w odpowiedzi na zdarzenia występujące w <xref:System.Windows.Controls.Menu>. Gdy wskaźnik myszy przesuwa się nad <xref:System.Windows.Controls.Menu>, kolor pierwszego planu i właściwości czcionki elementów menu, zmienić.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładu z galerii formantów WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
