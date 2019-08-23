---
title: 'Instrukcje: Określanie obiektu źródłowego powiązania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 418dc77ce7638698d4850b06dafcea57787e1015
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959699"
---
# <a name="how-to-specify-the-binding-source"></a>Instrukcje: Określanie obiektu źródłowego powiązania
W powiązaniu danych obiekt źródłowy powiązania odwołuje się do obiektu, z którego uzyskujesz dane. W tym temacie opisano różne sposoby określania źródła powiązania.  
  
## <a name="example"></a>Przykład  
 Jeśli powiążesz kilka właściwości ze wspólnym źródłem, chcesz użyć `DataContext` właściwości, która zapewnia wygodny sposób ustanowienia zakresu, w którym wszystkie właściwości powiązane z danymi dziedziczą wspólne źródło.  
  
 W poniższym przykładzie kontekst danych jest ustanowiony w elemencie głównym aplikacji. Dzięki temu wszystkie elementy podrzędne będą dziedziczyły ten kontekst danych. Dane dla powiązania pochodzą z niestandardowej klasy danych, `NetIncome`do których odwołuje się bezpośrednio za pomocą mapowania i podanego `incomeDataSource`klucza zasobu.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 W poniższym przykładzie przedstawiono definicję `NetIncome` klasy.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> Powyższy przykład tworzy wystąpienie obiektu w znaczniku i używa go jako zasobu. Jeśli chcesz powiązać z obiektem, który został już utworzony w kodzie, należy ustawić `DataContext` właściwość programowo. Aby zapoznać się z przykładem, zobacz [udostępnianie danych do powiązania w języku XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Alternatywnie, jeśli chcesz jawnie określić źródło dla konkretnych powiązań, masz następujące opcje. Mają pierwszeństwo przed dziedziczonym kontekstem danych.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Ta właściwość służy do ustawiania źródła do wystąpienia obiektu. Jeśli nie potrzebujesz funkcji ustanawiania zakresu, w którym kilka właściwości dziedziczy ten sam kontekst danych, możesz użyć <xref:System.Windows.Data.Binding.Source%2A> właściwości zamiast `DataContext` właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Jest to przydatne, gdy chcesz określić źródło względem lokalizacji docelowej powiązania. Niektóre typowe scenariusze, w których można użyć tej właściwości, można powiązać z jedną właściwością elementu z inną właściwością tego samego elementu lub w przypadku definiowania powiązania w stylu lub szablonie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Należy określić ciąg, który reprezentuje element, z którym ma zostać utworzone powiązanie. Jest to przydatne, gdy chcesz powiązać z właściwością innego elementu w aplikacji. Na przykład, <xref:System.Windows.Controls.Slider> Jeśli chcesz użyć elementu, aby kontrolować wysokość innej kontrolki w aplikacji, lub jeśli chcesz <xref:System.Windows.Controls.ContentControl.Content%2A> powiązać formant <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> z właściwością <xref:System.Windows.Controls.ListBox> kontrolki. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Dziedziczenie wartości właściwości](../advanced/property-value-inheritance.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Powiązanie deklaracji — omówienie](binding-declarations-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
