---
title: Jak powiązać z metodą
description: Postępuj zgodnie z tym przykładem, aby dowiedzieć się, jak powiązać metodę obiektu w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619601"
---
# <a name="how-to-bind-to-a-method"></a>Jak powiązać z metodą
Poniższy przykład pokazuje, jak powiązać z metodą przy użyciu <xref:System.Windows.Data.ObjectDataProvider> .  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `TemperatureScale` jest klasą, która ma metodę `ConvertTemp` , która przyjmuje dwa parametry (jeden z `double` i jeden z `enum` typów `TempType)` i konwertuje daną wartość z jednej skali temperatury na inną. W poniższym przykładzie <xref:System.Windows.Data.ObjectDataProvider> jest używany do tworzenia wystąpienia `TemperatureScale` obiektu. `ConvertTemp`Metoda jest wywoływana z dwoma określonymi parametrami.  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Teraz, gdy metoda jest dostępna jako zasób, można powiązać z jej wynikami. W poniższym przykładzie <xref:System.Windows.Controls.TextBox.Text%2A> Właściwość <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> elementu <xref:System.Windows.Controls.ComboBox> są powiązane z dwoma parametrami metody. Pozwala to użytkownikom na określenie temperatury do przekonwertowania oraz skali temperatury, z której ma zostać przeprowadzona konwersja. Należy pamiętać, że <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> jest ustawiona na, `true` ponieważ są one powiązane z <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> właściwością <xref:System.Windows.Data.ObjectDataProvider> wystąpienia i nie są właściwościami obiektu opakowanego przez <xref:System.Windows.Data.ObjectDataProvider> `TemperatureScale` obiekt (obiektu).  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>Ostatniej <xref:System.Windows.Controls.Label> aktualizacji, gdy użytkownik modyfikuje zawartość <xref:System.Windows.Controls.TextBox> lub zaznaczenie <xref:System.Windows.Controls.ComboBox> .  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Konwerter `DoubleToString` przyjmuje wartość podwójną i włącza ją do ciągu w <xref:System.Windows.Data.IValueConverter.Convert%2A> kierunku (ze źródła powiązania do powiązania docelowego, który jest <xref:System.Windows.Controls.TextBox.Text%2A> właściwością) i konwertuje `string` do na `double` w <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> kierunku.  
  
 `InvalidationCharacterRule`Jest <xref:System.Windows.Controls.ValidationRule> sprawdzana pod kątem nieprawidłowych znaków. Domyślny szablon błędu, który jest czerwonym obramowaniem wokół <xref:System.Windows.Controls.TextBox> , pojawia się, aby powiadomić użytkowników, gdy wartość wejściowa nie jest wartością podwójną.  
  
## <a name="see-also"></a>Zobacz także

- [— Tematy porad](data-binding-how-to-topics.md)
- [Powiąż z wyliczeniem](how-to-bind-to-an-enumeration.md)
