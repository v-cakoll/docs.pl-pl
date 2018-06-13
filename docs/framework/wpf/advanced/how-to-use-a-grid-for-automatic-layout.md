---
title: Jak użyć siatki do automatycznego układu
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 6ea0b64af07924867c2de97baf5a81f8e8da6a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544625"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="9b6f3-102">Jak użyć siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="9b6f3-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="9b6f3-103">W tym przykładzie przedstawiono sposób użycia siatki w ujęciu automatyczny układ do tworzenia aplikacji lokalizowalny.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="9b6f3-104">Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być czasochłonne procesu.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="9b6f3-105">Często wiadomość dla lokalizatorów należy zmieniać rozmiar i położenia elementów oprócz tłumaczenie tekstu.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="9b6f3-106">W przeszłości każdego języka, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="9b6f3-107">Teraz z funkcjami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementów pozwalających ograniczyć potrzebę dostosowania.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="9b6f3-108">Podejście do pisania aplikacji, które mogą być łatwo zmieniono rozmiar i zmienionym jest nazywany `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="9b6f3-109">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie pokazano, używając siatka do umieszczenia niektórych przycisków i tekst.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="9b6f3-110">Należy zauważyć, że ustawiono wysokość i szerokość komórek `Auto`; w związku z tym komórki, która zawiera przycisk Obraz jest dopasowywany obrazu.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="9b6f3-111">Ponieważ <xref:System.Windows.Controls.Grid> elementu można dostosować do jego zawartości, może być przydatne przy uwzględnieniu automatyczny układ podejście do projektowania aplikacji, które może być lokalizowany.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b6f3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b6f3-112">Example</span></span>  
 <span data-ttu-id="9b6f3-113">Poniższy przykład przedstawia użycie siatki.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="9b6f3-114">Na poniższym rysunku przedstawiono dane wyjściowe przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="9b6f3-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="9b6f3-115">![Przykład siatka](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="9b6f3-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="9b6f3-116">Siatka</span><span class="sxs-lookup"><span data-stu-id="9b6f3-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b6f3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b6f3-117">See Also</span></span>  
 [<span data-ttu-id="9b6f3-118">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="9b6f3-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="9b6f3-119">Używanie automatycznego układu do utworzenia przycisku</span><span class="sxs-lookup"><span data-stu-id="9b6f3-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
