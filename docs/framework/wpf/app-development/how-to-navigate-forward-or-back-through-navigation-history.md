---
title: Jak poruszać się w przód i wstecz w historii nawigacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546269"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="9e543-102">Jak poruszać się w przód i wstecz w historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="9e543-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="9e543-103">W tym przykładzie przedstawiono sposób przejdź do wpisów w historii przeglądania do przodu i do tyłu.</span><span class="sxs-lookup"><span data-stu-id="9e543-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e543-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e543-104">Example</span></span>  
 <span data-ttu-id="9e543-105">Kod uruchamiany z zawartości w następujące hosty można przejść do przodu i do tyłu za pośrednictwem historii nawigacji, jeden wpis w czasie.</span><span class="sxs-lookup"><span data-stu-id="9e543-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="9e543-106"><xref:System.Windows.Navigation.NavigationWindow> Za pomocą <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="9e543-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="9e543-107"><xref:System.Windows.Controls.Frame> Za pomocą <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="9e543-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="9e543-108">Zanim przejdziesz do przodu jednego wpisu, musisz najpierw sprawdzić, czy wpisy w historii przeglądania do przodu sprawdzając **CanGoForward** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e543-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="9e543-109">Aby przejść do przodu jednego wpisu, należy wywołać **GoForward** metody.</span><span class="sxs-lookup"><span data-stu-id="9e543-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="9e543-110">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9e543-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="9e543-111">Zanim można przejść trybu jednego wpisu, musisz najpierw sprawdzić, czy wpisy w historii nawigacji Wstecz sprawdzając **CanGoBack** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e543-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="9e543-112">Aby przejść wstecz jednego wpisu, należy wywołać **GoBack** metody.</span><span class="sxs-lookup"><span data-stu-id="9e543-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="9e543-113">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9e543-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="9e543-114">**CanGoForward**, **GoForward**, **CanGoBack**, i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="9e543-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e543-115">Jeśli wywołujesz **GoForward**, i nie ma żadnych wpisów w historii przeglądania do przodu, lub jeśli wywołujesz **GoBack**, i nie ma żadnych wpisów w historii nawigacji Wstecz <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="9e543-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
