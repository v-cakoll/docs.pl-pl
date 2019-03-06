---
title: 'Instrukcje: Utwórz powiązanie w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 666dbb4e2de0e8a7a83d6e0dfda50822cfdfd860
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371193"
---
# <a name="how-to-create-a-binding-in-code"></a>Instrukcje: Utwórz powiązanie w kodzie
W tym przykładzie pokazano, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> w kodzie.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.FrameworkElement> Klasy i <xref:System.Windows.FrameworkContentElement> klasy zarówno ujawnić `SetBinding` metody. Są wiązane element, który dziedziczy z jednej z tych klas, można wywołać <xref:System.Windows.FrameworkElement.SetBinding%2A> bezpośrednio metodę.  
  
 Poniższy przykład tworzy klasę o nazwie `MyData`, który zawiera właściwość o nazwie `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Poniższy przykład pokazuje, jak utworzyć obiekt wiążący, aby ustawić źródło wiązania.  W przykładzie użyto <xref:System.Windows.FrameworkElement.SetBinding%2A> powiązać <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość `myText`, czyli <xref:System.Windows.Controls.TextBlock> sterowania do `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Aby uzyskać cały przykładowy kod, zobacz [tylko kod przykładowy powiązanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Zamiast wywoływać metodę <xref:System.Windows.FrameworkElement.SetBinding%2A>, możesz użyć <xref:System.Windows.Data.BindingOperations.SetBinding%2A> metoda statyczna <xref:System.Windows.Data.BindingOperations> klasy. Poniższy przykład, wywołania <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> powiązać `myText` do `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
