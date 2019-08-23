---
title: 'Instrukcje: Pobieranie obiektu wiążącego z powiązanej własności docelowej'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965433"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="ea03a-102">Instrukcje: Pobieranie obiektu wiążącego z powiązanej własności docelowej</span><span class="sxs-lookup"><span data-stu-id="ea03a-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="ea03a-103">Ten przykład pokazuje, jak uzyskać obiekt powiązania z właściwości docelowej powiązanej z danymi.</span><span class="sxs-lookup"><span data-stu-id="ea03a-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea03a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea03a-104">Example</span></span>  
 <span data-ttu-id="ea03a-105">Aby pobrać obiekt, <xref:System.Windows.Data.Binding> można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ea03a-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> <span data-ttu-id="ea03a-106">Należy określić właściwość zależności dla powiązania, ponieważ jest możliwe, że więcej niż jedna właściwość obiektu docelowego używa powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="ea03a-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="ea03a-107">Alternatywnie możesz uzyskać <xref:System.Windows.Data.BindingExpression> wartość <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> właściwości, a następnie ją pobrać.</span><span class="sxs-lookup"><span data-stu-id="ea03a-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="ea03a-108">Aby zapoznać się z kompletnym przykładem, zobacz [przykładowe sprawdzanie poprawności powiązań](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="ea03a-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea03a-109">Jeśli powiązanie to <xref:System.Windows.Data.MultiBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea03a-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="ea03a-110">Jeśli jest <xref:System.Windows.Data.PriorityBinding>, użyj <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea03a-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="ea03a-111">Jeśli nie masz pewności, czy właściwość docelowa jest powiązana <xref:System.Windows.Data.Binding>przy użyciu <xref:System.Windows.Data.MultiBinding>, a lub <xref:System.Windows.Data.PriorityBinding>a, możesz użyć <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea03a-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea03a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea03a-112">See also</span></span>

- [<span data-ttu-id="ea03a-113">Tworzenie powiązania w kodzie</span><span class="sxs-lookup"><span data-stu-id="ea03a-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="ea03a-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ea03a-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
