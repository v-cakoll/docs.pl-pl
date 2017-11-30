---
title: "Jak wyczyścić powiązania"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f8e009d00960f40abcd3c3913a15fa51f1be4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="01687-102">Jak wyczyścić powiązania</span><span class="sxs-lookup"><span data-stu-id="01687-102">How to: Clear Bindings</span></span>
<span data-ttu-id="01687-103">W tym przykładzie pokazano, jak można wyczyścić powiązania z obiektu.</span><span class="sxs-lookup"><span data-stu-id="01687-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01687-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="01687-104">Example</span></span>  
 <span data-ttu-id="01687-105">Aby usunąć powiązanie z poszczególnych właściwości w obiekcie, należy wywołać <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="01687-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="01687-106">Poniższy przykład umożliwia usunięcie powiązania z <xref:System.Windows.Controls.TextBlock.TextProperty> z *tekst*, <xref:System.Windows.Controls.TextBlock> obiektu.</span><span class="sxs-lookup"><span data-stu-id="01687-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="01687-107">Wyczyszczenie powiązania usuwa powiązanie tak, aby wartość właściwości zależności jest zmieniana na dowolnym byłoby bez powiązania.</span><span class="sxs-lookup"><span data-stu-id="01687-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="01687-108">Ta wartość może być wartość domyślną, dziedziczona wartość lub wartość z zakresu od powiązanie szablonu danych.</span><span class="sxs-lookup"><span data-stu-id="01687-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="01687-109">Aby wyczyścić wiązania ze wszystkich możliwych właściwości w obiekcie, należy użyć <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="01687-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01687-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01687-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="01687-111">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="01687-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="01687-112">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="01687-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
