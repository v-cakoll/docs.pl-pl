---
title: 'Instrukcje: Wyświetlanie zawartości kontrolki ListView przy użyciu kontrolki GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9b467c95d541c326a41d1ed4bd9eb5c87e25bd5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910497"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Instrukcje: Wyświetlanie zawartości kontrolki ListView przy użyciu kontrolki GridView
Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridView> tryb widoku dla <xref:System.Windows.Controls.ListView> kontroli.  
  
## <a name="example"></a>Przykład  
 Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów. Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridViewColumn> obiektów, które należy powiązać zawartość danych, który jest określony dla <xref:System.Windows.Controls.ListView> kontroli. To <xref:System.Windows.Controls.GridView> przykład określa trzy <xref:System.Windows.Controls.GridViewColumn> obiekty, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest skonfigurowany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> kontroli.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Poniższa ilustracja przedstawia, jak pojawia się w tym przykładzie.  
  
 ![Zrzut ekranu pokazujący ListView z danymi wyjściowymi GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView — omówienie](listview-overview.md)
- [GridView — omówienie](gridview-overview.md)
- [Tematy z instrukcjami](listview-how-to-topics.md)
