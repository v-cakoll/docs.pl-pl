---
title: Jak wyczyścić powiązania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458879"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="ffd18-102">Jak wyczyścić powiązania</span><span class="sxs-lookup"><span data-stu-id="ffd18-102">How to: Clear Bindings</span></span>
<span data-ttu-id="ffd18-103">Ten przykład pokazuje, jak wyczyścić powiązania z obiektu.</span><span class="sxs-lookup"><span data-stu-id="ffd18-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffd18-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ffd18-104">Example</span></span>  
 <span data-ttu-id="ffd18-105">Aby usunąć powiązanie z pojedynczej właściwości obiektu, wywołaj <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ffd18-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="ffd18-106">Poniższy przykład usuwa powiązanie z <xref:System.Windows.Controls.TextBlock.TextProperty> obiektu "<xref:System.Windows.Controls.TextBlock>".</span><span class="sxs-lookup"><span data-stu-id="ffd18-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="ffd18-107">Wyczyszczenie powiązania usuwa powiązanie, tak aby wartość właściwości Dependency była zmieniana na niezależnie od powiązania.</span><span class="sxs-lookup"><span data-stu-id="ffd18-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="ffd18-108">Ta wartość może być wartością domyślną, dziedziczona wartością lub wartością z powiązania szablonu danych.</span><span class="sxs-lookup"><span data-stu-id="ffd18-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="ffd18-109">Aby wyczyścić powiązania ze wszystkimi możliwymi właściwościami obiektu, użyj <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="ffd18-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd18-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffd18-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="ffd18-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="ffd18-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ffd18-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ffd18-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
