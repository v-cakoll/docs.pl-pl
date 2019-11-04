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
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="0414a-102">Jak utworzyć powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="0414a-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="0414a-103">Ten przykład pokazuje, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0414a-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0414a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0414a-104">Example</span></span>  
 <span data-ttu-id="0414a-105">Klasa <xref:System.Windows.FrameworkElement> i Klasa <xref:System.Windows.FrameworkContentElement> uwidaczniają metodę `SetBinding`.</span><span class="sxs-lookup"><span data-stu-id="0414a-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="0414a-106">W przypadku powiązania elementu, który dziedziczy jedną z tych klas, można wywołać metodę <xref:System.Windows.FrameworkElement.SetBinding%2A> bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="0414a-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="0414a-107">Poniższy przykład tworzy klasę o nazwie, `MyData`, która zawiera właściwość o nazwie `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="0414a-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="0414a-108">Poniższy przykład pokazuje, jak utworzyć obiekt powiązania, aby ustawić źródło powiązania.</span><span class="sxs-lookup"><span data-stu-id="0414a-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="0414a-109">W przykładzie używa się <xref:System.Windows.FrameworkElement.SetBinding%2A>, aby powiązać Właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> `myText`, która jest kontrolką <xref:System.Windows.Controls.TextBlock>, `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="0414a-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="0414a-110">Aby uzyskać pełny przykład kodu, zobacz [przykład powiązania tylko z kodem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0414a-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="0414a-111">Zamiast wywoływania <xref:System.Windows.FrameworkElement.SetBinding%2A>, można użyć metody statycznej <xref:System.Windows.Data.BindingOperations.SetBinding%2A> klasy <xref:System.Windows.Data.BindingOperations>.</span><span class="sxs-lookup"><span data-stu-id="0414a-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="0414a-112">Poniższy przykład wywołuje <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>, a nie <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>, aby powiązać `myText` z `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="0414a-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="0414a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0414a-113">See also</span></span>

- [<span data-ttu-id="0414a-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="0414a-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="0414a-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0414a-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
