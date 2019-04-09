---
title: 'Instrukcje: Używanie niestandardowego menu kontekstowego z kontrolką TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129419"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Instrukcje: Używanie niestandardowego menu kontekstowego z kontrolką TextBox
W tym przykładzie pokazano, jak definiować ani implementować menu kontekstowego proste dla <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie zdefiniowano <xref:System.Windows.Controls.TextBox> formant, który zawiera menu kontekstowego.  
  
 Menu kontekstowe jest definiowana za pomocą <xref:System.Windows.Controls.ContextMenu> elementu.  Menu kontekstowe, sama składa się z szeregu <xref:System.Windows.Controls.MenuItem> elementy i <xref:System.Windows.Controls.Separator> elementów.  Każdy <xref:System.Windows.Controls.MenuItem> element definiuje polecenie w menu kontekstowym; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atrybut definiuje wyświetlany tekst dla polecenia menu i <xref:System.Windows.Controls.MenuItem.Click> atrybut określa metodę programu obsługi dla każdego elementu menu.  <xref:System.Windows.Controls.Separator> Elementu powoduje po prostu oddzielający wiersza do renderowania między elementami menu poprzednie i kolejne.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kod implementacji dla poprzedniego definicji menu kontekstowe, a także kod, który włącza i wyłącza menu kontekstowe.  <xref:System.Windows.Controls.ContextMenu.Opened> Zdarzeń służy do dynamiczne Włączanie lub wyłączanie niektórych poleceń w zależności od bieżącego stanu <xref:System.Windows.Controls.TextBox>.  
  
 Aby przywrócić ustawienia domyślne menu kontekstowe, użyj <xref:System.Windows.DependencyObject.ClearValue%2A> metodę, aby wyczyścić wartości <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwości.  Aby całkowicie wyłączyć menu kontekstowe, ustaw <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwość odwołanie o wartości null (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie sprawdzania pisowni z menu kontekstowym](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
