---
title: Jak wykazać czcionki systemowe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: 7fc996a2d3ba7042fce70afc20be5d64042c2b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-system-fonts"></a>Jak wykazać czcionki systemowe
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyliczyć czcionek w kolekcji czcionek systemu. Nazwę rodziny czcionek każdego <xref:System.Windows.Media.FontFamily> w <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> jest dodawana jako element do pola kombi.  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Jeśli wiele wersji tego samego rodziny czcionek znajdują się w tym samym katalogu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wyliczenie czcionki zwraca najbardziej aktualne wersje czcionki. Jeśli informacje o wersji nie zapewnia rozdzielczości, jest zwracana czcionki z sygnaturą czasową najnowsze. Jeśli informacje znaczników czasu są równoważne, zwracany jest plik czcionki, który jest pierwszy w kolejności alfabetycznej.
