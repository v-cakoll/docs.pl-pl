---
title: Jak sortować i grupować dane przy użyciu widoku w XAML
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
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460127"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Jak sortować i grupować dane przy użyciu widoku w XAML
Ten przykład pokazuje, jak utworzyć widok zbierania danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Widoki umożliwiają korzystanie z funkcji grupowania, sortowania, filtrowania i koncepcji bieżącego elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zasób statyczny o nazwie *miejsc* został zdefiniowany jako *Kolekcja obiektów miejsc* , w których każdy obiekt *miejsca* zawiera nazwę miasta i stan. Prefiks *src* jest mapowany do przestrzeni nazw, w której zdefiniowano *miejsce* źródła danych. Przedrostek *Menedżer SCM* mapuje do `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje do `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 Poniższy przykład tworzy widok zbierania danych, który jest posortowany według nazwy miasta i pogrupowane według stanu.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Widok może być następnie źródłem powiązań, tak jak w poniższym przykładzie:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 W przypadku powiązań z danymi XML zdefiniowanymi w zasobie <xref:System.Windows.Data.XmlDataProvider> poprzedź nazwę XML znakiem @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.CollectionViewSource>
- [Pobieranie widoku domyślnego kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
