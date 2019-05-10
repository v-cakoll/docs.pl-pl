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
ms.openlocfilehash: 00a41fcf85583ec0d081a2fa099f3a77cfcd2900
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625357"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="a3fae-102">Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="a3fae-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="a3fae-103">Ten przykład ilustruje sposób przejścia do przodu i Wstecz w historii nawigacji dla wpisów.</span><span class="sxs-lookup"><span data-stu-id="a3fae-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3fae-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3fae-104">Example</span></span>  
 <span data-ttu-id="a3fae-105">Kod, który jest uruchamiany z zawartości w następujących hostów można przejść do przodu lub Wstecz w historii nawigacji, jeden wpis w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="a3fae-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="a3fae-106"><xref:System.Windows.Navigation.NavigationWindow> za pomocą <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="a3fae-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="a3fae-107"><xref:System.Windows.Controls.Frame> za pomocą <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="a3fae-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="a3fae-108">Zanim przejdziesz do przodu o jedną pozycję, musisz najpierw sprawdzić, czy znajdują się wpisy w historii przeglądania do przodu, sprawdzając **CanGoForward** właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3fae-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="a3fae-109">Aby przejść do przodu o jedną pozycję, należy wywołać **GoForward** metody.</span><span class="sxs-lookup"><span data-stu-id="a3fae-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="a3fae-110">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a3fae-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="a3fae-111">Zanim można nawigować trybu jednego wpisu, musisz najpierw sprawdzić, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości.</span><span class="sxs-lookup"><span data-stu-id="a3fae-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="a3fae-112">Aby przejść z powrotem jeden wpis, należy wywołać **GoBack** metody.</span><span class="sxs-lookup"><span data-stu-id="a3fae-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="a3fae-113">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a3fae-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="a3fae-114">**CanGoForward**, **GoForward**, **CanGoBack**, i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="a3fae-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3fae-115">Jeśli wywołasz **GoForward**, i nie ma żadnych wpisów w historii przeglądania do przodu, lub jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="a3fae-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
