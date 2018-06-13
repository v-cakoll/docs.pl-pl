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
ms.openlocfilehash: 333a85bc59ded3fd42bef6aff5845c9a6ddeb49b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556877"
---
# <a name="how-to-specify-the-binding-source"></a>Jak określić źródło wiążące
W powiązaniu danych powiązania obiektu źródłowego odwołuje się do obiektu, do którego można uzyskać danych. W tym temacie opisano różne sposoby określania źródła powiązania.  
  
## <a name="example"></a>Przykład  
 Wspólne źródło są wiązane kilka właściwości, chcesz użyć `DataContext` właściwość, która umożliwia dogodny do ustalenia zakresu, w którym wszystkie właściwości powiązanych z danymi dziedziczą wspólne źródło.  
  
 W poniższym przykładzie kontekst danych jest określana w elemencie głównym aplikacji. Dzięki temu wszystkie elementy podrzędne dziedziczenia tego kontekstu danych. Dane dla powiązania pochodzi z klasy danych niestandardowych, `NetIncome`, do których odwołuje się bezpośrednio za pomocą mapowania i podany klucz zasobów `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 W poniższym przykładzie przedstawiono definicję `NetIncome` klasy.  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  Powyższy przykład tworzy wystąpienie obiektu w znaczniku i używa go jako zasób. Jeśli chcesz powiązać obiektu, który ma już wystąpienie w kodzie, musisz ustawić `DataContext` właściwości programowo. Na przykład zobacz [upewnij dostępnych danych dla powiązania w języku XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).  
  
 Alternatywnie Jeśli chcesz określić źródło powiązania poszczególnych jawnie, dostępne są następujące opcje. Te pierwszeństwo kontekstu danych dziedziczone.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Ta właściwość umożliwia ustawione źródło na wystąpienie obiektu. Jeśli nie potrzebujesz funkcji ustalenia zakresu w kilka właściwości, które dziedziczą z tego samego kontekstu danych, możesz użyć <xref:System.Windows.Data.Binding.Source%2A> właściwości zamiast `DataContext` właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Jest to przydatne, jeśli chcesz określić źródło względem gdzie to urządzenie docelowe powiązania. Niektóre typowe scenariusze, w których może używać tej właściwości jest należy powiązać jedną właściwość z elementu inną właściwość tego samego elementu, lub Jeśli powiązanie są definiowane w stylu lub w szablonie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Należy określić ciąg, który reprezentuje element, który chcesz utworzyć powiązania. Jest to przydatne, jeśli chcesz powiązać z właściwością innego elementu w swojej aplikacji. Na przykład, jeśli chcesz użyć <xref:System.Windows.Controls.Slider> mogą kontrolować jego wysokość formantem w aplikacji lub jeśli chcesz powiązać <xref:System.Windows.Controls.ContentControl.Content%2A> kontroli w celu <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości użytkownika <xref:System.Windows.Controls.ListBox> formantu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [Dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Powiązanie deklaracji — omówienie](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
