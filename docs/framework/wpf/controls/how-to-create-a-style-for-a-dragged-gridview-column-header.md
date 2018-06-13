---
title: Jak utworzyć styl dla przeciągniętego nagłówka kolumny GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 2e57b4cb1b8ddb90e8e6e0abc6db3e7f0b864cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554576"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Jak utworzyć styl dla przeciągniętego nagłówka kolumny GridView
W tym przykładzie pokazano, jak zmienić wygląd przeciąganego <xref:System.Windows.Controls.GridViewColumnHeader> gdy użytkownik zmienia pozycję kolumny.  
  
## <a name="example"></a>Przykład  
 Przeciągnięcie nagłówka kolumny w inne miejsce <xref:System.Windows.Controls.ListView> używającą <xref:System.Windows.Controls.GridView> trybu widoku kolumny jest przenoszony do nowego położenia. W trakcie są przeciągnięcie nagłówka kolumny, oprócz oryginalny nagłówek jest wyświetlana kopię przestawne nagłówka. Nagłówek kolumny w <xref:System.Windows.Controls.GridView> jest reprezentowana przez <xref:System.Windows.Controls.GridViewColumnHeader> obiektu.  
  
 Aby dostosować wygląd zmiennoprzecinkowych i oryginalnego nagłówki, można ustawić <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> do modyfikowania <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Te <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> są stosowane po <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> wartość właściwości jest `true` i <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> wartość właściwości jest <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Gdy użytkownik naciśnie przycisk myszy i zawiera, gdy wskaźnik myszy zatrzyma się w <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> zmiany wartości właściwości na `true`. Podobnie, gdy użytkownik rozpoczyna operację przeciągania <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> zmiany właściwości <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> zmienić <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.Background%2A> kolory nagłówków oryginalny i przestawne, gdy użytkownik przeciąga kolumny do nowej pozycji.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)
