---
title: 'Instrukcje: Powiąż z wyliczeniem'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: db7b02a961c148bbdc31b05e7c71ea5b5d301c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586569"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="22e92-102">Instrukcje: Powiąż z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="22e92-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="22e92-103">W tym przykładzie pokazano, jak powiązać z wyliczeniem przez powiązanie metoda GetValues wyliczania.</span><span class="sxs-lookup"><span data-stu-id="22e92-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22e92-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="22e92-104">Example</span></span>  
 <span data-ttu-id="22e92-105">W poniższym przykładzie <xref:System.Windows.Controls.ListBox> wyświetlana jest lista <xref:System.Windows.HorizontalAlignment> wartości wyliczenia za pomocą powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="22e92-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="22e92-106"><xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button> są powiązane w taki sposób, że można zmienić <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość właściwości <xref:System.Windows.Controls.Button> , wybierając wartość w <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="22e92-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="22e92-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22e92-107">See also</span></span>
- [<span data-ttu-id="22e92-108">Powiązywanie z metodą</span><span class="sxs-lookup"><span data-stu-id="22e92-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)
- [<span data-ttu-id="22e92-109">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="22e92-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="22e92-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="22e92-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
