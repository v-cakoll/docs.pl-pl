---
title: 'Instrukcje: Wyświetl dane za pomocą GridViewRowPresenter'
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: f05e1bd67d37d21a010562c7be5db5ca594f36db
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369581"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="df0a4-102">Instrukcje: Wyświetl dane za pomocą GridViewRowPresenter</span><span class="sxs-lookup"><span data-stu-id="df0a4-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="df0a4-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów do wyświetlenia danych w kolumnach.</span><span class="sxs-lookup"><span data-stu-id="df0a4-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df0a4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="df0a4-104">Example</span></span>  
 <span data-ttu-id="df0a4-105">Poniższy przykład pokazuje, jak określić <xref:System.Windows.Controls.GridViewColumnCollection> wyświetlającą <xref:System.DateTime.DayOfWeek%2A> i <xref:System.DateTime.Year%2A> z <xref:System.DateTime> obiektu za pomocą <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="df0a4-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="df0a4-106">Przykładzie zdefiniowano też <xref:System.Windows.Style> dla <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="df0a4-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="df0a4-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df0a4-107">See also</span></span>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [<span data-ttu-id="df0a4-108">GridView — omówienie</span><span class="sxs-lookup"><span data-stu-id="df0a4-108">GridView Overview</span></span>](gridview-overview.md)
