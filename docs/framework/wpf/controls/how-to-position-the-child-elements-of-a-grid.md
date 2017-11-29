---
title: "Jak ustawić położenie elementów podrzędnych siatki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dbe0bcb5d3c46edcb97410e00832f1b9d6205b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Jak ustawić położenie elementów podrzędnych siatki
W tym przykładzie pokazano, jak użyć get i ustawić metody, które są zdefiniowane na <xref:System.Windows.Controls.Grid> położenie elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano nadrzędne <xref:System.Windows.Controls.Grid> elementu (`grid1`) zawierającej trzy kolumny i trzy wiersze. Element podrzędny <xref:System.Windows.Shapes.Rectangle> elementu (`rect1`) jest dodawany do <xref:System.Windows.Controls.Grid> kolumny pozycji zero, wiersz pozycji zero. <xref:System.Windows.Controls.Button>elementy reprezentują metod, które mogą być wywoływane w celu zmiany położenia <xref:System.Windows.Shapes.Rectangle> w elemencie <xref:System.Windows.Controls.Grid>. Gdy użytkownik kliknie przycisk, jest uaktywniony powiązanej metody.  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 W poniższym przykładzie kodu powiązanego obsługuje metody który przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> wywoływanie zdarzeń. W przykładzie polecenie zapisuje te wywołania metody do <xref:System.Windows.Controls.TextBlock> elementów powiązanych Użyj get metody zwracać wartości właściwości jako ciągi.  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)
