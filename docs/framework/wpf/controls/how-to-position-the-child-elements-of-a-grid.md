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
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="3e117-102">Jak ustawić położenie elementów podrzędnych siatki</span><span class="sxs-lookup"><span data-stu-id="3e117-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="3e117-103">W tym przykładzie pokazano, jak używać get <xref:System.Windows.Controls.Grid> i set metody, które są zdefiniowane na położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3e117-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e117-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e117-104">Example</span></span>  
 <span data-ttu-id="3e117-105">Poniższy przykład definiuje <xref:System.Windows.Controls.Grid> element`grid1`nadrzędny ( ), który ma trzy kolumny i trzy wiersze.</span><span class="sxs-lookup"><span data-stu-id="3e117-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="3e117-106">Element <xref:System.Windows.Shapes.Rectangle> podrzędny`rect1`( ) <xref:System.Windows.Controls.Grid> jest dodawany do pozycji w kolumnie zero, pozycja wiersza zero.</span><span class="sxs-lookup"><span data-stu-id="3e117-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="3e117-107"><xref:System.Windows.Controls.Button>elementy reprezentują metody, które mogą <xref:System.Windows.Shapes.Rectangle> być wywoływane w celu zmiany położenia elementu w . <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="3e117-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="3e117-108">Gdy użytkownik kliknie przycisk, powiązana metoda jest aktywowana.</span><span class="sxs-lookup"><span data-stu-id="3e117-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="3e117-109">Poniższy przykład związany z kodem obsługuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> metody, które podnieść zdarzenia przycisku.</span><span class="sxs-lookup"><span data-stu-id="3e117-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="3e117-110">W przykładzie zapisuje <xref:System.Windows.Controls.TextBlock> te wywołania metody do elementów, które używają powiązanych get metody do wysuwania nowych wartości właściwości jako ciągi.</span><span class="sxs-lookup"><span data-stu-id="3e117-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="3e117-111">Oto gotowy wynik!</span><span class="sxs-lookup"><span data-stu-id="3e117-111">Here is the finished result!</span></span>

 ![zrzut ekranu przedstawia interfejs użytkownika WPF z dwiema kolumnami, po prawej stronie ma siatkę 3 x 3, a po lewej ma przyciski do przenoszenia kolorowego prostokąta między kolumnami i wierszami siatki](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="3e117-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e117-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="3e117-114">Przegląd Panele</span><span class="sxs-lookup"><span data-stu-id="3e117-114">Panels Overview</span></span>](panels-overview.md)
