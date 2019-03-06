---
title: 'Instrukcje: Wyczyść powiązania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8bffc34864a2bf929bcbed09f16eac282e1ba2a5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360237"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="fdec8-102">Instrukcje: Wyczyść powiązania</span><span class="sxs-lookup"><span data-stu-id="fdec8-102">How to: Clear Bindings</span></span>
<span data-ttu-id="fdec8-103">W tym przykładzie pokazano, jak wyczyścić powiązania z obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdec8-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdec8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdec8-104">Example</span></span>  
 <span data-ttu-id="fdec8-105">Aby wyczyścić powiązania z pojedynczej właściwości obiektu, wywołaj <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fdec8-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="fdec8-106">Poniższy przykład umożliwia usunięcie powiązania z <xref:System.Windows.Controls.TextBlock.TextProperty> z *kwerend*, <xref:System.Windows.Controls.TextBlock> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdec8-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="fdec8-107">Wyczyszczenie powiązanie powoduje usunięcie powiązania, dlatego, że wartość właściwości zależności jest zmieniana na dowolnie byłoby bez powiązania.</span><span class="sxs-lookup"><span data-stu-id="fdec8-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="fdec8-108">Ta wartość może być wartość domyślną, odziedziczona wartość lub wartość z zakresu od powiązanie szablonu danych.</span><span class="sxs-lookup"><span data-stu-id="fdec8-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="fdec8-109">Aby wyczyścić powiązania ze wszystkich możliwych właściwości do obiektu, należy użyć <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdec8-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdec8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdec8-110">See also</span></span>
- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="fdec8-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="fdec8-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="fdec8-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="fdec8-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
