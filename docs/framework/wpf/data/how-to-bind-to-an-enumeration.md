---
title: Jak powiązać z wyliczeniem
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 921f15a32eeb5ccb20e879466fcfee3233bbd29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="2ea73-102">Jak powiązać z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="2ea73-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="2ea73-103">W tym przykładzie pokazano, jak powiązać z wyliczeniem przez powiązanie do metody GetValues wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2ea73-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ea73-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ea73-104">Example</span></span>  
 <span data-ttu-id="2ea73-105">W poniższym przykładzie <xref:System.Windows.Controls.ListBox> Wyświetla listę <xref:System.Windows.HorizontalAlignment> wartości wyliczenia za pośrednictwem powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="2ea73-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="2ea73-106"><xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button> są powiązane w taki sposób, że można zmienić <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość właściwości <xref:System.Windows.Controls.Button> , wybierając wartość w <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="2ea73-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="2ea73-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ea73-107">See Also</span></span>  
 [<span data-ttu-id="2ea73-108">Powiązywanie z metodą</span><span class="sxs-lookup"><span data-stu-id="2ea73-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [<span data-ttu-id="2ea73-109">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="2ea73-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="2ea73-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="2ea73-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
