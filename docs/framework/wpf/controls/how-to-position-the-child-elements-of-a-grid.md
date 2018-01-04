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
ms.workload: dotnet
ms.openlocfilehash: 0ca385e1aee10fb10ac3e912999aec3a11d03ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
