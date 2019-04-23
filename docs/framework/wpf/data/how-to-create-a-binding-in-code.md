---
title: 'Instrukcje: Tworzenie powiązania w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 57ec845c5c9a5bddb801428b9ecde035a97cf447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089266"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="54b80-102">Instrukcje: Tworzenie powiązania w kodzie</span><span class="sxs-lookup"><span data-stu-id="54b80-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="54b80-103">W tym przykładzie pokazano, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="54b80-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54b80-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="54b80-104">Example</span></span>  
 <span data-ttu-id="54b80-105"><xref:System.Windows.FrameworkElement> Klasy i <xref:System.Windows.FrameworkContentElement> klasy zarówno ujawnić `SetBinding` metody.</span><span class="sxs-lookup"><span data-stu-id="54b80-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="54b80-106">Są wiązane element, który dziedziczy z jednej z tych klas, można wywołać <xref:System.Windows.FrameworkElement.SetBinding%2A> bezpośrednio metodę.</span><span class="sxs-lookup"><span data-stu-id="54b80-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="54b80-107">Poniższy przykład tworzy klasę o nazwie `MyData`, który zawiera właściwość o nazwie `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="54b80-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="54b80-108">Poniższy przykład pokazuje, jak utworzyć obiekt wiążący, aby ustawić źródło wiązania.</span><span class="sxs-lookup"><span data-stu-id="54b80-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="54b80-109">W przykładzie użyto <xref:System.Windows.FrameworkElement.SetBinding%2A> powiązać <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość `myText`, czyli <xref:System.Windows.Controls.TextBlock> sterowania do `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="54b80-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="54b80-110">Aby uzyskać cały przykładowy kod, zobacz [tylko kod przykładowy powiązanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="54b80-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="54b80-111">Zamiast wywoływać metodę <xref:System.Windows.FrameworkElement.SetBinding%2A>, możesz użyć <xref:System.Windows.Data.BindingOperations.SetBinding%2A> metoda statyczna <xref:System.Windows.Data.BindingOperations> klasy.</span><span class="sxs-lookup"><span data-stu-id="54b80-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="54b80-112">Poniższy przykład, wywołania <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> powiązać `myText` do `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="54b80-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="54b80-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54b80-113">See also</span></span>

- [<span data-ttu-id="54b80-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="54b80-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="54b80-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="54b80-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
