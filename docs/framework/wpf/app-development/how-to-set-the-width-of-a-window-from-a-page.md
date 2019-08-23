---
title: 'Instrukcje: Ustawianie szerokości okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: 1e16b75ecb85550facdf24a5b9e341cf0c061178
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940773"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Instrukcje: Ustawianie szerokości okna z poziomu strony
Ten przykład ilustruje sposób ustawiania szerokości okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.Page> może ustawić szerokość okna hosta przez ustawienie <xref:System.Windows.Controls.Page.WindowWidth%2A>. Ta właściwość umożliwia <xref:System.Windows.Controls.Page> niejawną wiedzę o typie okna, które obsługuje.  
  
> [!NOTE]
> Aby ustawić szerokość okna przy użyciu <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> musi być elementem podrzędnym okna.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
