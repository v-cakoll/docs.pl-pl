---
title: Jak kontrolować kiedy tekst TextBox aktualizuje źródło
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: b211eb67e3bac95f74255935a39cc0d6aec61531
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974784"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Jak kontrolować kiedy tekst TextBox aktualizuje źródło
W tym temacie opisano sposób użycia właściwości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> do kontrolowania czasu aktualizacji źródła powiązań. W temacie jest wykorzystywany formant <xref:System.Windows.Controls.TextBox>.

## <a name="example"></a>Przykład
 Właściwość <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ma domyślną wartość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Oznacza to, że jeśli aplikacja ma <xref:System.Windows.Controls.TextBox> z właściwością <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> powiązaną z danymi, tekst wpisywany w <xref:System.Windows.Controls.TextBox> nie aktualizuje źródła do momentu, gdy <xref:System.Windows.Controls.TextBox> utraci fokus (na przykład po kliknięciu poza <xref:System.Windows.Controls.TextBox>).

 Jeśli chcesz, aby źródło było aktualizowane podczas pisania, ustaw <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> powiązania na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. W poniższym przykładzie wyróżnione wiersze kodu pokazują, że właściwości `Text` obu <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> są powiązane z tą samą właściwością source. Właściwość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> powiązania <xref:System.Windows.Controls.TextBox> jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 W efekcie <xref:System.Windows.Controls.TextBlock> wyświetla ten sam tekst (ponieważ źródło zmienia się), ponieważ użytkownik wprowadza tekst do <xref:System.Windows.Controls.TextBox>, jak pokazano na poniższym zrzucie ekranu przykładu:

 ![Zrzut ekranu pokazujący proste powiązanie danych.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Jeśli masz okno dialogowe lub formularz do edycji, a chcesz odroczyć aktualizacje źródłowe do momentu zakończenia edycji pól przez użytkownika i kliknięcia przycisku "OK", możesz ustawić wartość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> powiązań na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jak w poniższym przykładzie:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Po ustawieniu wartości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>wartość źródłowa ulega zmianie tylko wtedy, gdy aplikacja wywoła metodę <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>. Poniższy przykład pokazuje, jak wywoływać <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> dla `itemNameTextBox`:

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Tej samej metody można użyć do właściwości innych kontrolek, ale należy pamiętać, że większość innych właściwości ma domyślną wartość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Aby uzyskać więcej informacji, zobacz stronę właściwości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.

> [!NOTE]
> Właściwość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> obsługuje aktualizacje źródłowe i w związku z tym ma zastosowanie tylko do powiązań <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource>. Aby powiązania <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> działały, obiekt źródłowy musi dostarczyć powiadomienia o zmianie właściwości. Więcej informacji można znaleźć w przykładach cytowanych w tym temacie. Ponadto możesz zapoznać się z tematem [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Zobacz także

- [Tematy z instrukcjami](data-binding-how-to-topics.md)
