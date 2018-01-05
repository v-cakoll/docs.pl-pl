---
title: 'Porady: przechodzenie wstecz przez historii nawigacji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3bfc809dbe76c17859cb3fcd83f8a293a24b308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="ecba3-102">Porady: przechodzenie wstecz przez historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="ecba3-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="ecba3-103">W tym przykładzie przedstawiono sposób przejdź do pozycji na spód historii nawigacji.</span><span class="sxs-lookup"><span data-stu-id="ecba3-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecba3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecba3-104">Example</span></span>  
 <span data-ttu-id="ecba3-105">Kod, który działa z zawartości, która jest obsługiwana w <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> użyj <xref:System.Windows.Navigation.NavigationService>, lub [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] można przejść za pośrednictwem historii nawigacji, jeden wpis w czasie.</span><span class="sxs-lookup"><span data-stu-id="ecba3-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> use <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="ecba3-106">Nawigacyjnego ponownie jeden wpis wymaga najpierw sprawdzanie, czy wpisy w historii nawigacji Wstecz, sprawdzając **CanGoBack** właściwości, zanim Nawigacja kopii jednego wpisu, wywołując **GoBack** Metoda.</span><span class="sxs-lookup"><span data-stu-id="ecba3-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="ecba3-107">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ecba3-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="ecba3-108">**CanGoBack** i **GoBack** są implementowane przez <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, i <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="ecba3-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecba3-109">Jeśli należy wywołać **GoBack**, i nie ma żadnych wpisów w historii nawigacji Wstecz <xref:System.InvalidOperationException> jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="ecba3-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
