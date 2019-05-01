---
title: 'Instrukcje: Ustawianie szerokości okna z poziomu strony'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: fee6d4c9ae9dae03e81cc4be56576763cb59958b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006723"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Instrukcje: Ustawianie szerokości okna z poziomu strony
Ten przykład ilustruje sposób ustawiania szerokości okna z <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.Page> szerokość okna hosta można ustawić, ustawiając <xref:System.Windows.Controls.Page.WindowWidth%2A>. Ta właściwość umożliwia <xref:System.Windows.Controls.Page> nie mają jawnych wiedzy o typie okna, który ją obsługuje.  
  
> [!NOTE]
>  Aby ustawić szerokość okna przy użyciu <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> musi być elementem podrzędnym okna.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
