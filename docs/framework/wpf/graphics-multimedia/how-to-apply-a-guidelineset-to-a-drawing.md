---
title: "Jak zastosować GuidelineSet do rysowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf689f8a7c475dbdda416297e28118d43bfdbff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Jak zastosować GuidelineSet do rysowania
W tym przykładzie pokazano, jak zastosować <xref:System.Windows.Media.GuidelineSet> do <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Klasy jest tylko typ <xref:System.Windows.Media.Drawing> mający <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> właściwości. Aby zastosować <xref:System.Windows.Media.GuidelineSet> do innego typu <xref:System.Windows.Media.Drawing>, dodaj go do <xref:System.Windows.Media.DrawingGroup> , a następnie zastosować <xref:System.Windows.Media.GuidelineSet> do Twojej <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa <xref:System.Windows.Media.DrawingGroup> obiektów, które są niemal identyczne; jedyna różnica polega na: drugi <xref:System.Windows.Media.DrawingGroup> ma <xref:System.Windows.Media.GuidelineSet> i nie jest pierwszym.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie. Ponieważ renderowanie różnica między nimi <xref:System.Windows.Media.DrawingGroup> obiektów jest więc niewielkie, części rysunki są powiększenia.  
  
 ![Obiekt DrawingGroup z włączonymi i wyłączonymi właściwością GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
