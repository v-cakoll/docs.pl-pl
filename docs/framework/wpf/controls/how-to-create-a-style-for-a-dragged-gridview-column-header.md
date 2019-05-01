---
title: 'Instrukcje: Tworzenie stylu dla przeciąganego nagłówka kolumny kontrolki GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dbcdd38e0397b8e637aff962420a2959f33203df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910887"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Instrukcje: Tworzenie stylu dla przeciąganego nagłówka kolumny kontrolki GridView
W tym przykładzie pokazano, jak zmienić wygląd przeciąganego <xref:System.Windows.Controls.GridViewColumnHeader> po użytkownik zmienia pozycję kolumny.  
  
## <a name="example"></a>Przykład  
 Przeciągnięcie nagłówka kolumny do innej lokalizacji w <xref:System.Windows.Controls.ListView> , który używa <xref:System.Windows.Controls.GridView> trybu wyświetlania, kolumna jest przenoszony do nowej pozycji. Gdy przeciągasz nagłówek kolumny, oprócz oryginalnego nagłówka pojawia się ruchomy kopię nagłówka. Nagłówek kolumny w <xref:System.Windows.Controls.GridView> jest reprezentowany przez <xref:System.Windows.Controls.GridViewColumnHeader> obiektu.  
  
 Aby dostosować wygląd zmiennoprzecinkowy a wersją z oryginalnego nagłówków, możesz ustawić <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> do modyfikowania <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Te <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> są stosowane po <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> wartość właściwości jest `true` i <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> wartość właściwości jest <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Gdy użytkownik naciśnie przycisk myszy i przechowuje w dół, gdy mysz <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> ulega zmianie wartość właściwości do `true`. Podobnie, gdy użytkownik rozpoczyna się operacja przeciągania <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> zmiany właściwości <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> zmienić <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.Background%2A> kolory nagłówków oryginalnego i zmiennoprzecinkowych, gdy użytkownik przeciągnie kolumny do nowej pozycji.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tematy z instrukcjami](listview-how-to-topics.md)
- [ListView — omówienie](listview-overview.md)
- [GridView — omówienie](gridview-overview.md)
