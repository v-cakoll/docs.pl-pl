---
title: Przegląd Style nagłówka kolumn i szablonów GridView
ms.date: 03/30/2017
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
ms.openlocfilehash: 83643d8acea706bad439683702e4228d240b97bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911368"
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>Przegląd Style nagłówka kolumn i szablonów GridView
To omówienie dotyczy kolejność pierwszeństwa dla właściwości, które umożliwia dostosowywanie nagłówek kolumny w <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> kontroli.  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>Dostosowywanie nagłówka kolumny w widoku GridView  
 Właściwości, które definiują, zawartość, układu i stylu Nagłówek kolumny w <xref:System.Windows.Controls.GridView> znajdują się na wiele powiązanych klas. Niektóre z tych właściwości mają funkcje, które są podobne lub taka sama.  
  
 Wiersze w tabeli poniżej pokazano grup właściwości, które pełnią taką samą funkcję. Te właściwości umożliwia dostosowywanie nagłówków kolumn w <xref:System.Windows.Controls.GridView>. Kolejność pierwszeństwa powiązane właściwości jest od prawej do lewej, gdy właściwość najdalej z prawej kolumnie ma najwyższy priorytet. Na przykład jeśli <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> jest ustawiona na <xref:System.Windows.Controls.GridViewColumnHeader> obiektu i <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> jest ustawiona na skojarzonej <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ma pierwszeństwo. W tym scenariuszu <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> nie ma wpływu.  
  
 **Powiązane właściwości dla nagłówków kolumn w kontrolce GridView**  
  
|||||  
|-|-|-|-|  
|**Klasy**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**Właściwości Menu kontekstowego**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|Nie dotyczy|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**Etykietka narzędzia**<br /><br /> **Właściwości**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|Nie dotyczy|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**Szablon nagłówka**<br /><br /> **Właściwości**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**Właściwości stylu**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>dla **właściwości szablonu nagłówka**, jeśli ustawisz szablonu i właściwości selektor szablonu, właściwości szablonu pierwszeństwo. Na przykład jeśli ustawisz zarówno <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> właściwości <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwość, pierwszeństwo.  
  
## <a name="see-also"></a>Zobacz także

- [Tematy z instrukcjami](listview-how-to-topics.md)
- [ListView — omówienie](listview-overview.md)
- [GridView — omówienie](gridview-overview.md)
