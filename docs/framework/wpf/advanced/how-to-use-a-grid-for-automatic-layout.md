---
title: 'Instrukcje: Używanie siatki do automatycznego układu'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 590ad7292fea572b20ccaa09ce2886724e004a6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052407"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Instrukcje: Używanie siatki do automatycznego układu
W tym przykładzie opisano, jak użyć siatki w ujęciu automatycznego układu do tworzenia aplikacji możliwych do zlokalizowania.  
  
 Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być procesem dużo czasu. Często lokalizatorzy muszą zmieniać rozmiar i zmienić położenie elementów oprócz tłumaczenie tekstu. W przeszłości każdego z języków, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań. Teraz z możliwościami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementy, które zmniejszyć zapotrzebowanie na dostosowanie. Nosi nazwę podejścia do pisania aplikacji, które mogą być łatwiejsze zmieniono rozmiar i zmienionym `auto layout`.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykład demonstruje użycie siatki, aby umieścić niektóre przyciski i tekst. Należy zauważyć, że wysokość i szerokość komórek są ustawione na `Auto`; w związku z tym komórkę, która zawiera przycisk za pomocą obrazu jest dopasowywany obrazu. Ponieważ <xref:System.Windows.Controls.Grid> elementu można dostosować do jego zawartości, może być przydatne podczas wykonywania metody automatycznego układu do projektowania aplikacji, które może być lokalizowana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć siatki.  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe przykładowego kodu.  
  
 ![Przykład Grid](./media/glob-grid.png "glob_grid")  
Siatka  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd używania automatycznego układu](use-automatic-layout-overview.md)
- [Używanie automatycznego układu do utworzenia przycisku](how-to-use-automatic-layout-to-create-a-button.md)
