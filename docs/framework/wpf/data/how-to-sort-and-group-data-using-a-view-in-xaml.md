---
title: Jak sortować i grupować dane przy użyciu widoku w XAML
description: Dowiedz się, jak utworzyć widok zbierania danych służący do grupowania, sortowania i filtrowania w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621681"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Jak sortować i grupować dane przy użyciu widoku w XAML
Ten przykład pokazuje, jak utworzyć widok zbierania danych w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Widoki umożliwiają korzystanie z funkcji grupowania, sortowania, filtrowania i koncepcji bieżącego elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zasób statyczny o nazwie *miejsc* został zdefiniowany jako *Kolekcja obiektów miejsc* , w których każdy obiekt *miejsca* zawiera nazwę miasta i stan. Prefiks *src* jest mapowany do przestrzeni nazw, w której zdefiniowano *miejsce* źródła danych. Przedrostek *Menedżer SCM* mapuje do `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje na `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` .  
  
 Poniższy przykład tworzy widok zbierania danych, który jest posortowany według nazwy miasta i pogrupowane według stanu.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Widok może być następnie źródłem powiązań, tak jak w poniższym przykładzie:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 W przypadku powiązań z danymi XML zdefiniowanymi w <xref:System.Windows.Data.XmlDataProvider> zasobie poprzedź nazwę XML symbolem @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.CollectionViewSource>
- [Pobierz domyślny widok kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
