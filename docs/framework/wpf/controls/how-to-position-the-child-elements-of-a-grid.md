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
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="1735e-103">Jak ustawić położenie elementów podrzędnych siatki</span><span class="sxs-lookup"><span data-stu-id="1735e-103">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="1735e-104">Ten przykład pokazuje, jak używać metod get i Set, które są zdefiniowane w, <xref:System.Windows.Controls.Grid> Aby pozycjonować elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="1735e-104">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1735e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1735e-105">Example</span></span>  
 <span data-ttu-id="1735e-106">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Grid> element nadrzędny ( `grid1` ), który ma trzy kolumny i trzy wiersze.</span><span class="sxs-lookup"><span data-stu-id="1735e-106">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="1735e-107">Element podrzędny <xref:System.Windows.Shapes.Rectangle> ( `rect1` ) zostanie dodany do <xref:System.Windows.Controls.Grid> kolumny w kolumnie w pozycji zero, pozycja wiersza zero.</span><span class="sxs-lookup"><span data-stu-id="1735e-107">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="1735e-108"><xref:System.Windows.Controls.Button>elementy reprezentują metody, które mogą być wywoływane w celu zmiany położenia <xref:System.Windows.Shapes.Rectangle> elementu w <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="1735e-108"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="1735e-109">Gdy użytkownik kliknie przycisk, powiązana Metoda zostanie aktywowana.</span><span class="sxs-lookup"><span data-stu-id="1735e-109">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="1735e-110">Poniższy kod służy do obsługi metod <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zgłaszanych przez zdarzenia przycisku.</span><span class="sxs-lookup"><span data-stu-id="1735e-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="1735e-111">Przykład zapisuje te wywołania metody do <xref:System.Windows.Controls.TextBlock> elementów, które używają pokrewnych metod get do wyprowadzania nowych wartości właściwości jako ciągi.</span><span class="sxs-lookup"><span data-stu-id="1735e-111">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="1735e-112">Oto gotowy wynik!</span><span class="sxs-lookup"><span data-stu-id="1735e-112">Here is the finished result!</span></span>

 ![zrzut ekranu przedstawia interfejs użytkownika WPF z dwiema kolumnami, po prawej stronie znajduje się siatka 3 x 3, a lewa ma przyciski do przenoszenia kolorowego prostokąta między kolumnami i wierszami siatki](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="1735e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1735e-114">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="1735e-115">Przegląd Panele</span><span class="sxs-lookup"><span data-stu-id="1735e-115">Panels Overview</span></span>](panels-overview.md)
