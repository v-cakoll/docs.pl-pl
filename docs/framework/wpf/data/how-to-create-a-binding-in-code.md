---
title: Jak utworzyć powiązanie w kodzie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458845"
---
# <a name="how-to-create-a-binding-in-code"></a>Jak utworzyć powiązanie w kodzie
Ten przykład pokazuje, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> w kodzie.  
  
## <a name="example"></a>Przykład  
 Klasa <xref:System.Windows.FrameworkElement> i Klasa <xref:System.Windows.FrameworkContentElement> uwidaczniają metodę `SetBinding`. W przypadku powiązania elementu, który dziedziczy jedną z tych klas, można wywołać metodę <xref:System.Windows.FrameworkElement.SetBinding%2A> bezpośrednio.  
  
 Poniższy przykład tworzy klasę o nazwie, `MyData`, która zawiera właściwość o nazwie `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Poniższy przykład pokazuje, jak utworzyć obiekt powiązania, aby ustawić źródło powiązania.  W przykładzie używa się <xref:System.Windows.FrameworkElement.SetBinding%2A>, aby powiązać Właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> `myText`, która jest kontrolką <xref:System.Windows.Controls.TextBlock>, `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Aby uzyskać pełny przykład kodu, zobacz [przykład powiązania tylko z kodem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Zamiast wywoływania <xref:System.Windows.FrameworkElement.SetBinding%2A>, można użyć metody statycznej <xref:System.Windows.Data.BindingOperations.SetBinding%2A> klasy <xref:System.Windows.Data.BindingOperations>. Poniższy przykład wywołuje <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>, a nie <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>, aby powiązać `myText` z `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
