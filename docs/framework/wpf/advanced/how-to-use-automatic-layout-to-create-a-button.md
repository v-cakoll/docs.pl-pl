---
title: 'Instrukcje: Używanie automatycznego układu do utworzenia przycisku'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 8eb1e93dd87c210812c9b7758c744a616ef2d862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052394"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Instrukcje: Używanie automatycznego układu do utworzenia przycisku
W tym przykładzie opisano sposób używania metody automatycznego układu to utworzenia przycisku w aplikacji możliwych do zlokalizowania.  
  
 Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być procesem dużo czasu. Często lokalizatorzy konieczne zmiany rozmiaru i położenia elementów oprócz tłumaczenie tekstu. W przeszłości każdego z języków, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań. Teraz z możliwościami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementy, które zmniejszyć zapotrzebowanie na dostosowanie. Nosi nazwę podejścia do pisania aplikacji, które można łatwiej o zmienionym rozmiarze i zmienionym `automatic layout`.  
  
## <a name="example"></a>Przykład  

Następujące dwa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady tworzenia aplikacji do tworzenia wystąpienia przycisku; jeden z tekstu w języku angielskim i jeden z tekstu w języku hiszpańskim. Należy zauważyć, że kod jest taki sam, z wyjątkiem tekstu. Ten przycisk jest dopasowywany tekstu.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe z przykładów kodu za pomocą przycisków o zmiennym rozmiarze automatycznie:
  
 ![Ten sam przycisk z tekstem w różnych językach](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd używania automatycznego układu](use-automatic-layout-overview.md)
- [Używanie siatki do automatycznego układu](how-to-use-a-grid-for-automatic-layout.md)
