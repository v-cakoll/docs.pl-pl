---
title: "Jak użyć automatycznego układu to utworzenia przycisku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d55dc1330c21e7eb9f7cfd7f554234dccd6f274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Jak użyć automatycznego układu to utworzenia przycisku
W tym przykładzie przedstawiono sposób użyć metody automatycznego układu, aby utworzyć element button w aplikacji lokalizowalny.  
  
 Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być czasochłonne procesu. Często wiadomość dla lokalizatorów konieczne rozmiar i położenie elementów oprócz tłumaczenie tekstu. W przeszłości każdego języka, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań. Teraz z funkcjami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementów pozwalających ograniczyć potrzebę dostosowania. Podejście do pisania aplikacji, które mogą być łatwo po zmianie rozmiaru i zmienionym jest nazywany `automatic layout`.  
  
 Następujące dwa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady tworzenia aplikacji, które wystąpienia przycisk; jeden z tekstu w języku angielskim i jeden z tekstu w języku hiszpańskim. Zwróć uwagę, że kod jest taki sam, z wyjątkiem tekstu. Ten przycisk jest dopasowywany tekst.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe przykładów kodu.  
  
 ![Ten sam przycisk z tekstem w różnych językach](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Przycisk o zmiennym rozmiarze automatycznie  
  
## <a name="see-also"></a>Zobacz też  
 [Użyj automatycznego układu — omówienie](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Użyj siatki układu automatycznego](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
