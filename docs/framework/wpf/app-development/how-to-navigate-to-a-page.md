---
title: 'Instrukcje: Przechodzenie do strony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: c8e808180682bfd97f397d8cadd1e4deafd7eb06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141053"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="e5e99-102">Instrukcje: Przechodzenie do strony</span><span class="sxs-lookup"><span data-stu-id="e5e99-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="e5e99-103">W tym przykładzie pokazano kilka sposobów, w których strony można nastąpi przejście z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="e5e99-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5e99-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5e99-104">Example</span></span>  
 <span data-ttu-id="e5e99-105">Możliwe jest <xref:System.Windows.Navigation.NavigationWindow> przejść do strony, przy użyciu jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e5e99-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="e5e99-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> Właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5e99-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="e5e99-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Metody.</span><span class="sxs-lookup"><span data-stu-id="e5e99-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] <span data-ttu-id="e5e99-108">może być względna lub bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="e5e99-108">can be either relative or absolute.</span></span> <span data-ttu-id="e5e99-109">Aby uzyskać więcej informacji, zobacz [pakiet URI w WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e5e99-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e99-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5e99-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
