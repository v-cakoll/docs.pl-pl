---
title: 'Instrukcje: Wyświetl zawartość ListView przy użyciu GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 0e2b37cb061cc92b34c3a4f94bcd42e8ffc69ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606010"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Instrukcje: Wyświetl zawartość ListView przy użyciu GridView
Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridView> tryb widoku dla <xref:System.Windows.Controls.ListView> kontroli.  
  
## <a name="example"></a>Przykład  
 Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów. Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridViewColumn> obiektów, które należy powiązać zawartość danych, który jest określony dla <xref:System.Windows.Controls.ListView> kontroli. To <xref:System.Windows.Controls.GridView> przykład określa trzy <xref:System.Windows.Controls.GridViewColumn> obiekty, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest skonfigurowany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> kontroli.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Poniższa ilustracja przedstawia, jak pojawia się w tym przykładzie.  
  
 ![ListView z danymi wyjściowymi GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
