---
title: 'Instrukcje: Wyświetl zawartość ListView przy użyciu GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 1066869c80bf5bd87d656bcb4994c188ee0e8efc
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185613"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="da65f-102">Instrukcje: Wyświetl zawartość ListView przy użyciu GridView</span><span class="sxs-lookup"><span data-stu-id="da65f-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="da65f-103">Ten przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridView> tryb widoku dla <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="da65f-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da65f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="da65f-104">Example</span></span>  
 <span data-ttu-id="da65f-105">Można zdefiniować tryb widoku <xref:System.Windows.Controls.GridView> , określając <xref:System.Windows.Controls.GridViewColumn> obiektów.</span><span class="sxs-lookup"><span data-stu-id="da65f-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="da65f-106">Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.GridViewColumn> obiektów, które należy powiązać zawartość danych, który jest określony dla <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="da65f-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="da65f-107">To <xref:System.Windows.Controls.GridView> przykład określa trzy <xref:System.Windows.Controls.GridViewColumn> obiekty, które mapują `FirstName`, `LastName`, i `EmployeeNumber` pola `EmployeeInfoDataSource` który jest skonfigurowany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="da65f-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="da65f-108">Poniższa ilustracja przedstawia, jak pojawia się w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="da65f-108">The following illustration shows how this example appears.</span></span>  
  
 ![Zrzut ekranu pokazujący ListView z danymi wyjściowymi GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a><span data-ttu-id="da65f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da65f-110">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="da65f-111">ListView — omówienie</span><span class="sxs-lookup"><span data-stu-id="da65f-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="da65f-112">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="da65f-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="da65f-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="da65f-113">How-to Topics</span></span>](listview-how-to-topics.md)
