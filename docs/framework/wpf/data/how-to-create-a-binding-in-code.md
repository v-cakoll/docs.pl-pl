---
title: Jak utworzyć powiązanie w kodzie
description: Dowiedz się, jak utworzyć powiązanie w kodzie w aplikacji Windows Presentation Foundation, wywołując metodę SetBinding bezpośrednio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165807"
---
# <a name="how-to-create-a-binding-in-code"></a>Jak utworzyć powiązanie w kodzie
Ten przykład pokazuje, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> kod w kodzie.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.FrameworkElement>Klasa i <xref:System.Windows.FrameworkContentElement> Klasa uwidaczniają `SetBinding` metodę. Jeśli tworzysz powiązanie elementu, który dziedziczy jedną z tych klas, możesz wywołać <xref:System.Windows.FrameworkElement.SetBinding%2A> metodę bezpośrednio.  
  
 Poniższy przykład tworzy klasę o nazwie, `MyData` , która zawiera właściwość o nazwie `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Poniższy przykład pokazuje, jak utworzyć obiekt powiązania, aby ustawić źródło powiązania.  W przykładzie używa <xref:System.Windows.FrameworkElement.SetBinding%2A> się do powiązania <xref:System.Windows.Controls.TextBlock.Text%2A> właściwości `myText` , która jest <xref:System.Windows.Controls.TextBlock> formantem, do `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Aby uzyskać pełny przykład kodu, zobacz [przykład powiązania tylko z kodem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Zamiast wywoływania <xref:System.Windows.FrameworkElement.SetBinding%2A> , można użyć <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statycznej metody <xref:System.Windows.Data.BindingOperations> klasy. Poniższy przykład wywołuje <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> powiązań z `myText` `myDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
