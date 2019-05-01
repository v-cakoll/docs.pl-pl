---
title: 'Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 4c20ebfab45a24cf34b1476fb94dae6913fb4d99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947761"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="e58e3-102">Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="e58e3-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="e58e3-103">Ten przykład ilustruje sposób przejścia do przodu i Wstecz w historii nawigacji dla wpisów.</span><span class="sxs-lookup"><span data-stu-id="e58e3-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e58e3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e58e3-104">Example</span></span>  
 <span data-ttu-id="e58e3-105">Kod, który jest uruchamiany z zawartości w następujących hostów można przejść do przodu lub Wstecz w historii nawigacji, jeden wpis w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="e58e3-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="e58e3-106"><xref:System.Windows.Navigation.NavigationWindow> za pomocą <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="e58e3-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="e58e3-107"><xref:System.Windows.Controls.Frame> za pomocą <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="e58e3-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="e58e3-108">Zanim przejdziesz do przodu o jedną pozycję, musisz najpierw sprawdzić, czy znajdują się wpisy w historii przeglądania do przodu, sprawdzając **CanGoForward** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e58e3-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="e58e3-109">Aby przejść do przodu o jedną pozycję, należy wywołać **GoForward** metody.</span><span class="sxs-lookup"><span data-stu-id="e58e3-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="e58e3-110">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e58e3-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="e58e3-111">Zanim można nawigować trybu jednego wpisu, musisz najpierw sprawdzić, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e58e3-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="e58e3-112">Aby przejść z powrotem jeden wpis, należy wywołać **GoBack** metody.</span><span class="sxs-lookup"><span data-stu-id="e58e3-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="e58e3-113">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e58e3-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="e58e3-114">**CanGoForward**, **GoForward**, **CanGoBack**, i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="e58e3-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58e3-115">Jeśli wywołasz **GoForward**, i nie ma żadnych wpisów w historii przeglądania do przodu, lub jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="e58e3-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
