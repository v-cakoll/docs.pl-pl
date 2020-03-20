---
title: Jak ustawić położenie elementów podrzędnych siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186719"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Jak ustawić położenie elementów podrzędnych siatki
W tym przykładzie pokazano, jak używać get <xref:System.Windows.Controls.Grid> i set metody, które są zdefiniowane na położenie elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje <xref:System.Windows.Controls.Grid> element`grid1`nadrzędny ( ), który ma trzy kolumny i trzy wiersze. Element <xref:System.Windows.Shapes.Rectangle> podrzędny`rect1`( ) <xref:System.Windows.Controls.Grid> jest dodawany do pozycji w kolumnie zero, pozycja wiersza zero. <xref:System.Windows.Controls.Button>elementy reprezentują metody, które mogą <xref:System.Windows.Shapes.Rectangle> być wywoływane w celu zmiany położenia elementu w . <xref:System.Windows.Controls.Grid> Gdy użytkownik kliknie przycisk, powiązana metoda jest aktywowana.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Poniższy przykład związany z kodem obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> metody, które podnieść zdarzenia przycisku. W przykładzie zapisuje <xref:System.Windows.Controls.TextBlock> te wywołania metody do elementów, które używają powiązanych get metody do wysuwania nowych wartości właściwości jako ciągi.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Oto gotowy wynik!

 ![zrzut ekranu przedstawia interfejs użytkownika WPF z dwiema kolumnami, po prawej stronie ma siatkę 3 x 3, a po lewej ma przyciski do przenoszenia kolorowego prostokąta między kolumnami i wierszami siatki](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Grid>
- [Przegląd Panele](panels-overview.md)
