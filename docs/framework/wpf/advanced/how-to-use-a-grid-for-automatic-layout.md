---
title: "Jak użyć siatki do automatycznego układu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbd8bd7e36b7b773837b839e77ec88a8e7c8f0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Jak użyć siatki do automatycznego układu
W tym przykładzie przedstawiono sposób użycia siatki w ujęciu automatyczny układ do tworzenia aplikacji lokalizowalny.  
  
 Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być czasochłonne procesu. Często wiadomość dla lokalizatorów należy zmieniać rozmiar i położenia elementów oprócz tłumaczenie tekstu. W przeszłości każdego języka, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań. Teraz z funkcjami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementów pozwalających ograniczyć potrzebę dostosowania. Podejście do pisania aplikacji, które mogą być łatwo zmieniono rozmiar i zmienionym jest nazywany `auto layout`.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie pokazano, używając siatka do umieszczenia niektórych przycisków i tekst. Należy zauważyć, że ustawiono wysokość i szerokość komórek `Auto`; w związku z tym komórki, która zawiera przycisk Obraz jest dopasowywany obrazu. Ponieważ <xref:System.Windows.Controls.Grid> elementu można dostosować do jego zawartości, może być przydatne przy uwzględnieniu automatyczny układ podejście do projektowania aplikacji, które może być lokalizowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie siatki.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe przykładowy kod.  
  
 ![Przykład siatka](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Siatka  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd używania automatycznego układu](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Używanie automatycznego układu do utworzenia przycisku](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
