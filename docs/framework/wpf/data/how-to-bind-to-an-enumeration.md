---
title: 'Instrukcje: Powiązywanie z wyliczeniem'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021014"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="f950d-102">Instrukcje: Powiązywanie z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="f950d-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="f950d-103">W tym przykładzie pokazano, jak powiązać z wyliczeniem przez powiązanie metoda GetValues wyliczania.</span><span class="sxs-lookup"><span data-stu-id="f950d-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f950d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f950d-104">Example</span></span>  
 <span data-ttu-id="f950d-105">W poniższym przykładzie <xref:System.Windows.Controls.ListBox> wyświetlana jest lista <xref:System.Windows.HorizontalAlignment> wartości wyliczenia za pomocą powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="f950d-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="f950d-106"><xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button> są powiązane w taki sposób, że można zmienić <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość właściwości <xref:System.Windows.Controls.Button> , wybierając wartość w <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="f950d-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="f950d-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f950d-107">See also</span></span>

- [<span data-ttu-id="f950d-108">Powiązywanie z metodą</span><span class="sxs-lookup"><span data-stu-id="f950d-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="f950d-109">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="f950d-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="f950d-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f950d-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
