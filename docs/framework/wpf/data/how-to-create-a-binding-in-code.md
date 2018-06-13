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
ms.openlocfilehash: 62c5610bf5590594f34a3401b9397bb17d23f5ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556682"
---
# <a name="how-to-create-a-binding-in-code"></a>Jak utworzyć powiązanie w kodzie
W tym przykładzie pokazano, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> w kodzie.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.FrameworkElement> Klasy i <xref:System.Windows.FrameworkContentElement> klasy ujawnia zarówno `SetBinding` metody. Element, który dziedziczy z jednej z tych klas są wiązane, należy wywołać <xref:System.Windows.FrameworkElement.SetBinding%2A> metody bezpośrednio.  
  
 Poniższy przykład tworzy klasę o nazwie, `MyData`, który zawiera właściwości o nazwie `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Poniższy przykład przedstawia sposób tworzenia obiektu wiązania, aby ustawić źródło wiązania.  W przykładzie użyto <xref:System.Windows.FrameworkElement.SetBinding%2A> powiązać <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość `myText`, która jest <xref:System.Windows.Controls.TextBlock> sterowania do `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Dla przykładu kompletny kod, zobacz [tylko kod przykładowy powiązanie](http://msdn.microsoft.com/library/764aaf0b-2216-4941-9548-9c98da18d1a6).  
  
 Zamiast wywoływać metodę <xref:System.Windows.FrameworkElement.SetBinding%2A>, można użyć <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statycznej metody <xref:System.Windows.Data.BindingOperations> klasy. Poniższy przykład, wywołania <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> powiązać `myText` do `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
