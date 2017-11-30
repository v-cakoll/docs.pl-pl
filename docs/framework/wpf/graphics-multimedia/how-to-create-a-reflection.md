---
title: "Jak utworzyć odbicie"
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
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3032f46843c6d8efc53c45a927feae7068c3eb5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-reflection"></a>Jak utworzyć odbicie
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia. Ponieważ <xref:System.Windows.Media.VisualBrush> można wyświetlić istniejące visual, ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia z <xref:System.Windows.Controls.Border> zawiera wiele elementów. Na poniższej ilustracji przedstawiono dane wyjściowe, który spowoduje utworzenie w tym przykładzie.  
  
 ![Obiekt wizualny odzwierciedlone A](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Obiekt Visual odbite  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Pełną przykładowej, który zawiera przykłady pokazujące powiększyć części ekranu oraz sposobu tworzenia odbicia, zobacz [próbki VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.VisualBrush>  
 [Malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
