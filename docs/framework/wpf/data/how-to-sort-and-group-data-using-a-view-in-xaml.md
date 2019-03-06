---
title: 'Instrukcje: Sortuj i grupuj dane przy użyciu widoku w XAML'
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
ms.openlocfilehash: 01cbd113502c3f953bd701930df6db090844fefa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351427"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Instrukcje: Sortuj i grupuj dane przy użyciu widoku w XAML
W tym przykładzie pokazano, jak utworzyć widok kolekcji danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Widoki umożliwiają funkcje grupowania, sortowanie, filtrowanie i pojęcie bieżącego elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie statycznych zasobów o nazwie *umieszcza* jest zdefiniowany jako kolekcja *miejscu* obiektów, w których każdy *miejscu* obiektu jest obejmowało nazwę miejscowości i Stan. Prefiks *src* jest zamapowana na przestrzeń nazw gdzie źródło danych *miejsc* jest zdefiniowana. Prefiks *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 Poniższy przykład tworzy widok zbierania danych, które są sortowane według nazwy miasta i pogrupowane według stanu.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Widok można następnie źródło powiązania, jak w poniższym przykładzie:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Dla powiązań z danymi XML zdefiniowane w <xref:System.Windows.Data.XmlDataProvider> zasobu, poprzedź nazwę XML przy użyciu znaku @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Data.CollectionViewSource>
- [Pobieranie widoku domyślnego kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
