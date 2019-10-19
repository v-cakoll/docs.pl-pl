---
title: 'Instrukcje: nawigowanie do strony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 25a0dbbc609c7b6f8f2878d2068e61e492a59c7e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582537"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="24aa7-102">Instrukcje: nawigowanie do strony</span><span class="sxs-lookup"><span data-stu-id="24aa7-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="24aa7-103">Ten przykład ilustruje kilka sposobów, w których można przechodzić do strony z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="24aa7-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24aa7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="24aa7-104">Example</span></span>  
 <span data-ttu-id="24aa7-105">Możliwe jest <xref:System.Windows.Navigation.NavigationWindow> przechodzenie do strony przy użyciu jednego z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="24aa7-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
- <span data-ttu-id="24aa7-106">Właściwość <xref:System.Windows.Navigation.NavigationWindow.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="24aa7-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
- <span data-ttu-id="24aa7-107">Metoda <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A>.</span><span class="sxs-lookup"><span data-stu-id="24aa7-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> <span data-ttu-id="24aa7-108">Uniform Resource Identifier (URI) może być względna lub bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="24aa7-108">Uniform resource identifiers (URIs) can be either relative or absolute.</span></span> <span data-ttu-id="24aa7-109">Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="24aa7-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24aa7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24aa7-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
