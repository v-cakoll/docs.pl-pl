---
title: 'Instrukcje: Ustawianie wysokości okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c1041af88241011b51c96d7b61423344a32b25ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940797"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a><span data-ttu-id="a5061-102">Instrukcje: Ustawianie wysokości okna z poziomu strony</span><span class="sxs-lookup"><span data-stu-id="a5061-102">How to: Set the Height of a Window from a Page</span></span>
<span data-ttu-id="a5061-103">W tym przykładzie pokazano, jak ustawić wysokość okna z <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="a5061-103">This example illustrates how to set the height of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5061-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5061-104">Example</span></span>  
 <span data-ttu-id="a5061-105">A <xref:System.Windows.Controls.Page> może ustawić wysokość okna hosta według ustawienia <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5061-105">A <xref:System.Windows.Controls.Page> can set the height of its host window by setting <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span></span> <span data-ttu-id="a5061-106">Ta właściwość umożliwia <xref:System.Windows.Controls.Page> niejawną wiedzę o typie okna, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="a5061-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5061-107">Aby ustawić wysokość okna przy użyciu <xref:System.Windows.Controls.Page.WindowHeight%2A> <xref:System.Windows.Controls.Page> , musi być elementem podrzędnym okna.</span><span class="sxs-lookup"><span data-stu-id="a5061-107">To set the height of a window using <xref:System.Windows.Controls.Page.WindowHeight%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
