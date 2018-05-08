---
title: Jak powiązać z metodą
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 58e243812f9c2dcb65dc37bfd50d9bcfb124e4f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-a-method"></a>Jak powiązać z metodą
Poniższy przykład pokazuje, jak można powiązać je przy użyciu metody <xref:System.Windows.Data.ObjectDataProvider>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `TemperatureScale` jest klasa, która ma metodę `ConvertTemp`, który przyjmuje dwa parametry (jeden z `double` i jeden z `enum` typu `TempType)` i konwertuje jeden temperatury skali podanej wartości. W poniższym przykładzie <xref:System.Windows.Data.ObjectDataProvider> służy do tworzenia wystąpienia `TemperatureScale` obiektu. `ConvertTemp` Metoda jest wywoływana z dwóch określonych parametrów.  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Teraz, że metoda jest dostępna jako zasób, można powiązać jej wyników. W poniższym przykładzie <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z <xref:System.Windows.Controls.ComboBox> są powiązane z dwa parametry metody. Umożliwia użytkownikom określanie temperatury do przekonwertowania i skali temperatury do przekonwertowania z. Należy pamiętać, że <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> ustawiono `true` ponieważ firma Microsoft powiązanie <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> właściwość <xref:System.Windows.Data.ObjectDataProvider> wystąpienie i nie właściwości obiektu opakowane przez <xref:System.Windows.Data.ObjectDataProvider> ( `TemperatureScale` obiektu).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Ostatniego <xref:System.Windows.Controls.Label> aktualizuje, gdy użytkownik modyfikuje zawartość <xref:System.Windows.Controls.TextBox> lub wybór <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Konwerter `DoubleToString` przyjmuje wartość o podwójnej precyzji i konwertuje go na ciąg w <xref:System.Windows.Data.IValueConverter.Convert%2A> kierunek (ze źródła powiązanie do powiązania obiektu docelowego, który jest <xref:System.Windows.Controls.TextBox.Text%2A> właściwości) i konwertuje `string` do `double` w <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> kierunek.  
  
 `InvalidationCharacterRule` Jest <xref:System.Windows.Controls.ValidationRule> kontrole nieprawidłowych znaków. Domyślny szablon błędów, który jest czerwonego obramowania wokół <xref:System.Windows.Controls.TextBox>, wydaje się powiadamianie użytkowników o wartość wejściowa nie jest wartość typu double.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Powiązywanie z wyliczeniem](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
