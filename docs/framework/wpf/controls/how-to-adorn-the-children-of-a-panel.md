---
title: 'Instrukcje: Zdób elementy podrzędne panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: ae039243ded93eb2bc7f85f9f07fad1dbe0eac2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544981"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="16c95-102">Instrukcje: Zdób elementy podrzędne panelu</span><span class="sxs-lookup"><span data-stu-id="16c95-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="16c95-103">W tym przykładzie pokazano, jak programowo powiązać moduł definiowania układu z element podrzędny określonego <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="16c95-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16c95-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="16c95-104">Example</span></span>  
 <span data-ttu-id="16c95-105">Aby powiązać moduł definiowania układu z elementami podrzędnymi <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="16c95-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="16c95-106">Zadeklaruj nowy <xref:System.Windows.Documents.AdornerLayer> obiektu, a następnie wywołać `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody do znalezienia warstwy moduł definiowania układu dla elementu, którego elementy podrzędne, które mają być powiązany.</span><span class="sxs-lookup"><span data-stu-id="16c95-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="16c95-107">Wyliczyć elementy podrzędne elementu nadrzędnego, a wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="16c95-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="16c95-108">Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), z elementami podrzędnymi <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="16c95-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="16c95-109">Za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać moduł definiowania układu z innego elementu nie jest obecnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="16c95-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c95-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16c95-110">See also</span></span>
- [<span data-ttu-id="16c95-111">Moduły indeksowania układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="16c95-111">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
