---
title: Jak użyć załączonych właściwości kanwy, aby ustawić położenie elementów podrzędnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 89327b834dfd71c0a7420eb42a598b98cdb5e9d8
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513404"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="0145b-102">Jak użyć załączonych właściwości kanwy, aby ustawić położenie elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="0145b-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="0145b-103">W tym przykładzie pokazano, jak użyć załączonych właściwości <xref:System.Windows.Controls.Canvas> położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0145b-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0145b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0145b-104">Example</span></span>  
 <span data-ttu-id="0145b-105">W poniższym przykładzie dodano cztery <xref:System.Windows.Controls.Button> jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0145b-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0145b-106">Każdy element jest reprezentowany przez <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, i <xref:System.Windows.Controls.Canvas.Top%2A>.</span><span class="sxs-lookup"><span data-stu-id="0145b-106">Each element is represented by a <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span>
<span data-ttu-id="0145b-107">Każdy <xref:System.Windows.Controls.Button> jest umieszczony względem nadrzędnego <xref:System.Windows.Controls.Canvas> i zgodnie z jej wartością właściwości przypisane.</span><span class="sxs-lookup"><span data-stu-id="0145b-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0145b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0145b-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="0145b-109">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="0145b-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="0145b-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0145b-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="0145b-111">Przegląd właściwości dołączonych</span><span class="sxs-lookup"><span data-stu-id="0145b-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
