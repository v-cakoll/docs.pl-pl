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
ms.openlocfilehash: 53b32e145390d7052262042c7a793699c163b373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969353"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="0571c-102">Instrukcje: Poruszanie się wstecz w historii nawigacji</span><span class="sxs-lookup"><span data-stu-id="0571c-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="0571c-103">Ten przykład ilustruje sposób nawigowania do wpisów w historii nawigacji wstecznej.</span><span class="sxs-lookup"><span data-stu-id="0571c-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0571c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0571c-104">Example</span></span>  
 <span data-ttu-id="0571c-105">Kod, który jest uruchamiany z zawartości <xref:System.Windows.Navigation.NavigationWindow>, która jest hostowana w, <xref:System.Windows.Controls.Frame> za pomocą <xref:System.Windows.Navigation.NavigationService>lub Internet Explorer, może nawigować wstecz w historii nawigacji, po jednym wpisie.</span><span class="sxs-lookup"><span data-stu-id="0571c-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or Internet Explorer can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="0571c-106">Przechodzenie do tyłu jednego wpisu wymaga wcześniejszego sprawdzenia, czy istnieją wpisy w historii nawigacji wstecznej, sprawdzając Właściwość **CanGoBack** przed przechodzeniem do tyłu jednego wpisu, wywołując metodę **GoBack** .</span><span class="sxs-lookup"><span data-stu-id="0571c-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="0571c-107">Jest to zilustrowane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0571c-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="0571c-108">**CanGoBack** i **GoBack** są implementowane <xref:System.Windows.Navigation.NavigationWindow>przez <xref:System.Windows.Controls.Frame>,, <xref:System.Windows.Navigation.NavigationService>i.</span><span class="sxs-lookup"><span data-stu-id="0571c-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0571c-109">Jeśli wywołasz **GoBack**i nie ma żadnych wpisów w historii nawigacji wstecznej, <xref:System.InvalidOperationException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0571c-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
