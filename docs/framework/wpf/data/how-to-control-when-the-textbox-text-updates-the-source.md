---
title: "Jak kontrolować kiedy tekst TextBox aktualizuje źródło"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c503eb3300aba4a44c5a013c62942e7a171ae96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="99a1a-102">Jak kontrolować kiedy tekst TextBox aktualizuje źródło</span><span class="sxs-lookup"><span data-stu-id="99a1a-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="99a1a-103">W tym temacie opisano sposób użycia <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwość, aby kontrolować czas powiązania źródła aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="99a1a-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="99a1a-104">Temat używa <xref:System.Windows.Controls.TextBox> formant jako przykład.</span><span class="sxs-lookup"><span data-stu-id="99a1a-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99a1a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="99a1a-105">Example</span></span>  
 <span data-ttu-id="99a1a-106"><xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Właściwość ma wartość domyślną <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="99a1a-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="99a1a-107">Oznacza to, czy aplikacja ma <xref:System.Windows.Controls.TextBox> z z danymi <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> właściwości, wpisz w <xref:System.Windows.Controls.TextBox> nie zaktualizować źródła do <xref:System.Windows.Controls.TextBox> traci fokus (na przykład po kliknięciu od <xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="99a1a-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="99a1a-108">Jeśli chcesz, aby źródło, aby pobrać zaktualizowane jako wpisywania, ustaw <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> powiązania <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="99a1a-108">If you want the source to get updated as you are typing, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="99a1a-109">W poniższym przykładzie `Text` właściwości obu <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> są powiązane z tą samą właściwością źródła.</span><span class="sxs-lookup"><span data-stu-id="99a1a-109">In the following example, the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="99a1a-110"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość <xref:System.Windows.Controls.TextBox> powiązania ma ustawioną wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="99a1a-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 <span data-ttu-id="99a1a-111">W związku z tym <xref:System.Windows.Controls.TextBlock> pokazuje tego samego tekstu (z powodu zmiany pliku źródłowego), jako użytkownik wprowadzi tekst do <xref:System.Windows.Controls.TextBox>, jak pokazano na poniższym zrzucie ekranu przykładu:</span><span class="sxs-lookup"><span data-stu-id="99a1a-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="99a1a-112">![Zrzut ekranu przedstawiający przykład powiązania danych proste](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="99a1a-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="99a1a-113">Jeśli masz okna dialogowego lub formularza można edytować użytkownika, a chcesz mają być odroczone aktualizacje źródłowego, dopóki użytkownik nie zakończy Edycja pól i kliknie przycisk "OK", można ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości powiązania do <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="99a1a-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="99a1a-114">Podczas ustawiania <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> do wartości <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, wartość źródła zmienia tylko, gdy aplikacja wywołuje <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99a1a-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="99a1a-115">Poniższy przykład przedstawia sposób wywołania <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> dla `itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="99a1a-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="99a1a-116">Użyj tę samą metodę dla właściwości inne formanty, ale należy pamiętać, że inne właściwości mają domyślnie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="99a1a-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="99a1a-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="99a1a-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99a1a-118"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość dotyczy źródło aktualizacji i w związku z tym dotyczy tylko <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania.</span><span class="sxs-lookup"><span data-stu-id="99a1a-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="99a1a-119">Aby uzyskać <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania do pracy źródła obiektu konieczność zapewnienia powiadomienia o zmianie właściwości.</span><span class="sxs-lookup"><span data-stu-id="99a1a-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="99a1a-120">Może się odwoływać do próbek wymienione w tym temacie, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="99a1a-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="99a1a-121">Ponadto można przyjrzeć się [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="99a1a-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a1a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99a1a-122">See Also</span></span>  
 [<span data-ttu-id="99a1a-123">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="99a1a-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
