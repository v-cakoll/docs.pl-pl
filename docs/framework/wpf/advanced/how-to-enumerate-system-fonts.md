---
title: 'Instrukcje: Wyliczanie czcionek systemowych'
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
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001601"
---
# <a name="how-to-enumerate-system-fonts"></a>Instrukcje: Wyliczanie czcionek systemowych
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyliczyć czcionek w kolekcji czcionek systemowych. Nazwa rodziny czcionek każdego <xref:System.Windows.Media.FontFamily> w ramach <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> jest dodawany jako element pola kombi.  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Jeśli wiele wersji tej samej rodziny czcionek znajdują się w tym samym katalogu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wyliczenie czcionki zwraca najbardziej aktualną wersję czcionki. Jeśli informacje o wersji nie dostarcza rozwiązania, zwracany jest czcionki z najnowszą sygnatury czasowej. Jeśli informacje sygnatur czasowych są równoważne, zwracany jest plik czcionki, który jest pierwszy w kolejności alfabetycznej.
