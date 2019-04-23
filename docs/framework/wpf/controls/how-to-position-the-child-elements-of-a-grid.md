---
title: 'Instrukcje: Ustawianie położenia elementów podrzędnych siatki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: c508f45c1ea3d0925503d6fe5600498a0558d5ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202992"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="88e4b-102">Instrukcje: Ustawianie położenia elementów podrzędnych siatki</span><span class="sxs-lookup"><span data-stu-id="88e4b-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="88e4b-103">W tym przykładzie pokazano, jak użyć i ustaw metody, które są zdefiniowane na <xref:System.Windows.Controls.Grid> położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="88e4b-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e4b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="88e4b-104">Example</span></span>  
 <span data-ttu-id="88e4b-105">W poniższym przykładzie zdefiniowano element nadrzędny <xref:System.Windows.Controls.Grid> — element (`grid1`) ma trzy kolumny i trzy wiersze.</span><span class="sxs-lookup"><span data-stu-id="88e4b-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="88e4b-106">Element podrzędny <xref:System.Windows.Shapes.Rectangle> — element (`rect1`) jest dodawany do <xref:System.Windows.Controls.Grid> w kolumnie pozycji zero, wiersz pozycji zero.</span><span class="sxs-lookup"><span data-stu-id="88e4b-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="88e4b-107"><xref:System.Windows.Controls.Button> elementy reprezentują metod, które mogą być wywoływane w celu zmiany położenia <xref:System.Windows.Shapes.Rectangle> elemencie <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="88e4b-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="88e4b-108">Gdy użytkownik kliknie przycisk, jest ono aktywowane powiązanej metody.</span><span class="sxs-lookup"><span data-stu-id="88e4b-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="88e4b-109">W poniższym przykładzie związanym z kodem obsługuje metody, przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="88e4b-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="88e4b-110">W przykładzie polecenie zapisuje te wywołania metody do <xref:System.Windows.Controls.TextBlock> elementy, które są związane z użycia metod get na dane wyjściowe nowe wartości właściwości jako ciągi.</span><span class="sxs-lookup"><span data-stu-id="88e4b-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="88e4b-111">W tym miejscu jest wynikiem gotowe!</span><span class="sxs-lookup"><span data-stu-id="88e4b-111">Here is the finished result!</span></span>
 
 ![Zrzut ekranu przedstawia interfejs użytkownika WPF z dwiema kolumnami, po prawej stronie ma siatka 3 x 3, a po lewej stronie przycisków, aby przenieść jako kolorowy prostokąt między kolumnami i wierszami siatki](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a><span data-ttu-id="88e4b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88e4b-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="88e4b-114">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="88e4b-114">Panels Overview</span></span>](panels-overview.md)
