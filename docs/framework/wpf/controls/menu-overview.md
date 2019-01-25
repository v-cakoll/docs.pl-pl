---
title: Przegląd Menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: b1f3889803ba681542349443276041d312293bcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626878"
---
# <a name="menu-overview"></a>Przegląd Menu
<xref:System.Windows.Controls.Menu> Klasy pozwala organizować elementy związane z poleceniami i procedury obsługi zdarzeń w kolejności hierarchicznej. Każdy <xref:System.Windows.Controls.Menu> element zawiera zbiór <xref:System.Windows.Controls.MenuItem> elementów.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Formant menu  
 <xref:System.Windows.Controls.Menu> Kontrolka Wyświetla listę elementów, które określają polecenia i opcje dla aplikacji. Zazwyczaj kliknięcie <xref:System.Windows.Controls.MenuItem> spowoduje otwarcie podmenu lub powoduje, że aplikacja do wykonania polecenia.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Tworzenie menu  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> do manipulowania tekstem w <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> Zawiera <xref:System.Windows.Controls.MenuItem> obiektów używających <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, i <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości i <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, i <xref:System.Windows.Controls.MenuItem.Click> zdarzenia.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Vlastnost MenuItems za pomocą skrótów klawiaturowych  
 Skróty klawiaturowe są kombinacje znaków, które mogą być wprowadzane z klawiatury do wywołania <xref:System.Windows.Controls.Menu> poleceń. Na przykład skrót do **kopiowania** jest klawisze CTRL + C. Istnieją dwie właściwości, za pomocą skrótów klawiaturowych z elementami menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> lub <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> właściwości, aby przypisać tekst skrótów klawiaturowych do <xref:System.Windows.Controls.MenuItem> kontrolki. Skrót klawiaturowy zostanie tylko umieszcza w elemencie menu.  Kojarzy polecenie <xref:System.Windows.Controls.MenuItem>. Aplikacja musi obsłużyć dane wejściowe użytkownika do wykonania akcji.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Polecenie  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.MenuItem.Command%2A> właściwość do skojarzenia **Otwórz** i **Zapisz** poleceń z <xref:System.Windows.Controls.MenuItem> kontrolki. Nie tylko właściwość polecenia Skojarz polecenia za pomocą <xref:System.Windows.Controls.MenuItem>, ale także dostarcza tekst wejściowy gestu do użycia jako skrót.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> Ma również klasy <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> właściwość, która określa element, gdzie występuje polecenie. Jeśli <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiony, element, który ma fokus klawiatury odbierze polecenie. Aby uzyskać więcej informacji na temat poleceń, zobacz [polecenia Przegląd](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Style menu  
 Nadawanie stylów kontrolek, można znacznie zmieniać wygląd i zachowanie <xref:System.Windows.Controls.Menu> formantów bez konieczności pisania niestandardowego formantu. Poza ustawieniem właściwości wizualnego, można także zastosować <xref:System.Windows.Style> do poszczególnych części kontrolkę, zmienić zachowanie części kontrolki za pomocą właściwości, Dodaj dodatkowe elementy lub zmienianie układu formantu. W poniższych przykładach pokazano kilka sposobów dodawania <xref:System.Windows.Style> do <xref:System.Windows.Controls.Menu> kontroli.  
  
 W pierwszym przykładzie kodu definiuje <xref:System.Windows.Style> o nazwie `Simple` który ilustruje sposób używania ustawień systemu swojego stylu. Kod przypisuje kolor `MenuHighlightBrush` jako menu Kolor tła i `MenuTextBrush` jako menu Kolor pierwszego planu. Zwróć uwagę, przy użyciu kluczy zasobu można przypisać Pędzle.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Następujące przykładowe używa <xref:System.Windows.Trigger> elementy, które pozwalają na zmianę wyglądu <xref:System.Windows.Controls.MenuItem> w odpowiedzi na zdarzenia występujące na <xref:System.Windows.Controls.Menu>. Po przesunięciu myszy <xref:System.Windows.Controls.Menu>, kolor pierwszego planu i cech czcionki elementów menu, zmienić.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Przykładu z galerii kontrolki WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
