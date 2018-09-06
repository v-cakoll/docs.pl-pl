---
title: 'Porady: poruszanie się wstecz historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 7266c9486524e962a859c34c9be5ab8f6d7bf7d5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037415"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="3f30d-102">Porady: poruszanie się wstecz historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="3f30d-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="3f30d-103">Ten przykład ilustruje sposób przejścia do wpisów na spód historii nawigacji.</span><span class="sxs-lookup"><span data-stu-id="3f30d-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f30d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f30d-104">Example</span></span>  
 <span data-ttu-id="3f30d-105">Kod, który jest uruchomiony przez zawartość, która znajduje się w <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> przy użyciu <xref:System.Windows.Navigation.NavigationService>, lub [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] przejść wstecz w historii nawigacji, jeden wpis w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="3f30d-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="3f30d-106">Po wstecz o jeden wpis wymaga najpierw sprawdzanie, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości przed przechodząc kopii jeden wpis, wywołując **GoBack** Metoda.</span><span class="sxs-lookup"><span data-stu-id="3f30d-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="3f30d-107">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3f30d-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="3f30d-108">**CanGoBack** i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="3f30d-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f30d-109">Jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="3f30d-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
