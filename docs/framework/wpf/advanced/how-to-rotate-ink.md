---
title: 'Instrukcje: Obracanie pisma odręcznego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
ms.openlocfilehash: 31f5d0ffb6f0fdcdaef13bc44653f8c7938ac7f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768462"
---
# <a name="how-to-rotate-ink"></a>Instrukcje: Obracanie pisma odręcznego
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod kopiuje pisma odręcznego z <xref:System.Windows.Controls.InkCanvas> do <xref:System.Windows.Controls.Canvas> zawierający <xref:System.Windows.Controls.InkPresenter>.  Gdy aplikacja kopiuje pisma odręcznego, także o pisma odręcznego 90 stopni w prawo.  
  
 [!code-xaml[HowToRotateInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia niestandardowe <xref:System.Windows.Documents.Adorner> , obraca się pociągnięć na <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[AdornerForStrokes#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 Poniższy przykład jest [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, który definiuje <xref:System.Windows.Controls.InkPresenter> i wypełnia pisma odręcznego. `Window_Loaded` Programu obsługi zdarzeń dodaje niestandardowy moduł definiowania układu kodu do <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-xaml[AdornerForStrokes#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
