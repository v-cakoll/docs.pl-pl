---
title: "Jak wykazać czcionki systemowe"
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
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf917dc2af256cdd0f3a0c579f86847e1bf4f1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-system-fonts"></a>Jak wykazać czcionki systemowe
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyliczyć czcionek w kolekcji czcionek systemu. Nazwę rodziny czcionek każdego <xref:System.Windows.Media.FontFamily> w <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> jest dodawana jako element do pola kombi.  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Jeśli wiele wersji tego samego rodziny czcionek znajdują się w tym samym katalogu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wyliczenie czcionki zwraca najbardziej aktualne wersje czcionki. Jeśli informacje o wersji nie zapewnia rozdzielczości, jest zwracana czcionki z sygnaturą czasową najnowsze. Jeśli informacje znaczników czasu są równoważne, zwracany jest plik czcionki, który jest pierwszy w kolejności alfabetycznej.
