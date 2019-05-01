---
title: 'Instrukcje: Używanie siatki do automatycznego układu'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 590ad7292fea572b20ccaa09ce2886724e004a6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052407"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="e8e60-102">Instrukcje: Używanie siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="e8e60-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="e8e60-103">W tym przykładzie opisano, jak użyć siatki w ujęciu automatycznego układu do tworzenia aplikacji możliwych do zlokalizowania.</span><span class="sxs-lookup"><span data-stu-id="e8e60-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="e8e60-104">Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być procesem dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="e8e60-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="e8e60-105">Często lokalizatorzy muszą zmieniać rozmiar i zmienić położenie elementów oprócz tłumaczenie tekstu.</span><span class="sxs-lookup"><span data-stu-id="e8e60-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="e8e60-106">W przeszłości każdego z języków, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań.</span><span class="sxs-lookup"><span data-stu-id="e8e60-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="e8e60-107">Teraz z możliwościami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementy, które zmniejszyć zapotrzebowanie na dostosowanie.</span><span class="sxs-lookup"><span data-stu-id="e8e60-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="e8e60-108">Nosi nazwę podejścia do pisania aplikacji, które mogą być łatwiejsze zmieniono rozmiar i zmienionym `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="e8e60-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="e8e60-109">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykład demonstruje użycie siatki, aby umieścić niektóre przyciski i tekst.</span><span class="sxs-lookup"><span data-stu-id="e8e60-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="e8e60-110">Należy zauważyć, że wysokość i szerokość komórek są ustawione na `Auto`; w związku z tym komórkę, która zawiera przycisk za pomocą obrazu jest dopasowywany obrazu.</span><span class="sxs-lookup"><span data-stu-id="e8e60-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="e8e60-111">Ponieważ <xref:System.Windows.Controls.Grid> elementu można dostosować do jego zawartości, może być przydatne podczas wykonywania metody automatycznego układu do projektowania aplikacji, które może być lokalizowana.</span><span class="sxs-lookup"><span data-stu-id="e8e60-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8e60-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8e60-112">Example</span></span>  
 <span data-ttu-id="e8e60-113">Poniższy przykład pokazuje, jak użyć siatki.</span><span class="sxs-lookup"><span data-stu-id="e8e60-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="e8e60-114">Na poniższym rysunku przedstawiono dane wyjściowe przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="e8e60-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="e8e60-115">![Przykład Grid](./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="e8e60-115">![Grid example](./media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="e8e60-116">Siatka</span><span class="sxs-lookup"><span data-stu-id="e8e60-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e60-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8e60-117">See also</span></span>

- [<span data-ttu-id="e8e60-118">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="e8e60-118">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="e8e60-119">Używanie automatycznego układu do utworzenia przycisku</span><span class="sxs-lookup"><span data-stu-id="e8e60-119">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
