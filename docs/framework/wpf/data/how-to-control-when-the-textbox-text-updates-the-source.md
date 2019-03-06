---
title: 'Instrukcje: Kontroluj kiedy tekst TextBox aktualizuje źródło'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 702f06a37aa98e3a84858a590655e8a4311cfa48
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362139"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Instrukcje: Kontroluj kiedy tekst TextBox aktualizuje źródło
W tym temacie opisano sposób użycia <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości, aby kontrolować chronometraż aktualizacji źródła powiązania. Temat używa <xref:System.Windows.Controls.TextBox> kontroli jako przykład.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Właściwość ma wartość domyślną <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Oznacza to, czy aplikacja ma <xref:System.Windows.Controls.TextBox> z wiązaniem danych <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Właściwość, można wpisać w tekst <xref:System.Windows.Controls.TextBox> nie aktualizuje źródło do momentu <xref:System.Windows.Controls.TextBox> traci fokus (na przykład po kliknięciu opuszczenie <xref:System.Windows.Controls.TextBox>).  
  
 Źródło aktualizacji podczas wpisywania, ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wiązania <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. W poniższym przykładzie wyróżnione wiersze kodu pokazują, że `Text` właściwościach <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> są powiązane z tej samej właściwości źródła. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość <xref:System.Windows.Controls.TextBox> powiązania jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 W rezultacie <xref:System.Windows.Controls.TextBlock> pokazuje ten sam tekst (z powodu zmiany pliku źródłowego), co użytkownik musi wprowadzić tekst do <xref:System.Windows.Controls.TextBox>, jak pokazano na poniższym zrzucie ekranu przykładu:  
  
 ![Zrzut ekranu przedstawiający przykładowe powiązania danych proste](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Jeśli okno dialogowe lub można edytować użytkownika formularza i mają być odroczone aktualizacje źródła, dopóki użytkownik nie jest gotowy, edycja pól i kliknie przycisk "OK", można ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości wiązania tak, aby <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jak w poniższym przykładzie:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Po ustawieniu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, wartość źródłowa zmienia się tylko wtedy, gdy aplikacja wywołuje <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metody. Poniższy przykład pokazuje sposób wywoływania <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> dla `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Użyj tej samej techniki dla właściwości innych kontrolek, ale należy pamiętać, że inne właściwości mają domyślne <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> stronę właściwości.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość dotyczy źródło aktualizacji i dlatego ma zastosowanie tylko dla <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania. Aby uzyskać <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania do pracy źródła obiektu musi zapewniać powiadomienia o zmianie właściwości. Mogą odwoływać się do przykładów wymienionych w tym temacie, aby uzyskać więcej informacji. Ponadto można przyjrzeć się [powiadomienie o zmianie właściwości Implementowanie](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Zobacz także
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
