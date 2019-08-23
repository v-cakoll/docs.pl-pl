---
title: 'Instrukcje: Kontrolowanie momentu aktualizowania źródła tekstu kontrolki TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966443"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Instrukcje: Kontrolowanie momentu aktualizowania źródła tekstu kontrolki TextBox
W tym temacie opisano sposób użycia <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości w celu kontrolowania czasu aktualizacji źródła powiązań. Ten temat używa <xref:System.Windows.Controls.TextBox> formantu jako przykładu.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Właściwość ma <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>wartość domyślną. Oznacza to, że aplikacja ma <xref:System.Windows.Controls.TextBox> powiązane <xref:System.Windows.Controls.TextBox>z danymi.<xref:System.Windows.Controls.TextBox.Text%2A> , tekst wpisywany w <xref:System.Windows.Controls.TextBox> programie <xref:System.Windows.Controls.TextBox>nie aktualizuje źródła <xref:System.Windows.Controls.TextBox> do momentu utraty fokusu (na przykład po kliknięciu poza).  
  
 Jeśli chcesz, aby źródło było aktualizowane podczas pisania, ustaw <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> dla <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>powiązania wartość. W poniższym przykładzie wyróżnione wiersze kodu pokazują, że `Text` właściwości <xref:System.Windows.Controls.TextBox> obu i <xref:System.Windows.Controls.TextBlock> są powiązane z tą samą właściwością source. Właściwość powiązania jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>wartość. <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 W efekcie <xref:System.Windows.Controls.TextBlock> wyświetla ten sam tekst (ponieważ źródło zmienia się), gdy użytkownik wprowadza tekst <xref:System.Windows.Controls.TextBox>do obiektu, jak pokazano na poniższym zrzucie ekranu przykładu:  
  
 ![Zrzut ekranu pokazujący proste powiązanie danych.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 Jeśli masz okno dialogowe lub formularz do edycji, a chcesz odroczyć aktualizacje źródłowe do momentu zakończenia edytowania pól przez użytkownika i kliknięcia przycisku "OK", możesz ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość powiązań na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, tak jak w poniższym przykładzie:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Po ustawieniu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości na <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>wartość źródłowa zmienia się tylko <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> wtedy, gdy aplikacja wywołuje metodę. Poniższy przykład pokazuje, jak wywołać <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>: `itemNameTextBox`  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> Tej samej metody można użyć do właściwości innych kontrolek, ale należy pamiętać, że większość innych właściwości ma <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>wartość domyślną. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stronę właściwości.  
  
> [!NOTE]
> Właściwość obsługuje aktualizacje źródłowe i w związku z tym dotyczy tylko <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Dla <xref:System.Windows.Data.BindingMode.TwoWay> i<xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań do pracy obiekt źródłowy musi dostarczyć powiadomienia o zmianie właściwości. Więcej informacji można znaleźć w przykładach cytowanych w tym temacie. Ponadto możesz zapoznać się z tematem [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tematy z instrukcjami](data-binding-how-to-topics.md)
