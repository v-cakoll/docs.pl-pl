---
title: Jak zdefiniować pióro
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
ms.openlocfilehash: 7c5be5eff06df55e465f3e34646ba1c34e8b7e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559867"
---
# <a name="how-to-define-a-pen"></a><span data-ttu-id="e4cd6-102">Jak zdefiniować pióro</span><span class="sxs-lookup"><span data-stu-id="e4cd6-102">How to: Define a Pen</span></span>
<span data-ttu-id="e4cd6-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Media.Pen> do konspektu kształtu.</span><span class="sxs-lookup"><span data-stu-id="e4cd6-103">This example shows how use a <xref:System.Windows.Media.Pen> to outline a shape.</span></span> <span data-ttu-id="e4cd6-104">Aby utworzyć prosty <xref:System.Windows.Media.Pen>, wystarczy określić jego <xref:System.Windows.Media.Pen.Thickness%2A> i <xref:System.Windows.Media.Pen.Brush%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4cd6-104">To create a simple <xref:System.Windows.Media.Pen>, you need only specify its <xref:System.Windows.Media.Pen.Thickness%2A> and <xref:System.Windows.Media.Pen.Brush%2A>.</span></span> <span data-ttu-id="e4cd6-105">Można tworzyć bardziej złożone pióra przez określenie <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, i <xref:System.Windows.Media.Pen.EndLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4cd6-105">You can create more complex pen's by specifying a <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, and <xref:System.Windows.Media.Pen.EndLineCap%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4cd6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4cd6-106">Example</span></span>  
 <span data-ttu-id="e4cd6-107">W poniższym przykładzie użyto <xref:System.Windows.Media.Pen> do konspektu kształtu zdefiniowane przez <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="e4cd6-107">The following example uses a <xref:System.Windows.Media.Pen> to outline a shape defined by a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 <span data-ttu-id="e4cd6-108">![Tworzy opisanych przez pióro](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")</span><span class="sxs-lookup"><span data-stu-id="e4cd6-108">![Outlines produces by a Pen](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")</span></span>  
<span data-ttu-id="e4cd6-109">Obiekt GeometryDrawing zawierający</span><span class="sxs-lookup"><span data-stu-id="e4cd6-109">A GeometryDrawing</span></span>
