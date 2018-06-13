---
title: Jak użyć niestandardowego menu kontekstowego za pomocą TextBox
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
ms.openlocfilehash: edcf6bdf381ae51a3354f9bc0b3c91d86e1f8f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552782"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Jak użyć niestandardowego menu kontekstowego za pomocą TextBox
W tym przykładzie pokazano, jak definiować i wdrażać menu kontekstowe niestandardowych proste <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie zdefiniowano <xref:System.Windows.Controls.TextBox> formant, który zawiera menu kontekstowe niestandardowych.  
  
 Menu kontekstowe jest definiowana za pomocą <xref:System.Windows.Controls.ContextMenu> elementu.  Menu kontekstowe sam składa się z szeregu <xref:System.Windows.Controls.MenuItem> elementów i <xref:System.Windows.Controls.Separator> elementy.  Każdy <xref:System.Windows.Controls.MenuItem> element definiuje polecenia w menu kontekstowym; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atrybut określa tekst wyświetlany dla polecenia menu i <xref:System.Windows.Controls.MenuItem.Click> atrybut określa metodę obsługi dla każdego elementu menu.  <xref:System.Windows.Controls.Separator> Elementu powoduje po prostu oddzielający linię, aby być renderowane między elementami poprzednich i następnych menu.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kod implementacji dla poprzedniego definicji menu kontekstowe, a także kod, który włącza i wyłącza menu kontekstowego.  <xref:System.Windows.Controls.ContextMenu.Opened> Zdarzeń umożliwia dynamiczne Włączanie lub wyłączanie niektórych poleceń, w zależności od bieżącego stanu <xref:System.Windows.Controls.TextBox>.  
  
 Aby przywrócić ustawienia domyślne menu kontekstowe, użyj <xref:System.Windows.DependencyObject.ClearValue%2A> metodę, aby wyczyścić wartość <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwości.  Aby całkowicie wyłączyć menu kontekstowego, ustaw <xref:System.Windows.FrameworkElement.ContextMenu%2A> odwołanie o wartości null dla właściwości (`Nothing` w języku Visual Basic).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie sprawdzania pisowni z menu kontekstowym](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
