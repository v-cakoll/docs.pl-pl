---
title: "Jak wyświetlić zawartość ListView przy użyciu GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24560a1e9b663a3145b589b5a03af8a8b72236ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Omówienie widoku GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
