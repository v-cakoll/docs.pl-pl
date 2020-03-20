---
title: Przegląd Menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186973"
---
# <a name="menu-overview"></a>Przegląd Menu
Klasa <xref:System.Windows.Controls.Menu> umożliwia organizowanie elementów skojarzonych z poleceniami i programami obsługi zdarzeń w kolejności hierarchicznej. Każdy <xref:System.Windows.Controls.Menu> element zawiera <xref:System.Windows.Controls.MenuItem> kolekcję elementów.  

<a name="menu_control"></a>
## <a name="menu-control"></a>Sterowanie menu  
 Formant <xref:System.Windows.Controls.Menu> przedstawia listę elementów, które określają polecenia lub opcje dla aplikacji. Zazwyczaj kliknięcie podmenu <xref:System.Windows.Controls.MenuItem> powoduje, że aplikacja wykonuje polecenie.  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>Tworzenie menu  
 Poniższy przykład <xref:System.Windows.Controls.Menu> tworzy do manipulowania <xref:System.Windows.Controls.TextBox>tekstem w . Zawiera <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.MenuItem> obiekty, które <xref:System.Windows.Controls.MenuItem.Command%2A> <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>używają <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> , , <xref:System.Windows.Controls.MenuItem.Checked>i <xref:System.Windows.Controls.MenuItem.Unchecked>właściwości <xref:System.Windows.Controls.MenuItem.Click> i , , i zdarzenia.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems ze skrótami klawiaturowymi  
 Skróty klawiaturowe to kombinacje znaków, które można <xref:System.Windows.Controls.Menu> wprowadzić za pomocą klawiatury w celu wywołania poleceń. Na przykład skrót do **kopiowania** to CTRL+C. Istnieją dwie właściwości do użycia ze skrótami<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> klawiaturowymi i elementami menu — lub <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>Tekst InputGestureText  
 W poniższym przykładzie <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> pokazano, jak używać <xref:System.Windows.Controls.MenuItem> właściwości do przypisywania tekstu skrótu klawiaturowego do formantów. Spowoduje to tylko umieszczanie skrótu klawiaturowego w elemencie menu.  Nie kojarzy polecenia z <xref:System.Windows.Controls.MenuItem>. Aplikacja musi obsługiwać dane wejściowe użytkownika w celu przeprowadzenia akcji.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>Polecenie  
 W poniższym przykładzie <xref:System.Windows.Controls.MenuItem.Command%2A> pokazano, jak używać właściwości do <xref:System.Windows.Controls.MenuItem> skojarzenia poleceń **Otwórz** i **Zapisz** z formantami. Właściwość polecenia nie tylko kojarzy <xref:System.Windows.Controls.MenuItem>polecenie z programem , ale także dostarcza tekst gestu wejściowego do użycia jako skrót.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 Klasa <xref:System.Windows.Controls.MenuItem> ma również <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> właściwość, która określa element, w którym występuje polecenie. Jeśli <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiona, element, który ma fokus klawiatury odbiera polecenie. Aby uzyskać więcej informacji o poleceniach, zobacz [Omówienie poleceń](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>Styl menu  
 Dzięki stylowi sterowania można radykalnie zmienić <xref:System.Windows.Controls.Menu> wygląd i zachowanie formantów bez konieczności pisania elementów sterujących. Oprócz ustawiania właściwości wizualnych, można <xref:System.Windows.Style> również zastosować do poszczególnych części formantu, zmienić zachowanie części formantu za pomocą właściwości lub dodać dodatkowe części lub zmienić układ formantu. Poniższe przykłady pokazują kilka <xref:System.Windows.Style> sposobów, <xref:System.Windows.Controls.Menu> aby dodać do formantu.  
  
 Pierwszy przykład kodu definiuje <xref:System.Windows.Style> `Simple` wywołanie, który pokazuje, jak używać bieżących ustawień systemowych w stylu. Kod przypisuje kolor `MenuHighlightBrush` jako kolor tła menu i `MenuTextBrush` kolor pierwszego planu menu. Należy zauważyć, że używasz kluczy zasobów, aby przypisać pędzle.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 W poniższym <xref:System.Windows.Trigger> przykładzie użyto elementów, <xref:System.Windows.Controls.MenuItem> które umożliwiają zmianę wyglądu <xref:System.Windows.Controls.Menu>w odpowiedzi na zdarzenia występujące w programie . Po przesunięciu <xref:System.Windows.Controls.Menu>wskaźnika myszy na kolor pierwszego planu i charakterystyki czcionek elementów menu zmieniają się.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Przykład galerii kontrolek WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
