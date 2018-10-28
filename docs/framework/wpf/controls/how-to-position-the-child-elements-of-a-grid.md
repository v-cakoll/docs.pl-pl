---
title: Jak ustawić położenie elementów podrzędnych siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 5ccdcb3d166e1b703faff1dc8046e61ee213d12a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187000"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Jak ustawić położenie elementów podrzędnych siatki
W tym przykładzie pokazano, jak użyć i ustaw metody, które są zdefiniowane na <xref:System.Windows.Controls.Grid> położenie elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano element nadrzędny <xref:System.Windows.Controls.Grid> — element (`grid1`) ma trzy kolumny i trzy wiersze. Element podrzędny <xref:System.Windows.Shapes.Rectangle> — element (`rect1`) jest dodawany do <xref:System.Windows.Controls.Grid> w kolumnie pozycji zero, wiersz pozycji zero. <xref:System.Windows.Controls.Button> elementy reprezentują metod, które mogą być wywoływane w celu zmiany położenia <xref:System.Windows.Shapes.Rectangle> elemencie <xref:System.Windows.Controls.Grid>. Gdy użytkownik kliknie przycisk, jest ono aktywowane powiązanej metody.  
  
 [!code-xaml[gridGetSetMethods](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 W poniższym przykładzie związanym z kodem obsługuje metody, przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zgłaszać zdarzenia. W przykładzie polecenie zapisuje te wywołania metody do <xref:System.Windows.Controls.TextBlock> elementy, które są związane z użycia metod get na dane wyjściowe nowe wartości właściwości jako ciągi.  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 W tym miejscu jest wynikiem gotowe!
 
 ![Zrzut ekranu przedstawia interfejs użytkownika WPF z dwiema kolumnami, po prawej stronie ma siatka 3 x 3, a po lewej stronie przycisków, aby przenieść jako kolorowy prostokąt między kolumnami i wierszami siatki](./media/grid-methods-sample.png) 
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
