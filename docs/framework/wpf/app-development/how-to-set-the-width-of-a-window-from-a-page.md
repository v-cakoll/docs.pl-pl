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
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="cdc2c-102">Instrukcje: Ustawianie szerokości okna z poziomu strony</span><span class="sxs-lookup"><span data-stu-id="cdc2c-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="cdc2c-103">Ten przykład ilustruje sposób ustawiania szerokości okna z <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="cdc2c-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdc2c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cdc2c-104">Example</span></span>  
 <span data-ttu-id="cdc2c-105">A <xref:System.Windows.Controls.Page> szerokość okna hosta można ustawić, ustawiając <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdc2c-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="cdc2c-106">Ta właściwość umożliwia <xref:System.Windows.Controls.Page> nie mają jawnych wiedzy o typie okna, który ją obsługuje.</span><span class="sxs-lookup"><span data-stu-id="cdc2c-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdc2c-107">Aby ustawić szerokość okna przy użyciu <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> musi być elementem podrzędnym okna.</span><span class="sxs-lookup"><span data-stu-id="cdc2c-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
