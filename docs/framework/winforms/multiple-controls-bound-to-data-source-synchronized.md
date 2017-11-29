---
title: "Porady: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2573f342530e59fa05e7f24342f251990b2ce47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="748b8-102">Porady: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych</span><span class="sxs-lookup"><span data-stu-id="748b8-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="748b8-103">Często, podczas pracy z powiązanie danych w formularzach systemu Windows, wielu formantów powiązanych z tym samym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="748b8-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="748b8-104">W niektórych przypadkach może być konieczne wykonać dodatkowe czynności, aby upewnić się, czy powiązania właściwości formantów pozostają zsynchronizowane ze sobą i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="748b8-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="748b8-105">Te kroki są niezbędne w dwóch sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="748b8-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="748b8-106">Jeśli źródło danych nie implementuje <xref:System.ComponentModel.IBindingList>i w związku z tym Generowanie <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span><span class="sxs-lookup"><span data-stu-id="748b8-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="748b8-107">Jeśli źródło danych implementuje <xref:System.ComponentModel.IEditableObject>.</span><span class="sxs-lookup"><span data-stu-id="748b8-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="748b8-108">W pierwszym przypadku można użyć <xref:System.Windows.Forms.BindingSource> można powiązać źródła danych do kontrolek.</span><span class="sxs-lookup"><span data-stu-id="748b8-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="748b8-109">W drugim przypadku należy użyć <xref:System.Windows.Forms.BindingSource> i obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń i wywołanie <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> na skojarzonym <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="748b8-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="748b8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="748b8-110">Example</span></span>  
 <span data-ttu-id="748b8-111">W poniższym przykładzie pokazano, jak powiązanie formantów trzy — dwa kontrolki pola tekstowego i <xref:System.Windows.Forms.DataGridView> kontroli — w tej samej kolumnie w <xref:System.Data.DataSet> przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="748b8-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="748b8-112">W tym przykładzie pokazano, jak obsługiwać <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzeń i upewnij się, że po zmianie wartości tekstowej pola tekstowego, okno dodatkowy tekst i <xref:System.Windows.Forms.DataGridView> formantu są aktualizowane przy użyciu poprawnej wartości.</span><span class="sxs-lookup"><span data-stu-id="748b8-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="748b8-113">W przykładzie użyto <xref:System.Windows.Forms.BindingSource> można powiązać źródła danych i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="748b8-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="748b8-114">Alternatywnie powiązanie formantów bezpośrednio ze źródłem danych i pobierania <xref:System.Windows.Forms.BindingManagerBase> dla powiązania z formularza <xref:System.Windows.Forms.Control.BindingContext%2A> , a następnie obsługi <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> zdarzenia dla <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="748b8-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="748b8-115">Na przykład jak to zrobić, zobacz stronę pomocy <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> zdarzenie <xref:System.Windows.Forms.BindingManagerBase>.</span><span class="sxs-lookup"><span data-stu-id="748b8-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="748b8-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="748b8-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="748b8-117">W tym przykładzie kodu wymaga</span><span class="sxs-lookup"><span data-stu-id="748b8-117">This code example requires</span></span>  
  
-   <span data-ttu-id="748b8-118">Odwołuje się do <xref:System>, <xref:System.Windows.Forms>, i <xref:System.Drawing> zestawów.</span><span class="sxs-lookup"><span data-stu-id="748b8-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="748b8-119">Formularz z <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń i wywołanie `InitializeControlsAndDataSource` metody w przykładzie z formularza <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="748b8-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748b8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="748b8-120">See Also</span></span>  
 [<span data-ttu-id="748b8-121">Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="748b8-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [<span data-ttu-id="748b8-122">Powiadomienie o zmianie w powiązaniu danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="748b8-122">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="748b8-123">Interfejsy dotyczące powiązania danych</span><span class="sxs-lookup"><span data-stu-id="748b8-123">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [<span data-ttu-id="748b8-124">Powiązanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="748b8-124">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
