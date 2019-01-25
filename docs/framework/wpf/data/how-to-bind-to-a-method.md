---
title: 'Instrukcje: Powiąż z metodą'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: afa7801709d733ed40389f240fa5d92a2557c7a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732079"
---
# <a name="how-to-bind-to-a-method"></a>Instrukcje: Powiąż z metodą
Poniższy przykład pokazuje, jak powiązać przy użyciu metody <xref:System.Windows.Data.ObjectDataProvider>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `TemperatureScale` to klasa, która ma metodę `ConvertTemp`, który przyjmuje dwa parametry (jeden z `double` i jeden z `enum` typu `TempType)` i konwertuje skalowania jednej temperatury danej wartości. W poniższym przykładzie <xref:System.Windows.Data.ObjectDataProvider> służy do tworzenia wystąpienia `TemperatureScale` obiektu. `ConvertTemp` Metoda jest wywoływana z dwóch określonych parametrów.  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Teraz, gdy metoda jest dostępna jako zasób, można powiązać jej wyników. W poniższym przykładzie <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> są powiązane z dwóch parametrów metody. Umożliwia użytkownikom na określenie temperatury do konwersji i skalowania temperatury do konwersji z. Należy pamiętać, że <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> ustawiono `true` ponieważ możemy dokonywane jest wiązanie <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> właściwość <xref:System.Windows.Data.ObjectDataProvider> wystąpienia i nie właściwości obiektu opakowane przez <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` obiektu).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Ostatniego <xref:System.Windows.Controls.Label> aktualizuje, gdy użytkownik modyfikuje zawartość <xref:System.Windows.Controls.TextBox> lub wybór <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Konwerter `DoubleToString` przyjmuje wartość o podwójnej precyzji i konwertuje go na ciąg w <xref:System.Windows.Data.IValueConverter.Convert%2A> kierunek (od źródła powiązania cel wiążący, który jest <xref:System.Windows.Controls.TextBox.Text%2A> właściwości) i konwertuje `string` do `double` w <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> kierunek.  
  
 `InvalidationCharacterRule` Jest <xref:System.Windows.Controls.ValidationRule> , sprawdza, czy nieprawidłowe znaki. Domyślny szablon błędów, czyli czerwone obramowanie wokół <xref:System.Windows.Controls.TextBox>, pojawi się powiadomienie użytkowników, gdy wartość wejściowa nie jest wartość typu double.  
  
## <a name="see-also"></a>Zobacz także
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
- [Powiązywanie z wyliczeniem](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
