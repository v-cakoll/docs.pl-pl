---
title: "Jak wyświetlić dane za pomocą GridViewRowPresenter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebe0a47d38a2cfda2a7d150b4a3886d9f63ee190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="0fc83-102">Jak wyświetlić dane za pomocą GridViewRowPresenter</span><span class="sxs-lookup"><span data-stu-id="0fc83-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="0fc83-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów do wyświetlenia danych w kolumnach.</span><span class="sxs-lookup"><span data-stu-id="0fc83-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc83-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fc83-104">Example</span></span>  
 <span data-ttu-id="0fc83-105">Poniższy przykład przedstawia sposób określić <xref:System.Windows.Controls.GridViewColumnCollection> wyświetlający <xref:System.DateTime.DayOfWeek%2A> i <xref:System.DateTime.Year%2A> z <xref:System.DateTime> obiektu za pomocą <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0fc83-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="0fc83-106">Definiuje również przykładzie <xref:System.Windows.Style> dla <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="0fc83-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="0fc83-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fc83-107">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [<span data-ttu-id="0fc83-108">Omówienie widoku GridView</span><span class="sxs-lookup"><span data-stu-id="0fc83-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
