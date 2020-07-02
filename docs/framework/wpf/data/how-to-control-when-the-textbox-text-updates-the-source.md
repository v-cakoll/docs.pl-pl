---
title: Jak kontrolować kiedy tekst TextBox aktualizuje źródło
description: Kontroluj chronometraż aktualizacji źródła powiązań przy użyciu właściwości UpdateSourceTrigger w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 8f6eb5beb0d14a951f6e6cf6eb81e130f5a3e194
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622786"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Jak kontrolować kiedy tekst TextBox aktualizuje źródło
W tym temacie opisano sposób użycia <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości w celu kontrolowania czasu aktualizacji źródła powiązań. Ten temat używa <xref:System.Windows.Controls.TextBox> formantu jako przykładu.

## <a name="example"></a>Przykład
 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>Właściwość ma <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> . Oznacza to, że jeśli aplikacja ma <xref:System.Windows.Controls.TextBox> Właściwość z właściwością powiązaną z danymi <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> , tekst wpisywany w programie <xref:System.Windows.Controls.TextBox> nie aktualizuje źródła do momentu <xref:System.Windows.Controls.TextBox> utraty fokusu (na przykład po kliknięciu przycisku poza <xref:System.Windows.Controls.TextBox> ).

 Jeśli chcesz, aby źródło było aktualizowane podczas pisania, ustaw dla powiązania wartość <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . W poniższym przykładzie wyróżnione wiersze kodu pokazują, że `Text` Właściwości obu <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> są powiązane z tą samą właściwością source. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Właściwość <xref:System.Windows.Controls.TextBox> powiązania jest ustawiona na wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> .

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 W efekcie <xref:System.Windows.Controls.TextBlock> wyświetla ten sam tekst (ponieważ źródło zmienia się), gdy użytkownik wprowadza tekst do obiektu <xref:System.Windows.Controls.TextBox> , jak pokazano na poniższym zrzucie ekranu przykładu:

 ![Zrzut ekranu pokazujący proste powiązanie danych.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Jeśli masz okno dialogowe lub formularz do edycji, a chcesz odroczyć aktualizacje źródłowe do momentu zakończenia edytowania pól przez użytkownika i kliknięcia przycisku "OK", możesz ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość powiązań na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> , tak jak w poniższym przykładzie:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Po ustawieniu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości na wartość <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> źródłowa zmienia się tylko wtedy, gdy aplikacja wywołuje <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metodę. Poniższy przykład pokazuje, jak wywołać <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> `itemNameTextBox` :

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Tej samej metody można użyć do właściwości innych kontrolek, ale należy pamiętać, że większość innych właściwości ma <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stronę właściwości.

> [!NOTE]
> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Właściwość obsługuje aktualizacje źródłowe i w związku z tym dotyczy tylko <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań. Dla <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań do pracy obiekt źródłowy musi dostarczyć powiadomienia o zmianie właściwości. Więcej informacji można znaleźć w przykładach cytowanych w tym temacie. Ponadto możesz zapoznać się z tematem [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Zobacz także

- [— Tematy porad](data-binding-how-to-topics.md)
