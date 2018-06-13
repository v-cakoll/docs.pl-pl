---
title: Jak wyświetlić zawartość ListView przy użyciu GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554054"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Jak wyświetlić zawartość ListView przy użyciu GridView
W tym przykładzie pokazano sposób definiowania <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> formantu.  
  
## <a name="example"></a>Przykład  
 Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów. Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.GridViewColumn> obiektów, które powiązania do określonego dla zawartości danych <xref:System.Windows.Controls.ListView> formantu. To <xref:System.Windows.Controls.GridView> przykładzie trzy <xref:System.Windows.Controls.GridViewColumn> obiektów, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest ustawiony jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> formantu.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Na poniższej ilustracji przedstawiono sposób wyświetlania w tym przykładzie.  
  
 ![Element ListView z danych wyjściowych w widoku GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
