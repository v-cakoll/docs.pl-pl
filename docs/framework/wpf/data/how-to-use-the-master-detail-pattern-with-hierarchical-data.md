---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e4183ddc3868a1568662853b46e05348df129092
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733483"
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
  
 Technika jest nieco inna w przypadku korzystania z danych XML. Aby zapoznać się z przykładem, zobacz [Używanie wzorca master-detail z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.HierarchicalDataTemplate>
- [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](data-templating-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
