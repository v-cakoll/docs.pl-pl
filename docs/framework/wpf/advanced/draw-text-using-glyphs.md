---
title: "Rysuj tekst z użyciem glifów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55ed079116d0f0e0c168984f16c5ff715667442f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="draw-text-using-glyphs"></a>Rysuj tekst z użyciem glifów
W tym temacie opisano sposób korzystania z niskiego poziomu <xref:System.Windows.Documents.Glyphs> obiektu do wyświetlania tekstu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano sposób definiowania właściwości <xref:System.Windows.Documents.Glyphs> obiektu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Obiekt reprezentuje dane wyjściowe <xref:System.Windows.Media.GlyphRun> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Przykładów założono, że czcionki Arial, Courier New i podzbiory są instalowane w folderze C:\WINDOWS\Fonts na komputerze lokalnym.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 W tym przykładzie pokazano sposób definiowania inne właściwości <xref:System.Windows.Documents.Glyphs> obiekty w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
