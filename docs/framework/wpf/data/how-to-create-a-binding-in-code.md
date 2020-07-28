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
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="973c9-103">Jak utworzyć powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="973c9-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="973c9-104">Ten przykład pokazuje, jak utworzyć i ustawić <xref:System.Windows.Data.Binding> kod w kodzie.</span><span class="sxs-lookup"><span data-stu-id="973c9-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="973c9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="973c9-105">Example</span></span>  
 <span data-ttu-id="973c9-106"><xref:System.Windows.FrameworkElement>Klasa i <xref:System.Windows.FrameworkContentElement> Klasa uwidaczniają `SetBinding` metodę.</span><span class="sxs-lookup"><span data-stu-id="973c9-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="973c9-107">Jeśli tworzysz powiązanie elementu, który dziedziczy jedną z tych klas, możesz wywołać <xref:System.Windows.FrameworkElement.SetBinding%2A> metodę bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="973c9-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="973c9-108">Poniższy przykład tworzy klasę o nazwie, `MyData` , która zawiera właściwość o nazwie `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="973c9-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="973c9-109">Poniższy przykład pokazuje, jak utworzyć obiekt powiązania, aby ustawić źródło powiązania.</span><span class="sxs-lookup"><span data-stu-id="973c9-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="973c9-110">W przykładzie używa <xref:System.Windows.FrameworkElement.SetBinding%2A> się do powiązania <xref:System.Windows.Controls.TextBlock.Text%2A> właściwości `myText` , która jest <xref:System.Windows.Controls.TextBlock> formantem, do `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="973c9-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="973c9-111">Aby uzyskać pełny przykład kodu, zobacz [przykład powiązania tylko z kodem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="973c9-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="973c9-112">Zamiast wywoływania <xref:System.Windows.FrameworkElement.SetBinding%2A> , można użyć <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statycznej metody <xref:System.Windows.Data.BindingOperations> klasy.</span><span class="sxs-lookup"><span data-stu-id="973c9-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="973c9-113">Poniższy przykład wywołuje <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> powiązań z `myText` `myDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="973c9-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="973c9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="973c9-114">See also</span></span>

- [<span data-ttu-id="973c9-115">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="973c9-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="973c9-116">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="973c9-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
