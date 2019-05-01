---
title: 'Instrukcje: Poruszanie się wstecz w historii nawigacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: c489a1593b3d1f22fe1ad6e648d3f8a3f7a6cd44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947787"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="e7a33-102">Instrukcje: Poruszanie się wstecz w historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="e7a33-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="e7a33-103">Ten przykład ilustruje sposób przejścia do wpisów na spód historii nawigacji.</span><span class="sxs-lookup"><span data-stu-id="e7a33-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7a33-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7a33-104">Example</span></span>  
 <span data-ttu-id="e7a33-105">Kod, który jest uruchomiony przez zawartość, która znajduje się w <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> przy użyciu <xref:System.Windows.Navigation.NavigationService>, lub [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] przejść wstecz w historii nawigacji, jeden wpis w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="e7a33-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="e7a33-106">Po wstecz o jeden wpis wymaga najpierw sprawdzanie, czy znajdują się wpisy w historii przeglądania do tyłu, sprawdzając **CanGoBack** właściwości przed przechodząc kopii jeden wpis, wywołując **GoBack** Metoda.</span><span class="sxs-lookup"><span data-stu-id="e7a33-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="e7a33-107">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e7a33-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="e7a33-108">**CanGoBack** i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="e7a33-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7a33-109">Jeśli wywołasz **GoBack**, i nie ma żadnych wpisów w historii przeglądania do tyłu <xref:System.InvalidOperationException> jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="e7a33-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
