---
title: Jak pobrać obiekt wiążący z powiązanej własności docelowej
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7cebaf1077fb66420d77d656db32f444dd932b85
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874075"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="81865-102">Jak pobrać obiekt wiążący z powiązanej własności docelowej</span><span class="sxs-lookup"><span data-stu-id="81865-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="81865-103">W tym przykładzie pokazano, jak uzyskać obiekt wiążący z właściwością target powiązanych z danymi.</span><span class="sxs-lookup"><span data-stu-id="81865-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81865-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="81865-104">Example</span></span>  
 <span data-ttu-id="81865-105">Można wykonać następujące polecenie, aby pobrać <xref:System.Windows.Data.Binding> obiektu:</span><span class="sxs-lookup"><span data-stu-id="81865-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  <span data-ttu-id="81865-106">Należy określić właściwość zależności dla powiązania, który ma, ponieważ istnieje możliwość, że więcej niż jednej właściwości obiektu docelowego jest używanie powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="81865-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="81865-107">Alternatywnie, możesz uzyskać <xref:System.Windows.Data.BindingExpression> , a następnie wartość <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="81865-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="81865-108">Aby uzyskać kompletny przykład zobacz [powiązania przykładowych weryfikacji](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="81865-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81865-109">Jeśli Twoje powiązanie <xref:System.Windows.Data.MultiBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="81865-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="81865-110">Jeśli jest <xref:System.Windows.Data.PriorityBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="81865-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="81865-111">Jeśli masz pewności, czy właściwość docelowa jest powiązany, za pomocą <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, lub <xref:System.Windows.Data.PriorityBinding>, możesz użyć <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="81865-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81865-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81865-112">See Also</span></span>  
 [<span data-ttu-id="81865-113">Tworzenie powiązania w kodzie</span><span class="sxs-lookup"><span data-stu-id="81865-113">Create a Binding in Code</span></span>](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [<span data-ttu-id="81865-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="81865-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
