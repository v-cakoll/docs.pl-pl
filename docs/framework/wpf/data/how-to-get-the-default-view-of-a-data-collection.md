---
title: Jak pobrać domyślny widok kolekcji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459119"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Jak pobrać domyślny widok kolekcji danych
Widoki umożliwiają wyświetlanie tych samych danych na różne sposoby, w zależności od sortowania, filtrowania lub kryteriów grupowania. Każda kolekcja ma jeden współużytkowany widok domyślny, który jest używany jako rzeczywiste Źródło powiązania, gdy powiązanie Określa kolekcję jako źródło. Ten przykład pokazuje, jak uzyskać domyślny widok kolekcji.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć widok, potrzebujesz odwołania do obiektu do kolekcji. Ten obiekt danych można uzyskać, odwołując się do własnego obiektu związanego z kodem, pobierając kontekst danych, pobierając Właściwość źródła danych lub pobierając właściwość powiązania. Ten przykład pokazuje, jak uzyskać <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu danych i użyć go do bezpośredniego uzyskania domyślnego widoku kolekcji dla tej kolekcji.  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 W tym przykładzie element główny jest <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> jest ustawiona na wartość *webdatasource*, która odnosi się do dostawcy danych, który jest <xref:System.Collections.ObjectModel.ObservableCollection%601> obiektów *kolejności* .  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternatywnie można utworzyć wystąpienie i utworzyć powiązanie z własnym widokiem kolekcji, korzystając z klasy <xref:System.Windows.Data.CollectionViewSource>. Ten widok kolekcji jest współużytkowany tylko przez formanty, które są bezpośrednio powiązane z nim. Aby zapoznać się z przykładem, zobacz sekcję jak utworzyć widok w temacie [powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Aby zapoznać się z przykładami funkcji udostępnianych przez widok kolekcji, zobacz [Sortowanie danych w widoku](how-to-sort-data-in-a-view.md), [filtrowanie danych w widoku](how-to-filter-data-in-a-view.md)i [nawigowanie po obiektach w CollectionView danych](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Sortowanie i grupowanie danych przy użyciu widoku w XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
