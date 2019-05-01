---
title: 'Instrukcje: Ustawianie wysokości okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007331"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Instrukcje: Ustawianie wysokości okna z poziomu strony
Ten przykład ilustruje sposób ustawiania wysokości okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.Page> wysokość okna hosta można ustawić, ustawiając <xref:System.Windows.Controls.Page.WindowHeight%2A>. Ta właściwość umożliwia <xref:System.Windows.Controls.Page> nie mają jawnych wiedzy o typie okna, który ją obsługuje.  
  
> [!NOTE]
>  Aby ustawić wysokość okna przy użyciu <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> musi być elementem podrzędnym okna.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
