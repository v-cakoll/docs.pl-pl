---
title: 'Instrukcje: Określ źródło wiążące'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 105924fec2956f2f74a2a574ee62f71a37df9366
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356724"
---
# <a name="how-to-specify-the-binding-source"></a>Instrukcje: Określ źródło wiążące
W powiązaniu danych obiektu źródłowego powiązania odnosi się do obiektu, który można uzyskać danych z. W tym temacie opisano różne sposoby określania źródło wiążące.  
  
## <a name="example"></a>Przykład  
 Wspólne źródło są wiązane kilka właściwości, chcesz użyć `DataContext` właściwość, która zapewnia wygodny sposób do ustalenia zakresu, w którym wszystkie właściwości powiązanych z danymi dziedziczą wspólne źródło.  
  
 W poniższym przykładzie kontekst danych zostanie nawiązane dla elementu głównego aplikacji. Dzięki temu wszystkie elementy podrzędne, które dziedziczy ten kontekst danych. Dane dla wiązania pochodzą z klasą danych niestandardowych `NetIncome`, do których odwołuje się bezpośrednio za pomocą mapowania i podany klucz zasobu `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 W poniższym przykładzie pokazano definicję `NetIncome` klasy.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  Powyższy przykład tworzy wystąpienie obiektu w znacznikach i używa go jako zasób. Jeśli chcesz powiązać z obiektu, który utworzono już wystąpienie w kodzie, musisz ustawić `DataContext` właściwość programowo. Aby uzyskać przykład, zobacz [wprowadzić dostępne dane do powiązania w XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Alternatywnie Jeśli chcesz określić źródło na swoje indywidualne powiązania jawnie, masz następujące opcje. Te pierwszeństwo kontekstu danych dziedziczonych.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Używasz tej właściwości można ustawić źródła do wystąpienia obiektu. Jeśli nie potrzebujesz funkcji ustalenia zakresu w kilka właściwości, które dziedziczy ten sam kontekst danych, możesz użyć <xref:System.Windows.Data.Binding.Source%2A> właściwości zamiast `DataContext` właściwości. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Jest to przydatne, jeśli chcesz określić źródło, względem których urządzenie docelowe powiązania jest. Kilka typowych scenariuszy, w których mogą używać tej właściwości jest, jeśli chcesz powiązać jedną właściwość elementu do innej właściwości tego samego elementu lub Jeśli powiązanie jest definiowany w stylu lub szablonu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Należy określić ciąg, który reprezentuje element, który chcesz powiązać. Jest to przydatne, jeśli chcesz powiązać właściwości innego elementu w swojej aplikacji. Na przykład, jeśli chcesz użyć <xref:System.Windows.Controls.Slider> kontrolować jego wysokość innej kontrolki w aplikacji, lub jeśli chcesz powiązać <xref:System.Windows.Controls.ContentControl.Content%2A> kontrolki do <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości usługi <xref:System.Windows.Controls.ListBox> kontroli. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Dziedziczenie wartości właściwości](../advanced/property-value-inheritance.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Powiązanie deklaracji — omówienie](binding-declarations-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
