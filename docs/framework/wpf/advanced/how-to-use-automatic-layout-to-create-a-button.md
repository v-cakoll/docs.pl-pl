---
title: Jak użyć automatycznego układu to utworzenia przycisku
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Przegląd używania automatycznego układu](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Używanie siatki do automatycznego układu](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
