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
ms.openlocfilehash: 6af87f1d6b8c4ee781c65d5a75872e8a72a02390
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747706"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="c6368-102">Instrukcje: Utwórz powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="c6368-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="c6368-103">W tym przykładzie pokazano, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c6368-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6368-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6368-104">Example</span></span>  
 <span data-ttu-id="c6368-105"><xref:System.Windows.FrameworkElement> Klasy i <xref:System.Windows.FrameworkContentElement> klasy zarówno ujawnić `SetBinding` metody.</span><span class="sxs-lookup"><span data-stu-id="c6368-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="c6368-106">Są wiązane element, który dziedziczy z jednej z tych klas, można wywołać <xref:System.Windows.FrameworkElement.SetBinding%2A> bezpośrednio metodę.</span><span class="sxs-lookup"><span data-stu-id="c6368-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="c6368-107">Poniższy przykład tworzy klasę o nazwie `MyData`, który zawiera właściwość o nazwie `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="c6368-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="c6368-108">Poniższy przykład pokazuje, jak utworzyć obiekt wiążący, aby ustawić źródło wiązania.</span><span class="sxs-lookup"><span data-stu-id="c6368-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="c6368-109">W przykładzie użyto <xref:System.Windows.FrameworkElement.SetBinding%2A> powiązać <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość `myText`, czyli <xref:System.Windows.Controls.TextBlock> sterowania do `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="c6368-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="c6368-110">Aby uzyskać cały przykładowy kod, zobacz [tylko kod przykładowy powiązanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c6368-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="c6368-111">Zamiast wywoływać metodę <xref:System.Windows.FrameworkElement.SetBinding%2A>, możesz użyć <xref:System.Windows.Data.BindingOperations.SetBinding%2A> metoda statyczna <xref:System.Windows.Data.BindingOperations> klasy.</span><span class="sxs-lookup"><span data-stu-id="c6368-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="c6368-112">Poniższy przykład, wywołania <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> powiązać `myText` do `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="c6368-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="c6368-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6368-113">See also</span></span>
- [<span data-ttu-id="c6368-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="c6368-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c6368-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c6368-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
