---
title: Jak określić źródło wiążące
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 4fde66b22bac6b4a2cfeb4eceb50027daadee387
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454366"
---
# <a name="how-to-specify-the-binding-source"></a>Jak określić źródło wiążące
W powiązaniu danych obiekt źródłowy powiązania odwołuje się do obiektu, z którego uzyskujesz dane. W tym temacie opisano różne sposoby określania źródła powiązania.  
  
## <a name="example"></a>Przykład  
 Jeśli powiążesz kilka właściwości ze wspólnym źródłem, chcesz użyć właściwości `DataContext`, która zapewnia wygodny sposób ustanowienia zakresu, w którym wszystkie właściwości powiązane z danymi dziedziczą wspólne źródło.  
  
 W poniższym przykładzie kontekst danych jest ustanowiony w elemencie głównym aplikacji. Dzięki temu wszystkie elementy podrzędne będą dziedziczyły ten kontekst danych. Dane dla powiązania pochodzą z niestandardowej klasy danych, `NetIncome`, do której odwołuje się bezpośrednio przy użyciu mapowania i nadanego klucza zasobu `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Poniższy przykład przedstawia definicję klasy `NetIncome`.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> Powyższy przykład tworzy wystąpienie obiektu w znaczniku i używa go jako zasobu. Jeśli chcesz utworzyć powiązanie z obiektem, który został już utworzony w kodzie, należy ustawić właściwość `DataContext` programowo. Aby zapoznać się z przykładem, zobacz [udostępnianie danych do powiązania w języku XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Alternatywnie, jeśli chcesz jawnie określić źródło dla konkretnych powiązań, masz następujące opcje. Mają pierwszeństwo przed dziedziczonym kontekstem danych.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Ta właściwość służy do ustawiania źródła do wystąpienia obiektu. Jeśli nie potrzebujesz funkcji ustanawiania zakresu, w którym kilka właściwości dziedziczy ten sam kontekst danych, możesz użyć właściwości <xref:System.Windows.Data.Binding.Source%2A> zamiast właściwości `DataContext`. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Jest to przydatne, gdy chcesz określić źródło względem lokalizacji docelowej powiązania. Niektóre typowe scenariusze, w których można użyć tej właściwości, można powiązać z jedną właściwością elementu z inną właściwością tego samego elementu lub w przypadku definiowania powiązania w stylu lub szablonie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Należy określić ciąg, który reprezentuje element, z którym ma zostać utworzone powiązanie. Jest to przydatne, gdy chcesz powiązać z właściwością innego elementu w aplikacji. Na przykład, jeśli chcesz użyć <xref:System.Windows.Controls.Slider>, aby kontrolować wysokość innej kontrolki w aplikacji, lub jeśli chcesz powiązać <xref:System.Windows.Controls.ContentControl.Content%2A> formantu z właściwością <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> formantu <xref:System.Windows.Controls.ListBox>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Dziedziczenie wartości właściwości](../advanced/property-value-inheritance.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Powiązanie deklaracji — omówienie](binding-declarations-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
