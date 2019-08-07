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
ms.openlocfilehash: 85d3562246170901d83d6314caec5747d52fb9a0
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817966"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="ba584-102">Instrukcje: Poruszanie się w przód i wstecz w historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="ba584-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="ba584-103">Ten przykład ilustruje sposób nawigowania do przodu lub z powrotem do wpisów w historii nawigacji.</span><span class="sxs-lookup"><span data-stu-id="ba584-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba584-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba584-104">Example</span></span>  
 <span data-ttu-id="ba584-105">Kod, który jest uruchamiany z zawartości na poniższych hostach, może przechodzić do przodu lub do tyłu przez historię przeglądania, po jednym wpisie.</span><span class="sxs-lookup"><span data-stu-id="ba584-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="ba584-106"><xref:System.Windows.Navigation.NavigationWindow>użyciu<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="ba584-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="ba584-107"><xref:System.Windows.Controls.Frame>użyciu<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="ba584-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="ba584-108">Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="ba584-108">Internet Explorer</span></span>  
  
 <span data-ttu-id="ba584-109">Przed przejściem do przodu jednego wpisu należy najpierw sprawdzić, czy istnieją wpisy w historii przeglądania do przodu, sprawdzając Właściwość **CanGoForward** .</span><span class="sxs-lookup"><span data-stu-id="ba584-109">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="ba584-110">Aby poruszać się po jednym wpisie, należy wywołać metodę **GoForward** .</span><span class="sxs-lookup"><span data-stu-id="ba584-110">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="ba584-111">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ba584-111">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="ba584-112">Aby móc nawigować po jednym wpisie, musisz najpierw sprawdzić, czy istnieją wpisy w historii nawigacji wstecznej, sprawdzając Właściwość **CanGoBack** .</span><span class="sxs-lookup"><span data-stu-id="ba584-112">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="ba584-113">Aby nawigować po jednym wpisie, należy wywołać metodę **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="ba584-113">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="ba584-114">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ba584-114">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="ba584-115">**CanGoForward**, **GoForward**, **CanGoBack**i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="ba584-115">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba584-116">Jeśli wywołasz **GoForward**i nie ma żadnych wpisów w historii przeglądania do przodu lub jeśli wywołasz **GoBack**i nie ma żadnych wpisów w <xref:System.InvalidOperationException> historii nawigacji wstecznej, zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="ba584-116">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
