---
title: 'Instrukcje: Zastosuj wiele przekształceń do obiektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 19fc87f04ca111f1fd0b6d7a4784fd96b464eb22
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363670"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="5fa55-102">Instrukcje: Zastosuj wiele przekształceń do obiektu</span><span class="sxs-lookup"><span data-stu-id="5fa55-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="5fa55-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.TransformGroup> do grupy co najmniej dwóch <xref:System.Windows.Media.Transform> obiektów do pojedynczego złożonego <xref:System.Windows.Media.Transform>.</span><span class="sxs-lookup"><span data-stu-id="5fa55-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa55-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fa55-104">Example</span></span>  
 <span data-ttu-id="5fa55-105">W poniższym przykładzie użyto <xref:System.Windows.Media.TransformGroup> do zastosowania <xref:System.Windows.Media.ScaleTransform> i <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="5fa55-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5fa55-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fa55-106">See also</span></span>
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="5fa55-107">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="5fa55-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="5fa55-108">Przykładowe transformacje 2-D</span><span class="sxs-lookup"><span data-stu-id="5fa55-108">2-D Transforms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=158252)
