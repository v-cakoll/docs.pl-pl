---
title: "Jak użyć siatki do automatycznego układu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d18563c44381a276d15996dff3f9552c46833b4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="f72d7-102">Jak użyć siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="f72d7-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="f72d7-103">W tym przykładzie przedstawiono sposób użycia siatki w ujęciu automatyczny układ do tworzenia aplikacji lokalizowalny.</span><span class="sxs-lookup"><span data-stu-id="f72d7-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="f72d7-104">Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być czasochłonne procesu.</span><span class="sxs-lookup"><span data-stu-id="f72d7-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="f72d7-105">Często wiadomość dla lokalizatorów należy zmieniać rozmiar i położenia elementów oprócz tłumaczenie tekstu.</span><span class="sxs-lookup"><span data-stu-id="f72d7-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="f72d7-106">W przeszłości każdego języka, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań.</span><span class="sxs-lookup"><span data-stu-id="f72d7-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="f72d7-107">Teraz z funkcjami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementów pozwalających ograniczyć potrzebę dostosowania.</span><span class="sxs-lookup"><span data-stu-id="f72d7-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="f72d7-108">Podejście do pisania aplikacji, które mogą być łatwo zmieniono rozmiar i zmienionym jest nazywany `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="f72d7-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="f72d7-109">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie pokazano, używając siatka do umieszczenia niektórych przycisków i tekst.</span><span class="sxs-lookup"><span data-stu-id="f72d7-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="f72d7-110">Należy zauważyć, że ustawiono wysokość i szerokość komórek `Auto`; w związku z tym komórki, która zawiera przycisk Obraz jest dopasowywany obrazu.</span><span class="sxs-lookup"><span data-stu-id="f72d7-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="f72d7-111">Ponieważ <xref:System.Windows.Controls.Grid> elementu można dostosować do jego zawartości, może być przydatne przy uwzględnieniu automatyczny układ podejście do projektowania aplikacji, które może być lokalizowany.</span><span class="sxs-lookup"><span data-stu-id="f72d7-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72d7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f72d7-112">Example</span></span>  
 <span data-ttu-id="f72d7-113">Poniższy przykład przedstawia użycie siatki.</span><span class="sxs-lookup"><span data-stu-id="f72d7-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="f72d7-114">Na poniższym rysunku przedstawiono dane wyjściowe przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="f72d7-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="f72d7-115">![Przykład siatka](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="f72d7-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="f72d7-116">Siatka</span><span class="sxs-lookup"><span data-stu-id="f72d7-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72d7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f72d7-117">See Also</span></span>  
 [<span data-ttu-id="f72d7-118">Użyj automatycznego układu — omówienie</span><span class="sxs-lookup"><span data-stu-id="f72d7-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="f72d7-119">Umożliwia utworzenie przycisk Automatyczny układ</span><span class="sxs-lookup"><span data-stu-id="f72d7-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
