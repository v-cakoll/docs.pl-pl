---
title: "Jak ozdobić elementy podrzędne panelu"
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
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d30e9e5ac15f48dabf983123ba007674a14626d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="9ce8d-102">Jak ozdobić elementy podrzędne panelu</span><span class="sxs-lookup"><span data-stu-id="9ce8d-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="9ce8d-103">W tym przykładzie pokazano, jak programowo powiązać modułu definiowania układu kodu do podrzędnych określonej <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="9ce8d-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce8d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ce8d-104">Example</span></span>  
 <span data-ttu-id="9ce8d-105">Aby powiązać modułu definiowania układu kodu do elementów podrzędnych <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9ce8d-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9ce8d-106">Zadeklaruj nową <xref:System.Windows.Documents.AdornerLayer> obiekt i wywołanie `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody do znalezienia warstwy modułu definiowania układu kodu dla elementu, którego elementy podrzędne mają być adorned.</span><span class="sxs-lookup"><span data-stu-id="9ce8d-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="9ce8d-107">Wyliczenia elementów podrzędnych elementu nadrzędnego i wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu do każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="9ce8d-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="9ce8d-108">Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej) do elementów podrzędnych <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="9ce8d-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="9ce8d-109">Przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać modułu definiowania układu kodu do innego elementu nie jest obecnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="9ce8d-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce8d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ce8d-110">See Also</span></span>  
 [<span data-ttu-id="9ce8d-111">Omówienie modułu definiowania układu kodu</span><span class="sxs-lookup"><span data-stu-id="9ce8d-111">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
