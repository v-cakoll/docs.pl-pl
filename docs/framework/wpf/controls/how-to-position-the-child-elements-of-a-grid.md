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
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="cd97f-102">Jak ustawić położenie elementów podrzędnych siatki</span><span class="sxs-lookup"><span data-stu-id="cd97f-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="cd97f-103">W tym przykładzie pokazano, jak użyć get i ustawić metody, które są zdefiniowane na <xref:System.Windows.Controls.Grid> położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cd97f-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd97f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd97f-104">Example</span></span>  
 <span data-ttu-id="cd97f-105">W poniższym przykładzie zdefiniowano nadrzędne <xref:System.Windows.Controls.Grid> elementu (`grid1`) zawierającej trzy kolumny i trzy wiersze.</span><span class="sxs-lookup"><span data-stu-id="cd97f-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="cd97f-106">Element podrzędny <xref:System.Windows.Shapes.Rectangle> elementu (`rect1`) jest dodawany do <xref:System.Windows.Controls.Grid> kolumny pozycji zero, wiersz pozycji zero.</span><span class="sxs-lookup"><span data-stu-id="cd97f-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="cd97f-107"><xref:System.Windows.Controls.Button>elementy reprezentują metod, które mogą być wywoływane w celu zmiany położenia <xref:System.Windows.Shapes.Rectangle> w elemencie <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="cd97f-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="cd97f-108">Gdy użytkownik kliknie przycisk, jest uaktywniony powiązanej metody.</span><span class="sxs-lookup"><span data-stu-id="cd97f-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="cd97f-109">W poniższym przykładzie kodu powiązanego obsługuje metody który przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> wywoływanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cd97f-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="cd97f-110">W przykładzie polecenie zapisuje te wywołania metody do <xref:System.Windows.Controls.TextBlock> elementów powiązanych Użyj get metody zwracać wartości właściwości jako ciągi.</span><span class="sxs-lookup"><span data-stu-id="cd97f-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cd97f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd97f-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="cd97f-112">Omówienie paneli</span><span class="sxs-lookup"><span data-stu-id="cd97f-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
