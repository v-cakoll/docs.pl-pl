---
title: 'Instrukcje: Dostosuj rozmiar miniatury na ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 30fc72e3f0631b01777bf058c7a7470cc376a547
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354326"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="6be5b-102">Instrukcje: Dostosuj rozmiar miniatury na ScrollBar</span><span class="sxs-lookup"><span data-stu-id="6be5b-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="6be5b-103">W tym temacie wyjaśniono, jak ustawić <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar> o stałym rozmiarze i jak określić minimalny rozmiar <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="6be5b-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6be5b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6be5b-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="6be5b-105">Opis</span><span class="sxs-lookup"><span data-stu-id="6be5b-105">Description</span></span>  
 <span data-ttu-id="6be5b-106">Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.ScrollBar> zawierający <xref:System.Windows.Controls.Primitives.Thumb> o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="6be5b-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="6be5b-107">Przykład ustawia <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> właściwość <xref:System.Windows.Controls.Primitives.Thumb> do <xref:System.Double.NaN> i Ustawia wysokość <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="6be5b-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="6be5b-108">Aby utworzyć poziomej <xref:System.Windows.Controls.Primitives.ScrollBar> za pomocą <xref:System.Windows.Controls.Primitives.Thumb> zawierającego stałej szerokości, Ustaw szerokość <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="6be5b-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="6be5b-109">Kod</span><span class="sxs-lookup"><span data-stu-id="6be5b-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="6be5b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6be5b-110">Description</span></span>  
 <span data-ttu-id="6be5b-111">Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.ScrollBar> zawierający <xref:System.Windows.Controls.Primitives.Thumb> przy użyciu minimalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="6be5b-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="6be5b-112">W przykładzie ustawiono wartość <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="6be5b-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="6be5b-113">Aby utworzyć poziomej <xref:System.Windows.Controls.Primitives.ScrollBar> z <xref:System.Windows.Controls.Primitives.Thumb> zawierający minimalnej szerokości, ustaw <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="6be5b-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="6be5b-114">Kod</span><span class="sxs-lookup"><span data-stu-id="6be5b-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6be5b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6be5b-115">See also</span></span>
- [<span data-ttu-id="6be5b-116">ScrollBar — style i szablony</span><span class="sxs-lookup"><span data-stu-id="6be5b-116">ScrollBar Styles and Templates</span></span>](scrollbar-styles-and-templates.md)
