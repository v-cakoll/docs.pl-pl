---
title: 'Instrukcje: Wyświetlanie danych za pomocą GridViewRowPresenter'
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: 0e471df3ab6fd10417fc58ece4cdb8ff1c457c95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149152"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="0749a-102">Instrukcje: Wyświetlanie danych za pomocą GridViewRowPresenter</span><span class="sxs-lookup"><span data-stu-id="0749a-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="0749a-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów do wyświetlenia danych w kolumnach.</span><span class="sxs-lookup"><span data-stu-id="0749a-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0749a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0749a-104">Example</span></span>  
 <span data-ttu-id="0749a-105">Poniższy przykład pokazuje, jak określić <xref:System.Windows.Controls.GridViewColumnCollection> wyświetlającą <xref:System.DateTime.DayOfWeek%2A> i <xref:System.DateTime.Year%2A> z <xref:System.DateTime> obiektu za pomocą <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0749a-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="0749a-106">Przykładzie zdefiniowano też <xref:System.Windows.Style> dla <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="0749a-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="0749a-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0749a-107">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [<span data-ttu-id="0749a-108">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="0749a-108">GridView Overview</span></span>](gridview-overview.md)
