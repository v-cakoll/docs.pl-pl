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
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Instrukcje: Ustawianie wysokości okna z poziomu strony
W tym przykładzie pokazano, jak ustawić wysokość okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.Page> może ustawić wysokość okna hosta według ustawienia <xref:System.Windows.Controls.Page.WindowHeight%2A>. Ta właściwość umożliwia <xref:System.Windows.Controls.Page> niejawną wiedzę o typie okna, które obsługuje.  
  
> [!NOTE]
> Aby ustawić wysokość okna przy użyciu <xref:System.Windows.Controls.Page.WindowHeight%2A> <xref:System.Windows.Controls.Page> , musi być elementem podrzędnym okna.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
