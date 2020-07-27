---
title: Jak ustawić położenie elementów podrzędnych siatki
description: Dowiedz się, jak używać metod get i Set, które są zdefiniowane na siatce Windows Presentation Foundation, aby pozycjonować elementy podrzędne.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167389"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Jak ustawić położenie elementów podrzędnych siatki
Ten przykład pokazuje, jak używać metod get i Set, które są zdefiniowane w, <xref:System.Windows.Controls.Grid> Aby pozycjonować elementy podrzędne.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Grid> element nadrzędny ( `grid1` ), który ma trzy kolumny i trzy wiersze. Element podrzędny <xref:System.Windows.Shapes.Rectangle> ( `rect1` ) zostanie dodany do <xref:System.Windows.Controls.Grid> kolumny w kolumnie w pozycji zero, pozycja wiersza zero. <xref:System.Windows.Controls.Button>elementy reprezentują metody, które mogą być wywoływane w celu zmiany położenia <xref:System.Windows.Shapes.Rectangle> elementu w <xref:System.Windows.Controls.Grid> . Gdy użytkownik kliknie przycisk, powiązana Metoda zostanie aktywowana.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Poniższy kod służy do obsługi metod <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zgłaszanych przez zdarzenia przycisku. Przykład zapisuje te wywołania metody do <xref:System.Windows.Controls.TextBlock> elementów, które używają pokrewnych metod get do wyprowadzania nowych wartości właściwości jako ciągi.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Oto gotowy wynik!

 ![zrzut ekranu przedstawia interfejs użytkownika WPF z dwiema kolumnami, po prawej stronie znajduje się siatka 3 x 3, a lewa ma przyciski do przenoszenia kolorowego prostokąta między kolumnami i wierszami siatki](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Grid>
- [Przegląd Panele](panels-overview.md)
