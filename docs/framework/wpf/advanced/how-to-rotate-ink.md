---
title: "Jak obrócić atrament"
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
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bfb3663d5fff7a1611732a016a6d17f143082e2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-rotate-ink"></a><span data-ttu-id="997a3-102">Jak obrócić atrament</span><span class="sxs-lookup"><span data-stu-id="997a3-102">How to: Rotate Ink</span></span>
## <a name="example"></a><span data-ttu-id="997a3-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="997a3-103">Example</span></span>  
 <span data-ttu-id="997a3-104">Poniższy przykładowy kod kopiuje pismo odręczne z <xref:System.Windows.Controls.InkCanvas> do <xref:System.Windows.Controls.Canvas> zawierający <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="997a3-104">The following example copies the ink from an <xref:System.Windows.Controls.InkCanvas> to a <xref:System.Windows.Controls.Canvas> that contains an <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="997a3-105">Gdy aplikacja kopiuje pismo odręczne, także o pismo odręczne 90 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="997a3-105">When the application copies the ink, it also rotates the ink 90 degrees clockwise.</span></span>  
  
 [!code-xaml[HowToRotateInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="997a3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="997a3-106">Example</span></span>  
 <span data-ttu-id="997a3-107">Poniższy przykład jest niestandardowy <xref:System.Windows.Documents.Adorner> który obraca naciśnięcia na <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="997a3-107">The following example is a custom <xref:System.Windows.Documents.Adorner> that rotates the strokes on an <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[AdornerForStrokes#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 <span data-ttu-id="997a3-108">Poniżej przedstawiono przykład [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, który definiuje <xref:System.Windows.Controls.InkPresenter> i wypełnia je pismo odręczne.</span><span class="sxs-lookup"><span data-stu-id="997a3-108">The following example is a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that defines an <xref:System.Windows.Controls.InkPresenter> and populates it with ink.</span></span> <span data-ttu-id="997a3-109">`Window_Loaded` Obsługi zdarzeń dodaje niestandardowy moduł definiowania układu kodu do <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="997a3-109">The `Window_Loaded` event handler adds the custom adorner to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-xaml[AdornerForStrokes#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
