---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459082"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Jak użyć wzorca szczegółowego z danymi hierarchicznymi
Ten przykład pokazuje, jak zaimplementować scenariusz wzorzec-szczegóły.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `LeagueList` jest kolekcją `Leagues`. Każda `League` ma `Name` i zbiór `Divisions`, a każda `Division` ma nazwę i kolekcję `Teams`. Każda `Team` ma nazwę zespołu.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Poniżej znajduje się zrzut ekranu przedstawiający przykład. `Divisions` <xref:System.Windows.Controls.ListBox> automatycznie śledzi wybory w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetla odpowiednie dane. `Teams` <xref:System.Windows.Controls.ListBox> śledzi zaznaczenia w innych dwóch kontrolkach <xref:System.Windows.Controls.ListBox>.  
  
 ![Zrzut ekranu, który pokazuje&#45;przykład scenariusza z szczegółami głównymi.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 Oto dwie rzeczy do zauważenia w tym przykładzie:  
  
1. Trzy formanty <xref:System.Windows.Controls.ListBox> są powiązane z tym samym źródłem. Właściwość <xref:System.Windows.Data.Binding.Path%2A> powiązania ustawia się w celu określenia poziomu danych, który ma być wyświetlany przez <xref:System.Windows.Controls.ListBox>.  
  
2. Należy ustawić właściwość <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> na `true` w kontrolkach <xref:System.Windows.Controls.ListBox>, dla których jest śledzone zaznaczenie. Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiany jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatywnie, jeśli <xref:System.Windows.Controls.ListBox> pobiera dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i walutę.  
  
 Technika jest nieco inna, gdy używasz danych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Aby zapoznać się z przykładem, zobacz [Używanie wzorca master-detail z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.HierarchicalDataTemplate>
- [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](data-templating-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
