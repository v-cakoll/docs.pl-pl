---
title: Jak pobrać obiekt wiążący z powiązanej własności docelowej
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: cf2ddc93a7c46ee6956d2731a786289f64086360
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976422"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="605b9-102">Jak pobrać obiekt wiążący z powiązanej własności docelowej</span><span class="sxs-lookup"><span data-stu-id="605b9-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="605b9-103">Ten przykład pokazuje, jak uzyskać obiekt powiązania z właściwości docelowej powiązanej z danymi.</span><span class="sxs-lookup"><span data-stu-id="605b9-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>

## <a name="example"></a><span data-ttu-id="605b9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="605b9-104">Example</span></span>
 <span data-ttu-id="605b9-105">Aby uzyskać <xref:System.Windows.Data.Binding> obiekt, można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="605b9-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> <span data-ttu-id="605b9-106">Należy określić właściwość zależności dla powiązania, ponieważ jest możliwe, że więcej niż jedna właściwość obiektu docelowego używa powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="605b9-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>

 <span data-ttu-id="605b9-107">Alternatywnie możesz uzyskać <xref:System.Windows.Data.BindingExpression> a następnie pobrać wartość właściwości <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="605b9-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>

 <span data-ttu-id="605b9-108">Aby zapoznać się z kompletnym przykładem, zobacz [przykładowe sprawdzanie poprawności powiązań](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="605b9-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>

> [!NOTE]
> <span data-ttu-id="605b9-109">Jeśli powiązanie jest <xref:System.Windows.Data.MultiBinding>, użyj <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="605b9-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="605b9-110">Jeśli jest to <xref:System.Windows.Data.PriorityBinding>, użyj <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="605b9-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="605b9-111">Jeśli nie masz pewności, czy właściwość docelowa jest powiązana przy użyciu <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>lub <xref:System.Windows.Data.PriorityBinding>, możesz użyć <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="605b9-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="605b9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="605b9-112">See also</span></span>

- [<span data-ttu-id="605b9-113">Tworzenie powiązania w kodzie</span><span class="sxs-lookup"><span data-stu-id="605b9-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="605b9-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="605b9-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
