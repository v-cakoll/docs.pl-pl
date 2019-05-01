---
title: 'Instrukcje: Wyświetlanie zawartości kontrolki ListView przy użyciu kontrolki GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9b467c95d541c326a41d1ed4bd9eb5c87e25bd5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910497"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="c9f52-102">Instrukcje: Wyświetlanie zawartości kontrolki ListView przy użyciu kontrolki GridView</span><span class="sxs-lookup"><span data-stu-id="c9f52-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="c9f52-103">Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridView> tryb widoku dla <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c9f52-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9f52-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9f52-104">Example</span></span>  
 <span data-ttu-id="c9f52-105">Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c9f52-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="c9f52-106">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridViewColumn> obiektów, które należy powiązać zawartość danych, który jest określony dla <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c9f52-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="c9f52-107">To <xref:System.Windows.Controls.GridView> przykład określa trzy <xref:System.Windows.Controls.GridViewColumn> obiekty, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest skonfigurowany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="c9f52-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="c9f52-108">Poniższa ilustracja przedstawia, jak pojawia się w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c9f52-108">The following illustration shows how this example appears.</span></span>  
  
 ![Zrzut ekranu pokazujący ListView z danymi wyjściowymi GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a><span data-ttu-id="c9f52-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9f52-110">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="c9f52-111">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="c9f52-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="c9f52-112">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="c9f52-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="c9f52-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c9f52-113">How-to Topics</span></span>](listview-how-to-topics.md)
